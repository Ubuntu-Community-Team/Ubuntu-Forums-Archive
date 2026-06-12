---
title: "Want to match my hosting setup"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by lemonpromotions on 2012-11-01
OK, so I pay for shared hosting with a great host but I want to be able to set up a LAMP server so that it makes the transition from local server to hosted server as simple and painless as possible,

I am sure thats all fairly straightforward if you know what you are doing, but if you don't (and I don't) the whole proposition of setting up a LAMP server from scratch with UBUNTU looks like a major task. 

So what I am asking is, if I want to set up a LAMP server on my home network - is it worth the learning curve or should I just stick to using my paid hosting for development ?

---

### Post by Cheesemill on 2012-11-01
Setting up LAMP on Ubuntu is as easy as doing:
```
sudo apt-get install lamp-server^ 
```

Then just put your files in the /var/www directory.

---

### Post by lemonpromotions on 2012-11-01
Yeah ok, thats the easy bit - even I get that - which is amazing as my old brains slowing down.

The bit where it begins to become more problematic is that I develop on a PC and I find that when it comes to getting my files over to the UBUNTU machine, or even installing packages remotely,  then the whole process becomes a ball ache when compared to logging on to the hosting server I allready have. Even things like CPANEL make a massive difference to someone with little knowledge, and little time to learn.

---

### Post by pkadeel on 2012-11-02
> **lemonpromotions said:**
> I find that when it comes to getting my files over to the UBUNTU machine, or even installing packages remotely,  then the whole process becomes a ball ache when compared to logging on to the hosting server I allready have. Even things like CPANEL make a massive difference to someone with little knowledge, and little time to learn.

Well I too develop my sites locally first on my development server but I could not understand what you exactly aim to achieve. Putting files in your local webserver is just a matter of copy/paste or downloading from your current remote host and putting those in the correct place locally. 

If you please explain, I am sure alot of members here are using LAMP setup to guide you through.

---

### Post by lemonpromotions on 2012-11-02
OK, I tend to get lost after allocating a static IP to my "server" (I install desktop and work from there) -then when I try and get ftp access to the server it becomes complicated and I am looking at a few possible solutions. Basically I have no knowledge of the SHELL environment so need to use FTP. 

 I am also unsure how to create new accounts (sites) as this done for me through my cpanel of course with my offiste hosting.

There are other things I need to get right but these would help for now.

Thank you

---

### Post by pkadeel on 2012-11-02
For creating new sites in local apache2 setup first make sure that your apache works at 
[http://localhost](http://localhost)

Here is a very good and detailed article on setting up apache and virtual hosts on ubuntu
[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)

---

### Post by dannyboy79 on 2012-11-02
isn't webmin similar to cpanel?

---

