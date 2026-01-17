# Practical Implementation Report

## Task 1: Edge AI Prototype (Recyclable Item Classifier)

### 1. Project Overview

This project demonstrates the development of a lightweight image classification model designed to run on resource-constrained hardware. By using Edge AI, we eliminate the need for constant cloud connectivity, ensuring faster results and better data privacy.

### 2. Technical Implementation

Model Architecture: We utilized MobileNetV2, a specialized deep learning structure that uses depthwise separable convolutions to maintain high accuracy with a small memory footprint.

Optimization Technique: We applied Post-Training Quantization. This process converts the model’s internal weights from 32-bit floating points to 8-bit integers.

Result: This reduced the file size by approximately 4x and allows for much faster processing on CPU-based edge devices like the Raspberry Pi.

### 3. Deployment Steps

Train: The model is trained in a .ipynb environment using TensorFlow/Keras.

Convert: The model is saved as a .tflite file.

Deploy: The .tflite file is loaded onto the local device using the tflite-runtime library.

Inference: The local camera feeds images directly into the model for real-time classification.

## Task 2: AI-Driven IoT Concept (Smart Agriculture)

### 1. System Design

The goal of this system is to automate irrigation and provide predictive insights into crop health using a network of IoT sensors.

### 2. Hardware & Sensors

Soil Moisture: Measures water levels to trigger automated irrigation.

DHT22 Sensor: Tracks ambient Temperature and Humidity.

BH1750 (Lux): Monitors sunlight exposure to calculate photosynthesis potential.

NPK Sensor: Measures soil nutrients (Nitrogen, Phosphorus, Potassium).

### 3. AI Processing Logic

Edge Layer: A local gateway processes moisture data. If Moisture < 30%, the water pump is activated immediately without waiting for a cloud response.

Cloud Layer: All sensor data is aggregated and fed into a Random Forest Regressor model to predict the final Crop Yield (kg) at the end of the season.

### 4. Data Flow Diagram

The following diagram illustrates the path from raw sensor data to actionable AI insights:

## Key Benefits of This Implementation

Real-time Response: Critical actions (like watering or trash sorting) happen in milliseconds.

Bandwidth Savings: Only analyzed metadata is sent to the cloud, rather than constant high-definition video or raw sensor streams.

Reliability: The system remains functional even if the farm or factory loses internet connectivity.
