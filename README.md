# Bangla_OCR
bn_text_recognition


# Prepare dataset

At this time, gt.txt should be {imagepath}<space>{label}\n
For example
```
test/word_1.png saiful
test/word_2.png sungargonj
test/word_3.png moniram kazy
```

```pip install fire```

```
 python create_lmdb_dataset.py --inputPath dataset/train/img --gtFile dataset/train/gt.txt --outputPath mdb_dataset/train
```




# Training 
```
CUDA_VISIBLE_DEVICES=0 python train.py \
--train_data mdb_dataset/train --valid_data mdb_dataset/val \
--select_data / --batch_ratio 1 \
--Transformation TPS --FeatureExtraction ResNet --SequenceModeling BiLSTM --Prediction Attn
```



# Test Demo
```
CUDA_VISIBLE_DEVICES=0 python demo.py \
--Transformation TPS --FeatureExtraction ResNet --SequenceModeling BiLSTM --Prediction Attn \
--image_folder demo_image/ \
--saved_model bn_models/TPS-ResNet-BiLSTM-Attn.pth
```


## For Cpu:
```
python demo.py \
--Transformation TPS --FeatureExtraction ResNet --SequenceModeling BiLSTM --Prediction Attn \
--image_folder demo_image/ \
--saved_model models/TPS-ResNet-BiLSTM-Attn.pth
```
# Screenshot
![1](img/1.png)
![1](img/2.png)
![1](img/3.png)
![1](img/4.png)
