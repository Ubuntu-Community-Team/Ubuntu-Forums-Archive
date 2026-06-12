---
title: "kA"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by niteblind on 2008-09-07
Hi All,

Can anyone assist? I have just installed hardy heron with and all was fine for the first couple of reboots now all of a sudden I no longer hvae a taskbar/panel.

I had a bit of a google and it would appear that i need to stop and resstart a program called plasma.

I have managed to open a terminal and run top but I cannot see plasma there at all. Can anyone assist me? I may need to get the new taskmanager open but have no idea what it is called to run it.

Also I NEED to change the colour scheme on the root account. I used to do so by using: kdesu kcontrol. Kcontrol is no lonher in KDE4 so what is the app that runs the control panel in kde4?

Any help would be appreciated.

niteblind

---

### Post by Crafty Kisses on 2008-09-07
For the panels you could try this:
```
kde-panel
```
See what that does for you.

---

### Post by niteblind on 2008-09-07
Hi

According to bash kde-panel does not exist as a command so I cannot run that. As I wrote earlier I need to be able to stop "plasma" which does exist in order to rectify this issue.

Can someone tell me the commands for the following?

a) to run the task manager app from konsole
b) the command to load the system settings control panel from konsole.

Cheers

---

### Post by Xiong Chiamiov on 2008-09-07
> **niteblind said:**
> 
a) to run the task manager app from konsole

Personally, I'd use htop (you'll have to apt-get install it), which is interactive and allows you to sort and kill things with the F-keys.
> **niteblind said:**
> 
b) the command to load the system settings control panel from konsole.

The KDE4 control panel is called "systemsettings".
> **niteblind said:**
> 
As I wrote earlier I need to be able to stop "plasma" which does exist in order to rectify this issue.

I think you actually need to *start* plasma, which should be something like
```

nohup plasma&

```
nohup prevents the output from going to your shell window, and the & lets you continue working in that terminal window.

Plasma's the reason I'm running fluxbox on top of KDE4.

Also, in the future, choosing a more helpful thread title will help us know whether it's a thread we should check or not (we all have specialities).

---

### Post by niteblind on 2008-09-07
Thanks for the info. Sorry about the post name I was literally typing blind when I submitted it and later could not find anywheree that let me edit the title.

Can I ask what is flushbox and if you know what exactly does plasma do I mean is it vital to the running of the desktop if so any idea where the hell it went to as it worked ok for a couple of reboots.

niteblind

---

### Post by Xiong Chiamiov on 2008-09-07
> **niteblind said:**
> Thanks for the info. Sorry about the post name I was literally typing blind when I submitted it and later could not find anywheree that let me edit the title.
You can click the edit button on the first post, then "go advanced" and change the title.  It won't change what shows up in the listings, though.
If you ever need to access the 'net and you're stuck in a terminal, try using one of the text-based browsers, like elinks.  They're actually fairly easy to use for basic operations.

> **niteblind said:**
> 
Can I ask what is flushbox

[Fluxbox]("http://www.google.com/search?hl=en&q=fluxbox&aq=f&oq=") is another window manager.  It's not particularly newbie-friendly, but it's very fast and customizable.  I was used to using KDE3, and it doesn't seem like KDE4 will ever have the customizability of 3, so I decided to ditch that part of it.  I love the new apps though, so I still run KDE underneath it all.

> **niteblind said:**
> 
 and if you know what exactly does plasma do I mean is it vital to the running of the desktop if so any idea where the hell it went to as it worked ok for a couple of reboots.
[Plasma]("http://en.wikipedia.org/wiki/Plasma_(KDE)") is the new desktop shell in KDE4.  As to why it's no longer running automatically, I have no ideas.  It seems to be a fairly common problem, though.

---

