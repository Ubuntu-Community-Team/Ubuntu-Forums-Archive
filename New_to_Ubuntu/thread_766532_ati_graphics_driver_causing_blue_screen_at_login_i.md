---
title: "ati graphics driver causing blue screen at login in 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Matt26 on 2008-04-25
i just finished the upgrade of ubuntu from 7.10 to 8.04 via the update manager this morning.. everything went fine and the computer restarted after the upgrade completed and i logged in with no issues, then i had a prompt on my taskbar to install an ATI graphics driver from the restricted drivers.. so i installed it and i restarted the computer again as prompted. when the login screen came up the screen was a little off in terms of positioning (not a big deal since this is probably related to the new driver) but once i logged in, nothing appeared on the screen- just a blank, beige screen.  then after a few seconds the screen color changed to a light blue, and that's the way it stays.  does anyone have any ideas as to how or why this would have happened?  is there a way that i can remove the driver via the live cd or otherwise since i can't see anything on my screen to do anything?  thanks.

---

### Post by philinux on 2008-04-25
Since you upgraded when it installed the driver it should have created a backup of your xorg.conf.

It should be /etc/X11/xorg.conf~

You could copy this file back from the recovery boot option.

---

### Post by Matt26 on 2008-04-25
forgive me i'm still learning the ins and outs of the linux system here- how would i go about doing this?  i can't see anything on the screen so i'm assuming this would be done from a terminal window?  would this be done through the live cd or another option?  thanks.

---

### Post by overdrank on 2008-04-25
> **Matt26 said:**
> forgive me i'm still learning the ins and outs of the linux system here- how would i go about doing this?  i can't see anything on the screen so i'm assuming this would be done from a terminal window?  would this be done through the live cd or another option?  thanks.

Hi and you may try the xfix suggested here
[http://ubuntuforums.org/showthread.php?t=765627&highlight=sudo+xfix](http://ubuntuforums.org/showthread.php?t=765627&highlight=sudo+xfix)

---

### Post by Matt26 on 2008-04-25
how do i get access to the grub boot menu to use the 'xfix' feature?  prior to the OS loading at the POST screens it just says something to the effect of grub loading with a 3 second countdown and then the list of services being started and then the ubuntu screen appears.  i'm not sure how to get into it.  thanks.

---

### Post by philinux on 2008-04-25
> **Matt26 said:**
> how do i get access to the grub boot menu to use the 'xfix' feature?  prior to the OS loading at the POST screens it just says something to the effect of grub loading with a 3 second countdown and then the list of services being started and then the ubuntu screen appears.  i'm not sure how to get into it.  thanks.


When you see grub stage 1.5 press the escape key. You will then see the grub menu. Choose the second option by using the down arrow key. It will say recovery.

---

### Post by Matt26 on 2008-04-28
thanks for the assistance- what exactly does the xfix feature do?  i've read that it is supposed to restore your X windows configuration to a usable condition and allow you to boot normally, but i'm not sure what that entails.  i have setup my desktop with custom shortcuts, folders etc- will the desktop be set back to default settings as when ubuntu was first installed or will it restore the driver configuration back to before the restricted video driver was installed?

---

