# Automatic-Anomaly-Detection-in-the-Industrial-Process-
PyTorch model for 'Anomaly Detection in the Industrial Process' - using AutoEncoder 

# The model was trained using Tennessee Eastman Process Dataset
 * the dataset has a total of 480000 fault free samples (faultNumber=0)
 * each sample contains 52 values of different sensors (temperature, pressure, etc)
 * the model is trained only on the fault free data (data without defects)

<img width="1412" height="208" alt="nndataset" src="https://github.com/user-attachments/assets/eae53bc7-7748-47ee-b251-875bac0de258" />


# Model Neural Network - AutoEncoder
 * a basic AutoEncoder is used to train the model
 * the Encoder gradually goes from the original input of 52 values, to an output of 8 values (where only the key features survive)
 * the Decoder takes the output from the Encoder as input and tries to reconstruct the original 52 input

<img width="475" height="251" alt="autoencoder" src="https://github.com/user-attachments/assets/23de4e4e-7fc5-4a59-9bf7-261c8f44b769" />


# Anomaly Detection - Reconstruction Error
 * since the model was trained only on Free Fault data, we can pass a Faulty sample and make a prediction using the Reconstruction Error
 * we take the mean of our distribution +- 1 or 2 standard deviation, and establish an error range
 * the Faulty data will have a higher reconstruction error when passed through the model, which will not be in that error range
 * basically when the model has a high reconstruction error it detects that as an Anomaly

<img width="618" height="458" alt="rerror" src="https://github.com/user-attachments/assets/a5930237-e062-493e-9b46-07b1ba8d2901" />
