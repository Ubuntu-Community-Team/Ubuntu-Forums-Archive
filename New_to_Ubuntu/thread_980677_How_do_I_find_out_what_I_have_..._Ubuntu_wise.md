---
title: "How do I find out what I have ... Ubuntu wise?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Yumpin_Yimminie on 2008-11-13
[FONT="Arial"][SIZE="3"]In my computer I have an 'ATI x300' video card to drive dual monitors.  Searches through the forums here show that it is a pain in the rear to configure things to be able to use the assets this card offers.  

So I decided to go to the manufacturers website and look for help.  Little poking around got me to this page: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_810_linux.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_810_linux.html")

So now I know what to do.  I just don't know how to do it!](*,)

I have installed Ubuntu 8.10.  That much I do know.  Now the instructions say:

[B][I]Before attempting to install the ATI Catalyst™ Linux software suite, the following software must be installed:

    * XOrg 6.8, 6.9, 7.0, 7.1, 7.2 or 7.3
    * Linux Kernel 2.6 and above
    * glibc version 2.2 or 2.3
    * POSIX Shared Memory (/dev/shm) support is required for 3D applications[/I][/B]


So how do I go about checking to find out if the above software is installed?

Help would be very much appreciated.

Thank you.

Have a Great Day,
Jim[/SIZE][/FONT]

---

### Post by cdtech on 2008-11-13
Use the command:
```
apt-cache show pkg
```
This will give the information about the installed package.

To find your kernel version:
```
uname -r
```

Hope this helps ya.....

---

### Post by Paqman on 2008-11-13
You could also just open Synaptic and search for those packages, it'll show what version you have installed.

---

### Post by Yumpin_Yimminie on 2008-11-13
[FONT="Arial"][SIZE="3"]Quick response.[B] Thank you for taking the time to respond.  
[/B]
The first code you gave:  

```
apt -cache show pkg 
```

gave me the response:

jim@Dell:~$ apt-cache show pkg
W: Unable to locate package pkg
E: No packages found


The second code you gave:

```
 uname -r 
```

gave me the response:

jim@Dell:~$ uname -r
2.6.27-7-generic

I appreciate your help.

Thank you!

Have a Great Day,
Jim




[/SIZE][/FONT]

---

### Post by Yumpin_Yimminie on 2008-11-13
> **Paqman said:**
> You could also just open Synaptic and search for those packages, it'll show what version you have installed.

[FONT="Arial"][SIZE="3"]Thanks for taking the time to respond.

I did open Synaptic and tried searching for the packages.  And got no where really slowly.  

Searching for **XOrg** I got a bunch of listings and one of them was:

XOrg                    1:7.4~5ubuntu3

which I assume will meet the criteria for that software package.

when I searched for **glibc**  I got the following packages that have been installed:

linux-libv-dev          2.6.27-7.14
libnss-mdns             0.10-3ubuntu2
libgqz2                 0.0.14.1-1build1

So I'm not sure if I have that package or not.  Because it doesn't read 'glibc'


Then **POSIX** is a nightmare of listings and I don't have a clue if they fit the parameter I am supposed to have.

dash                      0.5.4-ubuntu 1
libcap                    2.10-1
libcap1                   1:1.10-14 build 1
libac|1                   2.2.47-2
libpulse0                 0.9.10-2ubuntu9
locales                   2.7.9-5
libpulsecore5             0.9.10-2ubuntu9
bc                        1.06.94 3ubuntu1
pulseaudio-esound-compat  0.9.10-2ubuntu9
pulseaudio-module-gconf   0.9.10-2ubuntu9
libpath20                 2.07-10
pulseaudio                0.9.10-2ubuntu9
bash                      3.2-4ubuntu1
libpulse-browser0         0.9.10-2ubuntu9
gstreamer0.10-pulseaudio  0.10.10.4.1ubuntu1
pulseaudio-module-x11     0.9.10-2ubuntu9
mawk                      1.3.3-11.1ubuntu1
pulseaudio-utils          0.9.10-2ubuntu9
libarchive1               2.4.17-2
pulseaudio                0.9.10-2ubuntu9


If anybody could help I'd appreciate it because I'm kind of lost.  I don't speak Ubuntu.
[/SIZE][/FONT]

---

### Post by Tomatz on 2008-11-13
They will already be installed ;)


Once installed add the options below to the **"device"** section in **/etc/X11/xorg.conf** to allow you to use the s-video and dual monitors:


Dual monitors:

```
Option  "ForceMonitors" "lvds,crt1"
```


S-video:

```
Option  "ForceMonitors" "lvds,tv"

```

---

### Post by Yumpin_Yimminie on 2008-11-13
> **Tomatz said:**
> They will already be installed ;)


Once installed add the options below to the **"device"** section in **/etc/X11/xorg.conf** to allow you to use the s-video and dual monitors:


Dual monitors:

```
Option  "ForceMonitors" "lvds,crt1"
```


S-video:

```
Option  "ForceMonitors" "lvds,tv"

```

[SIZE="3"][FONT="Arial"]**Thank you very much for taking time to respond**.  I am definitely a neophyte when it comes to Ubuntu/Linux.  I found the file and the section of the file where you stated to put in the line for dual monitors.  I typed it in.  Then when I went to save ... it wouldn't let me do it.  ](*,)  It gave me a message that I didn't have the necessary permissions or something like that.  I'm the only person on this system.  I installed it on the computer, I'm the only user. [SIZE="1"] help[/SIZE] ...** please**!!

Thank you.

Have a Great Day,
Jim[/FONT][/SIZE]

---

### Post by Tomatz on 2008-11-13
> **Yumpin_Yimminie said:**
> [SIZE="3"][FONT="Arial"]**Thank you very much for taking time to respond**.  I am definitely a neophyte when it comes to Ubuntu/Linux.  I found the file and the section of the file where you stated to put in the line for dual monitors.  I typed it in.  Then when I went to save ... it wouldn't let me do it.  ](*,)  It gave me a message that I didn't have the necessary permissions or something like that.  I'm the only person on this system.  I installed it on the computer, I'm the only user. [SIZE="1"] help[/SIZE] ...** please**!!

Thank you.

Have a Great Day,
Jim[/FONT][/SIZE]

PM'd you back :)

---

### Post by Yumpin_Yimminie on 2008-11-13
[SIZE="3"][FONT="Arial"]Well a very long day and a bad cold I think are interfering with my brain.  I sure do appreciate your help.

Have a Great Day,
Jim[/FONT][/SIZE]

---

