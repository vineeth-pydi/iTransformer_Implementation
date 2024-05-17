# iTransformer for Multivariate Time Series Forecasting

This folder contains the code of the iTransformers for Multivariate Time Series Forecasting of the ETTm1 Dataset.

## Dataset

ETTm1. Can be downloaded from here: [Google Drive](https://drive.google.com/file/d/1l51QsKvQPcqILT3DwfjCgx8Dsg2rpjot/view?usp=drive_link)


## Scripts

We have the iTransformer under 3 different prediction lengths - 48, 96 and 192.


To evaluate the model under other input/prediction lengths, we can change the ```seq_len``` and ```pred_len``` arguments:

```
# iTransformer on the ETTm1 Dataset, where 180 time steps are inputted as the observations, and the task is to predict the future 60 steps

!python -u run.py \
  --is_training 1 \
  --root_path ./dataset/ETT-small/ \
  --data_path ETTm1.csv \
  --model_id ETTm1_96_48 \
  --model iTransformer \
  --data ETTm1 \
  --features M \
  --seq_len 96 \
  --pred_len 48 \
  --e_layers 2 \
  --enc_in 7 \
  --dec_in 7 \
  --c_out 7 \
  --des 'Exp' \
  --d_model 128 \
  --d_ff 128 \
  --itr 1

!python -u run.py \
  --is_training 1 \
  --root_path ./dataset/ETT-small/ \
  --data_path ETTm1.csv \
  --model_id ETTm1_96_96 \
  --model iTransformer \
  --data ETTm1 \
  --features M \
  --seq_len 96 \
  --pred_len 96 \
  --e_layers 2 \
  --enc_in 7 \
  --dec_in 7 \
  --c_out 7 \
  --des 'Exp' \
  --d_model 128 \
  --d_ff 128 \
  --itr 1

!python -u run.py \
  --is_training 1 \
  --root_path ./dataset/ETT-small/ \
  --data_path ETTm1.csv \
  --model_id ETTm1_96_192 \
  --model iTransformer \
  --data ETTm1 \
  --features M \
  --seq_len 96 \
  --pred_len 192 \
  --e_layers 2 \
  --enc_in 7 \
  --dec_in 7 \
  --c_out 7 \
  --des 'Exp' \
  --d_model 128 \
  --d_ff 128 \
  --itr 1
```


## Training on Custom Dataset

To train with a custom time series dataset like for demand sensing, you can follow these steps:

1. Check the ```Dataset_Custom``` class under the ```data_provider/data_loader``` folder, which can be used to load and process custom time series files.
2. The file should be ```csv``` format with the first column containing the timestamp and the following columns containing the variates of time series.
3. Set ```data=custom``` and modify the ```enc_in```, ```dec_in```, ```c_out``` arguments according to your number of variates in the training script.
