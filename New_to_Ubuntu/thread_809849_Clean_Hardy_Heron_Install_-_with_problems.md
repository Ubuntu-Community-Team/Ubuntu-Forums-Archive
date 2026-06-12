---
title: "Clean Hardy Heron Install - with problems"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by angelsneverdie on 2008-05-27
Alright, so I just did a clean install of Hardy Heron (I had upgraded to it, than tried to install windows for dual boot, which didn't work, so just wiped it all and did a clean install).  

things were working much better after I had updated it - now with a clean install I'm having a few problems.

first, i put in the dvd's that I burned as a back up before i formated everything.  Some work fine, but the majority are being read as "blank dvds".  i put the dvd's in a different computer and they are read fine . . .

when i switch users it gives me a white screen.  That's it, no error message, no nothing, just a white screen.

If i press the reset button on the computer it won't boot, it gives me a grub error 21.

firefox crashes all the time - this might specifically be a firefox issue, but as i'm using whatever was shipped with hardy heron, it still needs a fix.

anyone have any ideas on these issues?

---

### Post by angelsneverdie on 2008-05-28
bump

---

### Post by xenocide13 on 2008-05-28
as for the cds i have no idea

the white screen there are several threads about it look around a little

what version of firefox are you running?

---

### Post by angelsneverdie on 2008-05-28
i'm running 3.0b5

the b makes me think i'm in beta . . . but i didn't do any upgrades . . this is what came on the live cd.

---

### Post by xenocide13 on 2008-05-28
yea your running in beta and of course it is still having problems try reverting back to firefox 2 see if that helps

---

### Post by spiderbatdad on 2008-05-28
I'm wondering if the dvd were from an ext3 file system and are owned by a unique user id other than root. This might pose a problem...not really sure, but here is a lengthy report.[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550)

While it deals with an older version of ubuntu, there is considerable discussion regarding permissions of unix filesystems mounted in userspace.
> there is *no way* for any userspace program to randomly alter permissions on file systems that support permissions (like ext3 and UDF, unlike VFAT and iso9660). If at all, this needs to be fixed at the kernel level.

---

### Post by Primefalcon on 2008-05-28
ust a couple of thoughts here

have you tried installing the restricted extra's?

yes beta 5 in the default

as for yuor white screen problem when you try to change users, thats easy, have a look at my post on this thread:

> do the 

```
sudo displayconfig-gtk
```

just to make sure the xorg file is properly filled, the less you have to fill out with it manualy the better....

then go into the xorg file 

```
sudo gedit /etc/X11/xorg.conf
```

under this section

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
```

just change the virtual to what you want such as

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	800	600
```

that should solve you login screen resolution

its down a bit on the first page, and change your virtual to match your resolution, that'll change the login screen res to yours so it wont need to change modes when switching users, which means no more white screens

---

### Post by angelsneverdie on 2008-05-29
Ok, i changed the file to show a virtual resolution of 1440x900.  all that did was make the login screen look zoomed in a bit.  Now i can however quick change to the other user, but when i try to change back I still get the white screen - do i have to do that on each account?

as far as the cd's go the thread you directed me to makes  no sense to me.  It is mounting them as blank cd's - so i'm not sure if it is the same problem.

---

