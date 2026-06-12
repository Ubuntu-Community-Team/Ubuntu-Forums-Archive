---
title: "I need serious help! screen resolution"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Paz13 on 2008-07-05
i was fiddling with the screen resolution and saved and un-displayable resolution i can't see what is on the screen just like one colour and smushed pixels. 
i'm begging can any body help me by mabey telling me to set the screen settings to default by using the teminal i could just type if i can't see what i'm doing??? any body got my back?

---

### Post by Troll_the_Great on 2008-07-05
I would suggest to try this:
Open a terminal and type 
```
sudo reboot
```
This will reboot the computer.When the computer boots up, select "safe mode" and then select what resolution you want.Tell me if it worked.
Cheers!

---

### Post by Paz13 on 2008-07-05
ok m8 giving it a go :)

---

### Post by Paz13 on 2008-07-05
problem is i can't see the safe mode button is there a way of tell the system to reboot in safe mode auto?

---

### Post by Troll_the_Great on 2008-07-05
I didn't fully understand your last post.Did you manage to reboot or not with the command I gave you?
To open a terminal press Alt+F2 and then type:
```
gnome-terminal
```
After it reboots, you have several options to choose :the current kernel (should be something like 2.6.24-19) current kernel in safe mode and memtest (memory test).Just choose safe mode and it should work.Tell me if it deed.
Cheers

---

### Post by merlo on 2008-10-14
I have the same problem.
I changed my screen resolution and now I can't read a thing on the gui.
Rebooting to recovery mode (version 7.10) brings up a text screen with me logged on as root.

1. Can I use a command from here to reset the screen resolution?
   xrandr says "can't open" 

2. Startx brings lots of horizontal lines so I can't see where the mouse is clicking, but could use keyboard shortcuts.

3. I have a live cd ... maybe I could change settings from here?

Any help would be much appreciated.

---

### Post by freak42 on 2008-10-14
after you booted into your text console you can try
to manually edit the xorg.conf file (where X settings are saved)

try 
```
cd /etc/X11/

```
make a copy of your xorg.conf file
```
sudo cp xorg.conf xorg.conf.backup
```

now edit it with a command line editor of your choice.
if you haven't edited this way I suggest nano:
```
sudo nano xorg.conf
```

locate the Section "Screen" and look for resolution settings,
change them to whatever is better for you.
(I am no xorg expert, you might have to search for better explanations
of the xorg.conf file and it's usage)

to save (in nano) use Ctrl-o + enter
to exit (in nano) use Ctrl-x

reboot with
```
sudo reboot
```

hth

---

### Post by Greyed on 2008-10-14
Or run:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

This will reset xorg.conf to the factory settings, as it were, which should at least get the GUI up and running again.

---

### Post by merlo on 2008-10-15
> **Greyed said:**
> Or run:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

This will reset xorg.conf to the factory settings, as it were, which should at least get the GUI up and running again.

Thank you for your help. I tried this. It brings up a tool for editing the video card driver settings. 
I think the one it had been set to (Vesa) is the correct one because the file at /etc/X11/xorg.conf seems to have the details of my monitor make and model. 
I clicked ok to accept the default and exited the program. If there is a facility to put settings back to the original, I didn't find it.

---

### Post by merlo on 2008-10-15
> **freak42 said:**
> 
```
sudo nano xorg.conf
```

locate the Section "Screen" and look for resolution settings,
change them to whatever is better for you.
(I am no xorg expert, you might have to search for better explanations
of the xorg.conf file and it's usage)



I looked on the net and found some info on how to find the correct values for your monitor [www.freebsd.org/doc/en/books/handbook/x-config.html]("http://www.freebsd.org/doc/en/books/handbook/x-config.html")

I put in the modeline values for my 1680x1050 screen. (This is the resolution on the blue square which keeps flashing on my screen to remind me to change the reolution)
I didn't know the -h, -v values at end of modeline, but ran it anyway.
It didn't fix the problem.

I used a live ubuntu disk and entered the resolution and 'save as default for this computer' but it had altered back when I rebooted.
I copied some of the values from the xorg.conf in the live system over to my /etc/X11.

The next time I booted, a program offered to reset my graphics settings because it was in a state of low graphics.
I chose the closest monitor to mine, not exact, but same make, family and able to do my monitor's resolutions.

Now the xwindows is improved but still unreadable.

The xorg.conf file contains all my resolution modes and more. I don't know what else I can edit! 

Might have to be a reinstall. 

Unless one of you lovely people has any more ideas??

---

### Post by merlo on 2008-10-15
One more try on the screen resolution wizard on the live cd "save as default resolution on this computer" and it worked!!
Hurrah!

Apart from being a random success, it might have been that the modeline for that resolution was not an option in xorg.conf when I first tried it??

Anyway, thanks guys.

---

### Post by Kellemora on 2008-10-15
Hi Paz

Since nobody mentioned it, the next time you mess up the resolution and can't see anything, just hit Ctrl-Alt-Backspace, if that don't work, do it again, and again if necessary.  Eventually you will get back to the original default setting.

TTUL
Gary

---

### Post by Greyed on 2008-10-16
Er, where'd you hear that.  CNTL-ALT-Backspace only kills the X server and restarts it *with the same configuration*.  Are you mistaking it for CNTL-ALT-+/- which increases or reduces the resolution?

---

### Post by Kellemora on 2008-10-16
Hi Greyed

I guess that depends upon whether Ctrl Alt + or - works on your particular computer.

I have Ubuntu on 7 computers here and Ctrl Alt + or - does NOT work on ANY of them.  But Ctrl Alt Backspace WILL definitely get you out of a resolution jamb if you changed it from Properties and ended up with a really messed up screen.
I know, I've had to do it at least a hundred times when I was first working with Ubuntu and before I learned WHERE to FIX IT.

TTUL
Gary

---

