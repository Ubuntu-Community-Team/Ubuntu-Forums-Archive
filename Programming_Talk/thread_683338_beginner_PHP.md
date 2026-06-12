---
title: "beginner PHP"
date: 2008-01-30
forum: Programming Talk
---

### Post by mfederwi on 2008-01-30
Just getting started with PHP on Ubuntu.  So I am sure this is something that I am doing wrong.  I am doing some simple php examples to get my feet wet, but PHP doesn't seem to be handling double quotes the way I would expect.  For example the following code:
<?php
    echo '<html>
        <head>
        <title>Title of the site</title> '.
       '</head>';
    echo "<body>hello world<br></body></html>\n";
?>

results in
Parse error: syntax error, unexpected '>' in /var/www/sample3.php on line 6.

Can someone point me in the right direction.

Thanks.

---

### Post by LaRoza on 2008-01-30
> **mfederwi said:**
> 
<?php
    echo '<html>
        <head>
        <title>Title of the site</title> '.
       '</head>';
    echo "<body>hello world<br></body></html>\n";
?>


(I realize you are learning this, but what it looks like you are trying to do is not how PHP should be used. It is OK to do stuff like this when learning though)

[php]
<?xml version="1.0" encoding="utf-8" standalone="yes"?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">

<head>

<title>LaRoza</title>

<meta http-equiv="content-type" content="application/xhtml+xml;charset=utf-8" />

<meta http-equiv="Content-Style-Type" content="text/css" />

</head>

<body>
<?php
    echo "You are $_SERVER['REMOTE_ADDR'] and I know where you live";
?>
</body>

</html>

[/php]

---

### Post by mfederwi on 2008-01-30
Thanks for your reply.  Yes this code has nothing to do with what I want to program, just learning.

I just found the answer to my question, though.
I was creating the php file with open office and saving as a text file.  That apparently does not work.  I created the same file using the VI editor and it worked ok.  I'm amazed that I still remember vi from 20 years ago in college.

I'll need to find something else to use as a text editor.

mfederwi

---

### Post by LaRoza on 2008-01-30
> **mfederwi said:**
> Thanks for your reply.  Yes this code has nothing to do with what I want to program, just learning.

I just found the answer to my question, though.
I was creating the php file with open office and saving as a text file.  That apparently does not work.  I created the same file using the VI editor and it worked ok.  I'm amazed that I still remember vi from 20 years ago in college.

I'll need to find something else to use as a text editor.

mfederwi
Gedit is very good, and has great plugins.

(20 years ago in college? I just graduated college, and I am 19)

---

### Post by Erikina on 2008-01-30
> **LaRoza said:**
> You can't have quotes like that cover more than one line.

That is wrong. PHP allows multi-line strings (unlike say, C/C++/C#).

It's also worth noting, that the character '\n' is stored in multi-line strings:

$var = 'how are
you';

$var == "how are\nyou";


Regards.

---

### Post by LaRoza on 2008-01-30
> **Erikina said:**
> That is wrong. PHP allows multi-line strings (unlike say, C/C++/C#).


In what version of PHP? I am not up on all the lastest developments because my host uses an older version.

---

### Post by Erikina on 2008-01-30
> **LaRoza said:**
> In what version of PHP? I am not up on all the lastest developments because my host uses an older version.

Ever since I started, it's been like that (5 or 6 years?). In fact, I'd be pretty sure it was a language feature from day 1. (as it's pretty important for readability). But I might be wrong about that. The php manual ([http://www.php.net/types.string](http://www.php.net/types.string)) makes no mention when it was introduced.

Try a multiline string on your host, and I'd be very surprised if it doesn't work. And if it doesn't work. I'd be interested in what version of PHP that is (phpinfo() will return it).

Eric

---

### Post by LaRoza on 2008-01-30
> **Erikina said:**
> Ever since I started, it's been like that (5 or 6 years?). In fact, I'd be pretty sure it was a language feature from day 1. (as it's pretty important for readability). But I might be wrong about that. The php manual ([http://www.php.net/types.string](http://www.php.net/types.string)) makes no mention when it was introduced.

Try a multiline string on your host, and I'd be very surprised if it doesn't work. And if it doesn't work. I'd be interested in what version of PHP that is (phpinfo() will return it).


I must be confusing it with something else then, perhaps my preferences as I do not like strings spanning more than one line.

---

### Post by faulkes on 2008-01-30
Interesting,

If I cut/paste your supplied code into a sample php file and run it from my web server it executes just fine.

Have you checked /var/log/httpd/error_log (or wherever you have setup your error logs if not in default location).

Also, shouldn't the file be in /var/www/html (vs. /var/www)

Faulkes

---

### Post by Erikina on 2008-01-30
> **faulkes said:**
> Interesting,

If I cut/paste your supplied code into a sample php file and run it from my web server it executes just fine.

Have you checked /var/log/httpd/error_log (or wherever you have setup your error logs if not in default location).

Also, shouldn't the file be in /var/www/html (vs. /var/www)

Faulkes

The problem has been solved. It was caused by him not saving it in plain text. The code is fine :)

---

