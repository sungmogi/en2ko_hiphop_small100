# en2ko_hiphop_small100

# Model Description
**en2ko_hiphop_small-100** is a fine-tuned version of [SMaLL-100](https://huggingface.co/alirezamsh/small100) on [en2ko_hiphop](https://huggingface.co/datasets/sungmogi/en2ko_hiphop) dataset. 

# Introduction
SMaLL-100 is a distilled version of M2M100. SMaLL-100 was pre-trained on supervised data of parallel texts in ~100 different languages. In pre-training, its loss was calculated based on cross-entropy loss and knowledge distillation loss from M2M100, which is a much larger model. SMaLL-100 was also trained on data that is perfectly balanced across all languages. This allows SMaLL-100 to perform well in translations that involve languages that are relatively low-resource. 

This model was trained on the most recent version of the en2ko_hiphop dataset (~50k rows) using HuggingFace Trainer. A previous version of this model, which is a SMaLL-100 model fine-tuned on the previous version of the dataset (~20k rows), will be referenced in the evaluation section for comparison. 

Hyperparameters are specified below. 

# Training Result

<img width="547" alt="Screen Shot 2023-08-27 at 2 57 32 PM" src="https://github.com/sungmogi/en2ko_hiphop_small100/assets/131221622/d9660c55-4461-4f5b-9417-d3b6d47acebe">

# Evaluation
I compared the performances of the pre-trained (and not fine-tuned) SMaLL-100 model, the SMaLL-100 model that was fine-tuned on the previous ~20k-row dataset, and this model. The input texts for the comparison were chosen from songs outside of the dataset. Here is one example that shows that this model can capture the word "GOAT":

<img width="1104" alt="Screen Shot 2023-08-27 at 3 25 03 PM" src="https://github.com/sungmogi/en2ko_hiphop_small100/assets/131221622/23742896-42e2-433e-9404-5c6f19f8e0ee">

Further examples are discussed on [this notion page](https://complete-cowbell-18a.notion.site/Aug-2023-Fine-Tuning-En2Ko-Translation-Models-Part-2-afa6079679a440e58ff301fefe1eedc3?pvs=4). 

Comparison with GPT-3.5 (zero-shot and few-shot) is discussed on [this notion page](https://complete-cowbell-18a.notion.site/Sep-2023-Zero-Shot-Few-Shot-Translation-with-GPT-3-5-76752b2ffee04f469332b373de73bfa1?pvs=4).

# Training Hyperparameters
- per_device_train_batch_size: 4
- per_device_eval_batch_size: 4
- weight_decay: 0.01
- num_train_epochs: 4
- num_devices: 4
- learning_rate: 4e-5
