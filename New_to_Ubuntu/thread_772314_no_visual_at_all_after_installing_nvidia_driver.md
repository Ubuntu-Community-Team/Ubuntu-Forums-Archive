---
title: "no visual at all after installing nvidia driver"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ming on 2008-04-28
hi all, 
i had just installed it and played around with it.
however after i installed the hardware driver of my video card, nvidia and was prompted to restart ... i did so and once it restarted, although i can hear the startup sound, there is no visual at all. the only way i can see anything again is to reinstall ubuntu but the max resolution i can put is only 800 by 600 without installing the video driver. 
hope that someone can enlighten me.

---

### Post by alienexplorers on 2008-04-28
What model nvidia card are you using?

---

### Post by martrn on 2008-04-28
> **ming said:**
> hi all, 
i had just installed it and played around with it.
however after i installed the hardware driver of my video card, nvidia and was prompted to restart ... i did so and once it restarted, although i can hear the startup sound, there is no visual at all. the only way i can see anything again is to reinstall ubuntu but the max resolution i can put is only 800 by 600 without installing the video driver. 
hope that someone can enlighten me.

What do you mean by there is no visual at all ?  If you hold down <ctrl> <alt> <bspc> will it resart the x-server ?

after installing the driver have you tried typeing at a terminal
```
sudo dpkg-reconfigure xserver-xorg
```
to edit your /etc/X11/xorg.conf files and check you have the correct /etc/X11/xorg.conf  settings ?

What kernel are you using ?
```
uname -r
```

I am presume you aare talking about a black screen and not any freezeing and lock-ups.

---

### Post by ming on 2008-04-28
> **alienexplorers said:**
> What model nvidia card are you using?

i am using 6800gs

---

### Post by ming on 2008-04-28
> **martrn said:**
> What do you mean by there is no visual at all ?  If you hold down <ctrl> <alt> <bspc> will it resart the x-server ?

after installing the driver have you tried typeing at a terminal
```
sudo dpkg-reconfigure xserver-xorg
```
to edit your /etc/X11/xorg.conf files and check you have the correct /etc/X11/xorg.conf  settings ?

What kernel are you using ?
```
uname -r
```

I am presume you aare talking about a black screen and not any freezeing and lock-ups.

thanks for replying so promptly, i am checking out if pressing ctrl alt bspc will result in x-server(which i don't comprehend)
i have not type at a terminal ... i am a real noob ... oh man it sounds difficult ...

---

### Post by ming on 2008-04-28
i did the ctrl alt bspc for many times until it tells me to wait for 2 min b4 doing it again. 

the problem is .. i cant see anything at all after ubuntu has loaded finish the bar at startup ... so i cant do anything as well

what i did b4 this happened was that i went into ubuntu and "enabled" the hardware driver for nvidia and then restart as prompted. 

T_T what should i do now?

---

### Post by gusjones on 2008-04-28
Do you have a second monitor handy by any chance? If so, then try powering down, replacing the monitor (assuming it is a different make and model) and powering up again. It may be that your graphics card driver is fine but that Ubuntu is not picking up your monitor correctly.

---

### Post by martrn on 2008-04-28
> **ming said:**
> i had just installed it and played around with it.
however after i installed the hardware driver of my video card, nvidia and was prompted to restart ... i did so and once it restarted,

[..]

> **ming said:**
>  although i can hear the startup sound, there is no visual at all. the only way i can see anything again is to reinstall ubuntu but the max resolution i can put is only 800 by 600 without installing the video driver. hope that someone can enlighten me.

when you say you can't see anything again, do you mean, you get a lockup - or do you mean - It boots grub, then boots and goes black ?  - I don't get i can hear the startup sound, there is no visual at all.

I cant understand how it boots grub and then after installing a kernel module (driver), it go black but doesn't boot grub any-more.... ????

...??? 

If you wan't anyone to give you an answer, sometimes it helps to be more desriptive than less descriptive.

<ctrl> <alt> <bspc>   just means :-
Hold the control button down, hold the alt key down and tap the backspace key.

---

### Post by ming on 2008-04-28
oh ... here is what happens after i had "enabled" the driver ... when i load ubuntu ... i can see the loading bar at the beginning ... and then after it loads finish, the screen goes blank and at the same time i hear "some sound" which sounds like the start up sound(i am not totally sure becos i had only heard it a few times b4 this mishap)
the monitor goes blank as in ... it is like switching on the monitor's power without booting on the computer. by the way, i typed on my keyboard and i hear beeps beeps ... like how the keyboard responds whenever the system hangs
sorry for being quite vague ... if there is anything else i have not describe please let me know ... thanks
oh ya .. with regards to the <ctrl> <alt> <bspc>, i did it ... and it responded by making a sound from the monitor(not computer) but then there is no visual still .. it's like struggling to come alive but went dead quickly whenever i do the <ctrl> <alt> <bspc>

---

### Post by ming on 2008-04-28
oh ... here is what happens after i had "enabled" the driver ... when i load ubuntu ... i can see the loading bar at the beginning ... and then after it loads finish, the screen goes blank and at the same time i hear "some sound" which sounds like the start up sound(i am not totally sure becos i had only heard it a few times b4 this mishap)
the monitor goes blank as in ... it is like switching on the monitor's power without booting on the computer. by the way, i typed on my keyboard and i hear beeps beeps ... like how the keyboard responds whenever the system hangs
sorry for being quite vague ... if there is anything else i have not describe please let me know ... thanks
oh ya .. with regards to the <ctrl> <alt> <bspc>, i did it ... and it responded by making a sound from the monitor(not computer) but then there is no visual still .. it's like struggling to come alive but went dead quickly whenever i do the <ctrl> <alt> <bspc>

---

### Post by ming on 2008-04-28
hi ... i do not have a second monitor ... i doubt my monitor is having problem because i have been switching to and from windows every now and then... though i am using lappy to post forum now ...

---

### Post by alienexplorers on 2008-04-28
What nvidia driver are you using?  can you post your xorg.conf file?

---

### Post by ming on 2008-04-28
i am not sure what driver i used ... and how do i go about looking for the xorg.conf file?

---

### Post by nineowls on 2008-04-28
> **ming said:**
> and how do i go about looking for the xorg.conf file?
i tried typing [HTML]xorg.conf[/HTML] into a Google search
the first result is the man (manual) page for xorg.conf
I went there
right at the top there is a Description that indicates 
i can look for xorg.conf in /etc/X11/
[HTML]ls /etc/X11[/HTML]
wow--I have 36 backups of xorg.conf and one xorg.conf
:guitar:

---

### Post by martrn on 2008-04-28
You would need to have accsess to your machine to do this, boot up the cd in recovery mode or from a live distro and from a terminal/xwindows type

for X11 you would type at a terminal
```
gedit /etc/X11/xorg.conf
```

from a terminal (or command line interface) you would type
```
nano /etc/X11/xorg.conf
```

and post the contents of you X11 file.
and someone might know what is wrong with it.

---

### Post by ming on 2008-04-28
i tried doing wat was suggested .. but i have no idea how to show u guys the file. anyway after i did that i restarted the computer as i have no idea what to do nx ... and amazingly ... i am able to log into ubuntu! 
now i am trying to install the driver from nvidia's website but after d/ling the file i do not know how to open it.

qns: what is the proper way to change resolution? i do it thru system > preferences > screen resolution ... but max resolution is juz 800 by 600

cheers

---

### Post by martrn on 2008-04-28
> **ming said:**
> i tried doing wat was suggested .. but i have no idea how to show u guys the file. anyway after i did that i restarted the computer as i have no idea what to do nx ... and amazingly ... i am able to log into ubuntu! 
now i am trying to install the driver from nvidia's website but after d/ling the file i do not know how to open it.

qns: what is the proper way to change resolution? i do it thru system > preferences > screen resolution ... but max resolution is juz 800 by 600
cheers

Please Read [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") for how to install the nvidia drivers from the nvidia site.  The is not the offical 'ubuntu' recommended way, but imho this works very well, however please be sure to read this before installing the drivers, as the process is quiet difficult.

Please double check your settings in your 
```
sudo gedit /etc/X11/xorg.conf
```
file.

And make sure you monitor resolution and everything is set correctly first before you do anything.

If you know the exact displaymodes your monitor is capebel of displaying before proceeding note them down. And then,
```
sudo dpkg-reconfigure xserver-xorg
```
Don't think you can guess here you need your monitor setting and the resolution it is capable of displaying, and frequency settings etc, and you need to know the number of keys on your keyboard, and the number of buttons on your mouse, etc.....  But this is the way to change your max resolution :

From a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

Look for a program called terminal console to start a terminal (command line interface).

=================

[TO ADD]
Just to recap.
1. Open a terminal
2. Configure X11 properly by *[COLOR="SeaGreen"]sudo dpkg-reconfigure xserver-xorg[/COLOR]*
3. Then download nvidia drivers
4. Follow [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

