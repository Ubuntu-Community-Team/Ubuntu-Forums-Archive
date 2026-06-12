---
title: "Problems after installing Ubuntu 12"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by eduardo saxel on 2012-10-15
Hi there,

I've installed Ubuntu 12 a month ago, and everything was OK for a week or so. Then
one day everything was missing from the desktop. I had to create an empty folder to have access to the rest of the folders, and use the terminal (though I'm really far from get a decent use out of it) for a few simple tasks.
So as I'm new on Ubuntu I'm forced to ask: what to do

Thanks on advance

---

### Post by androssofer on 2012-10-15
> **eduardo saxel said:**
> Hi there,

I've installed Ubuntu 12 a month ago, and everything was OK for a week or so. Then
one day everything was missing from the desktop. I had to create an empty folder to have access to the rest of the folders, and use the terminal (though I'm really far from get a decent use out of it) for a few simple tasks.
So as I'm new on Ubuntu I'm forced to ask: what to do

Thanks on advance

when you say everything went missing from the desktop what do you mean?

for example: the side bar went missing? and the black bar along the top?

if so, it means unity is broken and needs restored. try this:

press:

```
ctrl   atl    F1
```

it will open a virtual terminal. Login to it. then type:

```
sudo killall Xorg
```

this will kill the window manager, then run:

```
mv -v ~/.config/compiz-1 ~/.config/compiz-1.BROKEN
```

and finally

```
mv -v ~/.config/dconf ~/.config/dconf.BROKEN
```

then press:

```
ctrl     alt    F7
```

and log in as normal. It should restore unity for you.. :-)

---

### Post by eduardo saxel on 2012-10-15
when you say :
"sudo killall Xorg" 

is it a small "x" or  a capital ?

---

### Post by androssofer on 2012-10-15
> **eduardo saxel said:**
> when you say :
"sudo killall Xorg" 

is it a small "x" or  a capital ?

oo not sure... 

just do both.. will get the right 1 :-)

---

### Post by eduardo saxel on 2012-10-15
When I try to run :

mv -v ~/.config/compiz-1 ~/.config/compiz-1.BROKEN

it says :

mv: cannot stat '/home/bastien/.config/confiz-1' : No such file or directory

---

### Post by androssofer on 2012-10-15
> **eduardo saxel said:**
> When I try to run :

mv -v ~/.config/compiz-1 ~/.config/compiz-1.BROKEN

it says :

mv: cannot stat '/home/bastien/.config/confiz-1' : No such file or directory

if you try:

```
cd ~/.config
``` 

does it let you?

if so type 

```
ls
```

and it should look like:

```
autostart  feedindicator   totem
compiz-1   gedit                 ibus              Trolltech.conf
dconf      gnome-control-center  libimobiledevice  update-notifier
Empathy    gnome-disk-utility    libreoffice       user-dirs.dirs
enchant    gnome-session         monitors.xml     user-dirs.locale
eog        gnome-sudoku          nautilus          vlc     
goa-1.0    nautilus-actions      evolution         google-chrome
software-center

```

---

### Post by eduardo saxel on 2012-10-15
> **androssofer said:**
> if you try:

```
cd ~/.config
```does it let you?

if so type 

```
ls
```and it should look like:

```
autostart  feedindicator   totem
compiz-1   gedit                 ibus              Trolltech.conf
dconf      gnome-control-center  libimobiledevice  update-notifier
Empathy    gnome-disk-utility    libreoffice       user-dirs.dirs
enchant    gnome-session         monitors.xml     user-dirs.locale
eog        gnome-sudoku          nautilus          vlc     
goa-1.0    nautilus-actions      evolution         google-chrome
software-center

```


Ok, it looks like that
then ?

---

### Post by androssofer on 2012-10-15
> **eduardo saxel said:**
> Ok, it looks like that
then ?

does it have 'compiz-1' in the list?

---

### Post by audiomick on 2012-10-15
> **androssofer said:**
> does it have 'compiz-1' in the list?

> **eduardo saxel said:**
> When I try to run :

mv -v ~/.config/compiz-1 ~/.config/compiz-1.BROKEN

it says :

mv: cannot stat '/home/bastien/.config/[COLOR="Red"]**[SIZE="2"]confiz-[/SIZE]**[/COLOR]1' : No such file or directory

Watch out. There are typos happening here. The OP might have entered the mv command incorrectly.

---

### Post by eduardo saxel on 2012-10-15
> **androssofer said:**
> does it have 'compiz-1' in the list?

yep. and it says ".BROKEN" after it.

---

### Post by eduardo saxel on 2012-10-15
> **audiomick said:**
> Watch out. There are typos happening here. The OP might have entered the mv command incorrectly.

it was my mistake. it should read ".config/compiz-1' : no such file or directory

---

### Post by audiomick on 2012-10-15
Ok, so the typo was only in the post. 

Going by the last post, the mv command was successful, ie. the file has been re-named so that it has "broken" after it. If that is also the case for the dconf file, then you are ready to log back in, if I have been reading this correctly.

---

### Post by androssofer on 2012-10-15
> **eduardo saxel said:**
> yep. and it says ".BROKEN" after it.

so tht part worked.. 

then do the:

```
mv -v ~/.config/dconf ~/.config/dconf.BROKEN
```

so you should have both 

```
compiz-1.BROKEN
```

and 

```
dconf.BROKEN
```

in 

```
~/.config
```

then proceed with the last stages

---

### Post by eduardo saxel on 2012-10-15
> **androssofer said:**
> so tht part worked.. 

then do the:

```
mv -v ~/.config/dconf ~/.config/dconf.BROKEN
```so you should have both 

```
compiz-1.BROKEN
```and 

```
dconf.BROKEN
```in 

```
~/.config
```then proceed with the last stages

I'm sorry, I logged in as usual after that and I'm still having an empty desktop.....

---

### Post by eduardo saxel on 2012-10-15
Hi,
after the "compiz-1.BROKEN" and "dconf.BROKEN" issue done, still have an empty desktop.

---

