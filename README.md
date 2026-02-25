**🕵️‍♀️ Fake News Detection with BERT, XAI (SHAP) & LLM Agent**
This repository contains an end-to-end, state-of-the-art Natural Language Processing (NLP) pipeline designed to classify fake and real news. Going beyond standard classification, this project incorporates Explainable AI (XAI) to understand model behavior, Adversarial Testing to prove semantic understanding, and a Generative AI (LLM) agent to provide media literacy reports to end-users.

**🌟 Key Features**
Deep Data Cleaning & Leakage Prevention: Custom RegEx functions to remove agency tags (e.g., "WASHINGTON (Reuters)") and reporter signatures, forcing the models to learn semantic context rather than memorizing leaked structural clues.

Dual-Level Classification: Models were trained and evaluated on two separate paradigms:

Text-Only: Analyzing the full body of the news article.

Title-Only: Identifying "clickbait" and fake news solely from the headlines.

State-of-the-Art Modeling: Fine-tuned bert-base-uncased via HuggingFace for deep contextual understanding, alongside a highly optimized TF-IDF + Logistic Regression baseline.

Explainable AI (SHAP): Unpacking the black-box nature of Deep Learning. SHAP analysis proves the model detects subjective, emotionally manipulative language (e.g., "despicable", "perfect") rather than just names or locations.

Adversarial Robustness (Stress Testing): The model was tested against manipulated text (e.g., real news written angrily, fake news written in a formal BBC style). The BERT model successfully saw through the stylistic wrappers and classified based on the actual semantic truth.

Gemini LLM Integration: Converts raw model probabilities and SHAP insights into academic, easy-to-understand explanations for the end-user, acting as an automated media literacy assistant.

**📊 Dataset**
The project utilizes the ISOT Fake News Dataset, containing over 44,000 articles (approx. 21K True, 23K Fake).

**🚀 Performance & Results**
The models demonstrated exceptional accuracy, particularly the contextual Deep Learning approach:


Model,Input Feature,Accuracy,F1-Score (Macro)
Logistic Regression (TF-IDF),Full Text,99.0%,99.0%
Logistic Regression (TF-IDF),Title Only,94.0%,94.0%
BERT (Fine-Tuned),Title Only,98.6%,98.7%
BERT (Fine-Tuned),Full Text,99.9%,99.9%


**🧠 What the Model Actually Learned**
By extracting feature importances (coef_) from the baseline model and applying SHAP to the BERT model, we discovered the linguistic footprints of fake news:

Fake News Footprint: Heavy reliance on clickbait (video, watch, breaking), extreme emotional adjectives, and hyper-partisan language.

Real News Footprint: Objective, geographical, and institutional terminology (senate, court, pm, turkey, lawmakers).

**🛠️ Tech Stack**
Language: Python

Deep Learning & NLP: PyTorch, Transformers (HuggingFace), Datasets

Machine Learning: Scikit-Learn

Explainable AI: SHAP

Generative AI: Google GenAI SDK (Gemini 2.5 Flash)

Data Manipulation & Viz: Pandas, NumPy, Matplotlib, Seaborn
