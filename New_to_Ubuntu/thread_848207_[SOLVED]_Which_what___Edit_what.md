---
title: "[SOLVED] Which what ??  Edit what ??"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-07-03
I have searched, so please excuse me if this is redundant.  I am in the learning process of Linux (Ubuntu), and read alot about cleaning, repairing, editing, etc. I have printed out FOSSwire Ubuntu Reference, and Linux Command Reference, But is there a good tutorial on what folder contains what, which should and shouldn't be "messed" with, etc.  I do read most of the threads in Absolute Beginner, but usually end up more confused than when I started ](*,)  Thanks for any help.

---

### Post by Xzallion on 2008-07-03
Heres an article I found that explains the linux filesystem failrly well.  [http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/").

Now out of curiosity, what exactly have you read about "cleaning, repairing, editing, etc"?  The main stuff a normal user has to mess with is in the /home section since most applications store their settings for each user in that users home folder.  and just from experience there isn't much cleaning to do in Ubuntu or its variants, that can't be done with an apt-get command. i.e. apt-get autoremove.

The only thing I had to edit outside of my home folder was for running a webserver where its files were in /var/www/, and I tend to edit /boot/grub/menu.lst just to customize my boot menu, but those are the only things I've edited outside the home folder in the two years I've been using Ubuntu.

---

### Post by dominiquec on 2008-07-03
For starters, have a look at 

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Follow more info from there.

---

### Post by original_jamingrit on 2008-07-03
To do anything big outside your /home, there will almost always be a program or front-end for doing it.

---

### Post by erginemr on 2008-07-03
I recommend you to read this tutorial for Linux beginners: [www.tuxfiles.org](www.tuxfiles.org)

---

### Post by gettinoriginal on 2008-07-03
Thank you very much for your response, I find the article you mentioned to be very helpful and I did bookmark it.  No, I am not wanting to do anything outside of home, but find that when I go to the home folder, the folders are confusing as to what does what, and what I can clean ie: cache, temp, etc, and or if that is necessary.  Also, when someone else asks for help, the responder will say (not factual LOL) code: blah blah, and I have no idea what that is doing to what.  Or they will say "in your bluetooth folder, find the greentooth file, and edit it to say blah blah. then when I do a search to find that folder, there are 14 bluetooth folders!!  LOL.  Just very confusing to someone older than dirt as myself.  I just enjoy learning new things. \\:D/

---

### Post by brian_p on 2008-07-03
> **gettinoriginal said:**
> I have searched, so please excuse me if this is redundant.  I am in the learning process of Linux (Ubuntu), and read alot about cleaning, repairing, editing, etc. I have printed out FOSSwire Ubuntu Reference, and Linux Command Reference, But is there a good tutorial on what folder contains what, which should and shouldn't be "messed" with, etc.  I do read most of the threads in Absolute Beginner, but usually end up more confused than when I started ](*,)  Thanks for any help.

I'm with Xzallion here. Assuming you have the basic desktop installation anything you want to customise can be done from your own account and in your home directory.

/etc is where the the system configuration files live and in 15 years I've hardly had to touch them. Anyway,to add to the growing list of references you are getting:

[http://www.debian-administration.org/articles/256](http://www.debian-administration.org/articles/256)

[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by Fingers &amp; Thumbs on 2008-07-03
Hello gettinoriginal,

  As you've said, you like to learn new things, you have come to the right place. I have been a computer user for many years but only switched to linux/ubuntu within the last 12 months and I have learned more about computers in the past year than ever.

  Occasionally you may find yourself in a situation where (for example: trying to configure some new hardware) and you are instructed to edit /somefolder/somefile.where, by somebody. All I can say is, editing any file can prevent something functioning, or at least change the way in which it functions, so 2 points, always make a backup of the original file, and always make an effort to understand the changes that somebody is instructing you to make.

  It's a bit like riding a bike really, occasionally you will graze your elbow, but you'll get back on more confident, having realised that falling off doesn't hurt so bad.

---

### Post by gettinoriginal on 2008-07-03
Thank you all so much for the links, I will spend the weekend reading and experimenting.  That's one of the things I love about Linux and it's users, sharing.  Never had that with windows !!  :lolflag:

---

### Post by steveneddy on 2008-07-03
> **gettinoriginal said:**
> Thank you all so much for the links, I will spend the weekend reading and experimenting.  That's one of the things I love about Linux and it's users, sharing.  Never had that with windows !!  :lolflag:

You really like those little :lolflag: flags, don't you?

To clean the system of any unwanted or unused software after an upgrade or removal of any application via synaptic or otherwise, open a terminal and type

```
sudo apt-get autoclean
```

then

```
sudo apt-get autoremove
```

That will get some little snippets of stuff that you really don't need wiped to help the system run faster and to only have the most up to date package installed.

---

