---
title: "[SOLVED] Splash then...Black"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by bull205 on 2008-09-23
So while working to figure out the wireless drivers that will make my sony vaio SR-165E network, i did something...not sure what and now after the splash screen the display goes black.  I can hear the du,du,dum drums and I can log in blindly, but no display.

I have tried to reboot in safe graphics mode to no avail and I have tried to run the dpkg-reconfigure xserver-xorg command in the terminal and have run that but nothing gets my screen back.

I am not even going to go into the fact that the resolution wasn't correct in the first place, that was gonna be a fix later, but Hardy forced my hand.

HELP!

---

### Post by NT4usB on 2008-09-23
Can you Ctrl+Alt+F1 to a terminal?
Did you try dpkg with the -phigh switch?
From a terminal, you can cd to /X11 and see if maybe there's a backup of your xorg.conf from before you started messing with it. cp it to xorg.conf see if that works.
Try changing the driver in xorg to vesa.
Lots of other ways to get it going...

---

### Post by bull205 on 2008-09-24
I entered 'dpkg -phigh' in the terminal and it spit out a page of globedygook that i don't understand...

> From a terminal, you can cd to /X11 and see if maybe there's a backup of your xorg.conf from before you started messing with it. cp it to xorg.conf see if that works.
Try changing the driver in xorg to vesa

1. Ummm...how do I 'cd' to X11? and find the backup to copy
2. how do i paste it to xorg.conf?
3. how do i go about changing the driver to vesa?


new guy here!

---

### Post by RequinB4 on 2008-09-24
Edit: realized you already did safe graphics mode...

How are you accessing the terminal without graphics? Control+alt+f1?

You can ```

cd /etc/X11/
ls

```

to see if you have an old xorg.conf you can use - say if you see you have a backup "xorg.conf.backup":

```

sudo mv xorg.conf xorg.conf.broken
sudo cp xorg.conf.backup xorg.conf

```

for example, then reboot.

As for using vesa drivers, that's what safe graphics mode is so i'm wondering why that didn't work...

---

### Post by bull205 on 2008-09-24
yup, ctrl+alt+f1 gets me to terminal...right now, I just figured out the full command was:
sudo dpkg-reconfigure -phigh server-xorg

The output says:
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2008092402042

---

### Post by RequinB4 on 2008-09-24
> **bull205 said:**
> yup, ctrl+alt+f1 gets me to terminal...right now, I just figured out the full command was:
sudo dpkg-reconfigure -phigh server-xorg

The output says:
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2008092402042

That's GREAT - in all instances above of
```

xorg.conf.backup

```

use (still have to cd to the /etc/X11/ directory)

```

xorg.conf.2008092402042

```

and reboot;

---

### Post by bull205 on 2008-09-25
How do I "use" xorg.conf.20080924042?

---

### Post by RequinB4 on 2008-09-25
> **bull205 said:**
> How do I "use" xorg.conf.20080924042?

[http://ubuntuforums.org/showpost.php?p=5851020&postcount=4](http://ubuntuforums.org/showpost.php?p=5851020&postcount=4)

But where i said xorg.conf.backup, instead type xorg.conf.20080924042

---

### Post by bull205 on 2008-09-27
I tried to follow your link, but I'm not sure I did it right, so, I go to do this, starting at the beginning of the thread to go step by step.  But this time when I input
> sudo dpkg-reconfigure -phigh server xorg

The terminal outputs: usr/sbin/dpkg-reconfigure: server is not installed

That is not what is said last time...

When I did enter
sudo cd/etc/X11
ls

I got an output that looked like I was on the right track

first line says:
app-defaults    xorg.conf.20080922201706     xorg.conf.broken

last line says:
xorg.conf       xorg.conf.20080924202042

Still swimming in black...

---

### Post by RequinB4 on 2008-09-27
> **bull205 said:**
> I tried to follow your link, but I'm not sure I did it right, so, I go to do this, starting at the beginning of the thread to go step by step.  But this time when I input


The terminal outputs: usr/sbin/dpkg-reconfigure: server is not installed

That is not what is said last time...

When I did enter
sudo cd/etc/X11
ls

I got an output that looked like I was on the right track

first line says:
app-defaults    xorg.conf.20080922201706     xorg.conf.broken

last line says:
xorg.conf       xorg.conf.20080924202042

Still swimming in black...

Ok, I'm having slight trouble understanding you output - i can assume now you finished what i told you --
> 
AFTER you
```

cd /etc/X11/

```

You need to
```

sudo mv xorg.conf xorg.conf.broken
sudo cp xorg.conf.2008092402042 xorg.conf

```


Now you should reboot .

---

### Post by bull205 on 2008-09-27
after i enter the following commands, it says:

cp: cannot stat 'xorg.conf.2008092402042': No such file or directory

I guess i don't have a backup config file anymore...somehow?

---

### Post by RequinB4 on 2008-09-27
then try it again with one of the files listed in  
```

ls /etc/X11/

```

There's still no guarentee this will work...

---

### Post by bull205 on 2008-09-27
just tried it...rebooting now

---

### Post by Xiong Chiamiov on 2008-09-27
> **bull205 said:**
> How do I "use" xorg.conf.20080924042?
X (the window server) will (by default) use the file /etc/X11/xorg.conf.  To change the file it uses, you need to copy/rename the file you want to that address:
```

cd /etc/X11
sudo cp xorg.conf.bak xorg.conf
startx

```

It's worth noting that you don't have to type out full filenames in terminal - just start typing it, then press tab, and it will autocomplete.

Also, what video card do you have?

---

### Post by bull205 on 2008-09-27
i copied and moved the file to the xorg.conf address and I still get nothing

How do I find out what kind of video card I have?

Also when I enter the command: sudo dpkg-reconfigure -phigh server-xorg
it says:

Package 'server-xorg' is not installed and no info is available

Is that bad?

---

### Post by RequinB4 on 2008-09-27
For hardware: post the output of
```

lspci

```

remember that it's xserver-xorg

---

### Post by NT4usB on 2008-09-27
ed: ...oops. RequinB4 corrected the xserver-xorg 2 minutes before me so I'll add to the lspci suggestion instead.

```
lspci | grep -i vga
```will show the video card portion of the output.

---

### Post by bull205 on 2008-09-27
how would i post all that considering...
1. the output goes beyond one page and i can't scroll up
2. i am using a different machine while i work on the ubuntu laptop
3. if the ubuntu machine could be networked, I have no way of getting to this forum could i?

---

### Post by bull205 on 2008-09-27
output of > lspci | grep -i vga

is

> 00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)

i still am getting black after the splash boot up screen.  Black and drums...

---

### Post by RequinB4 on 2008-09-27
Well, this seems to be a known bug

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=903182](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=903182)

Seems to be all I can get - read through that thread and if you need help trying something post here.

---

### Post by bull205 on 2008-09-28
OH THANKYOUTHANKYOUTHANKYOUTHANKYOU...

I needed to:

nano /etc/X11/xorg.conf

and add:

driver "vesa"

under the default monitor section.  Thanks for pointing me in the right direction.  Not the correct resolution, but at least I have seen the light (GUI) after the darkness.  Now it is a matter of refining and refining.

Thanks a bunch.

---

