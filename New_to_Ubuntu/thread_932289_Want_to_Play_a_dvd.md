---
title: "Want to Play a dvd"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by gotanothergrot on 2008-09-28
I Want to Play a dvd but can't, not sure what to do next,

 /home/graham/Desktop/Screenshot.png

---

### Post by fooman on 2008-09-28
simplest solution may be to install vlc:

```
sudo apt-get install vlc
```

here is a great guide for getting *all* your mulimedia up and running:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by gotanothergrot on 2008-09-28
Thanks.
Is the code in that place called terminal?

---

### Post by fooman on 2008-09-28
sorry,  yeah...open a terminal (applications > accessories > terminal)

type or copy/paste the following:

```
sudo apt-get install vlc
```

hit enter,  then type your password followed by enter again.

---

### Post by epicmono on 2008-09-28
Applications-->Accessories-->Terminal

Copy this code: sudo apt-get update
Paste in the terminal and hit enter.

Copy this code: sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Paste in the terminal and hit enter.

When you hit enter the first time, the terminal will ask for the root password. For security reasons you will not see anything while typing the password. But that doesn't matter, just type the password and hit enter.

Applications-->Sound & Video-->VLC Media Player

Ctrl+D and hit enter. If dvd doesn't play then,

Ctrl+D, type **/cdrom** in the customize box at the bottom and hit enter.



These are the solutions to the problems that I faced once. Peace.

---

### Post by szymon_g on 2008-09-28
type

sudo aptitude install libdvdcss2

(if it will give errors try to install libdvdcss - i'm not on ubuntu now, so i'm not sure which one is a right one :~)

---

### Post by steveneddy on 2008-09-28
From a link in my sig:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron)

---

### Post by gotanothergrot on 2008-09-28
wow!!! done that,my first thing with terminal, now thats finnished shall i just close it?

---

### Post by epicmono on 2008-09-28
yeah... start it again if u like... in the top panel right click 'Add to panel' and then select the terminal... so then just click that everytime u want to open the terminal...

---

### Post by fooman on 2008-09-28
well,  i'm not sure where your at...but yeah,  close the terminal window.

if you installed vlc...then go to applications > sound and video > vlc

see if it will play a dvd.

---

### Post by gotanothergrot on 2008-09-28
here goes,
Clint Eastwood in the drawer, 


Totem is still telling me error, Could not read from resource.


Shall i reboot??

---

### Post by fooman on 2008-09-28
reboot should not be necessary.  when dvd loads up,  close totem.

go to applications > sound and video > vlc

when vlc opens,  click on file > open disc

it should show the dvd thats in the drawer...click ok and it see if it plays.

---

### Post by gotanothergrot on 2008-09-28
> **epicmono said:**
> Applications-->Accessories-->Terminal

Copy this code: sudo apt-get update
Paste in the terminal and hit enter.

Copy this code: sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Paste in the terminal and hit enter.

When you hit enter the first time, the terminal will ask for the root password. For security reasons you will not see anything while typing the password. But that doesn't matter, just type the password and hit enter.

Applications-->Sound & Video-->VLC Media Player

Ctrl+D and hit enter. If dvd doesn't play then,

Ctrl+D, type **/cdrom** in the customize box at the bottom and hit enter.



These are the solutions to the problems that I faced once. Peace.


Tried the above also still not working,

sorry to be a pain but i will keep trying, thanks for the help so far......

---

### Post by gotanothergrot on 2008-09-28
Think i have found the problem:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

After installing the needed packages, ( in terminal) any help please.

---

### Post by sdowney717 on 2008-09-28
try this one, should work!

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/)


[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

here is a general guide

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

### Post by mc4100 on 2008-09-28
> **gotanothergrot said:**
> Think i have found the problem:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

After installing the needed packages, ( in terminal) any help please.
Open the Terminal, again; type the following:
```
sudo dpkg --configure -a
```
And then, when it's finished, you can close it.

---

### Post by panhandle on 2008-09-28
Carefully read the pertinent sections and use this tutorial:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It is reliable and well composed. I have used it many times on a number of machines and though there are no guarantees, it may very well help.

---

### Post by kkkkatie on 2008-09-28
hey,
my technical knowlage is about this level...normally dad bails me out...how can i stop it automatically opening with totem movie player which doesn't like the vob files????

---

### Post by kkkkatie on 2008-09-28
> **mc4100 said:**
> Open the Terminal, again; type the following:
```
sudo dpkg --configure -a
```
And then, when it's finished, you can close it.

i tried this and terminal did nottin...do i need to have commands beforehand..tried it in a clean terminal

---

### Post by gotanothergrot on 2008-09-29
> **panhandle said:**
> Carefully read the pertinent sections and use this tutorial:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It is reliable and well composed. I have used it many times on a number of machines and though there are no guarantees, it may very well help.

Well i persevered and followed all the steps needed and Hey Presto..

 Thanks in order... 

Now wheres the solved button

---

### Post by crjackson on 2008-09-29
This is my personal magic bullet for all things codec, player, and java.  Works everytime for me. ymmv...:)

Open a terminal screen and past the following code in one shot.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by gotanothergrot on 2008-09-29
> **crjackson said:**
> This is my personal magic bullet for all things codec, player, and java.  Works everytime for me. ymmv...:)

Open a terminal screen and past the following code in one shot.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

WoW, Just put that one in,, thanks crjackson

---

### Post by crjackson on 2008-09-30
> **gotanothergrot said:**
> WoW, Just put that one in,, thanks crjackson

You're welcome. If it was helpful, please click the thank you button (little gold star at the bottom right of the post) for me. I'm collecting them :D

---

