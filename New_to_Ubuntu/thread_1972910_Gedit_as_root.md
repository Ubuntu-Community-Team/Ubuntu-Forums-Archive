---
title: "Gedit as root"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by MHN on 2012-05-04
I have one c program file.

I ran

$gedit w.c

it worked fine

then I login to root

again

#gedit w.c

I get the following messages.


** (gedit:5583): WARNING **: The connection is closed

(gedit:5583): EggSMClient-WARNING **: Failed to connect to the session manager: 
None of the authentication protocols specified are supported


** (gedit:5583): WARNING **: Could not connect to session bus

...
What is this ? Just curious.

---

### Post by MG&amp;TL on 2012-05-04
The message are from gedit. AFAIK, it means that being root has shut you off from dbus, the thing that lets applications communicate. Don't ask me why though. In the case of gedit, it's probably not harmful.

---

### Post by muteXe on 2012-05-04
This is a really strange coicidence but a guy at work today in the office was saying pretty much the exact same thing. gedit does not work for him when he's logged in as root.
I'd be interested to know if anyone knows why as well as the OP.
Ta.

---

### Post by mörgæs on 2012-05-04
If this is repeatable a bug report should be opened in Launchpad (or the existing one should be confirmed, if it has already been reported).

[https://bugs.launchpad.net/gedit](https://bugs.launchpad.net/gedit)

---

### Post by Morbius1 on 2012-05-04
First of all you seem to be unaware of the official position of our Gnome overlords: Don't use graphical applications as root or gksu - period.

A selected quote from the following bug report: [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404)

> 
[Sam_ (and-sam)]("https://launchpad.net/%7Eand-sam")             wrote             on 2011-10-09:                                                            [ #2]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/2")                                                               Quote comment from upstream developer:
< You shouldn't start GNOME programmes with elevated privileges, it's not
supported. In any case, not a gnome-terminal bug. >

              
                                                                                                                                     [Sean Fitzpatrick (sean-fitzpatrick)]("https://launchpad.net/%7Esean-fitzpatrick")             wrote             on 2011-10-09:                                                            [ #3]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/3")                                   
                            I see.  So does  that make the official GNOME position "editing system files should be  done with nano or similar" or "system files?  why would a user want to  edit a system file?"

              
     
                                                                                                                                [Sam_ (and-sam)]("https://launchpad.net/%7Eand-sam")             wrote             on 2011-10-09:                                                            [ #4]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/4")                                   
                            Yep, from my understanding they don't agree with running graphical apps as root. [Bug #805682]("https://bugs.launchpad.net/bugs/805682")

              
     
                                                                                                            So welcome to the land of yesterday. This might help:
**Linux vi and vim editor**: [http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html)

Seriously, Install leafpad and see if you have the same problem. I run "gksu leafpad /path" when I want to edit something as root only because if you use "gksu gedit /path" it also brings up that irritating second " Untitled Document 1" tab in gedit.

---

### Post by Zill on 2012-05-04
> **MHN said:**
> ...then I login to root...
Please do not login as root.  It is simply not necessary or even desirable with Ubuntu.
> **MHN said:**
> #gedit w.c

I get the following messages.

** (gedit:5583): WARNING **: The connection is closed...
To edit a file with root privileges use the prefix "sudo" for terminal applications and "gksudo" for graphical applications, such as gedit.

See [RootSudo]("https://help.ubuntu.com/community/RootSudo") for further information.

---

