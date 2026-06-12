---
title: "[SOLVED] I'm confused, and trying set up a multi purpose server"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by TheAddict on 2008-06-04
Firstly, I apologise if this post is kind of confusing. My reading today has been very scattered, and I'm quite confuddled about what I need to let you know.

With that out of the way, onto my actual post

I have previously built the worst machine ever to be called a server - a feisty desktop install with Samba added for file serving. I am now wanting to expand upon what I have already, with a new box.

I am wanting to have file serving (and perhaps print serving, but thats not a requirement), and am fairly comfortable setting up Samba the way I need it. I would like to add remote access, via FTP or SFTP, or something to my shared folders from anywhere in the world. I would like to have a web server to perform 2 functions - 1. web development sandbox, and 2. host an intranet. I would like the intranet to be accessible remotely as well. I would also like to be able to send my mates a url, or an FTP connection details if they want a file from my system, and its too large to email or whatever..

And thats about all that is clear in my mind. I don't even know if it's all possible from a single box, of if I would need to use  a couple of systems to get the functionality that I want.

Working on the assumption that its all possible in a single box, where would I start to learn about how to get it all set up. As for partitions and the like, I will have 120GB (108GB usable) at my disposal via an 80GB (72GB Usable) internal drive, and 40GB(36GB usable) external drive. The second drive has to be external as the system is a disused laptop.

okay, I think I lost it too much there, so I will leave it up to any responders to ask me questions where things aren't clear

thanks in advance

---

### Post by spiderbatdad on 2008-06-04
Yes it is all possible...for simple file transfer through scp:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

For hosting via webpage, apache2 or a lamp setup is easy to get going:[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

And my own simple guide to getting the most basic apache2 server running:[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by TheAddict on 2008-06-04
thanks for the response spiderbatdad

I'm about to start reading the links and will go from there...

---

### Post by TheAddict on 2008-06-05
Okay, so I have gotten the Samba shares up and running (they look a bit bare at the minute), and have access to the terminal remotely through ssh, i have also got LAMP installed, but apparently something went wrong with PHP, or I need to change directory permissions or something, as at first it didn't seem to be parsing PHP correctly, it  was just parsing it as plain text. I then reinstalled php, as per the help docs, and now when I try to open a file with as simple php as 
```
<?php phpinfo(); ?>
```
I get the following error:


```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/test.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```.

Any ideas on what I've done wrong?

---

### Post by messyhead on 2008-06-08
Can I ask what you did to fix the error you were getting? I'm having the same problem.

---

### Post by TheAddict on 2008-06-08
Yeh, i didn't try to unzip the php I was sending over "on the fly" between my windows machine and the server!

---

