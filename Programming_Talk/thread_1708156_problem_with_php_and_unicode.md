---
title: "problem with php and unicode"
date: 2011-03-16
forum: Programming Talk
---

### Post by nHacker on 2011-03-16
I have the following php code to give a single devanagari word:
[PHP]
<?php
echo "&#2344;&#2368;&#2352;&#2332;";
?>
[/PHP]
but instead of showing &#2344;&#2368;&#2352;&#2332;, what it shows is : à¤¨à¥€à¤°à¤œ

I use gedit as as my text editor. Is this a problem with gedit?

---

### Post by An Sanct on 2011-03-16
You have to "save as" and select UTF-8 encoding.

Edit: does the same for me, but it is okay, if I use this code

[PHP]
<HTML>
<HEAD>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<TITLE>utf8</TITLE>
</HEAD>
<?php
echo '&#2344;&#2368;&#2352;&#2332;';
?>[/PHP]

---

### Post by SeijiSensei on 2011-03-16
Not necessarily.  First, try viewing the script in Firefox, then choosing View > Character Encoding.  What encoding is it using?  If it's not set to Unicode, try selecting that and see if the word appears correctly.  If so, it's likely that Apache is configured to use a different encoding than UTF-8.  

Try removing the "#" to activate "AddDefaultCharset" in /etc/apache2/conf.d/charset.  If you have multiple virtual hosts, you may want to include the AddDefaultCharset directive in the <VirtualHost> container rather than defining it globally in /etc/apache2/conf.d/charset.  When you're done, restart apache by running "sudo service apache2 restart" at a terminal prompt.

You'll need to edit the charset file with sudo.

---

### Post by nHacker on 2011-03-16
@ An Sanct : Saving as UTF-8 didn't do anything, but the meta tag solved the problem. Thanks.

@ SeijiSensei : Setting the encoding to Unicode did the job, but the meta tag works on other browsers too. I don't think apache is misconfigured. Thanks

---

### Post by SeijiSensei on 2011-03-16
Defining the encoding in a <meta> tag overrides the default encoding used by the server.

---

