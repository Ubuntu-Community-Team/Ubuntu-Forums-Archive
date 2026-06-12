---
title: "Can't run Eclipse"
date: 2007-08-07
forum: Programming Talk
---

### Post by rockballad on 2007-08-07
I'm using Ubuntu 7.04, 64-bit. Trying to install Eclipse, but it didn't work so far.

Install from web is too slow, so that I download the package from eclipse download page, unzip and move to /software (I don't know how we have to move to /opt). chmod to 777 (for sure). I also test java and javac from the terminal, everything is ok. But when I try to run

```
/software/eclipse/eclipse
```

It said: > bash: /software/eclipse/eclipse: No such file or directory

So strange, because I see eclipse and its content in the /software directory.

Could you tell me how to make it run please?

Thanks so much!

---

### Post by Pinger05 on 2007-08-07
navagate to the directory then type in ./eclipse.  Should do it.

---

### Post by rockballad on 2007-08-07
Yes. I cd to /sofware/eclipse, type ls and it shows a lot : 
> about_files    eclipse.ini    feature   eclipse  icon.xpm....

And I type "./eclipse" but it's still the same: No such file or directory.

How strange it is.

---

### Post by Pinger05 on 2007-08-07
Check the eclipse directory for a readme file.  You may need to run 'make' to create the files needed to kick off the installation.  The readme file will have all that on it (if it is there).  Another option is to go online and see if there are directions out there.  

I just went to [www.eclipse.org](www.eclipse.org) and it appears that all of their files are .rpm format.  That means you will have to find that readme file and make the install.

Typically you type
make config
make install
./install

---

### Post by rockballad on 2007-08-07
Thanks, Pinger05. There's a dir "readme", and it contains file "readme_eclipse.html". I'm reading it now, but there's no installation instruction here. In Windows, it was so easy. 

I did follow the instruction here : [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)

What wrong do you see?

---

### Post by Pinger05 on 2007-08-07
Go to this link and look for the eclipse install.  This is directly from the Ubuntu Wiki [https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools).

I am thinking that unless you really really really want to inflict pain and suffering on yourself you may be better off trying to install from the repositories.  But then again I am not the most knowlegeable about Debian based Linux.  Sorry

---

### Post by rockballad on 2007-08-07
In fact, I read around [https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools), [https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE), but I forgot their URL then I googled and got the same page. All right, tomorrow I will start over again.

Thanks so much for helping me. I highly appeciate about it. Thanks, and have fun!

---

### Post by rockballad on 2007-08-08
I don't see startup.jar file in Eclipse directory. Is it the reason why it can't run?

I download Eclipse Java here:
[http://eclipse.stu.edu.tw/technology/epp/downloads/release/20070702/eclipse-java-europa-linux-gtk.tar.gz](http://eclipse.stu.edu.tw/technology/epp/downloads/release/20070702/eclipse-java-europa-linux-gtk.tar.gz)

---

### Post by Damiel on 2007-08-08
New Eclipse versions, starting from v3.3 aka Europa, don't come with the startup.jar file.

twinky had the same problem when manually installing Eclipse in his 64-bits Ubuntu. You may want to check his [thread]("http://ubuntuforums.org/showthread.php?t=488487"). There are 2 possible solutions on the last 2 posts.

---

### Post by rockballad on 2007-08-08
Oops, no chance to do it now. I'm reinstall Ubuntu. Some error during boot, so I start over again. Wait some minutes then. Thanks a lot!

---

