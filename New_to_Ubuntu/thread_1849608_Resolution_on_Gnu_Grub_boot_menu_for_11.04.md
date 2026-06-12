---
title: "Resolution on Gnu Grub boot menu for 11.04"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by jsymons on 2011-09-24
Very new to Ubuntu. I just installed Ubuntu rel 11.04 on a triboot PC. Using WIN XP,WIN7 and Ubuntu. My issue is with the resolution of what I think is called the GNU Grub boot menu. The menu that allows you to select wich os to boot. With a standard monitor everything is fine. But I use this PC on a Dynex flatscreen connected to VGA interface. When used with the Dynex when it gets to that boot menu its just all garbled. Just using the Ubuntu menu is fine for me. I know of EasyBCD and tried it but still working on that to work. For now I can get by with Ubuntu menu. I can boot to all three os's.

---

### Post by alegomaster on 2011-09-24
> **jsymons said:**
> Very new to Ubuntu. I just installed Ubuntu rel 11.04 on a triboot PC. Using WIN XP,WIN7 and Ubuntu. My issue is with the resolution of what I think is called the GNU Grub boot menu. The menu that allows you to select wich os to boot. With a standard monitor everything is fine. But I use this PC on a Dynex flatscreen connected to VGA interface. When used with the Dynex when it gets to that boot menu its just all garbled. Just using the Ubuntu menu is fine for me. I know of EasyBCD and tried it but still working on that to work. For now I can get by with Ubuntu menu. I can but to all three os's.

Sorry, I cant really understand the last part of your post. Would it be okay if you clarify it? Also what do you mean by garbled? Is it just random pixels, or is it a messed up resolution, or something else.

---

### Post by papibe on 2011-09-24
Are you talking something like this [thread]("http://ubuntuforums.org/showthread.php?t=1849623")?

That is, that the grub menu is not presented correctly? If so, take a look at my response there.

Regards.

---

### Post by jsymons on 2011-09-24
> **alegomaster said:**
> Sorry, I cant really understand the last part of your post. Would it be okay if you clarify it? Also what do you mean by garbled? Is it just random pixels, or is it a messed up resolution, or something else.
 
Sorry I corrected my last sentence. Its messed up resolution.

---

### Post by jsymons on 2011-09-24
> **papibe said:**
> Are you talking something like this [thread]("http://ubuntuforums.org/showthread.php?t=1849623")?
 
That is, that the grub menu is not presented correctly? If so, take a look at my response there.
 
Regards.
 
I followed your thread link and that may be what I'm looking for. However in the line that was changed the resolution is 640x480 changed to 800x600 to fix issue. 640 x 480 is supported on my flatscreen for vga port. Find it odd anyone would have an issue with 640x480. Maybe the freq? My flatscreen would display 720x400 at 70hz when that menu would appear. It does not support 70hz.
 
But as I said this all works on a standard monitor And all other menus work fine on my Dynex flatscreen except for the boot menu. I pasted below from other thread and will try that.
 
 
Hi, this is how I fixed mine and helped other people do the same.
 
Code:
gksudo gedit /etc/default/grub
and change this line:
 
#GRUB_GFXMODE=640x480
 
to this:
 
GRUB_GFXMODE=800x600
 
Then save and exit the document.
 
 
Then do:
 
Code:
sudo update-grub

---

### Post by jsymons on 2011-09-25
> **papibe said:**
> Are you talking something like this [thread]("http://ubuntuforums.org/showthread.php?t=1849623")?
 
If so, take a look at my response there.
 
Regards.
 
I made the changes and that issue has been corrected. Now I need to fix it so EasyBCD works too.
 
Thanks all!:D

---

### Post by papibe on 2011-09-25
:p Great! Please Mark the thread solved, when you have the chance.
Regards.

---

