---
title: "Monitor loses signal randomly"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by Dan Law 001 on 2013-01-21
Hello, this is a problem related to the monitor. In fact, after booting into the OS, often the monitor loses signal randomly in the moment I hear some noises from the computer (it may come from the hard disk but I am not quite sure) and a message "No Signal" will be displayed and it seems that it goes to some kind of sleep mode after in the way that I can not turn it back on. This happens everywhere, including the Log on screen.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Have you checked to see if your monitor cable is either 1) torn, bent, ripped or 2) plugged in right? Make sure you have it in properly. Please see this link, as another had your problem and I did as well. Same thing worked for me, oddly.

[http://www.computerhope.com/forum/index.php?topic=110828.0](http://www.computerhope.com/forum/index.php?topic=110828.0)

I'm curious. Did you install any GPu drivers? Here is a workaround I want to see if it works. Press "ctrl+alt f1" when you get to the login screen, regardless of if you can see it or not, and then "ctrl+alt f7". Those commands connected by the "+" must be hit at the same time.

---

### Post by Dan Law 001 on 2013-01-21
Thanks for your suggestion, I'll try the command tomorrow. By the way, that will not be a wire problem since it works perfectly on other platform.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Very well, I hope it helps though. If it does, be sure to mark this thread as solved so others know it helps if they come across the same problem. And for me, even though my VGA cord works in Windows or Linux Mint, it refuses to work in Ubuntu 12.04, so either way it is worth a shot switching cords or cord types.

Good luck and comment back if it doesn't help.

---

### Post by Dan Law 001 on 2013-01-22
OK, I tried the commands on the login screen and it brings me to a "black screen" with white letters where it asks me to enter the ubuntu login (I believe that it is my user name). So, I entered the user name, and it asks me to enter the password. However, it seems that it doesn't recognize what I type as I can not see my password on the display and the cursor doesn't move at all. When I enter that screen, must I enter all the information or simply just type the command ctrl+alt f7 to get back?

Information about my computer: Acer Aspire with Nvidia GeForce GT220 1024MB

Ubuntu 10. (something) I will tell you after I check.

---

### Post by Lightning Dragon on 2013-01-22
Hello,

This is the CLI, you will not see a mouse cursor and it is standard that the terminal does not show you typing your password. It will always appear blank. Just type your password regardless of being able to see it. It will be exactly like your login details.

You can try the command without logging it, but I have always logged in before I did that.

Ah, I knew it was the culprit. Did you happen to install Nvidia drivers before you reboot/shutdown?

---

### Post by Dan Law 001 on 2013-01-22
Ok, I just figured it out that I use the wrong username. So I enter my username and my password and it shows the welcome message and the rest and it shows a message like this: daniel@ubtuntu:"$ 

What should I do now. If I enter the command "ctrl+alt f7", it will exit.

---

### Post by Dan Law 001 on 2013-01-22
No, I did not install anything (include Nvidia driver) since I am not even connected to the internet.

---

### Post by Lightning Dragon on 2013-01-22
Hello,

Alright, if drivers were not installed before this issue or whatnot, then try the combo "ctrl+alt f7". And you made sure you didn't "type" the command, right? It should bring you to the Ubuntu login screen or desktop if pressed, not exit you out.

What type of monitor cord are you using? If your GPU can support a VGA or DVI, or even HDMI, please try switching to a different output. For example, if you are using DVI, try VGA. This made it so it could boot into the rest of the computer for some users.

There are also these fixes;

[http://ubuntuforums.org/showthread.php?t=1969751](http://ubuntuforums.org/showthread.php?t=1969751)
[http://ubuntuforums.org/showthread.php?t=1969868](http://ubuntuforums.org/showthread.php?t=1969868)

---

### Post by Dan Law 001 on 2013-01-23
I mean "exit" as it brings me back to where I was either login screen and desktop before doing the command Ctrl+alt f1 and its basically what you said in the previous reply. By the way, what should I do as it displays daniel@ubuntu:"$ as mentioned. Do I need to enter something or just the command Ctrl+Alt f7 that brings me back to where I was? Also, I am using DVI cable and I will try to change the video cable as soon as possible to see what will happen.

---

### Post by Lightning Dragon on 2013-01-23
Hello,

Ah, I see. The command combo I gave you was supposed to take you into the Ubuntu GUI login screen. If switching the video does not work, trying putting the monitor cord into your on board GPU (on board monitor port) and try to boot off of on board (no external GPU equipped). 

If neither of those works for you, in the interface you are in (after logging in) try this (and make sure you are in tty *CTRL+ALT F1*);

sudo /etc/init.d/gdm restart

Or

sudo service gdm restart
 
And tell me if this does anything for you. If the commands say they don't exist, switch out "gdm" with "lightdm". If that doesn't work, try the command "startx" and once again if that doesn't work, get the log for X by doing;

/var/log/Xorg.0.log | grep EE

Finally, if that rewards you with nothing, try pressing ESC or SPACE depending on your GRUB to get the GRUB menu and seeing if you can boot into the GUI that way OR you need to set nomodeset. See the following link concerning nomodeset;

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Also, while in the command line, perform an update;

sudo apt-get update

EDIT:

Does your monitor have an "auto detect" button on it? If so, I have found pressing it when getting the "signal out of range" problem in the CLI to work. It only brings the monitor back to life for about 1 minute or two, but it should be more than enough to run commands needed. And if not, just press the detect button again.

How I found the solution? I purposely gave myself the issue so I could find workarounds.

---

