---
title: "Help: how to program a graphical TrueCrypt"
date: 2006-09-25
forum: Programming Talk
---

### Post by simone.brunozzi on 2006-09-25
Hi there,
I'm a decent PHP programmer, but have almost no experience with Python, and I want to learn it.
Therefore, I thought that the best way was to produce a real world application, and my choice is going toward TrueCrypt, which in Ubuntu is only textual, not graphical like in Windows.

Now the point is: how long do you think it would take to do a graphical frontend to TrueCrypt?
Second: which tools/IDE/manuals are the best for such a task?
third: do you think it could be a useful learning experience (I think so)?

Thanks for any suggestion and comment!

Cheers,

---

### Post by cleverselfreferentialname on 2006-09-25
Well....Truecrypt is a beautiful example of something that I would like to see in Ubuntu, in the default install, with a GUI. I wish you luck.

I guess the first step would be to actually get it working in Ubuntu. I've never been able to compile it, and the Ubuntu/debian package on the site is outdated.

---

### Post by simone.brunozzi on 2006-09-26
> **cleverselfreferentialname said:**
> Well....Truecrypt is a beautiful example of something that I would like to see in Ubuntu, in the default install, with a GUI. I wish you luck.

I guess the first step would be to actually get it working in Ubuntu. I've never been able to compile it, and the Ubuntu/debian package on the site is outdated.

I was able to use it (from the command prompt) without any problem. In fact I was also able to correctly open a TC volume created in windows XP.

---

### Post by bluntu on 2006-09-28
I love TrueCrypt and on Windows it's easy to install and use. Here on Ubuntu I'm having a hard time getting it to work I guess I didn't really try cause there are a lot of things that I don't know yet.

How did you get it to work? I don't mind using command lines.

---

### Post by bbukh on 2006-09-29
Since you want to write a front-end not just for any program but for cryptographic software you will need to have the knowledge of how to write secure software, which is not something most of us learn.

-Boris

---

### Post by mark_g on 2006-10-02
A graphical frontend would be a very useful thing to program. Your efforts would be very much appreciated by many I think, so good luck.
To those who have trouble installing TrueCrypt, have you read this howto on the forums yet? 

[http://www.ubuntuforums.org/showthread.php?t=199367&highlight=truecrypt](http://www.ubuntuforums.org/showthread.php?t=199367&highlight=truecrypt)

---

### Post by nightfrost on 2006-12-17
Hi,

I was just wondering how it's faring with the truecrypt frontend (btw, I noticed over at truecrypt homepage that they have official edgy packages nowadays).

Wouldn't it be possible to hack on a simple zenity wrapper pretty fast? I'm thinking of doing that myself (which means learning zenity as well ;-))...

---

### Post by bone2006 on 2007-02-02
I would also love to see a gui for truecrypt in linux.

---

### Post by WKnew on 2007-02-14
There is a KDE based GUI for Truecrypt. It is listed in the LINUX section of Softpedia. I wasn't able to get it running, but that's just due to my experience level I'm sure.

Has anyone been successful? If so please post a how-to. I believe my problem was that I didn't get kommander-executor installed.

Edit: the GUI is called: Onekript.

---

### Post by bone2006 on 2007-02-15
Thanks for letting us know about the software.  I see it at [http://onekript.sourceforge.net](http://onekript.sourceforge.net)
I'm guessing you need to install truecrypt first or do you know if you install the frontend gui that it will be installed as well

---

### Post by WKnew on 2007-02-15
Truecrypt is a dependency. Already installed and a volume created. But it is command line accessible only.

---

### Post by gteachey on 2007-02-21
> **WKnew said:**
> There is a KDE based GUI for Truecrypt. It is listed in the LINUX section of Softpedia. I wasn't able to get it running, but that's just due to my experience level I'm sure.

Has anyone been successful? If so please post a how-to. I believe my problem was that I didn't get kommander-executor installed.

Edit: the GUI is called: Onekript.

I got the program to run, but it doesn't appear to mount any files, I guess I'll be sticking to commandline for this
Here's how I got it to run, maybe someone will have better luck.....

Download the file to Desktop
```
 
sudo tar zxf onekript-0.7.2.tar.gz 
sudo  kmdr-executor onekript.kmdr 

```

---

### Post by bone2006 on 2007-02-22
The GUI was really disappointing to be honest.

---

### Post by nightfrost on 2007-02-22
Since I realized gnome-volume-manager has support for luks-formatted drives, I don't see any point in using truecrypt... try that instead ;-)

---

