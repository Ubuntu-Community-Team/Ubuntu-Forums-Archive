---
title: "exit X"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Gandalf6596 on 2008-08-30
The title is not a joke.

I am trying to install the driver for my NVIDIA Geforce 8400GS video card.

The "NVIDIA driver installer" information says after downloading the driver package (done), "begin installation by exiting X".

I have no idea what this X refers to or how to exit it.

Thanks for the help...

---

### Post by overdrank on 2008-08-30
> **Gandalf6596 said:**
> The title is not a joke.

I am trying to install the driver for my NVIDIA Geforce 8400GS video card.

The "NVIDIA driver installer" information says after downloading the driver package (done), "begin installation by exiting X".

I have no idea what this X refers to or how to exit it.

Thanks for the help...

Hi and you can use the keys ctrl, alt, F1 at the same time and this will bring you to the command prompt where you will login and then you can use the command ```
sudo /etc/init.d/gdm stop

``` Then install the driver as directed and then you can use 
```
sudo /etc/init.d/gdm start
```

---

### Post by tuxerman on 2008-08-30
> **Gandalf6596 said:**
> The title is not a joke.
I have no idea what this X refers to or how to exit it.


X refers to the X-Window system, which provides you the Graphical user interface in linux.

---

### Post by Gandalf6596 on 2008-08-30
Thanks [B]overdrank
[/B]
I followed your directions.
I ended up in a black screen with about five OKed lines of text.
I entered the **sh NVIDIA.run** command (file name modified by me).
But, this doesn't make sense to me.  I must have done something wrong.
According to the NVIDIA webpage, the installer is supposed to walk me through the installation.  That never happened.

Your gdm commands worked OK, it's just what occurred in between that I messed up.

Any suggestions?

---

### Post by jemate18 on 2008-08-30
> **Gandalf6596 said:**
> The title is not a joke.

I am trying to install the driver for my NVIDIA Geforce 8400GS video card.

The "NVIDIA driver installer" information says after downloading the driver package (done), "begin installation by exiting X".

I have no idea what this X refers to or how to exit it.

Thanks for the help...

Yes, as stated in the above reply X refers to the X Window System which basically runs all the "graphical" things you see.

By the way, in Ubuntu pressing CTRL + ALT + BACKSPACE doesn't kill X. When you press it, it will terminate your session and will put you back on the login screen. 

Try these steps:
1. Try opening a terminal and type sudo init 1 [your password] 
2. X Server will be killed and you will be prompted in a menu.
3. Select "root Drop to root shell prompt"
4. to verify X is killed, type ps -ef | grep gdm
5. There should be no other entry except the command you have typed
6. then install the drivers as directed in the manual of your graphics card. You may also see it in the readme files.
7. after installation type, shutdown -r now


I hope this helps.

jemate18

---

### Post by Nythain on 2008-08-30
after getting to the black screen with a bunch of ok's and logging in to it with your username and password, then killing x with a
sudo /etc/init.d/gdm stop

the next thing you would want to do is run the installer, make sure you run it with sudo
sudo sh NVIDIA-xxxxxxxx.pkg.run

should work like a charm... though its gonna require kernel headers to compile... will ask you a few different questions, most of wich is pretty straight forward, and most of wich the default answers will be ok...

should hopefully be that easy

---

### Post by overdrank on 2008-08-30
> **jemate18 said:**
> Yes, as stated in the above reply X refers to the X Window System which basically runs all the "graphical" things you see.

By the way, in Ubuntu pressing CTRL + ALT + BACKSPACE doesn't kill X. 




jemate18

This is correct and I have corrected my post. I was in error  and stated the wrong keys.

---

### Post by bumanie on 2008-08-30
The 8400gs should install fine via hardware tools if using 8,04, if on anything prior to this (ie 7.10, 7.04), one should use restricted drivers - both are found under System --> Administration.

---

### Post by marufaberlin on 2008-08-30
Yes, CTRL + ALT + BACKSPACE kills X.
But as GDM is a daemon, and is always running in the background, it notices and starts X again.

---

### Post by Gandalf6596 on 2008-08-30
> **jemate18 said:**
>  
Try these steps:
1. Try opening a terminal and type sudo init 1 [your password] 
2. X Server will be killed and you will be prompted in a menu.
3. Select "root Drop to root shell prompt"
4. to verify X is killed, type ps -ef | grep gdm
5. There should be no other entry except the command you have typed
6. then install the drivers as directed in the manual of your graphics card. You may also see it in the readme files.
7. after installation type, shutdown -r now

 
Thanks,** jemate18**
This almost worked.  NVIDIA Installer said I needed to switch to runlevel 3 (telinit 3).
How does your procedure change to implement this difference?
 
Nothing I do seems to work.

---

### Post by jemate18 on 2008-08-30
> **Gandalf6596 said:**
> Thanks,** jemate18**
This almost worked.  NVIDIA Installer said I needed to switch to runlevel 3 (telinit 3).
How does your procedure change to implement this difference?
 
Nothing I do seems to work.

Did the telinit 1 command was successful?

What was the problem encountered?

If it says you should go to runlevel 3,

then just open a terminal and type

```
sudo telinit 3
```

hope this helps

jemate18

---

### Post by jemate18 on 2008-08-30
> **Gandalf6596 said:**
> Thanks,** jemate18**
This almost worked.  NVIDIA Installer said I needed to switch to runlevel 3 (telinit 3).
How does your procedure change to implement this difference?
 
Nothing I do seems to work.

Ummmmm..

If you open a shell and typed 
```
sudo telinit 3
```
This results into nothing as in it will not do anything

However, if you follow my first instructions
```
sudo telinit 1
```
and choose "root Drop to root shell prompt" 
you will be on a shell prompt.
then when you type
```
telinit 3
```
in the shell prompt, it will just put you back on the log in screen and X will be started again. :) This doesnt help you of course.

What problems was encountered during the first procedures I gave you?

It should work fine there, and there should be some..... compilation of module for when running the shell script for nvidia driver, the questions would be straightforward as .. anyway, could you give us the procedure and the problems..


Thanks

jemate18

---

### Post by Tatty on 2008-09-03
Hey Gandalf, just before you go ahead and install the driver, have you tried using the restricted drivers manager or EnvyNG to install the driver for your card?

One or both of these methods usually works fine and is much less hassle than trying to manage drivers yourself.


EDIT:  Oops, I just realised that the last post on this was 4 days ago...  in fact i have no idea how i ended up on this thread, lol, just keep on browsing!

---

