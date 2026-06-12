---
title: "Ubuntu components does not load completely"
date: 2017-01-11
forum: New to Ubuntu
---

### Post by uday4all on 2017-01-11
my OS(Ubuntu 16.04)  is  unstable and also unusable,login screen changed as below picture.
[https://s29.postimg.org/ahif6z8av/20170112_070635.jpg](https://s29.postimg.org/ahif6z8av/20170112_070635.jpg)
But I can login using username and password.after logging in ,what I get is 
[https://s30.postimg.org/699thoz01/20170112_070713.jpg](https://s30.postimg.org/699thoz01/20170112_070713.jpg)
No launcher,no GUI,no account options totally unstable.
I do have access to terminal.
How do I restore it back to normal

---

### Post by Bucky Ball on 2017-01-11
Welcome. You have just installed? You say that the login has changed, so I suspect not. In that case, a full explanation of exactly what you did prior to this would help. An update/upgrade perhaps? Attempted to install a different desktop environment? Changed graphics drivers? 

It would be highly unusual to switch your computer on one day and the login screen has changed to what looks like GDM rather than LightDM or whatever you were using with no manual help whatsoever. What were you using? Please give full details of what occurred prior to this for best support. ;)

---

### Post by uday4all on 2017-01-11
> **Bucky Ball said:**
> Welcome. You have just installed? You say that the login has changed, so I suspect not. In that case, a full explanation of exactly what you did prior to this would help. An update/upgrade perhaps? Attempted to install a different desktop environment? Changed graphics drivers? 

It would be highly unusual to switch your computer on one day and the login screen has changed to what looks like GDM rather than LightDM or whatever you were using with no manual help whatsoever. What were you using? Please give full details of what occurred prior to this for best support. ;)
this problem occured before,but i made a fresh installation.installed chromium,xdm,aptik and thats it. i have used this system normally for 3 days and then this happened again.

---

### Post by Geoffrey_Arndt on 2017-01-11
Well, that explains it then.    Do a reinstall.   Don't install xdm.   Use the default Unity DE and LightDM . . . and you will be happy again.

---

### Post by Bucky Ball on 2017-01-12
> **Geoffrey_Arndt said:**
> Well, that explains it then.    Do a reinstall.   Don't install xdm.   Use the default Unity DE and LightDM . . . and you will be happy again.

+1. If you want to install xdm, uninstall lightdm. 

That is the xdm login you are looking at. Nothing unusual there. What happens after that I have no idea about, but that's the first problem solved and its probably at the root of what comes next: a conflict caused by the fact you are trying to use two dms at the same time, or at least have two installed.

If you don't want Unity and Lightdm then you could try a minimal install which just installs the kernel. Then you can install whatever dm you want from scratch, along with everything else.

Just one question: what were you trying to achieve by installing xdm? 

Good luck.

PS: If you installed xdm and were happily using lightdm, only thinking there was a problem when the xdm login screen appeared, which it should have done to start with, think you should perhaps do a bit more research on dms and what they do. Simply, you shouldn't have two installed at the same time, lightdm and xdm for instance. Unpredictable things, crashes and bangs can occur ... ;)

---

### Post by uday4all on 2017-01-12
> **Geoffrey_Arndt said:**
> Well, that explains it then.    Do a reinstall.   Don't install xdm.   Use the default Unity DE and LightDM . . . and you will be happy again.
[COLOR=#00ff00][SIZE=6]PROBLEM SOLVED
[/SIZE][/COLOR]Thank you very much.it really worked,i used XDM as a download manager.
but i have removed it now and everything was fine.
however my login screen changed to another form something like this  (related images from internet,slightly different) 
[http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg](http://www.techotopia.com/images/9/95/Ubuntu_10.10_login_screen.jpg)
but i created a file in [FONT=impact]/etc/lightdm/lightdm.conf[/FONT]  using terminal and root privilege and added
 ```
[SeatDefaults]greeter-session=unity-greeter
```
line in it  and switched to TTY  using ctrl+alt+f1 and then 
```
sudo service lightdm restart
```
.,,,,thats it ....everything is ok now
i'm using Ubuntu 16.04 Xenial
really,thank you very much. :)

---

### Post by deadflowr on 2017-01-12
Easy fix
Create a file called /etc/lightdm/lightdm.conf.d/10-mygreeter.conf
add this
```
[SeatDefaults]
greeter-session=unity-greeter
```
save as on restart you should see the login screen for the second image post.

the file needs to be written as root so you'll need to create it, or edit it as root.
easy way is with nano (or vi if that's your thing)
but nano is simple enough, just run
```
sudo nano /etc/lightdm/lightdm.conf.d/10-mygreeter.conf
```
enter your password
enter the above text.
press ctrl + X <<this will begin the save and exit
then press Y 
and then hit enter

to see if the new login screen is working a reboot works best.

---

### Post by Bucky Ball on 2017-01-12
Good news. You might like to mark this thread as solved to help others. It won't close the thread. See the last, blue link in my signature, bottom of this post.

---

