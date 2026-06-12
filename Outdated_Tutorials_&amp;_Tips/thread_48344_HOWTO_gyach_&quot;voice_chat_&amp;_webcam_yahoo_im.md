---
title: "HOWTO: gyach &quot;voice chat &amp; webcam yahoo im client&quot;"
date: 2005-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by drews_blunted on 2005-07-12
Gyach-Enhanced-pYVoiceChat is a program that will alow you to use your mic and webcam in a yahoo chat. You can find out more at there webpage: [http://www.phrozensmoke.com/projects/pyvoicechat/](http://www.phrozensmoke.com/projects/pyvoicechat/)

To get and install do the following commands:
> 
wget [http://www.bongload.org/files/linux/gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb](http://www.bongload.org/files/linux/gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb)

sudo dpkg -i gyach-enhanced-pyvoicechat-1.0.7-2.i386.deb

gyach

This was tested and works on my i586 AMD, Ubuntu hoary machine. Let me know if anyone has any problems.

The program requires the following files.
I already had all of this installed on my system.
I am not sure if its all standard with hoary.

Requires

    * python
    * pygtk >= 0.6.6
    * /usr/bin/env
    * ld-linux.so.2
    * libasound.so.2
    * libatk-1.0.so.0
    * libaudiofile.so.0
    * libc.so.6
    * libdl.so.2
    * libesd.so.0
    * libexpat.so.0
    * libfreetype.so.6
    * libgdk_pixbuf-2.0.so.0
    * libgdk_pixbuf_xlib-2.0.so.0
    * libgdk-x11-2.0.so.0
    * libglib-2.0.so.0
    * libgmodule-2.0.so.0
    * libgobject-2.0.so.0
    * libgthread-2.0.so.0
    * libgtkhtml-2.so.0
    * libgtk-x11-2.0.so.0
    * libltdl.so.3
    * libm.so.6
    * libpango-1.0.so.0
    * libpangox-1.0.so.0
    * libpangoxft-1.0.so.0
    * libpthread.so.0
    * libX11.so.6
    * libXext.so.6
    * libXft.so.1
    * libXi.so.6
    * libxml2.so.2
    * libXrender.so.1
    * libz.so.1

---

### Post by nickj6282 on 2005-10-06
You are my new best friend!!! I've been racking my brain on how to get webcam support under Yahoo. I tried ayttm but it would just blank out. My girlfriend and I thank you, now we can use our cams to chat since it's hard to be together at different colleges!

Thanks again!
-Nick

---

### Post by Trullo on 2005-10-07
thanks man! it works really well, and with lot of features.. nice! =D&gt;

---

### Post by brentroos on 2005-10-08
*

---

### Post by fakie_flip on 2005-10-16
I got it the software to come up, but I can't use voice chat or webcam. Is the pvoice thing a seperate download from gyatch that I have to get? I can never get a window to come up that says push button to talk on mic and mic volume ect. I downloaded all the required packages. Before that the program would not work, so I must of got them all. I used alien -d to convert the rpm package to a deb that I got from the official website. The chat and IM works fine, but I have gaim to do that. Do I need a seperate plugin to get the mic working or a seperate one for webcam to work? Neither are working. I was able to send a voice mail to someones email using sip with my mic, so I must have the right drivers for a mic. Are special drivers needed for webcam? I have a standard Logitech webcam and Ubuntu Hoary 5.04. Also I run it from a terminal with the command gytch because I do not have it in the menu. I get alot of output in the terminal when I am running it. Sometimes the program will just disappear and I have to start it again. I am not sure, but the output in the terminal could be errors.

---

### Post by wasdak on 2005-10-17
Hi,

i got this error after I install gyach

root@ubuntu:~# gyach

(gyach:7517): Gtk-WARNING **: cannot open display:
root@ubuntu:~#

---

### Post by fakie_flip on 2005-10-17
Do not run from root. Login as a normal user and run it.

Can anyone reply to my post above and tell me how to get gyach working?

---

### Post by aldar on 2005-10-20
How about getting this to work with video inputs on an ATI all-iun-wonder card? I can watch TV on my system, so I know that works. I just don't know the /dev to put into gyach to tell it to use that as my webcam. Any ideas?

---

### Post by drews_blunted on 2005-10-21
Hey, im glad to see everyone enjoyed my post, this was my first tutorial faq etc. i made for ubuntu!  i have had some success some failure with this program! 

But i have a new solution for those who still wish to do i have found that the new version of macromedia flash works AWSOME with linxu webcam.

do a test to see if yours works too rght clikc and go to settings in any flash movie or video embeded on a website and clikcon the webcam tab! Sure enough it loads a live view of my webcam on my desktop! Also i have found that there is enterprise webcam flash software that works like a perfect video chat!

all in this Gayach tutorial was written for hoary hopefully it still works on Breezy! :KS

---

### Post by BLTicklemonster on 2005-10-27
Endersshadow made a neat way to install it.

[http://ubuntuforums.org/showthread.php?t=82567](http://ubuntuforums.org/showthread.php?t=82567)

---

### Post by illidian on 2005-11-03
i can't find the following file:

[COLOR="RoyalBlue"]libXft.so.1
libXrender.so.1[/COLOR]

where do i get them?

---

### Post by illidian on 2005-11-03
[QUOTE=drews_blunted]Gyach-Enhanced-pYVoiceChat is a program that will alow you to use your mic and webcam in a yahoo chat. You can find out more at there webpage: [http://www.phrozensmoke.com/projects/pyvoicechat/](http://www.phrozensmoke.com/projects/pyvoicechat/)

To get and install do the following commands:

This was tested and works on my i586 AMD, Ubuntu hoary machine. Let me know if anyone has any problems.

The program requires the following files.
I already had all of this installed on my system.
I am not sure if its all standard with hoary.

Requires

    * python
    * pygtk >= 0.6.6
    * /usr/bin/env
    * ld-linux.so.2
    * libasound.so.2
    * libatk-1.0.so.0
    * libaudiofile.so.0
    * libc.so.6
    * libdl.so.2
    * libesd.so.0
    * libexpat.so.0
    * libfreetype.so.6
    * libgdk_pixbuf-2.0.so.0
    * libgdk_pixbuf_xlib-2.0.so.0
    * libgdk-x11-2.0.so.0
    * libglib-2.0.so.0
    * libgmodule-2.0.so.0
    * libgobject-2.0.so.0
    * libgthread-2.0.so.0
    * libgtkhtml-2.so.0
    * libgtk-x11-2.0.so.0
    * libltdl.so.3
    * libm.so.6
    * libpango-1.0.so.0
    * libpangox-1.0.so.0
    * libpangoxft-1.0.so.0
    * libpthread.so.0
    * libX11.so.6
    * libXext.so.6
    * libXft.so.1
    * libXi.so.6
    * libxml2.so.2
    * libXrender.so.1
    * libz.so.1[/QUOTE]


i have all the files execept these two:

[COLOR="RoyalBlue"]libXft.so.1
libXrender.so.1
[/COLOR]
How do i download them?

help please
thnx:D

---

### Post by Ricky-9000 on 2006-02-21
Is there a way to get gyach to appear in my KMenu? Im on Kubuntu Breezy. Sorry for the n00b question, Im new to linux on a pc.

---

### Post by Lizzy on 2006-04-01
Hi, i got gyach to run. The problem is that gyach constantly crashes!! 
Any ideas why? Do i miss something? I thought that the bug was fixed according to their homepage. :-k

---

### Post by sabitha on 2006-04-01
if gyach crash try disable animated smiley on general setup

---

### Post by chocbar31 on 2006-05-11
[QUOTE=drews_blunted]Hey, im glad to see everyone enjoyed my post, this was my first tutorial faq etc. i made for ubuntu!  i have had some success some failure with this program! 

But i have a new solution for those who still wish to do i have found that the new version of macromedia flash works AWSOME with linxu webcam.

do a test to see if yours works too rght clikc and go to settings in any flash movie or video embeded on a website and clikcon the webcam tab! Sure enough it loads a live view of my webcam on my desktop! Also i have found that there is enterprise webcam flash software that works like a perfect video chat!

all in this Gayach tutorial was written for hoary hopefully it still works on Breezy! :KS[/QUOTE]


LOL, I can't tell that you had any problem with this...It's me with the problem. I have installed ubuntu a million times. Not because of trying to install Gyach, but the other stuff that never completed the installation process...like WINE!

Anyways, it took me two friggin days to find this post again, even though I have been here a million times already, and was having a hissy-fit until I found it...bout time, LOL!

I am a Breezy user, date 5/11/2006. Still perfect, as long as I disable the animated smileys.

Thank You a million times!

choc

---

