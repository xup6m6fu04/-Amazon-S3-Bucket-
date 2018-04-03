# Amazon-S3-Bucket 儲存桶完全公開的方式
將 Amazon S3 Bucket 儲存桶完全公開的方式

原本在使用 Amazon S3 Bucket 的時候沒有這個問題

因為都是私人的圖片

但有一次想要公開儲存桶時，發現沒有可以完全公開桶的選項

都只能讓圖片自己公開

爬文後找到解法，在此分享

1. 進入儲存桶後
2. 點選上方的 Permissions
3. 點選下面的 Bucket Policy
4. 輸入以下內容 


```
{
    "Version": "2008-10-17",
    "Statement": [
        {
            "Sid": "AllowPublicRead",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::your_bucket_name/*"
        }
    ]
}
```
記住最後那一行為你的儲存桶名稱
 
請將 your_bucket_name 替代成你的儲存桶名稱

設定完成後圖片就可以直接經由一般網址公開，不需額外送Token解密
