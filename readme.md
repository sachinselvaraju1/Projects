# My Projects

This repository contains two academic projects in the field of cybersecurity with Machine Learning : Malware Detection using CNN and Deep Learning Firewall. Please note that the code for both projects is confidential as it is part of my academic research.

## Malware Detection using Convolutional Neural Networks

The project is used in antivirus protection systems where traditional signature-based identifiers  are no longer effective to newly updated malwares. Since they are not cost effective and time  consuming, this project based on Convolutional Neural Networks (CNN) is proposed.  

This is a tool  that can detect an executable file whether it is a malware or an ordinary software, which is  developed upon CNN along with TensorFlow for the separation of malware types. As the  project title implies, the main aim of this project is to create a system for detecting malware  and securing the system. The project helps to identify a malware within seconds using CNN  techniques and avoid the longer waiting time.


### Backend

- **Language**: Python

- **Frameworks**: TensorFlow, Flask and Keras

### Frontend

- **Framework**: Flask

### Dataset

- **Name**: Malimg dataset from Kaggle

  - The Malimg Dataset contains 9339 malware images, belonging to 25 families/classes. The goal is to perform a multi-class classification of malware. Each file's raw data contains the hexadecimal representation of the file's binary content. These files are converted into PNG images and used as input for the Convolutional Neural Network (CNN).

### Architecture Diagram

![](/Diagrams/malwarearch.png)

### System Methodology

#### System Architecture 

The system architecture consists of several modules that work together to achieve malware detection. Below is a simplified description of the system methodology:

1.  Data Acquisition: Collect malware samples from Kaggle.
2.  Data Pre-processing: Convert malware binary files into images.
3.  Feature Engineering: Extract features from images for training.
4.  Model Training: Train the CNN model using the pre-processed data.
5.  Prediction: Use the trained model to predict and classify new malware samples.
6.  Web Interface: Create a web interface using Flask for user interaction and result visualization.

### Data Pre-processing

We obtain malware samples from Kaggle, which are executable files. These data should be converted into image files to be used in the Convolutional layers for further classification. For each file, the raw data contains the hexadecimal representation of the file's binary content. The goal is to convert those files into PNG images and use them as the input for our CNN.

Training Data Example: For example, the byte sequence: E4 C0 56 A3 D2 78 56 A3 FF, can be represented by the following matrix:

`E4 C0 56 A3
D2 78 56 A3
FF`

Gray Scale Image: The previous matrix will be transformed into a gray image where each box of the matrix will be a pixel in the image (degrees of Gray between 0 and 255).

Image of a Malware 128x128: This transformation results in an image of size 128x128 for each malware sample.

### Feature Engineering

Feature engineering is a machine learning technique that leverages data to create new variables that aren't in the training set. It can produce new features for both supervised and unsupervised learning, with the goal of simplifying and speeding up data transformations while also enhancing model accuracy. Feature engineering is required when working with machine learning models. Regardless of the data or architecture, a poor feature will have a direct impact on the model's performance.

### Model Training

A training model is a dataset that is used to train a machine learning algorithm. It consists of sample output data and the corresponding sets of input data that influence the output. The training model runs the input data through the algorithm to correlate the processed output against the sample output. This iterative process, called "model fitting," is crucial for modifying and improving the model. The accuracy of the training dataset or the validation dataset is critical for the precision of the model.

Convolutional Layer Structure:

-   Convolutional Layer: 30 filters, (3x3) kernel size
-   Max Pooling Layer: (2x2) pool size
-   Convolutional Layer: 15 filters, (3x3) kernel size
-   Max Pooling Layer: (2x2) pool size
-   Dropout Layer: Dropping 25% of neurons
-   Flatten Layer
-   Dense/Fully Connected Layer: 128 neurons, ReLU activation function
-   Dropout Layer: Dropping 50% of neurons
-   Dense/Fully Connected Layer: 50 neurons, Softmax activation function
-   Dense/Fully Connected Layer: num_class neurons, Softmax activation function

The input has a shape of [64x64x3]: [width x height x depth]. In our case, each malware is an RGB image.

### Creating CNN

We design a convolutional neural network to analyze the images and predict the maliciousness of a file. The CNN design includes considerations for image size, kernel size, number of kernels, and number of layers.

Architecture of CNN: From previous sections, we combine the best parameters to design our CNN: 2 hidden layers, 16 filters, and 64x64 images. The architecture of the network includes multiple conv2d layers grouped into two convolution layers, pooling layers, and possibly dropout layers. The flatten layer transforms the output into one long vector, which is then processed by a classification layer.

### Prediction

"Prediction" refers to the output of an algorithm after it has been trained on a historical dataset and applied to new data, forecasting the likelihood of a particular outcome, such as whether the given file is malware or a benign file.

### Web Interface using Flask Framework

Flask is a way for web servers to pass requests to web applications or frameworks. Flask relies on the WSGI external library to function, as well as the Jinja2 template engine. In this module, the processed model is connected to the Flask API, and a web interface is created to insert an executable file, which is the test data, to test whether the file is malware or a normal executable file.

### Illustrations

![](https://github.com/sachinselvaraju1/Projects/assets/170783877/210d3522-13ae-4417-9937-9486b57dd4b1)

![](https://github.com/sachinselvaraju1/Projects/assets/170783877/ca70bf85-8c22-4068-b128-4cd053e19256)

### Future Enhancements

** Real-Time Detection:** 
   -  Improve the framework to perform real-time malware detection and classification.
** Integration with Antivirus Software: **
   -  Integrate the model with existing antivirus software to enhance their detection capabilities.
** Additional Features: **
   -  Incorporate additional features such as behavior analysis and network traffic monitoring for more comprehensive malware detection.
** User Interface Improvements:**
   -  Improve the dashboard and user interface for better user experience and interaction.

-------------------------------------------------------------------------------------------------------------------------------------------------


## Deep Learning Firewall

The **Deep Learning Firewall** project focuses on developing a firewall system that uses deep learning algorithms to intelligently filter and block malicious network traffic. This project enhances traditional firewall capabilities by incorporating advanced machine learning techniques to predict and prevent cyber-attacks.

### Backend

- **Language**: Python

- **Frameworks**: TensorFlow, Flask and Keras

### Frontend

- **Framework**: Flask 

### Dataset

- **Name**: CSIC HTTP Attacks Dataset

### Model Architecture

![](/Diagrams/dlf.png)

### Modular Description

#### Data Pre-processing

- **Dataset**: HTTP DATASET CSIC 2010

  - Produced by the Spanish Research National Council (CSIC).

  - Summary: 36,000 normal traffic and over 25,000 malicious traffic.

  - Includes attacks such as SQL injection, buffer overflow, and information gathering queries.

- **Approach**:

  - The raw dataset contains HTTP requests with URL encoding.

  - Challenges include extracting useful features due to a large number of escape characters (`%`).

#### Model Training

- **Embedding Layer**:

  - Converts each letter of the input HTTP request sentence into a 128-dimensional vector.

- **Architecture**:

  - Characterized by significant dimensional reduction at the second max-pooling layer (498:1 at K=2).

  - Greatly reduces the number of fully connected (FC) elements in subsequent layers.

  - Reduces the size of GPU memory required.

#### Connection of WAF

- **Integration**:

  - The created model is connected with a sample web application using the Flask framework in Python.

  - A proxy is created between the model and the sample application to evaluate incoming requests.

#### Malicious Query Detection

- **Process**:

  - Malicious requests executed to the sample application are detected and blocked.

  - User IP addresses of malicious requests are logged and displayed in the WAF panel.

### Illustrations

Figure 1.1 Sample Web Application Output when applied normal request
![](/Diagrams/1.1.png)

Figure 1.2 Sample Web Application Output when applied malicious request
![](/Diagrams/1.2.png)

Figure 2.1 WAF Dashboard for the sample web application
![](/Diagrams/2.1.png)



### Future Extensions

**Intrusion Detection Systems (IDS)**:

  -  The WAF can be used as an IDS in a large-scale network to protect systems from major cyber attacks.

**Blockchain Protection**:

  - The firewall can be modified to act as an enhanced protection system for bitcoin mines and decentralized applications (DApps).

**Antivirus**:

  - Antivirus systems can use this model to classify different types of HTTP attacks that pose a threat to a computer and block the malicious actors.


---

Please note that the source code for this project is confidential and not publicly available, as it is part of my academic research. Feel free to explore the project description and reach out if you have any questions or need further assistance.
