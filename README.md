# Image Segmentation of Brain MRI

This involves training a Unet Model to segment and predict masks from Brain MRI images. 

Data: https://www.kaggle.com/mateuszbuda/lgg-mri-segmentation

UNet model architecture:
1. Input - 128X128X1
2. Downward Layers
  - 2x Conv Layer - 128x128x64 (D1)
  - Max Pool - 64x64x64
  - Dropout  
  - 2x Conv Layer - 64x64x128 (D2)
  - Max Pool - 32x32x128
  - Dropout 
  - 2x Conv Layer - 32x32x256 (D3)
  - Max Pool - 16x16x256
  - Dropout 
  - 2x Conv Layer - 16x16x512 (D4)
  - Max Pool -8x8x512
  - Dropout 
  - 2x Conv Layer - 8x8x1024
3. Upward Layers
  - Conv Transpose - 16x16x1024 (U1)
  - Concatenate U1 + D4
  - Dropout
  - 2x Conv Layer - 16x16x1024
  - Conv Transpose - 32x32x512 (U2)
  - Concatenate U2 + D3
  - Dropout
  - 2x Conv Layer - 32x32x512
  - Conv Transpose - 64x64x256 (U3)
  - Concatenate U3 + D2
  - Dropout
  - 2x Conv Layer - 64x64x256
  - Conv Transpose - 128x128x128 (U4)
  - Concatenate U4 + D1
  - Dropout
  - 2x Conv Layer - 128x128x128
 4. Prediction layer using Sigmoid
  - Conv Layer - 128x128x1
