---
title: "Recently upgraded 8.04 lt to 8.10"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Dorenrab on 2008-11-29
Now every time I log in I get a blank screen.  I tried using the other sessions, but only the failsafe terminal gets me anything other than a blank screen.  I know that is probably the key to fixing the problem, but I'm a bit lost as to how.

---

### Post by nothingspecial on 2008-11-29
Try this

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This reconfigures your display manager which may be toast.

---

### Post by Dorenrab on 2008-11-29
Nope, still blank.

---

### Post by Olivier2371 on 2008-11-29
Hello there,

Try rebooting your pc then press escape key while grub is loading.

Then go to the recovery mode, then click xfix.

Reboot then try to log in again.

---

### Post by Dorenrab on 2008-11-29
Still nothing.  Is there any diagnostic I can run that would clarify what the problem is?

---

### Post by Olivier2371 on 2008-11-29
from the command prompt could do the following.

sudo lspci

Post the result please.

---

### Post by sarang on 2008-11-29
On some laptops, after an upgrade to Intrepid, the EDID detection of the display fails and bad things happen. 
Try changing the [FONT="Courier New"]GdmXserverTimeout[/FONT] to something like [FONT="Courier New"]100[/FONT] in [FONT="Courier New"]/etc/gdm/gdm.conf[/FONT] I am not sure if that will help, but it is worth a try. Also, make sure you wait a little more than 100 seconds at login time before deciding that it does not work for you!

Another thing: before running [FONT="Courier New"]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT] as was suggested in one of the above posts, I strongly suggest backing up [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] as it will be overwritten. I have once lost working settings because of that.

---

### Post by Dorenrab on 2008-11-29
Ran lspci, and here are the results:

> 0:00.0 Host bridge: Intel Corporation 82845G/GL [Brookdale-G]/GE/PE DRAM Controller/Host-Hub interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL [Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82891DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USBUHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-L) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet Controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

EDIT: > **sarang said:**
> On some laptops, the EDID detection of the display fails and bad things happen. Try changing the [FONT="Courier New"]GdmXserverTimeout[/FONT] to something like [FONT="Courier New"]100[/FONT] in [FONT="Courier New"]/etc/gdm/gdm.conf
[/FONT]

I am not sure if that will help, but it is worth a try. Also, make sure you wait a little more than 100 seconds at login time before deciding that it does not work for you!

Another thing: before running [FONT="Courier New"]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT] as was suggested in one of the above posts, I strongly suggest backing up [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] as it will be overwritten. I have once lost working settings because of that.
Ah, I'm sorry I failed to mention it before, but the computer is a destop Dell.  Sorry for not stating that earlier.

---

### Post by linux_tech on 2008-11-29
You may also want to post xorg.conf-
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Dorenrab on 2008-11-29
> **linux_tech said:**
> You may also want to post xorg.conf-
```
sudo nano /etc/X11/xorg.conf
```

Hm, that's odd.  When I entered that command, it didn't display anything.  Just a blank document with the blinking cursor.

---

### Post by Olivier2371 on 2008-11-29
It appears that your xconfig file is empty, which would explain why you get a blank screen. 

Or it could be that you don't have an xconfig file.

This is very strange.

---

### Post by Dorenrab on 2008-11-29
What must I do to fix this problem?

---

### Post by Olivier2371 on 2008-11-29
Try the following and post the output.

ls /etc/X11

---

### Post by Dorenrab on 2008-11-29
> **Olivier2371 said:**
> Try the following and post the output.

ls /etc/X11Alright, here are the results.

> [COLOR="Cyan"]X[/COLOR]   [COLOR="Navy"]app-defaults[/COLOR]   xorg.con
[COLOR="Navy"]Xresources   cursors[/COLOR]   xorg.conf.20081129105309
[COLOR="Lime"]Xsession[/COLOR]   default-display-manager   xorg.conf.20081129111946
[COLOR="Navy"]X session.d   fonts[/COLOR]   xorg.conf.20081129112155
Xsession.options   rgb.txt   xorg.con.dist-upgrade-200811272336
XvMCConfig   [COLOR="Navy"]xinit[/COLOR]
Xwrapper.config   [COLOR="Navy"]xkb[/COLOR]

---

### Post by Olivier2371 on 2008-11-29
Did you put a space between "ls" and the rest?

The command I gave you in the previous post should have shown you what you had in the X11 folder.

try this:

sudo nano /etc/X11/xorg.conf~

---

### Post by linux_tech on 2008-11-29
You need to delete the current xorg.conf and name one of the other xorg.conf.####### to xorg.conf
see here for details
[http://ubuntuforums.org/showthread.php?t=258186](http://ubuntuforums.org/showthread.php?t=258186)
[http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/](http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/)

---

### Post by Voland on 2008-11-29
You can look up is there any xorg.conf.****** file with command ls -la.

---

### Post by Dorenrab on 2008-11-29
> **Olivier2371 said:**
> Did you put a space between "ls" and the rest?

The command I gave you in the previous post should have shown you what you had in the X11 folder.

try this:

sudo nano /etc/X11/xorg.conf~Indeed, I did put a space between ls and the rest of the command.

As for the command in the quoted post, when I entered it, I got another blank document.

---

### Post by Olivier2371 on 2008-11-29
Try the command given by Voland.

ls -la

---

### Post by Dorenrab on 2008-11-29
The files I'm looking for would be in the /etc/X11/ folder, right?  When i looked in there, I found:

> xorg.conf.20081129105309
xorg.conf.20081129111948
xorg.conf.20081129112155
xorg.conf.dist-upgrade-200811272336

---

### Post by falcon61102 on 2008-11-29
What you can do is try renaming the last file in that list (xorg.conf.dist-upgrade-200811272336)  to just xorg.conf and that should get you back to the default setup of your display.  Rename and then restart.

If that doesn't work, boot back up in the Recovery mode and you'll have to try to adjust things from there.  Does you graphics chip require Restricted Drivers?  You can check that by going to System>Administration>Hardware Drivers and look for your chip.

---

### Post by Dorenrab on 2008-11-29
Hm, renaming the oldest xorg.conf had no effect.  Still getting a blank screen once I log in.  As for my settings, I cannot access that menu in the state that my computer is in.

I think I'll just end up wiping the hard drive.  No one who uses this computer has anything that's irreplaceable, so it would be no loss if everything was deleted.

---

### Post by Olivier2371 on 2008-11-29
That is probably a good idea, if you have nothing that you would like to keep.

For me the first time I tried to upgrade to 8.10, it failed. But for some reason the second time it worked without any problem.

---

### Post by falcon61102 on 2008-11-29
Other people have also experienced problems upgrading from 8.04 to 8.10 so a fresh install might be the easiest, and quickest way to handle that.  If you can, download the 8.10 iso and burn it to a cd and just install fresh from that so you don't have to worry about doing the upgrade again.

---

### Post by Dorenrab on 2008-11-29
Indeed I shall.  I already have an 8.10 ready, so all I need to do is figure out how to wipe the HD.:lol:

Thank you all for your patience through all of this.

---

### Post by falcon61102 on 2008-11-29
The easiest way to accomplish that would be to restart the computer from the CD, verify the CD integrity and then install.  When you install, use the guided partitioner and select the entire drive.  That will wipe everything currently on the drive and replace it with the partitions necessary for Ubuntu to run.  Only do this method if you do not have a dual boot setup currently.

---

### Post by Dorenrab on 2008-11-29
Blargh, it's not letting me boot to the live disk.  I changed the boot sequence, but it won't run.

---

### Post by falcon61102 on 2008-11-29
Could it be the CD?

Try inserting one of your Windows CDs and see if they will boot.  If they boot then it is more than likely the CD.  If not, then something probably isn't setup correctly in your BIOS.

---

