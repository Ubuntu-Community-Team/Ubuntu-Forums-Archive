---
title: "[SOLVED] Averatec 6200 series laptop errors"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by vocalstud69 on 2008-05-31
I'm trying to install xubuntu on an old laptop of mine, to see if it will work.  But, it didn't.  I got XP to install, but xubuntu hangs, as does every other distro I've tried.  The only linux I've gotten to work on here has been DSL on a liveCD without the hard drive installed.  This the output when I try to install or run the LiveCD:

[27.167504] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[94.566951] ata1.00: revalidation failed (errno=-5)
[129.679101] ata1.00: revalidation failed (errno=-5)
[136.476479] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[136.476531] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
[136.476576] ata2.00: status: {DRDY}
[166.896968] ata2.00: revalidation failed (errno=-5)
Starting system log daemon: syslogd, klogd

And after that, it just sits there.  I let it sit there for an hour, but nothing happened.  I tried Xubuntu and Fluxbuntu as well, and the same thing happens every time.  I haven't tried anything other than those three, xubuntu, fluxbuntu, and DSL.

---

### Post by vocalstud69 on 2008-06-01
Just an update for anyone interested.  I got it to install with the alternative cd image, and then when it started up I had to go into the GRUB menu and append to the boot script 'vga=771 noapic nolapic acpi=off' to the end.  

I can't figure out how to permanently append those to the boot script, because every time I restart, it resets to the original script. I would love it if someone could show me how to permanently apply those four things to it.

---

### Post by vocalstud69 on 2008-06-01
Nevermind, I figured it out on my own.  I have to edit the /boot/grub/menu.lst to get it to work correctly.  I just added those four things above to the boot script at the end of menu.lst.  I haven't been able to get the livecd to work at all.  It's not important, since I got it to install already, but it gave me a headache for a while.

---

### Post by vocalstud69 on 2008-06-01
I realize that there are several other posts with people 
that have the same problem I did, but they are two years 
old, and I don't know if it would matter any longer.  I'm 
still a newbie, but here's exactly what I did to get it
to work.  It does work, it's what I'm typing on right 
now, actually.  

-This does work with Xubuntu 8.04-
The things required are an alternative install cd of your favorite
flavor and some other liveCD, one that supports a 
Safeboot of some kind.  I used PCFluxboxOS, simply because 
it's a small download, it automounts your hard drive 
and it has the built in Safeboot option with the four 
operands that are needed to do this:

```
noapic nolapic vga=771 acpi=off
```

So, you start your computer and put in the *buntu alternate 
install cd, and when the menu comes up, hit F6, because 
it will not work without those four openands at the end; 
noapic nolapic vga=771 acpi=off. Type those in, and then 
hit enter.  The installer should run normally.  
  
The installer wants you to be hooked up to the internet
for it to install completely, so just have it hooked up 
to a CAT5.  When it's done, it's going to tell you that 
you have to reboot.  Let it reboot, and quickly put the 
liveCD of your choice in the drive.  On the Averatec 6200, 
I just hit F11, because then it lets me chose when to boot
and which device to boot from.  You obviously boot from your
cd drive, and when the menu for your liveCD comes up, highlight
the option for 'Safeboot' and hit enter.  I'll keep on going 
assuming that your using PCFluxboxOS.  I just used a CD-RW for 
it, that way I didn't waste a CD. 

When the login screen comes up, type in 'guest' for both user 
and password.  This way you have a desktop with internet and 
can surf for answers if need be, and edit what you need to on 
your hard drive. 

I had to edit three files to get this to work properly: xorg.conf, 
menu.lst, and acpi-support.  

To edit the first, right click on the desktop, and click on 'Terminal'.
Then you have to type in 'su', not 'sudo su', because for some reason
PCFOS doesn't have sudo installed.  I dont' know why.

Then, enter the root password, which is 'root', and hit enter.  Then, 
type in 

```
nano /mnt/hda1/etc/X11/xorg.conf
```

Now, the file that comes up has a bunch of 'Sections', and we want the 
one that says 'Device' on it.  If you used 6.06 and have the 6200, it 
should look like this:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection
```


You need to add a line after 'Identifier', and call it 'Driver' and then name the driver as "sis"

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "sis"
EndSection
```

Don't change anything else, and hit 'CRTL+x' to exit, then 'y' to save, and enter to overwrite the original file.

After you hit enter, it should bring you back to the root command prompt.  
Then, type in: 

```
nano /mnt/hda1/boot/grub/menu.lst
```

What comes up is a long file, but all of it is gibberish and unimportant to what I needed, so I just scrolled down to the end, until I see:

```
## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=ccbbaff4-9cdf-49ff-a7dc-15dbba7bab2b ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic


```

All we want to do is append four things to the end of the 'kernel' line. So, arrow over until the cursor is after 'splash', and type: noapic nolapic vga=771 acpi=off

So, it would look like this:

```
## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=ccbbaff4-9cdf-49ff-a7dc-15dbba7bab2b ro quiet splash noapic nolapic vga=771 acpi=off
initrd          /boot/initrd.img-2.6.24-16-generic


```

The four operands go after the word 'splash'.

Then, after adding those four things, you again hit 'CRTL+x' and 'y', and then enter.

Then, the last file to edit is the acpi-support file.  Type in:

```
nano /etc/default/acpi-support
```

When the file comes up, scroll down until you see:

```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate
```

All you have to do is change 'true' to 'false', so it reads:

```
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate
```

Then, hit 'CRTL+x', 'y', and enter.  Then, you're done.  Close out of the terminal and out of PCFOS, and then try to log onto your *buntu install.  It worked for me twice, so it shouldn't be a fluke. I hope this is readable enough to follow.  It is working on 8.04, which is what I'm using to type this.

---

### Post by phyrewall on 2008-07-24
Thanks for all the hard work and documenting it. 

My only question is: If ACPI support is off, are we losing important functionality?

---

