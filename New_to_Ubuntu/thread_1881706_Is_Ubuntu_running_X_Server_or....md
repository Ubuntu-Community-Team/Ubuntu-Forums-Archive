---
title: "Is Ubuntu running X Server or...?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by zghawking on 2011-11-16
Hi
I've been using Ubuntu (11.10) for a week or two, new to linux/unix, learning the ropes.

I noticed in terminal
```
ps a
```That it appears the desktop is running on tty7 a process '/usr/bin/X'

On searching this is something called X server?  I also saw some mention that Ubuntu is not using X server.  I thought it might be Gnome Desktop or Unity.  Maybe these are both implementations of X Server?

---

### Post by jaddi27 on 2011-11-16
Hi,

Ubuntu (and most linux distributions) use X Server as the low level graphics engine. Ubuntu then uses Gnome on top of X Server as the main graphical user interface. Unity is another layout in addition to Gnome that provides the Dash and Launcher that you use to manage applications.

Hope that answers your question
Joel

---

### Post by zghawking on 2011-11-16
Ah okay that is what I was starting to suspect. How can I tell if I'm using Unity or Gnome though?

---

### Post by jaddi27 on 2011-11-16
Gnome is installed on Ubuntu, and you will be using Gnome applications, such as  Nautilus, but the desktop interface will be Unity by default on a clean  install of Ubuntu 11.10.

If you are using a fairly modern computer with adequate graphics capability to run Compiz, then I think you will be using Unity 3D.  If your computer does not have great graphics capability, then you will be using Unity 2D, which does not rely on Compiz desktop effects. Both look similar, but Unity 3D with Compiz offers more visual effects.

If you would like to use the Gnome desktop environment, you can install Gnome Shell from the Ubuntu repositories. A tutorial on installing and setting up Gnome Shell can be found at [http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/), along with many others that are available by searching on Google.

---

### Post by SheaMan on 2011-11-16
is there a terminal command that will report the answer to the question? :guitar:

---

### Post by jaddi27 on 2011-11-16
You can easily test if your computer is capable of running Unity3D using the command:
```
/usr/lib/nux/unity_support_test -p
```
(from [http://askubuntu.com/questions/34579/how-do-i-know-if-my-video-card-can-run-unity](http://askubuntu.com/questions/34579/how-do-i-know-if-my-video-card-can-run-unity))

I also suggest taking a look at [http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d), which has some good details on differentiating the two versions of Unity.

Joel

---

### Post by SheaMan on 2011-11-16
:D frack! I am using a UK keyboard... no ampersand.. :D

"jaddi27 how do I run that command? ( shift £2 = " :confused:  FRACK! shift 3 = £ )

see attached screenshot for (an) explanation of my conundrum.....

---

### Post by jaddi27 on 2011-11-16
Hi SheaMan,

Are you running Ubuntu 11.10? I do not have any problem running that command on my computer, as the file exists. As far as I know, Natty also includes the command (based on [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)):
```
/usr/lib/nux/unity_support_test -p
```You could also try running 
```
ps -ef | grep compiz | grep $USER
```as if this returns a result, it should indicate that you are using Compiz, and hence Unity should be running (on Natty and Oneiric).

Also, where do you need the ampersand? I haven't seen any commands in the links I posted that need ampersands...

---

### Post by SheaMan on 2011-11-16
@jaddi27

forum etiquette, when you are directing a statement at a specific person other than the OP you are suppoda use @user (yeah found it) in text. And no, I am running the LTS distro.

---

### Post by lolpenguin on 2011-11-16
The X Window System is the base for the GUI, while GNOME is the Desktop Environment, and Unity is a shell for GNOME.
To look at the default X server (without any DEs), install X and no DEs on Arch Linux.
To look at the default GNOME, install [_GNOME Classic_]("http://ubuntuforums.org/showthread.php?t=1859960") in Ubuntu

---

### Post by jaddi27 on 2011-11-16
@SheaMan

If you are on 10.04 LTS, that would explain why you don't have that script for the Unity test. However, it looks like your computer has compiz running at the moment, so when you decide to upgrade to a Unity based system, it should hopefully work.

Glad to see you found the 'at' symbol on your keyboard. Apologies for not using the @ tag to refer to you earlier.

---

