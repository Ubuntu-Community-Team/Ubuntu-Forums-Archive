---
title: "[SOLVED] Login screen out of place"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by warleggon on 2008-10-26
Hi,

I just downloaded and installed 8.04 Hardy running Gnome.

I managed to get my 7300GT configured to use nvidia-glx-new, and used Screens and Graphics to get the monitor id'ed and the resolution set. 

But now, my login screen is all messed up. The login textbox is in the lower right corner and is barely useable. I suspect that it is a resolution problem, but have not been able to locate where or how to adjust that. Any ideas?:confused:

Thx

---

### Post by louieb on 2008-10-26
This worked on 2 out of 3 PCs for me.
```
gksudo displayconfig-gtk
```

Kinda weird that the resolution in gdm is out of whack. But after log in things are just fine.

---

### Post by DoricMan on 2008-10-26
> **warleggon said:**
> Hi,

I just downloaded and installed 8.04 Hardy running Gnome.

I managed to get my 7300GT configured to use nvidia-glx-new, and used Screens and Graphics to get the monitor id'ed and the resolution set. 

But now, my login screen is all messed up. The login textbox is in the lower right corner and is barely useable. I suspect that it is a resolution problem, but have not been able to locate where or how to adjust that. Any ideas?:confused:

ThxI had this problem recently when I replaced my monitor with a 22 inch one. This pointed out that 
I had not set the display to 1360 x 768 pixels.
Hope it helps.

---

### Post by warleggon on 2008-10-26
> **louieb said:**
> This worked on 2 out of 3 PCs for me.
```
gksudo displayconfig-gtk
```

Kinda weird that the resolution in gdm is out of whack. But after log in things are just fine.

Thank you louieb. I'll mess with that some and see what happens.

---

### Post by warleggon on 2008-10-26
> **DoricMan said:**
> I had this problem recently when I replaced my monitor with a 22 inch one. This pointed out that 
I had not set the display to 1360 x 768 pixels.
Hope it helps.

I've checked my xorg.conf file, and all the listed resolutions are supported. There must be something that I need to add to the conf to make it work for the login screen. Thanks, that gives me something to work on.

---

### Post by warleggon on 2008-10-26
I got it. :)

I was looking for some help with the xorg.conf configuration and I found it at [http://ubuntuforums.org/showthread.php?t=359310&page=2](http://ubuntuforums.org/showthread.php?t=359310&page=2). The poster foska had the answer that I was looking for.

---

