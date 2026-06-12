---
title: "A starting point"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by North_Star_ on 2008-05-06
Ok, I'm new. I have a few questions. If you don't mind. I have 32 bit 8.04 hardy

What is the "SUPER" button, CompuFuzion has it as a bind.

How do i customize the cube and backround in compiz? I inserted links in the compiz settings for both .png and .jpg files, nothing worked.


Also how to a start a program from terminal?

And most important, PLEASE help me get wine and steam running. I've trying since last monday and can't get it to work. Currently I have wine installed and steam and ie6 through terminal. When IE6 launches all i can see is a blank white screen. When I try to start counter strike source I get a message saying I need to install the latest directx from ms. I have no idea what to do here. I can use terminal with some reading, I appriciate any help, thanks.

would 64 bit hardy work better? the only windows programs i need are internet explorer and steam. well i really don't need ie

---

### Post by tamoneya on 2008-05-06
super button is the windows key.

type ccsm in terminal to customize compiz

to start a program in terminal you typically just type its name eg:```
firefox
```

you wont find it any easier in 64 bit linux.  64 bit is if anything a little bit more difficult primarily because of problems with flash.

---

### Post by mapes12 on 2008-05-06
You would be best to ask one question at at time. Can't see why you need anything windoze ish like wine or Internet Explorer?? Can you provide any additional configuration info for these please.

---

### Post by kestrel1 on 2008-05-06
It depends on what programs you want to be able to run from the terminal.
With regard to Wine & Steam, I no longer use them. Wine only works with some programs.
A better way to run Windows progs is to install a virtual machine such as VirtualBox & run Windows from there.
Find VirtualBox here: [http://www.virtualbox.org/](http://www.virtualbox.org/)
You can get IE6 to run via Wine, but I wouldn't recommend it. Install a VM & do it that way.
This is only my opion, others may think differently.

---

### Post by North_Star_ on 2008-05-06
**Didn't see the above, I'll try virual box. thanks man**




thank you, I hate to wear out my welcome but do you have any advice to get steam and counter strike source running? I get a direct x error. I read alot of different material on wine. Some on terminal installs, some on wine door installs. Many mention differnt things like replacing dll files to get rid of the directx error and replace ie6 with mozilla, but none mention how to do that. Also what on earth is a repository. I'm assuming it's nothing more than supporting files. I don't mind reading if you have any guide suggestions, I've already tried alot of different stuff with wine guides on this forum already though, I can't figure out what i'm doing wrong. I'm guesing it's a dll problem, well any help is appriciated. Only goal is steam and css.

---

### Post by Catalyst2Death on 2008-05-06
the "super" button is the button with the windows logo on it. On a mac I think its the funny looking button. but I'm not sure because I don't use mac...

You need to install a plugin to have multiple desktop backgrounds... I'm not sure how to do that.

For the background, I think there are certain conditions on how they're formatted again, I'm not sure.

As for wine and steam... I could never get it working until I used playonlinux which is very nice.
Instructions for getting wine:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

after following those, then type:

```
$sudo apt-get update
$sudo apt-get install wine

```
and for PlayOnLinux:

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Finally, or more appropriately, to do these things, you need to type commands in the terminal which is found at:

Applications>Accessories>Terminal

You'll probably want to put a shortcut on the startbar or on the desktop, just drag the icon onto the desktop... 

Personally, I have the terminal bount to Ctrl+`  which can be done by going to:
System>Preferences>Keyboard Shortcuts
and selecting open a terminal followed by the key you want to bind to it.


Subtle suggestion, and I realize that you won't want to hear this but, DON'T use compiz... It is a resource hog, and it breaks ATI direct rendering.  You system will run much better if you turn it off.

When I started using ubuntu, I insisted on having all of the glitz of compiz, and after much headache and bad driver installs, I finally realized that its not worth the resource hit...

Proprietary drivers are a must if you are going to play games!

---

### Post by Catalyst2Death on 2008-05-06
Sorry, I was too slow...

The repository is a server which hosts all the packages that are available using apt-get or synaptic package manager..
packages are bundles of files and scripts which usually install programs and utilities, but they can also be libraries and development files for writing your own software.

---

