---
title: "ubuntu sloweed down to a crawl"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-06-03
ubuntu has just recentley slowed down so much it's like using windows 95 it's dreadfull ive checked system monitor and there's no programs using loads of resources i cant even use the compiz cube effect because it just stalls and stutters, it can take at least five tries to close firefox because ubuntu is to slow to keep up with the mouse and sometimes i will be typing and i will have to wait a minute while the pc catches up:mad: i've been using the pc fine problems started occuring when i got my aluminium apple mac keyboard like a day ago i also installed some updates to day,

please help!

---

### Post by gameryoshi600 on 2008-06-03
What version of ubuntu are you using? If its Hardy then it probably will go slow since it is unstable. did you try reloading compiz fusion or a restart? You should also give Opera try just download the .deb for 9.50 beta 2 as flash and java work out of the box with it.

---

### Post by SunnyRabbiera on 2008-06-03
How much memory are you using?
do you have swap and have you tried restarting your computer?

---

### Post by kamitsukai on 2008-06-03
this is the second time it's happened and a restart is a tempoary fix! i have 2 gigs of ram and a 3gig swap and I'm using hardy

---

### Post by SunnyRabbiera on 2008-06-03
alright, well you are using effects... have you encountered the gnome terminal bug i wonder, does the slowdown happen after you open the gnome terminal?

---

### Post by kamitsukai on 2008-06-03
Yes! I was trying to run nautilus from root and now you mention it, I was using the terminal emulator Yakuake but it wasn't working so I went to the terminal but that didn't work either. The command just stalled!

---

### Post by SunnyRabbiera on 2008-06-03
That might be the source of your issues, as that is what happened to me.
Right now I use roxterm as opposed to the gnome terminal, give that a shot.
Also try xterm too, its a bit primitive but it works.

---

### Post by raven on 2008-06-03
kamitsukai, the way I tackle this issue is
1- first I will put back the old keyboard, if you don't have it just borrow a regular basic keyboard from a friend and try it (since you mention it started when you got your mac keyboard)
if still does not work
2- go in the synaptic history and check which packages were installed/upgraded around that time and try to uninstall/downgrade the packages
if still does not work

what I would do is backup the list of the packages with this command

1- ```
sudo dpkg --get-selections > /home/username/Desktop/packages_hardy 
```reinstall Ubuntu 
[COLOR=Red]IMPORTANT: WHEN YOU REINSTALL DO NOT FORMAT YOUR HOME PARTITION[/COLOR]
[COLOR=Red]AND DO NOT USE THE MAC KEYBOARD[/COLOR]
[COLOR=Black]once you reinstall you should have your home directory with the package list on your Desktop (if you followed this command [/COLOR]```
[COLOR=Black]sudo dpkg --get-selections > /home/username/Desktop/packages_hardy [/COLOR]
```[COLOR=Black])
don't worry about some errors when you boot/reboot after installation ex: the panel could not load applet xxx or what ever, just answer to load it next time
upgrade your system with this command
[/COLOR]```
[COLOR=Black]sudo apt-get update [/COLOR]
``````
[COLOR=Black] sudo apt-get upgrade [/COLOR]
```[COLOR=Black]reboot if you need to
now you need to use this command
```
 sudo dpkg --set-selections <[/COLOR] /home/username/Desktop/packages_hardy
```[COLOR=Black]

basically you should come to the same system as before
try the system for days/weeks, once you know it is working fine
try your mac keyboard
if it happens again "the slow system" you know for sure that the keyboard is not compatible or you need to find a hack for it

any easier/better suggestion than this one, should be applied before
good luck[/COLOR]

---

### Post by kamitsukai on 2008-06-03
thanks everyone i think i will wait and see what happens if it happens again then i will probably just reinstall ubuntu, i cant see it being the keyboard as there are hundreds of mac users out there using this exact keyboard perfectly fine with ubuntu :)

---

### Post by raven on 2008-06-03
kamitsukai, the way I tackle this issue is
1- first I will put back the old keyboard, if you don't have it just borrow a regular basic keyboard from a friend and try it (since you mention it started when you got your mac keyboard)
if still does not work
2- go in the synaptic history and check which packages were installed/upgraded around that time and try to uninstall/downgrade the packages
if still does not work

what I would do is backup the list of the packages with this command

1- ```
sudo dpkg --get-selections > /home/username/Desktop/packages_hardy 
```
reinstall Ubuntu 
[COLOR=Red]IMPORTANT: WHEN YOU REINSTALL DO NOT FORMAT YOUR HOME PARTITION[/COLOR]
[COLOR=Red]AND DO NOT USE THE MAC KEYBOARD[/COLOR]
[COLOR=Black]once you reinstall you should have your home directory with the package list on your Desktop (if you followed this command [/COLOR]```
[COLOR=Black]sudo dpkg --get-selections > /home/username/Desktop/packages_hardy [/COLOR]
```[COLOR=Black])
don't worry about some errors when you boot/reboot after installation ex: the panel could not load applet xxx or what ever, just answer to load it next time
upgrade your system with this command
[/COLOR]```
[COLOR=Black]sudo apt-get update [/COLOR]
```
```
[COLOR=Black] sudo apt-get upgrade [/COLOR]
```
[COLOR=Black]reboot if you need to
now you need to use this command
[/COLOR]```
[COLOR=Black]sudo dpkg --set-selections <[/COLOR]/home/username/Desktop/packages_hardy
```
[COLOR=Black]
basically you should come to the same system as before
try the system for days/weeks, once you know it is working fine
try your mac keyboard
if it happens again "the slow system" you know for sure that the keyboard is not compatible or you need to find a hack for it

any easier/better suggestion than this one, should be applied before
good luck[/COLOR]

---

### Post by philinux on 2008-06-03
> **gameryoshi600 said:**
> What version of ubuntu are you using? If its Hardy then it probably will go slow since it is unstable. did you try reloading compiz fusion or a restart? You should also give Opera try just download the .deb for 9.50 beta 2 as flash and java work out of the box with it.

This is just plain wrong. Sorry.

---

### Post by SunnyRabbiera on 2008-06-03
> **raven said:**
> kamitsukai, the way I tackle this issue is
1- first I will put back the old keyboard, if you don't have it just borrow a regular basic keyboard from a friend and try it (since you mention it started when you got your mac keyboard)
if still does not work
2- go in the synaptic history and check which packages were installed/upgraded around that time and try to uninstall/downgrade the packages
if still does not work

what I would do is backup the list of the packages with this command

1- ```
sudo dpkg --get-selections > /home/username/Desktop/packages_hardy 
```
reinstall Ubuntu 
[COLOR=Red]IMPORTANT: WHEN YOU REINSTALL DO NOT FORMAT YOUR HOME PARTITION[/COLOR]
[COLOR=Red]AND DO NOT USE THE MAC KEYBOARD[/COLOR]
[COLOR=Black]once you reinstall you should have your home directory with the package list on your Desktop (if you followed this command [/COLOR]```
[COLOR=Black]sudo dpkg --get-selections > /home/username/Desktop/packages_hardy [/COLOR]
```[COLOR=Black])
don't worry about some errors when you boot/reboot after installation ex: the panel could not load applet xxx or what ever, just answer to load it next time
upgrade your system with this command
[/COLOR]```
[COLOR=Black]sudo apt-get update [/COLOR]
```
```
[COLOR=Black] sudo apt-get upgrade [/COLOR]
```
[COLOR=Black]reboot if you need to
now you need to use this command
[/COLOR]```
[COLOR=Black]sudo dpkg --set-selections <[/COLOR]/home/username/Desktop/packages_hardy
```
[COLOR=Black]
basically you should come to the same system as before
try the system for days/weeks, once you know it is working fine
try your mac keyboard
if it happens again "the slow system" you know for sure that the keyboard is not compatible or you need to find a hack for it

any easier/better suggestion than this one, should be applied before
good luck[/COLOR]


de je vu...

---

### Post by gameryoshi600 on 2008-06-03
> **philinux said:**
> This is just plain wrong. Sorry.

I try.

---

### Post by SteveNorman on 2008-06-03
Got your graphics card, xorg.conf and your vidcard drivers correct?

in xorg.conf there is a keyboard section I believe,,you may need to edit it

---

