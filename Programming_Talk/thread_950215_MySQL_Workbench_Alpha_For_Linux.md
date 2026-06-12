---
title: "MySQL Workbench Alpha For Linux"
date: 2008-10-16
forum: Programming Talk
---

### Post by tinny on 2008-10-16
MySQL workbench is a great tool. It allows me to visually design a database schema for a MySQL database. I have used this tool in Windows and it works well. I was wondering if anyone has used this tool on Ubuntu? 

There is now an alpha version available for Linux
[http://dev.mysql.com/workbench/?p=158](http://dev.mysql.com/workbench/?p=158)

Has anyone used it? Is it good?

Im very keen to use this tool on Ubuntu, anyone got any tips that may help me?

Thanks :-)

---

### Post by slimx3m on 2008-10-31
tinny,

i've been trying to actually install it on my Hardy and it has fail so far to do so.  have you had any success installing it on your ubuntu?

---

### Post by arcardenas on 2008-11-08
Thank you so much for posting that link. I have been trying to build this from source for the last 16 hours. 

slimx3m, I'm using Intrepid and it installed without a glitch and from the 2 seconds I ran it for it seems it's working great. However, I did just spend almost a full day installing all the many dependencies that workbench needs (including cairo with glitz, which has to be built from source).

If the apt-get instructions from the mysql blog don't work you might want to try to build it from source. It's a real pain, but Synaptic was very useful in installing all the libraries (except for cairo with glitz).

Get the cairo sources from 
[http://www.cairographics.org/download/](http://www.cairographics.org/download/)

and follow the instructions to download the sources with git.

Then use

sudo sh ./autogen.sh --enable-glitz
sudo make
sudo make install

That will install cairo with glitz.

Then download the source from
[http://dev.mysql.com/downloads/workbench/5.0.html](http://dev.mysql.com/downloads/workbench/5.0.html)

use sudo sh ./autogen.sh and keep synaptic open to download whatever libraries sh says are missing.

Then make the changes to the source code as mention in [http://bugs.mysql.com/bug.php?id=39520](http://bugs.mysql.com/bug.php?id=39520)

I did not finish making the all the changes as I found this post and the instructions worked, but I think the changes in that bug report should be complete.

After that using sudo make and sudo make install should yield a working version of workbench.

---

### Post by tinny on 2008-11-08
> **slimx3m said:**
> tinny,

i've been trying to actually install it on my Hardy and it has fail so far to do so.  have you had any success installing it on your ubuntu?

I just followed the installation instructions word for word from the MySQL workbench site.

[http://dev.mysql.com/workbench/?p=158]("http://dev.mysql.com/workbench/?p=158")

Make sure you get and install libctemplate0_0.91-1_i386.deb from that google code site.

---

