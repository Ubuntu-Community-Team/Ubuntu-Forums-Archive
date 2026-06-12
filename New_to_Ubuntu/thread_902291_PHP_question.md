---
title: "PHP question"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by adamgram on 2008-08-27
Hi everyone.  I'm trying to learn PHP and want to figure out a way to work on websites on my laptop running Ubuntu 8.4.  My server supports PHP, and I have uploaded a few scripts to the server and been able to view them just fine.  

This is obviously quite cumbersome for figuring stuff out though, and I'd like to be able to open .php files directly in Firefox or some other browser without uploading them to a server, like I can with .html files, so I can compare side by side the code and the resulting webpage, without access to the internet.

This seems like something I should be able to do, but Firefox won't open .php files.  I searched the 'add/remove applications' section for 'PHP' and found nothing that looked relevant, and I did a 'sudo apt-get php5' which downloaded something but no new applications show up and still I can only open .php files as text to see the code.  

What do I need to be able to open .php files and see the web page?

---

### Post by mcduck on 2008-08-27
PHP files always need a server to work, as they are not web pages but instead code that tells the server how the page should be like. The server then reads the PHP code and based on that creates a web page which it sends to your browser. Anyway, you can install the LAMP server on your computer and use that to test your PHP code off-line..

To do this just run "sudo tasksel install lamp-server". It will install & configure Apache, MySQL and PHP for you.

---

### Post by eggdeng on 2008-08-27
Open Synaptic Package Manager, go to Edit, Mark Packages by task and tick LAMP server and click OK. This will install Apache, MySQL and PHP on your computer. You will be asked to specify a MySQL root user password during the install.
When you have Apache set up, you will need to change permissions on the document root directory
```
chmod 777 /var/www
```
(Not recommended on a production server!) and copy your html & php files to that directory.
Reboot and you should be able to access your files through the browser at [http://localhost](http://localhost)

---

### Post by cookdn on 2008-08-27
You are going to need a web server with PHP support running on your laptop to do this. The scripting within the PHP file has to be parsed and then converted to standard HTML ouput by the web server before it can be read by the browser.

This thread on setting up XAMPP may help you out:

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Hope this helps.
David

---

### Post by owenll on 2008-08-27
I use [Xampp]("http://www.apachefriends.org/en/xampp-linux.html") and find it very handy, and easy to start and stop the server.> XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl. XAMPP is really very easy to install and to use - just download, extract and start.

Edit: **cookdn** beat me to it!

---

### Post by adamgram on 2008-08-27
Thanks for the help guys!  I get that PHP is script that creates html files and not a webpage in and of itself, I just thought there would be an easier way to run the script locally for website development without also setting up a server... I'll play around with it some more when I get home, maybe it isn't as hard as I imagine it is hahaha  thanks again!

---

### Post by mcduck on 2008-08-27
> **adamgram said:**
> Thanks for the help guys!  I get that PHP is script that creates html files and not a webpage in and of itself, I just thought there would be an easier way to run the script locally for website development without also setting up a server... I'll play around with it some more when I get home, maybe it isn't as hard as I imagine it is hahaha  thanks again!

It really isn't hard at all. Took me about 10 minutes when I installed LAMP first time on Ubuntu. I just installed LAMP with Synaptics "Mark packages by task"-tool (does the same as the tasksel command I gave you), and then created a symbolic link from a directory in my home into /var/www/ ("sudo ln -s /home/mcduck/www /var/www/mcduck"). This way I can keep my development files inside my home dir, and access them at [http://localhost/mcduck](http://localhost/mcduck) without having to worry about permissions and stuff like that. I suppose there is a better way to do the same but this works very well and is easy, and as I'm only using it as development server not open to Internet it should also be safe enough.

---

### Post by adamgram on 2008-08-29
Thanks again for the help guys!  Had a few minor glitches setting it up but nothing too hard to figure out.  Now time for the fun part learning the code!  Thanks again this forum rocks!

---

