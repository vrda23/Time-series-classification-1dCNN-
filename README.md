# Time-series-classification-1dCNN-
Implementation of 1D-cNN architecture from the following paper: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8675938/

Detecting Coronary Artery Disease Using Rest Seismocardiography and Gyrocardiography

Abstract
In this study, we present a non-invasive solution to identify patients with coronary artery disease (CAD) defined as ⩾50% stenosis in at least one coronary artery. The solution is based on the analysis of linear acceleration (seismocardiogram, SCG) and angular velocity (gyrocardiogram, GCG) of the heart recorded in the x, y, and z directional axes from an accelerometer/gyroscope sensor mounted on the sternum. The database was collected from 310 individuals through a multicenter study. The time-frequency features extracted from each SCG and GCG data channel were fed to a one-dimensional Convolutional Neural Network (1D CNN) to train six separate classifiers. The results from different classifiers were later fused to estimate the CAD risk for each participant. The predicted CAD risk was validated against related results from angiography. The SCG z and SCG y classifiers showed better performance relative to the other models (p < 0.05) with the area under the curve (AUC) of 91%. The sensitivity range for CAD detection was 92–94% for the SCG models and 73–87% for the GCG models. Based on our findings, the SCG models achieved better performance in predicting the CAD risk compared to the GCG models; the model based on the combination of all SCG and GCG classifiers did not achieve higher performance relative to the other models. Moreover, these findings showed that the performance of the proposed 3-axial SCG/GCG solution based on recordings obtained during rest was comparable, or better than stress ECG. These data may indicate that 3-axial SCG/GCG could be used as a portable at-home CAD screening tool.


Model architecture
1D CNN Architecture An architecture based on the one-dimensional Convolutional Neural Network (1D CNN) was proposed for training the classifiers (Figure 3). The standard CNN, also called 2D CNN, was initially introduced as a deep learning architecture for analyzing image data. The CNN extracts the spatial features of the data by using sliding kernels. In 2D CNN, the kernels slide in two dimensions while the kernels in 1D CNN slide in one dimension. It makes the 1D CNN a powerful tool for analyzing time-series data which has spatial characteristics only in one dimension.
An external file that holds a picture, illustration, etc.
Object name is fphys-12-758727-g0003.jpg
Figure 3
1D CNN architecture proposed for training the classifiers.

The proposed model contained three convolutional blocks, two fully connected layers, and a Softmax layer as the output prediction layer. The convolutional block consisted of a convolutional layer, an activation layer with Rectified Linear Unit (ReLU) function, and a max-pooling layer. A batch normalization layer was added to the first convolutional block after ReLU activation to normalize the input layer. A dropout layer was applied to the second and third conventional blocks (Figure 3).

The first conventional layer had 32 filters, and the second and third conventional layers each had 16 filters. The kernel size in all layers was set to 10. The pooling layers with the kernel sizes of two were added to downsample the convolutional output. The output of conventional blocks was flattened to one long vector and passed through two fully connected layers. Each fully connected layer contained 1,000 nodes, a ReLU activation function, and a dropout layer of rate 0.5. The Softmax function in the last layer was used to estimate the prediction probability over the two classes of CAD and non-CAD.
NOTE: I changed the kernel size to 3
