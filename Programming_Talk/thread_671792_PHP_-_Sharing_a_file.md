---
title: "PHP - Sharing a file"
date: 2008-01-18
forum: Programming Talk
---

### Post by t3hi3x on 2008-01-18
Ok. I have a MySQL db that has a field that has a full file name. I am wanting to create a page that will pull the file so you can dl it. For security reasons I don't what the files accesible from the web sever directly. 

Is there a way I can use a PHP file to pull the file and push the file to the client?

If you need more info let me know.

Thanks for the help!

---

### Post by mathisdermaler on 2008-01-18
You can do this by using fopen() to open the file, and then use fread() to read the bytes from the file and print to send them to the client browser.  I think there's actually some built-in php functions that may do this as well.

Note that there's a lot of little gotchas when doing this.  Two of the most common are: 

First, you have to send the proper set of http headers (such as content-type)

Second, since the file extension of your page will be .php, in some circumstances IE may get confused about what kind of file it is receiving even if send the proper content-type header.

---

### Post by t3hi3x on 2008-01-19
So since in this case I want to do an MP3...I would do something like this:
[PHP]
<?php 

$mp3 = fopen($file);
$bytes = readfile($mp3);

echo $bytes;

?>
[/PHP]

This is psuedocode, but you get the point. I only semi-understand what you are referring to when it comes to the headers.

---

### Post by rowanparker on 2008-01-19
An example header (content-type) would be:
[php]header("Content-Type: audio/mpeg");[/php]

I don't know about anyone else but I'd use require() instead of readfile().

---

### Post by aks44 on 2008-01-19
> **rowanparker said:**
> I don't know about anyone else but I'd use require() instead of readfile().

So that PHP tries to parse and execute the file? Better pray that the file doesn't contain an opening PHP tag... :-\"

[fpassthru]("http://php.net/manual/function.fpassthru.php") is what the OP is looking for, but some web hosts disallow that function so you're basically left with an fread loop [SIZE="1"][COLOR="Gray"](readfile isn't a solution since it first reads the *whole* file into memory before sending it, IOW it is absolutely not scalable and should be avoided at all costs).
[/COLOR][/SIZE]

EDIT: damn, I got confused by that **$bytes = readfile($mp3); echo $bytes;** thing, and I mistook readfile for file_get_contents. :oops: Looks like my PHP is a bit rusty.
So please disregard my comment about readfile (which I just put in gray / small font).
Anyway those web hosts that disable fpassthru will also probably disable readfile.

---

### Post by t3hi3x on 2008-01-19
Thanks a lot. That worked quite well. PHP reveals itself as more and more powerful everyday.

---

### Post by t3hi3x on 2008-01-19
> **aks44 said:**
> 
EDIT: damn, I got confused by that **$bytes = readfile($mp3); echo $bytes;** thing, and I mistook readfile for file_get_contents. :oops: Looks like my PHP is a bit rusty.
So please disregard my comment about readfile (which I just put in gray / small font).
Anyway those web hosts that disable fpassthru will also probably disable readfile.

haha it's all good. I think you're way will work well for what I am doing.  But I do have a question. This way works good, except I would like to be able to push it as an mp3 as well. Would it be possible to do that? I do love this way, in fact it will have it's uses. It kinda opens it like a stream, which is sorda what is.

Ideas?

check out what it does: [http://jbuflashradio.com/test/play-test.php](http://jbuflashradio.com/test/play-test.php)

Thanks again. You all have been super helpful. This information was very difficult to find on Google.

---

### Post by aks44 on 2008-01-19
Try to replace **header("Content-Type: audio/mpeg");** by:
[php]// prevent the browser from knowing the real MIME type:
header('Content-Type: application/octet-stream');
// force download as a file:
header('Content-Disposition: attachment; filename="whatever.mp3"');[/php]

---

### Post by t3hi3x on 2008-01-19
Wow. That was very informative. I appriceiate how much help you have been. This seems to be a huge part of HTML or I guess on a more broad scale HTTP. Is there a place you know of that will help with all of this in the future?

---

### Post by aks44 on 2008-01-19
> **t3hi3x said:**
> This seems to be a huge part of HTML or I guess on a more broad scale HTTP.
Headers really are part of the HTTP protocol, and have not much to do with HTML (except for the **<meta http-equiv=...>** tag which is nothing more than a "backport" of HTTP headers into the HTML language).


> **t3hi3x said:**
> Is there a place you know of that will help with all of this in the future?
The HTTP specification (preferably [version 1.1]("http://www.w3.org/Protocols/rfc2616/rfc2616.html")) may be of interest. It lists most (if not all) possible headers. Unfortunately like any standards specification it's quite indigestible.

FWIW I found the application/octet-stream + Content-Disposition trick on the PHP site ([header]("http://www.php.net/header") function) thanks to Google that helped me refreshing my very capricious memory. :)

---

