---
title: "[SOLVED] Wrecked my HAL"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by BGFG on 2008-06-19
HI,
I'm too ashamed to say why, but i removed my HAL packages via synaptic. Is there any way to reinstall HAL barring a full ubuntu re-installation ?

Any Guidance Appreciated.

---

### Post by Sarah L on 2008-06-19
Do you still have access to a terminal? If so, try reinstalling the HAL packages using aptitude.

If not, please elaborate! :D

---

### Post by BGFG on 2008-06-19
Hi, thanks for such a speedy reply.
Basically, in synaptic i sorted by local and obsolete packages and removed HAL (still ashamed) i immediately lost networking and when i re-started, after entering my login name and password nothing seemes to happen. the desktop does not appear. 

Is there a HAL package that i can manually install at boot ? or can i somehow repair the system ?

---

### Post by sdennie on 2008-06-19
If you removed hal, you probably need to reinstall the following packages with this command:

```

sudo apt-get install gnome-mount gnome-power-manager gnome-session gnome-volume-manager hal hal-cups-utils hal-device-manager hwdb-client-common hwdb-client-gnome network-manager network-manager-gnome pulseaudio-module-hal sound-juicer ubuntu-desktop update-notifier

```

From a clean VM, those are the packages that get removed if you remove hal.

---

### Post by BGFG on 2008-06-19
Would removing HAL also kill my networking ? If so, can it be installed manually ? 
Thanks for the command though. If i get into the desktop environment i'll try it.

---

### Post by sdennie on 2008-06-19
Yes, removing hal would break network manager, power management, probably printing, etc.  However, that command that I posted above re-installs all those things.

Edit:
If you've only recently installed, it's possible that all those packages are still sitting in the apt cache so, you may not need a network connection to get them back.

---

### Post by BGFG on 2008-06-19
I think I'm out of luck. I selected completly remove. I'm going to try the command you gave me. I'm in vista right now (dual boot) so i'll be back in a while, hopefully from gnome.

On another note. is HAL included in gnome ? could the gnome live cd help me ? 

Be back in a few. thanks.

---

### Post by sdennie on 2008-06-19
Yes, all those packages are on the CD as well.  If you put in your install CD and then go to System->Preferences->Software Sources, you should be able to re-enable the CD if it isn't already enabled.  When it asks to update it may fail miserably without an internet connection but, I think it will still work.  (It's also possible that just sticking the install CD in will enable it again).

---

### Post by BGFG on 2008-06-19
Was going to ask a question but i'll try one more thing then bug you again. back in a flash. I go forth, in search of HAL!

---

### Post by BGFG on 2008-06-19
Back,
I executed the command in the 'emergency' session (i forgot the correct name) in login options and this error was returned

E: couldn't find package hal-device-manager

Please tell me how : 1 - i can start the terminal from the keyboard
and 2 - use the terminal to launch the panels. Or at least access the cd from the terminal. I do remember setting it as a software source.

Thanks...

---

### Post by sdennie on 2008-06-19
Once the machine boots into recovery mode, insert the installation CD and then try:

```

sudo mount /media/cdrom0
sudo apt-get update

```

You may get a bunch of warnings doing that but, it should work.  Then try the original command I posted.  If it fails saying it can't find a particular package, just erase that package from the list.  If you can get hal and network manager working again, it will be much easier to get your system back.

---

### Post by BGFG on 2008-06-20
Well then i'm off again. :)

---

### Post by BGFG on 2008-06-20
Hi VOR,
Just want to say thanks for all your help and for pointing me in the right direction. I message you from a freshly fixed Gnome session. Check back here if you like.I'm gonna post all my adventures.

Thanks to you and the unanswered post team.

Later...

---

### Post by sdennie on 2008-06-20
I'm glad you were able to fix it.  At the very least you now have some experience fixing broken machines.  ;)

---

### Post by BGFG on 2008-06-20
Second time i'm writing this, My browser pulled a fast one....

Back at the batcave....
Well as you said, apt-get using the live cd didn't really work. After checking around the forums i decided to try recovery via live cd. After booting, i attempted chroot on my filesystem (thanks to user 'tuxcantfly' for that post) and then downloaded the relevant packages. I used the forums to find out where the package cache is (thanks for the hint VOR) and using sudo nautilus, i copied the packages over to my default system. I attempted the installation in the live environment but to no avail.... :(
-I thought this was quite inspired-

I then logged back in using the failsafe session and tried installing the packages via the gnome command you provided me but again, no luck.
Tired and depressed, i slept.

Woke up and immediately attempted to log in, this time, for some reason (later explained) I chose the GNOME session and BOOM! desktop :) I was now able to install the HAL packages via synaptic.
As to why i tried the gnome session ? well in the failsafe session, i also attempted manual package installation through sudo nautilus and the 'right click' options, but when i tried installing the hal package, a message returned that a more updated version was already installed. So maybe it wasn't ALL HAL as i thought.

It's still a little disturbing that i don't know what CRAP i did to my system and why my session changed from GNOME to X but it was still fun. I really think the next UBUNTU distro should have a 'Repair System' feature.

Anyways, thanks for being online and waiting for overzealous noobs to #@%! their systems and help us bring them back. Now i need to fix my sound :) i'll be posting soon.....

Laters

---

