---
title: "Screen blackout"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Applesauce on 2011-11-16
I am having trouble with this since I switched from 11.04 to 11.10.
If I allow the computer to sit until it goes into sleep mode it will not wake up. When I try to get it going again I get a totally black screen with a purple strip across the top.

I cannot get it to respond to anything when it does this, and the only thing I could do was force a shutdown by holding the power button.

Did anyone else have anything like this? I am fairly new to Ubuntu, so I need all the help I can get. Thanks in advance.

---

### Post by Sealbhach on 2011-11-16
You can change the length of time before sleep mode in the power management settings. Also if you find the screen is unresponsive do Ctrl+Alt+F1 (or F2) and log in at the login prompt. Then run the command

```
sudo service gdm restart
```

Which will get you back to the login screen again. It's better than rebooting. I've no idea how to fix your problem with the screen freezing. :oops:

.

---

### Post by David006 on 2011-11-16
Check that this not the same issue as:

Unable to Resume after Screen has Locked
[http://askubuntu.com/questions/73117/unable-to-resume-after-screen-has-locked/77757#77757](http://askubuntu.com/questions/73117/unable-to-resume-after-screen-has-locked/77757#77757)


The workaround is to remove: gnome-screensaver

---

### Post by Applesauce on 2011-11-17
Well thanks for the ideas, I will try them and see if I can get a response out of this thing.

---

### Post by Applesauce on 2011-11-17
I intentionally left it go into suspend mode, just to try it out. I cannot get any key combination to do anything.
Ctrl-Alt-F1 or F2 gets no response at all. The screen is totally black except for about a 1/2" at the top. From the little I can see it looks like the Debian Universal boot page.(or whatever its called, I'm a newb)
It is a Compaq laptop and it has a little LED for the hard drive activity, and I noticed that it is not lit or blinking at all. I wonder what that means?
It is sitting here right now with screen blacked out. Any more stuff to try?

---

