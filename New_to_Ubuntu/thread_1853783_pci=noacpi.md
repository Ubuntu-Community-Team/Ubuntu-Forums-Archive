---
title: "pci=noacpi"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by michaelcarey95 on 2011-10-03
Hey.  Today I downloaded the Ubuntu 11.10 daily build and created a live USB.  To boot, I had to set pci=noacpi as well as noapic.  I installed, and everything went just fine, but before I reboot, how do I set this for when Ubuntu boots without the live USB?  And how do I set it to do this every boot, so I don't have to worry about it?

---

### Post by 2F4U on 2011-10-03
The grub2 configuration can be changed in the file /etc/default/grub. Don't forget to execute update-grub after you are finished. You add your parameters to a line that reads something like this

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by michaelcarey95 on 2011-10-05
Thanks for the info.  I looked up Boot Options on Google and am able to boot every time with these parameters.  However, I can't set this as permanent.  I used terminal to "sudo nano /etc/default/grub" and added the correct parameters and did an update-grub, but it still won't boot properly without me doing it manually each time.

---

### Post by Quackers on 2011-10-05
After making the edits to that line did you exit nano correctly. saving the file?
Please post the line in question in your next reply. Thanks

---

### Post by michaelcarey95 on 2011-10-05
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=off pci=noacpi
GRUB_CMDLINE_LINUX=""

```

After this, I hit CTRL+X to exit, and then hit Enter to save as /etc/default/grub (it asks me).  Then it takes me back to terminal without nano and I typed update-grub.  I'll real quick do a reboot and see if it works.  

The problem is, once I get to the log in screen, and type my password, all I get is a blank purple screen without the desktop ever loading.  When I set the parameters at startup, it loads the desktop very quickly.

---

### Post by sanderd17 on 2011-10-05
It should be

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off pci=noacpi**"**
GRUB_CMDLINE_LINUX=""

```

So with the quotes after noacpi

---

### Post by Quackers on 2011-10-05
The boot options should be within the quotes

---

### Post by anewguy on 2011-10-05
> **michaelcarey95 said:**
> ```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=off pci=noacpi
GRUB_CMDLINE_LINUX=""

```

After this, I hit CTRL+X to exit, and then hit Enter to save as /etc/default/grub (it asks me).  Then it takes me back to terminal without nano and I typed update-grub.  I'll real quick do a reboot and see if it works.  

The problem is, once I get to the log in screen, and type my password, all I get is a blank purple screen without the desktop ever loading.  When I set the parameters at startup, it loads the desktop very quickly.

Using the editor again, enclose the entire string in quotes like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=off pci=noacpi
                                        :
                                        : remove this quote


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off pci=noacpi"
                                                            :
                                           put quote here   :


Remember to run update-grub again - BTW you might need sudo update-grub.

Dave ;)

---

### Post by michaelcarey95 on 2011-10-05
Thanks so much guys.  It works now!!  Ubuntu Forums is so great; the support is better than paid.  :p

Just two more things.  Not terrible problems, but annoying.  Ever since I got this working a couple minutes ago, my volume buttons (hardware) don't work, and the sound is all the way up automatically with the login sound.  Anyway to fix this?  Also, the power button (hardware) automatically turns off the entire machine.  It used to give me an option.

Again, thanks for all the help so far!

---

### Post by Quackers on 2011-10-05
The volume buttons are possibly acpi controlled - and you've turned that off, so are unlikely to work.
The volume can be controlled from the top menu bar via the speaker icon.

As acpi is off you should keep an eye on temperature. Listen for fans being on all the time. You don't want to overheat your pc!

There are options for the power button setting in Power Options/System Settings.

---

### Post by michaelcarey95 on 2011-10-05
Alright, thanks for the info.  I'll keep an eye on heat.  I figured out the sound keys, partly.  I have to press fn THEN the volume keys.  I think I accidentally turned f-lock on and can't figure out how to turn it off.  I'm looking it up right now.

Edit: Everything is working fine now, after a reboot.  Thanks so much for the help!

---

