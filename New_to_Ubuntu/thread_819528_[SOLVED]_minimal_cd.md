---
title: "[SOLVED] minimal cd"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-05
I've been told to burn a minimal cd for what I want to do (build from the ground up).  -- that is without going gentoo or anything like that :D

is this hard to do?  apt-getting everything?  have you gone through it yourself and is there a place that lists applications and how you can get them via apt-get?

thanks!

If I can figure this out this is the way to go for me :)

---

### Post by avtolle on 2008-06-05
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) while not strictly about a minimal CD install has much information which you might find helpful.

---

### Post by AnLGP on 2008-06-05
thanks!  that'll definately get me started!  I'm **so** looking forward to this!

also, it says to "check the repositories for other package ideas".

me being on a live disc of a different distro is there a way to check the repositories online? 

ps.

this might sound dumb but repositories = programs?

---

### Post by Duck2006 on 2008-06-05
This is how to install a text base install.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by kerry_s on 2008-06-05
go debian, it's the perfect base to build on.
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

at package selection uncheck everything, that will give you a base install.
log in as root
**apt-get install xorg**
(that gives you X, you need a window manager, i'll do fluxbox since it's most common)

**apt-get install fluxbox menu**
then
**update-menus**

now log out, type->
**exit**

log in as your user, type->
**startx**

open a terminal and build on.

---

### Post by AnLGP on 2008-06-05
thanks for the second day in a row :)

is there a package list somewhere with apt-get instructions?  i'll search around in the meantime.

think I found it.  

this it?

[http://packages.debian.org/stable/](http://packages.debian.org/stable/)

also also:  would I want to install i386 packages?

---

### Post by Duck2006 on 2008-06-05
> would I want to install i386 packages?

Yes.

---

### Post by AnLGP on 2008-06-05
I believe I'll be good to go here soon thanks to this post :)

---

### Post by Inxsible on 2008-06-05
Keep in mind, that if you install just the base, you will have to manually install EVERYTHING.

and that means you have to install packages for your sound/webcam/microphone etc.

I installed E17 on a minimal of Ubuntu and then was trying to get to play music...and then it hit me that I didn't install any sound drivers :)

Good Luck.

P.S.  It would be better if there was a list somewhere which listed these kinda things. You can remember which app you want as an editor -- but its these background things like sound drivers and mic drivers that people tend to forget until they actually want to use it.

---

### Post by AnLGP on 2008-06-05
Ya know..  I didn't think of that.  Thanks.  If I install a minimal ubuntu would it have the sound installed or is that the same thing?

---

### Post by cariboo on 2008-06-05
It will install the modules needed for your sound card, but it won't install a sound driver like alsa or oss or the codecs you need to play the various types of media files. 

Have fun.

Jim

---

### Post by AnLGP on 2008-06-05
so it'll be able to recognize the sound card but not play media?  

I'll have to install them much like I had to enable MP3 support when I installed ubuntu?

---

### Post by kerry_s on 2008-06-05
if your using debian, its:
**apt-get install alsa-base alsa-utils alsa-oss**
then while your still root
**alsaconf**

that will run you through the setup of your card. you then need to:
**reboot**

that will load everything. when you get back to the gui, just use alsamixer to adjust the volumes where you want them.

---

### Post by AnLGP on 2008-06-05
I've got it up ..  not running.  I've installed xorg (at least it told me I'd better abide by the rules and listed three things)...

but when I say "startx" in the terminal it says "command can't be found".  

I've gotten all the way up to installing fluxbox but when I do "sudo update-menus" it says "command not found.  I'm stuck!

I installed this:

x-window-system

after the fluxbox.  is that a prob.?

---

### Post by Inxsible on 2008-06-05
> **AnLGP said:**
> I've got it up ..  not running.  I've installed xorg (at least it told me I'd better abide by the rules and listed three things)...

but when I say "startx" in the terminal it says "command can't be found".  

I've gotten all the way up to installing fluxbox but when I do "sudo update-menus" it says "command not found.  I'm stuck!

I installed this:

x-window-system

after the fluxbox.  is that a prob.?

You need to install the package "menu" to be able to use the update-menus command.

Try this [link]("https://help.ubuntu.com/community/Fluxbox?highlight=%28fluxbox%29") for a minimal + fluxbox installation. I think its a great tutorial.

---

### Post by wolfen69 on 2008-06-05
> **Inxsible said:**
> Keep in mind, that if you install just the base, you will have to manually install EVERYTHING.

and that means you have to install packages for your sound/webcam/microphone etc.



not true. all of my hardware was recognized and working after a minimal install.

---

### Post by Inxsible on 2008-06-05
> **wolfen69 said:**
> not true. all of my hardware was recognized and working after a minimal install.
Well, its great if everything worked for you out of the box. It didn't work for me :(

---

### Post by AnLGP on 2008-06-06
The sound isn't working even after I installed all those things :(

also,

when I start the system up it goes into the CL prompt.  I'd like some kind of login window.  slim or grub or somethin'.  I've got grub installed but it is somehow skipped on boot?  I'm pretty sure I've got to configure it somehow but am unsure of how to do that.

---

### Post by Inxsible on 2008-06-06
> **AnLGP said:**
> The sound isn't working even after I installed all those things :(
Did you type in ```
alsamixer
``` in a terminal and max all the volumes?

Also note, that if it says Mm at the bottom, it means that its muted. To toggle mute/unmute, select the level and hit M

---

### Post by AnLGP on 2008-06-06
some I can't move for some reason and they're all unlocked.  The ones I can move are up all the way.

---

