---
title: "php, need help!"
date: 2007-03-29
forum: Programming Talk
---

### Post by lamalex on 2007-03-29
I'm trying to code a form that will upload a file but it's not working. this is my code.
```

$target_path = '/var/www/virtual/acetechgroup.com/noc/htdocs/uploads/';
$file = $target_path . basename($_FILES['uploadedfile']['name']);
echo $file;

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'],$file)) {
        echo "The file has been uploaded \n";
}
else {
        echo "There was an error uploading the file, please try again! \n";

        switch ($_FILES['uploadedfile']['error']) {
                case 0:
                        echo "Well that doesn't make much sense does it? \n";
                        break;
                case 1:
                        echo "The file is bigger than this PHP install allows. \n";
                        break;
                case 2:
                        echo "This file is bigger than this form allows \n";
                        break;
                case 3:
                        echo "Only part of the file was uploaded \n";
                        break;
                case 4:
                        echo "No file was uploaded \n";
                        break;
        }
}
print_r($_FILES);

```

this being the output
```

/var/www/virtual/acetechgroup.com/noc/htdocs/uploads/client.txt

There was an error uploading the file, please try again! 
Well that doesn't make much sense does it? 
Array
(
    [uploadedfile] => Array
        (
            [name] => client.txt
            [type] => text/plain
            [tmp_name] => /tmp/phpP3ba67
            [error] => 0
            [size] => 17
        )

)

```

I'm getting error code 0, which means that php thinks the transfer went ok, but my if statement returns false and the file is not in my upload directory. I'm more or less a php noob. This form is a dummy form while I try to figure out why my upload wasn't working in a more complex environment, and it's not even working in this very simple situation. please help!

---

### Post by Mr. C. on 2007-03-29
Do you have PHP version >= 4.2 ?

MrC

---

### Post by lamalex on 2007-03-29
Indeed I do. 5.1.2

---

### Post by Mr. C. on 2007-03-29
Perhaps this will help:

[http://us2.php.net/manual/en/features.file-upload.errors.php](http://us2.php.net/manual/en/features.file-upload.errors.php)

There may be an error elsewhere, and the 'error' code is not meaningful in such a case.  The meaningful value is the boolean false returned from the move_uploaded_file() call.

MrC

---

### Post by lamalex on 2007-03-29
Yes I know, thats why my switch statement for error 0 says "well that doesn't make much sense does it?" because an error 0 means successful and is not much of an error at all. My question is why is my move_uploaded_file() returning 0.

---

### Post by Mr. C. on 2007-03-29
Undefined != does'nt make much sense.

W can't know why your upload is failing - what do your web logs show ?

MrC

---

### Post by lamalex on 2007-03-29
which log would I check? I don't think  there's a php log, and my apache log for my site doesn't have any related info it just shows that I visited and did a POST.

---

### Post by Mr. C. on 2007-03-29
Enable "display_errors" in php.ini:

display_errors = On

and review:

[http://us3.php.net/manual/en/ref.errorfunc.php](http://us3.php.net/manual/en/ref.errorfunc.php)

for enabling additional error messages.

Always check both of apache's access and error logs.

MrC

---

### Post by lamalex on 2007-03-29
ahh thank you very much. this is my error.
```

[Thu Mar 29 16:51:54 2007] [error] [client 69.17.28.131] PHP Warning:  move_uploaded_file() [<a href='function.move-uploaded-file'>function.move-uploaded-file</a>]: Unable to move '/tmp/phpps5lIM' to '/var/www/virtual/acetechgroup.com/noc/htdocs/uploads/client.txt' in /var/www/virtual/acetechgroup.com/noc/htdocs/fileupload.php on line 7, referer: http://noc.acetechgroup.com/form.html

```

---

### Post by Mr. C. on 2007-03-29
Excellent.  Now figure out what the apache user/group (www-data) has no permission to move the file.  Check file and directory permissions.

Become user www-data and try it manually in a shell:

```
$ sudo -s -u www-data
$ mv /tmp/phpps5lIM /var/www/virtual/acetechgroup.com/noc/htdocs/uploads/client.txt
```

This will help you understand.

MrC

---

### Post by lamalex on 2007-03-29
thanks so much, I didn't realize PHP had error handling off by default. Thanks for your help.

---

### Post by Mr. C. on 2007-03-29
You're welcome.

You'll want to disable error messages once your site is up and running, if the site goes public.  No need to present the outside world with the internal workings of your system.

MrC

---

