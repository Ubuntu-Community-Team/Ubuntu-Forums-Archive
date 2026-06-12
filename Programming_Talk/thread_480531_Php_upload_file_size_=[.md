---
title: "Php upload file size =["
date: 2007-06-21
forum: Programming Talk
---

### Post by tipalm73 on 2007-06-21
Let us see if I can make some sense here.

I have a basic php script to upload files to a browser on server.

I have changed:

upload_max_filesize
memory_limit
post_max_size

all too 128m.

Then in my httpd.conf file(which was empty) i added:

<Files *.php>
SetOutputFilter PHP
SetInputFilter PHP
LimitRequestBody 131072
</Files>
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

I still cannot upload a 3m file =[ It will successfully move smaller files..but I am stumped.


Thanks in advance!

---

### Post by Mr. C. on 2007-06-21
> **tipalm73 said:**
> 
LimitRequestBody 131072
...
I still cannot upload a 3m file =[ It will successfully move smaller files..but I am stumped.


In my book, 131072 is about 131 K.

MrC

---

### Post by tipalm73 on 2007-06-21
Sorry, my mistake, apache LimitRequest is 9524288.

All the phpinfo settings are 128m.. will transfer a picture but not a 3meg song.

---

### Post by 1oki on 2007-06-22
Ooo! this is what I am looking to do! I am setting up an internal website with Apache-ssl for my office and would like to be able to upload files to the server from the website... I am not a programmer or developer, but do have experience with html, and C+. 

Can you guys point me in the right direction where I can get a basic, starters side information on how I can accomplish this? It would make my life so much easier! 

Thanks in advance!

-L

---

### Post by srqhiker on 2008-11-11
Try this blog post for changing the file upload size

[http://www.miscdebris.net/blog/2008/04/14/changing-the-php-file-upload-limit-in-ubuntu-linux/](http://www.miscdebris.net/blog/2008/04/14/changing-the-php-file-upload-limit-in-ubuntu-linux/)

---

### Post by kennedy7 on 2009-02-27
Ok, i have done the things that your blog said. I was able to upload allot of files before but then with phpfilemanagers and things like that i sudenly was not able to delete upload or even mess with the files on my server. I have  1gig of ram, memory limit set to 128m and post_limit 5120M that is 5gigs and upload_max 5120M. You can also check this file out at tyspage.doesntexist.com/info.php
I swear it exsists. i got the doesntexist.com from dyndns.org.
Please help. I am running a file server and i really need to be able to upload, zip, unzip, delete, copy, cut and more with a php filemanager.

---

