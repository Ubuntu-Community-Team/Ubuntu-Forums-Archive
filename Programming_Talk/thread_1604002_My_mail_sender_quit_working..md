---
title: "My mail sender quit working."
date: 2010-10-23
forum: Programming Talk
---

### Post by Silvernail on 2010-10-23
A couple weeks ago this code worked OK. 
Was there a PHP update I missed. 

Now I get these errors.

> 
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/curl.so' - /usr/lib/php5/20090626+lfs/curl.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/gmp.so' - /usr/lib/php5/20090626+lfs/gmp.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/ldap.so' - /usr/lib/php5/20090626+lfs/ldap.so: cannot open shared object file: No such file or directory in Unknown on line 0


These 2 classes are also needed.

class.phpmailer.php
class.smtp.php 

```

#!/bin/bash
main()
{
cat pdlist37 | ( \
     while read admin; \
     do check_link $admin; done \
     )

}

PHP_EXEC='php5 -r'

check_link()
{
    member_email=$1
    
    php5 -f meeting-announcement.php "$member_email" "two";
}

```


```

#!/bin/php5

<?php5
 
if($_SERVER['argv'][2]=="two") {
$filename = 'monthly-meeting-announcement';
$fp = fopen($filename, "r");
$php_file_name = fread($fp, filesize($filename));
fclose($fp);
$send_report_flag = 0;
#$php_file_attachment = '2010 Lydia Ann Fly Masters Tournament Package.pdf';
}

 
require("class.phpmailer.php");
$mail = new PHPMailer();
$mail->IsSMTP(); // telling the class to use SMTP
$mail->Host = "smtp.myhostserver.com"; // SMTP server
$mail->Username = "daveekelly1@myhostserver.com";
$mail->Password = "secretword";
$mail->FromName = "Dave Kelly";
$mail->From = "daveekelly1@myhostserver.com";
$mail->Sender = "daveekelly1@myhostserver.com";
$mail->ReturnPath = "daveekelly1@myhostserver.com";
$mail->ReturnReceiptTo = "BobB@hishostserver.com";
$mail->AddAddress(" {$_SERVER['argv'][1]}");

if($send_report_flag != 0 ) {
    $mail->AddAttachment($php_file_attachment);
    }
$mail->Subject = "Texas FlyFishers Monthly Meeting Announcement";
$mail->Body = $php_file_name;
$mail->WordWrap = 50;

if(!$mail->Send())
{
   echo "Message was not sent ";
   echo "Mailer Error: " . $mail->ErrorInfo;
}
else
{
   echo "Message has been sent to: " . $mail->AddAddress(" {$_SERVER['argv'][1]}");
}

?>

```

Thanks for any help you can provide.
Dave

---

### Post by Silvernail on 2010-10-23
Post #6 in this thread [http://ubuntuforums.org/showthread.php?t=1459163](http://ubuntuforums.org/showthread.php?t=1459163) solved my  problem.

---

