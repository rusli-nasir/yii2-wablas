# yii2-wablas
Yii2 Extension for https://wablas.com/

Usage
-----

To use this extension,  simply add the following code in your application configuration:

```php
    //...
    'waBlast' => [
        'class' => \ruslidev\wablas\WablasClient::className(),
        'wablasEndpoint' => getenv('WABLAS_ENDPOINT'),
        'apiToken' => getenv('WABLAS_API_TOKEN'),
    ],
    //...
```

Default config:

```dotenv
WABLAS_ENDPOINT=https://wablas.com/
WABLAS_API_TOKEN=123456
```

You can then send an whatsapp as follows:

Send Message

```php
    $message = 'Hello...';
    $phone_number = '08xxxxx'
    $result = Yii::$app->waBlast->sendMessage($message,'08xxxxxx');
    if($result instanceof StreamInterface){
        $resultContent = json_decode($result->getContents());
        $message = $resultContent->data->message[0];
    }
```

Send Image

```php
    
    $phone_number = '08xxxxx'
    $result = Yii::$app->waBlast->sendImage($imageCaption, $phone_number,$imageUrl ,$secret = false, $priority = false, $type = 'random');
    if($result instanceof StreamInterface){
        $resultContent = json_decode($result->getContents());
    }
```

Send Document Url

```php
    
    $phone_number = '08xxxxx'
    $result = Yii::$app->waBlast->sendDocumentUrl($docUrl, $phone_number = null , $secret = false, $priority = false, $type = 'random');
    if($result instanceof StreamInterface){
        $resultContent = json_decode($result->getContents());
    }
```

Send Document File

```php

    $phone_number = '08xxxxx'
    $result = Yii::$app->waBlast->sendDocumentFile($file, $phone_number = null, $secret = false, $priority = false, $type = 'random');
    if($result instanceof StreamInterface){
        $resultContent = json_decode($result->getContents());
    }
```


