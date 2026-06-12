---
title: "suggestions to newbies"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by ozan2201 on 2015-08-17
As you may see, I am a newbie and with me, there are many more newbies who decide switch to ubuntu from their old windows, mac or some other linux distros.
Switching to a completely new environment is not easy at all if you jump into this new world with a small amount of information like me. (I guess that was unneccessary to say since you lived it :D)
With my little knowledge, I am trying to gain experience and know ubuntu/linux better, like thousands of other newbies who join this friendly community everyday.

So, here comes my question. What do you suggest us to do? Where to start? What to read? What to watch? What to learn first and how?

It would be great to have the ideas of people who have been enjoying ubuntu longer than me.

Thank you for your help.
ozi
(Honestly I don't even know if this is a proper thread hope it is)

---

### Post by monkeybrain20122 on 2015-08-17
I dunno. Make a test partition and start messing around, or install Ubuntu on an external hd and start messing around but play it safe with your 'real' Ubuntu system. It may sound terrible, but there is no learning experience like screwing things up and trying to fix it. :) But then you don't want to do it under stress, hence the test partition.

---

### Post by howefield on 2015-08-17
You could do worse than download and read this free book : [Ubuntu Pocket Guide and Reference ]("http://www.ubuntupocketguide.com/index_main.html")

Learn how to backup your files, image your drive and how to source/find help, ubuntuforums.org being one way of course :)

---

### Post by grahammechanical on 2015-08-17
Every installation of Ubuntu comes with a Ubuntu Help document. That explains the basics. And then there is the Ubuntu wiki. Here is the index.

[https://help.ubuntu.com/community/PopularPages/](https://help.ubuntu.com/community/PopularPages/)

And do not forget that becoming comfortable with the User Interface is a lot different from becoming competent with the Linux command line. Linux commands have their uses and in certain situations are indispensable. But the purpose of a Graphical User Interface is to do away with the need to know commands.

To put it another way. There is the easy way and there is the hard way. It is our choice as to how hard we want learning Linux/Ubuntu to be.

Regards.

---

### Post by yancek on 2015-08-17
In addition to using the resources mentioned above, install it and use it or run it from a Live CD or in virtual software to learn.  When you have problems, use the internet to search for answers to problems.  It's the biggest library in the world.  When you do searches, always check sites for dates and try to find sites specific to your distribution.

---

### Post by SeijiSensei on 2015-08-17
If your current machine has enough memory (at least 2 GB, preferably 3-4+), one way to start experimenting with Linux distribution is to run them in a "virtual machine" on top of Windows or OS X using a program called [VirtualBox](https://www.virtuabox.org).  You can install VB on Windows (or OS X), then use it to create a virtual machine and install Ubuntu or any other Linux distribution.  You can create multiple VMs so you can try out vanilla Ubuntu, Kubuntu, Lubuntu, and Xubuntu, for instance.  Or you can try Fedora or Arch or other distributions as well.

---

### Post by TheFu on 2015-08-17
Lots of good answers above. I think the answer depends on what you want to do with Linux.  If you are like my 82 yr old mother was, she didn't want to know anything more than what to click X to make Y happen. That worked for her for years.

If you want to be able install the OS on 1 machine and use it barely, that's fine too.  The **Ubuntu Desktop Guide** is a good place to start - easily found by any websearch.

If you want to run virtual machines or be a programmer, then a deeper understanding is required.

To GUI or to shell?  IMHO - the GUI is abused.  Every 3 yrs some new GUI is presented as the greatest thing ever and New books have to be written and settings are moved around so end users cannot find anything anymore. It is a new learning curve.  With Linux, the GUI is NOT the OS.  We don't need to be tied to any GUI at all.  Switching to a different GUI is 3 minutes of effort for the installation.  You can even run a GUI similar to what was used in 1995 if you like.  Back then, people weren't dumb. We just has slower hardware and less RAM, so we had to be more efficient.  Those older-style GUIs are lightning fast on the hardware of today.

If you aren't comfortable just swapping the GUI part of the OS, you can install a different release with a different GUI.  There are Mate, LXDE, XFCE, Unity and other GUI versions of Ubuntu. Each includes a tailored set of applications that the maintainers believe reflect what most users choosing that GUI would appreciate.  I don't bother with those, since I don't use 99% of those applications - why have anything loaded that isn't actually used?

So - if you stay with a lighter GUI (or a pure Window-Manager setup), you will learn how to do things from the shell. This learning happens once.  I'm using the same commands from 1994 today. Don't have to re-learn much just because some new GUI has been released.  It doesn't impact me.  My Ubuntu desktop doesn't have any menus, no panels, no buttons.  The 10 or so applications that I use daily have keyboard accelerators assigned and for anything else, it can be run from a terminal easily.  For example, about once a month, I need to record my desktop as a video - use simplescreenrecorder for that. It isn't worth having a keyboard chord for it, plus I want to disable the screen blanker/locking first and set a non-default config file to be used.  So I wrote a tiny script (really about 5 lines) to stop the screen stuff, run the recorder using my config file, and when the recording is done, re-enable the screen lock/blanking. This tiny script could be connected to a menu, but why bother?  

So - to me the effort that all these people are doing to make it so end-users don't need to leave the GUI to do common things is a complete waste of their time.  Give me an editor and a config file any day.  I shouldn't need a special tool just to control config changes.  This follows the "[Art of Unix Programming]("http://www.amazon.com/Programming-Addison-Wesley-Professional-Computng-Series/dp/0131429019")" guidelines.  More and more, a bunch of Windows-programmer types are dumbing down this stuff and breaking those long-held tenants for this OS. It will be the downfall of Unix/Linux and needs to stop ... IMHO.  Make a GUI that modifies the config files. Storing configs in non-trivial formats is bad for user, bad for programmers and bad for Unix. Let it work for both types of users.

**OTOH, I am just 1 type of Linux user and having the option for anyone to pick it up and get some use out of the system **is** and excellent thing. Flexibility is the core of Unix - being flexible for all users of all skill levels is a great thing.**

Ok - so if you want to know more about Linux and have a deeper understanding - to be a programmer, pen-tester, system administrator ... then point-n-click won't hack it.  IMHO, PnC only accesses about 10% of the power the system provides. If you want the other 90%, learn the shell, a little scripting, and automation.  That question is asked all the time, so I wrote an article about it: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) which has links to about 20 other helpful places.

If you want to be fluent in Mandarin Chinese, you need to go there and live with the people for a few years. The same applies to Linux. If you just want to read 10% of a Chinese restaurant menu, that's fine too - there is a cheat sheet for that.

I'm just one person with 1 unpopular opinion in these forums. I leave it to others to have the kinder, nicer, answers and opinions. ;)

---

### Post by ozan2201 on 2015-08-17
Thank you all for answering this question which means a great deal to me and other newcomers.
I see that I should back up everything and start messing around with the OS. 
The  e-book mentioned and the blog seem to be what I was just looking for  since there aren't sufficient sources on linux (actually computers in  general) in my native language :( . (I should have posted this way  earlier, schools are starting back again and reading them is going take a  long time, but I am sure they will worth it :D).
I don't want read %10 of a Chinese restaurant menu. I don't want to stick with GUI and just know about a small part. 
I want to be fluent in Mandarin Chinese and have the best out of my Linux computer.
It seems I am going to stay away from windows for some time.  :D

---

### Post by Habitual on 2015-08-17
[http://pastie.org/pastes/10357546/text](http://pastie.org/pastes/10357546/text)
Share that with your buddies. ;)

---

### Post by rebusgadfly on 2015-08-22
Thank you so much for starting this thread. I am a newbie too. I also offer a big thank you to those that responded and offered their assistance. I have installed Ubuntu as a dual boot but using it as my primary op system. The reference book is fantastic.

---

### Post by thatsallurspaceships on 2015-08-23
...tbh...if ur experienced with other os than win...only...it is totally different...not everyone starting ubuntu is a newbie...im just trying to tell people to get into it rather than following advice from people...even though theyre professors and know how to teach it...its still something different to use linux...it is free open source software...

---

### Post by coldraven on 2015-08-23
Maybe you can get some new ideas from this free magazine. If you like it you can get all the back issues. They have special editions for learning to program Python.
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Topsiho on 2015-08-24
Also see the Ubuntu manual, which may be available in your own language. It is available for Ubuntu 14.04 in English and maybe some other languages (and 12.04 for other languages):

[http://ubuntu-manual.org/?lang=en_US](http://ubuntu-manual.org/?lang=en_US)

Topsiho

---

### Post by Topsiho on 2015-08-24
> **thatsallurspaceships said:**
> ...tbh...if ur experienced with other os than win...only...it is totally different...not everyone starting ubuntu is a newbie...im just trying to tell people to get into it rather than following advice from people...even though theyre professors and know how to teach it...its still something different to use linux...it is free open source software...

The main difference from Windows for the average user, is that Linux just works :)

If he knows a graphic interface, such as of Windows, the ordinary user can use the Graphic User Interface (GUI) in any other system: a mouse click is a mouse click. Of course one needs to find their way within the GUI system: see Unity, and that may put some people off..

It is when you have to --> manage <-- a system, that you need to know more of the backgrounds of Linux (or Mac or Windows).
My wife is using her (Lubuntu) computer all the time: games, mail, browsing, managing her photo's and music, without ANY knowledge of Linux, and would be able to do so in any other GUI, if someone installs the necessary applications for her (which is me :), with maybe some first guidance ).

When you realize that Linux stems from Unix, and that Unix is/was an operating system run on mainframes, which had many users, possibly from everywhere (in the building, country, world), each with a (paid) account, running many many programs at the same time, using the internet; and that Windows was a --> Personal <-- Computer OS originally, for one user only, running only one program at the same time, originally without any connections to other computers, then you are on your way understanding Linux. (A Linux system is not a personal computer, looked at in this way :), which is OK to me ).

Topsiho

---

### Post by thatsallurspaceships on 2015-08-25
...depends...there are many sysadmins...that have very much knowledge...maybe more than both of us together...even though they dont use...another os...linux...if you think it is easier to change from an...lets say macintosh os...than from windoze...to linux...then why are so many threads opned by those user...?...there is many positive feedback from non computer users though...total new to computers might go better along with gnu/linux than...everyone else...

---

