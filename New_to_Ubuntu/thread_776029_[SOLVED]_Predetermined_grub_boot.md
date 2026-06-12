---
title: "[SOLVED] Predetermined grub boot"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-04-30
I now have Ubuntu installed on two machines.

The 2nd machine is a dual boot with Hardy and XP Pro.  If I can work out the snags with VNC (that is in another thread), I would like to control this machine remotely.  I already do that on the Windows side with VNC without problems.  Assuming that I get VNC to work correctly on Hardy, would be able to control it from that side.

Some of the tasks that need to be done have to be done under Windows (older, proprietary software), so sometimes I need to be in Windows and sometimes I want to be in Ubuntu.

My question is can I predetermine which system to boot into BEFORE the reboot is started from both sides?  I can see where one could come up with a custom menu.lst and make XP the default boot.  Is there a way, from XP, to change the default boot to Ubuntu?

---

### Post by Adramelech on 2008-04-30
Install ext3 drivers for windows and then change menu.lst by hand.

---

### Post by nowhere@cox.net on 2008-04-30
I asked this a while ago with no resolution yet. Currently this is how I work around the issue. I have Ubuntu set as the default boot in /boot/grub/menu.lst. If I HAVE to remotely boot to XP, I edit the default entry in the menu.lst file and reboot. 

I don't have a way yet to boot back remotely.  I have however almost NEVER wanted to remotely control Windows anymore. 

I am pretty sure there is a command to set only the next boot location. Any reboots after the next one go back to the default. This would be ideal but I could not get it to work...

Eric

---

### Post by H.Callahan on 2008-04-30
> **Adramelech said:**
> Install ext3 drivers for windows and then change menu.lst by hand.

I didn't know there were such things.  Just installed them and it seems to work just fine.  Now to create batch/shell files on both sides to automate the process!

Thanks!

---

### Post by Adramelech on 2008-04-30
This worked for me, not tested under windows but in theory you should only need to change the PATH variable.

REMEMBER TO MAKE A BACKUP OF THE MENU.LST BEFORE TRYING IT

---

