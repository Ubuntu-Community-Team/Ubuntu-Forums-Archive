---
title: "Increase putty font size?"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by d4m1r on 2012-03-26
Hey guys, I am using 11.10 and Putty to connect to a remote linux server via SSH. However, no matter how large I stretch the large black putty window when I am connected, the font remains tiny....Ideally, I'd like the font to change according to the size of the window, but I'll settle to increasing it overall if I have to.

Does anyone know how to do this? I've tried [THIS]("http://malektips.com/putty-font-anti-aliasing.html") guide and other similar ones, but they all must be written for windows because they don't seem to keep in mind that once I am connected to a server, I do NOT have access to that left settings pane.

Thanks in advance guys!

---

### Post by bodhi.zazen on 2012-03-26
> **d4m1r said:**
> Hey guys, I am using 11.10 and Putty to connect to a remote linux server via SSH. However, no matter how large I stretch the large black putty window when I am connected, the font remains tiny....Ideally, I'd like the font to change according to the size of the window, but I'll settle to increasing it overall if I have to.

Does anyone know how to do this? I've tried [THIS]("http://malektips.com/putty-font-anti-aliasing.html") guide and other similar ones, but they all must be written for windows because they don't seem to keep in mind that once I am connected to a server, I do NOT have access to that left settings pane.

Thanks in advance guys!

You make the setting change before you connect to the server.

---

### Post by d4m1r on 2012-03-27
Even then, I don't see anything in all the Putty options to increase font size...Does anyone know **where** in Putty I can configure to increase the font size?

Ideally, it would resize as I resize the window.

---

### Post by bodhi.zazen on 2012-03-27
Take a look at this thread, the very last post in particular

[http://www.bleepingcomputer.com/forums/topic425629.html](http://www.bleepingcomputer.com/forums/topic425629.html)

[http://www.thegeekstuff.com/2009/07/10-practical-putty-tips-and-tricks-you-probably-didnt-know/](http://www.thegeekstuff.com/2009/07/10-practical-putty-tips-and-tricks-you-probably-didnt-know/)

---

### Post by vijay496 on 2012-03-27
hi all,

I am using ubuntu 11.10 along with windows7 previously I can boot to any of the OS.

Now I am unable to boot ubuntu, only windows is booting.
lastly when windows is booting it asked for checkdisk and I continued(it deleted some 2 files) from that moment I am unable to boot Ubuntu.
In C: drive I have windows 
in E: I have ubuntu

In either of these locations I can't find nothing(menu.lst)
E:\ubuntu\disks\boot\grub\
E:\ubuntu\install\boot\grub\

main problem is I don't have CD drive to reinstall.
but i have the copy of the CD in my windows pc.
if anybody share their 11.10 menu.lst if i copied to these locations will it work.


any idea??

plz help...


Regards

---

### Post by codemaniac on 2012-03-27
> **vijay496 said:**
> hi all,

I am using ubuntu 11.10 along with windows7 previously I can boot to any of the OS.

Now I am unable to boot ubuntu, only windows is booting.
lastly when windows is booting it asked for checkdisk and I continued(it deleted some 2 files) from that moment I am unable to boot Ubuntu.
In C: drive I have windows 
in E: I have ubuntu

In either of these locations I can't find nothing(menu.lst)
E:\ubuntu\disks\boot\grub\
E:\ubuntu\install\boot\grub\

main problem is I don't have CD drive to reinstall.
but i have the copy of the CD in my windows pc.
if anybody share their 11.10 menu.lst if i copied to these locations will it work.


any idea??

plz help...


Regards

Hello vijay496 , please start a new thread and post your issue there .

---

### Post by d4m1r on 2012-03-27
> **bodhi.zazen said:**
> Take a look at this thread, the very last post in particular
[http://www.bleepingcomputer.com/forums/topic425629.html](http://www.bleepingcomputer.com/forums/topic425629.html)


Thanks for this but it still isn't ideal...that lets me increase the font size but I have to change it manually for each saved connection AND it resets itself to the tiny default text size every time I close and re-open putty....

Anyone have any other suggestions? So far, putty sucks under linux as opposed to what it can do under windows ](*,)

---

### Post by bodhi.zazen on 2012-03-27
> **d4m1r said:**
> Thanks for this but it still isn't ideal...that lets me increase the font size but I have to change it manually for each saved connection AND it resets itself to the tiny default text size every time I close and re-open putty....

Anyone have any other suggestions? So far, putty sucks under linux as opposed to what it can do under windows ](*,)

As you can see, I know very few people who use putty in Linux. Now that I said that someone will pipe in.

It is a nice client for windows, but most people just use a terminal in Linux.

Terminal + ssh agent (ssh-add) + screen and you are good to go.

---

### Post by collisionystm on 2012-03-27
> **d4m1r said:**
> Thanks for this but it still isn't ideal...that lets me increase the font size but I have to change it manually for each saved connection AND it resets itself to the tiny default text size every time I close and re-open putty....

Anyone have any other suggestions? So far, putty sucks under linux as opposed to what it can do under windows ](*,)


Adjust your settings

on the main screen, where you choose SSH, telnet, whatever

You can save your profile

name it Default Settings and hit save. It will overwrite the current default and you wont have to change it again.

---

### Post by collisionystm on 2012-03-27
oh and BTW, I would use mRemote

It has tabs, vnc support and better features. It also uses putty though. Putty seems to be the standard. There is also Penguinet

[http://www.mremote.org/wiki/](http://www.mremote.org/wiki/)

[http://www.siliconcircus.com/](http://www.siliconcircus.com/)

---

### Post by d4m1r on 2012-03-27
> **collisionystm said:**
> Adjust your settings

on the main screen, where you choose SSH, telnet, whatever

You can save your profile

name it Default Settings and hit save. It will overwrite the current default and you wont have to change it again.

Thank you!! It is now saving my settings!

FYI for anyone else having this problem, load a session, go to Window>Font, and I changed "font used for ordinary text" to Ubuntu Mono, size 12. Go back to session, and hit save.

The annoying thing is you will have to do that for each of your saved sessions...But then it works! Also, Putty > Terminal in terms of functionality so its mandatory for me...

---

