✅ Explanation: How the Architecture Processes the Image  

The architecture diagram present in **Architecture.png** represents our hybrid feature fusion approach for soil classification. Below is a detailed breakdown of each component:  

🔷 Input Image  

- Accepts soil/non-soil images in various resolutions
   
- Handles diverse lighting conditions and backgrounds  

🔹 Dual Preprocessing  

- **ResNet Standardization**: Normalizes pixels using ResNet50's expected input range

- **EfficientNet Standardization**: Simultaneously prepares images for EfficientNet-B0

🟦 Feature Extraction  

- **ResNet50 Pathway**: Extracts 2048-D hierarchical spatial features
  
- **EfficientNet-B0 Pathway**: Generates 768-D texture-focused features
  
- **Feature Fusion**: Combines both into a 2816-D vector  

🟩 Dimensionality Reduction  

- **Standardization**: Centers features (μ=0, σ=1)
  
- **PCA**: Reduces to 500-600 components while preserving 95% variance
  
- **Whitening**: Decorrelates features for better SVM performance  

🟥 One-Class Classification  

- **One-Class SVM objective**  

🟪 Training Process  

- **Objective**: Learns decision boundary around soil features

🟪 Evaluation Metrics  

- **Primary**: F1-score (harmonic mean of precision/recall)

🟩 Results Output  

- Generates CSV with:
  
  - `image_id`
    
  - `prediction` (0=Non-Soil, 1=Soil)
