# Seinfeld-Chatbot

### Details
This project was conducted as part of the course requirements for Natural Language Processing with Representation Learning (DS-GA-1011) at NYU. The project involved generating conversations between two characters from the TV sitcom Seinfeld. Modeling was performed with and without hand-crafted personas, however our hypothesis, that the model can effectively produce indentity-distinct and context-sensitive responses, proved to be true. 

1. We first performed baseline modeling using Seq2Seq models. Notebooks used for training in the `Baseline` folder.
2. Then we used transfer learning to fine tune a transformer on the Seinfeld corpus, adding persona information as part of the conversation history during training. Notebook used for training in the `Transformer_model` folder.
3. Lastly, we experimented with fine-tuning this pre-trained transformer model on individual characters separately, and having the dialogue agents converse with each other. Model file are found in the `Character_models` folder can can be used with the `talking_gpt2_2char` function in `utils/sienfield_utils.py`. 

These three major experiments are depicted below.

![image](https://github.com/akuz91/Seinfeld-Chatbot/blob/main/Figures/flowchart.png)
<img height="1000" src="https://github.com/akuz91/Seinfeld-Chatbot/blob/main/Figures/flowchart.png" />

### Evaluation and Results
We chose to evaluate the test set on BLEU and Perplexity as they are standard metrics for chatbots and translation models.

![image](https://github.com/akuz91/Seinfeld-Chatbot/blob/main/Figures/eval_viz.png)
<img height="1000" src="https://github.com/akuz91/Seinfeld-Chatbot/blob/main/Figures/eval_viz.png" />

The left graph breaks up the BLEU score for each model per character, each possible interaction was tested and then averaged.

An example of an interaction would be between Jerry and George with George’s output as the candidate line. 

The scores are very close, but Seq2Seq does well across the board. For character specific, our novel experiments perform the best for Elaine and Kramer. The right side shows how close each overall BLEU score is and the perplexities on the test set; our novel experiments do the best with perplexity.

We believe that the BLEU scores are not a great metric for our task as it is not capturing the context of the scene. It is also very surprising that the Seq2Seq model did the best with BLEU as its output isn’t intuitive. This is why we moved onto human evaluation on scenes with multiple lines instead of just two.
![image](https://github.com/akuz91/Seinfeld-Chatbot/blob/main/Figures/survey_results.png)
<img height="1000" src="https://github.com/akuz91/Seinfeld-Chatbot/blob/main/Figures/survey_results.png" />

This survey was aimed at those who are familiar with the show, we asked them to identify if a conversation between the characters is real or machine generated. Half were real and half were our one phase GPT model. Link to the survey can be found here: https://forms.gle/yjMoBq9qjLgrBpWH6 

Out of the machine questions, 41% of those respondents weren’t able to detect machine generated dialogue and out of the real conversations 30% thought they were machine generated. Some participants may have recognized scenes from the show, however a great deal of them couldn’t discern the real from machine generated conversations. 


