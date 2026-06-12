---
title: "PHP bash script problem aliases handling incoming mail"
date: 2008-03-02
forum: Programming Talk
---

### Post by yanny on 2008-03-02
Hi,

I'm not sure if this post belongs to this forum.

I have followed this tutorial: [http://www.devpapers.com/article/155](http://www.devpapers.com/article/155)
I am unlucky because it did not work.

In /etc/aliases file I have put this line:
```
script: "|/var/www/mail/script.php"
```

The script.php is in /var/www/mail/ and looks like: 

[PHP]#!/usr/bin/php

<?php
include "functions.php";

// read from stdin
$fd = fopen("php://stdin", "r");
$email = "";
while (!feof($fd)) {
    $email .= fread($fd, 1024);
}
fclose($fd);

// handle email
$lines = explode("n", $email);

// empty vars
$to = "";
$from = "";
$subject = "";
$headers = "";
$message = "";
$splittingheaders = true;

for ($i=0; $i<count($lines); $i++) {
    if ($splittingheaders) {
        // this is a header
        $headers .= $lines[$i]."n";

        // look out for special headers
        if (preg_match("/^Subject: (.*)/", $lines[$i], $matches)) {
            $subject = $matches[1];
        }
        
        if (preg_match("/^To: (.*)/", $lines[$i], $matches)) {
        	$to = $matches[1];
        }
        
        if (preg_match("/^From: (.*)/", $lines[$i], $matches)) {
            $from = $matches[1];
        }
    } else {
        // not a header, but message
        $message .= $lines[$i]."n";
    }

    if (trim($lines[$i])=="") {
        // empty line, header section has ended
        $splittingheaders = false;
    }
}

//save to db 'from','to','cc','bcc','subject','message')
$fields['date'] = date('Y-m-d H:i:s');
$fields['from'] = $from;
$fields['to'] = $to;
$fields['subject'] = $subject;
$fields['message'] = $message;

insertquery('sent',$fields);
?>[/PHP]

When I send email, it should first send to this script and saves in the database (as the tutorial stated) then really send it to the person. It did not save, but it is sent.

There could be two problems:

1. It is not passed to the script.php
2. insertquery() function does not work properly so not saved...

How do you know what my problem is? How do you know if script.php has read the mail?

---

