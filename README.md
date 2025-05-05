### SMS Spam Detector
## Overview
SMS Spam Detector is a machine learning project that classifies SMS text messages as either “spam” or “ham” (not spam). The project uses the well-known SMS Spam Collection dataset to train and evaluate a text classification model. The final solution includes an interactive Gradio web interface for real-time message prediction.

## Project Goals
- Build an accurate, automated SMS spam classifier.
- Apply natural language processing (NLP) to extract features from SMS text.
- Deliver an interactive demo for real-time spam detection.
- Interpret model performance and discuss potential business applications.

## Data
- Source: SMSSpamCollection.csv
- Size: 5,574 SMS messages
  - Labels:
    - ham: Legitimate (non-spam) message
    - spam: Unwanted or unsolicited message

Sample:
| label | text_message                                                                                                                                                |
|-------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ham   | Go until jurong point, crazy.. Available only in bugis n great world la e buffet... Cine there got amore wat...                                             |
| ham   | Ok lar... Joking wif u oni...                                                                                                                               |
| spam  | Free entry in 2 a wkly comp to win FA Cup final tkts 21st May 2005. Text FA to 87121 to receive entry question(std txt rate)T&C's apply 08452810075over18's |
| ham   | U dun say so early hor... U c already then say...                                                                                                           |
| ham   | Nah I don't think he goes to usf, he lives around here though                                                                                               |

## Model Architecture and Rationale
The model is built using a scikit-learn Pipeline:
1. TF-IDF Vectorizer
    - Converts SMS text into numerical features based on word frequency and importance.
    - Removes English stop words to focus on the most meaningful content.
2. Linear Support Vector Classifier (LinearSVC)
    - Chosen for its efficiency and effectiveness in high-dimensional, sparse datasets typical for text classification.
    - Provides robust separation between spam and ham messages.

Rationale:
This pipeline is a proven, interpretable baseline for text classification, balancing accuracy, interpretability, and computational efficiency.

## Results
| Metric    | Value |
|-----------|-------|
| Accuracy  | ~98%  |
| Precision | ~97%  |
| Recall    | ~95%  |
| F1 Score  | ~96%  |

>Metrics are based on a 67/33 train/test split of the SMS Spam Collection dataset. Actual results may vary slightly depending on random seed and preprocessing.

Interpretation:
- The model achieves high accuracy and recall, meaning it correctly identifies most spam messages while minimizing false positives.
- This makes it reliable for filtering spam without blocking legitimate messages.

## Business Application
Automated SMS spam detection has broad commercial value:
- Telecom Providers:
Block spam before it reaches customers, reducing complaints and fraud risk.
- Messaging Apps:
Enhance user trust and experience by filtering unwanted messages.
- Enterprises:
Protect employees from phishing and malware sent via SMS.

A lightweight, accurate model like this can be integrated into SMS gateways, mobile apps, or backend services with minimal computational overhead.

## Usage
1. Clone the Repository
```git clone https://github.com/tenshimizu/sms_spam_detector.git cd sms_spam_detector```

2. Install Requirements
```pip install pandas scikit-learn gradio```

3. Run the Gradio App
Open the notebook gradio_sms_text_classification.ipynb in Jupyter and run all cells, or run the script if available.

4. Try the Demo
  - Enter an SMS message in the input box.
  - The model will classify it as “spam” or “not spam” in real time.
