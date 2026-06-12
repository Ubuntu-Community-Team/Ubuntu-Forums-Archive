---
title: "Parse error when adding XML declaration in a PHP script"
date: 2006-08-23
forum: Programming Talk
---

### Post by Ferio on 2006-08-23
Hi, I've just begun today to learn PHP; I'm using the XHTML 1.1 doctype and it works like a charm:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <meta http-equiv="content-type" content="application/xhtml+xml; charset=utf-8" />
        <meta http-equiv="expires" content="-1" />
        <meta name="author" content="Ferio"/>
        <meta name="Description" content="PHP exercises" />
        <meta name="Keywords" content="Exercises, PHP" />
        <meta name="Robots" content="all" />
        <title>Mi 1st PHP program</title>
    </head>
    <body>
        <?php
        echo "Hello World!";
        ?>
    </body>
</html>
```
The problem is that I wanted to add the XML declaration on top of the code to make it completely XHTML 1.1 compliant:
```
**<?xml version="1.0" encoding="UTF-8"?>**
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <meta http-equiv="content-type" content="application/xhtml+xml; charset=utf-8" />
        <meta http-equiv="expires" content="-1" />
        <meta name="author" content="Ferio"/>
        <meta name="Description" content="PHP exercises" />
        <meta name="Keywords" content="Exercises, PHP" />
        <meta name="Robots" content="all" />
        <title>Mi 1st PHP program</title>
    </head>
    <body>
        <?php
        echo "Hello World!";
        ?>
    </body>
</html>
```
But when I do this, Firefox returns:
```
**Parse error**:  syntax error, unexpected T_STRING in **/var/www/firstprog.php** on line **1**
```
How could I add this line without getting this error?

---

### Post by kthakore on 2006-08-23
because tags begining with <? get confused as php tags by the parser, you have to print or echo the xml line. As <?php echo '<?xml ... '; ?>

---

### Post by Ferio on 2006-08-24
I thought it was something like this, but my mind was wondering about escape sequences embedded in the XML code, only God knows why ](*,) Thank you!

---

### Post by kthakore on 2006-08-24
no problem! And I am glad a fellow web developer ( or at least a starting one) is taking the proper route to web standards

---

### Post by ifokkema on 2006-08-26
You don't necessarily need to use PHP to print the XML header. If you turn off PHP short tags, it'll work just as well.
But absolutely true; good you care about that tag. I started off using HTML with IE and it was very error-forgiving. Made me use very very lazy HTML, that I had to fix when I switched to Linux.

---

### Post by Ferio on 2007-03-31
I'm not sure why I didn't reply to this when I should, but I just wanted to let you know that, after months studying PHP, I've just got an amazing job, and I wanted to thank you for your participation in this achievement of mine, so: thank you!

---

### Post by ifokkema on 2007-04-01
> **Ferio said:**
> I'm not sure why I didn't reply to this when I should, but I just wanted to let you know that, after months studying PHP, I've just got an amazing job, and I wanted to thank you for your participation in this achievement of mine, so: thank you!
Wow, great, congratulations! :D \\:D/ =D>

---

