---
title: "Generate a favourite program-autodownload script?"
date: 2008-02-28
forum: Programming Talk
---

### Post by Redlazer on 2008-02-28
Is there any way i can make a script that will automagically download all my favourite programs from aptitude?

Is there any easy way to do it, or will i have to figure out the apt-get command for each program i want?

And, what if i want a program that isnt available from aptitude (like Opera and Netbeans 6.0)?

And while we're at it - when i install some things from Aptitude, it asks for the Ubuntu DVD - thats pretty annoying. Is there any way i can keep it from asking for it?

Thanks for your help : )

-Fred

Ooh, i have an idea - what about setting everything up the way i want it, then slipstreaming it onto a new DVD?

---

### Post by chewearn on 2008-02-29
> **Redlazer said:**
> Is there any way i can make a script that will automagically download all my favourite programs from aptitude?

Is there any easy way to do it, or will i have to figure out the apt-get command for each program i want?

Here:
[http://ubuntuforums.org/showthread.php?t=144817](http://ubuntuforums.org/showthread.php?t=144817)


> And, what if i want a program that isnt available from aptitude (like Opera and Netbeans 6.0)?

Don't know about this one.


> And while we're at it - when i install some things from Aptitude, it asks for the Ubuntu DVD - thats pretty annoying. Is there any way i can keep it from asking for it?

Top Panel Menu > System > Administration > Software Sources > uncheck the box at the bottom about ubuntu Cdrom

> 
Thanks for your help : )

-Fred

Ooh, i have an idea - what about setting everything up the way i want it, then slipstreaming it onto a new DVD?

See the first link about back-up of the /var/cache/apt/archives directories.

---

### Post by Redlazer on 2008-02-29
Awesome! thanks a lot.

How does the other post tell me how to slipstream onto a new DVD?

-Fred

---

### Post by chewearn on 2008-03-01
The thread doesn't tell you how to slipstream.  You can however, use the backup of /var/cache/apt/archives to save on downloading the packages again, when you make a fresh ubuntu install.

To do the linux equivalent of Windows Slipstream, you would need to learn how to create your own linux distribution disc; i.e. a custom ubuntu disc.  I'm not knowledge in this area, unfortunately.

Someone else wants to step in here and post a link to a howto?

---

