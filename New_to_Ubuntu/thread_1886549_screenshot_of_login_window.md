---
title: "screenshot of login window"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by praneethu on 2011-11-25
Hi UBUNTU folks.
i am a newbie to UBUNTU and using from 11.10 edition. 
to take screenshots i use <prtsc> button. But i want to take a sceenshot at login time when ubuntu asks for password verification. How can i do this.

---

### Post by sudodus on 2011-11-25
Welcome to the Ubuntu Forums

If you want to make a tutorial or some other kind of instruction, it would be nice. But not so easy unless you run in a virtual machine.

You can install VirtualBox, create a file system and then install Ubuntu into it. Then from the host operating system, you can 'print screen' (or 'alt + print screen' for the window of the virtual machine) and get screenshots of everything (also the grub menu).

---

### Post by lincoln32 on 2011-11-25
It is hard to use a program before the operating system is installed so one way is to install virtualbox then install 11.10 again in the virtual machine to get login screen shots from the host os of the virtual os start-up:D

---

### Post by sophia911 on 2011-11-25
I am the new ,too . 
Welcome to join us . 
Good luck ~~~~~

---

### Post by gordintoronto on 2011-11-25
Another option is to use a camera.

---

### Post by r_mano on 2011-11-25
Well, this is quite convoluted but "should" work. At least, it works if you are logged in, I never tried otherwise.

Previous: install imagemagick: 

```
sudo apt-get install imagemagick
```

Now it's a bit tricky, but well... when you are on the login screen, press 
ctrl-alt-F1. You are switching to a text-only console, and you will have a text-only login. Do the login as ever, you'll have a shell prompt. Go to the folder where you want the shot (for example, Desktop):

```
cd Desktop
```

Issue the following command: 

```
sleep 10 && import -display :0 -window root shot1.png
```

(all in one line). Press return and switch rapidly to the graphic console with Alt-F7. After 10 seconds (that's the "sleep 10" thing) a shot will be taken --- there will be no feedback so just count till 10 slowly. Now login and see if it worked. 

By the way, remember to come back to the ctrl-alt-F1 console and logout with "exit".

---

### Post by r_mano on 2011-11-25
> **r_mano said:**
> Well, this is quite convoluted but "should" work. At least, it works if you are logged in, I never tried otherwise.


:(

Ok, tested, doesn't work, problems with permission I suppose (cannot open display :0). Maybe some developer/expert can use the info to find a working trick...

---

### Post by Frogs Hair on 2011-11-25
I am no expert , but I don't think there is a way to use an application before you have logged in .

---

### Post by r_mano on 2011-11-25
Yes, but you can log in in a tty console and have a X server running on another one. The trick I posted will work if you are logged into the graphic session too, so it must be some trick --- or the login screen is not a normal X session?

---

### Post by r_mano on 2011-11-25
...yes, it was a permission thing. Check: 

[http://www.howtoforge.com/how-to-take-a-screenshot-of-your-login-screen](http://www.howtoforge.com/how-to-take-a-screenshot-of-your-login-screen)

and

[http://askubuntu.com/questions/43458/how-can-i-take-a-screenshot-of-the-login-screen](http://askubuntu.com/questions/43458/how-can-i-take-a-screenshot-of-the-login-screen)

will try as soon as I have to log-out (which I do seldom, really :P)

---

