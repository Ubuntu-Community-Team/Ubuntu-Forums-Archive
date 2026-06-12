---
title: "PS Vita wont detect content manager in Virtualbox (through usb)"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by littleslayer15 on 2012-04-19
I downloaded content manager from sony's website and set it up fine, but when I plugged my vita in to my usb port my vita says "could not connect to the device." This isn't just a problem with my vita because VB doesn't detect my flash drive either. I am running Ubuntu 10.04 and using windows 7 in VB. VB does detect my wireless mouse though.

---

### Post by jerome1232 on 2012-04-19
Have you installed guest additions? (goto your top toolbar-devices-install guest additions) Follow the instructions. Reboot your guest.

Try right clicking the small usb icon in the lower right of virtualbox's window, and giving the guest access to the usb device.

See screenshot for example

---

### Post by littleslayer15 on 2012-04-19
I don't see that in mine and my wireless mouse works which uses a usb port so I don't know why that is the only thing that works

---

### Post by jerome1232 on 2012-04-19
> **littleslayer15 said:**
> I don't see that in mine and my wireless mouse works which uses a usb port so I don't know why that is the only thing that works
What is it you don't see I mentioned 2 menu's to look at in my post.

Virtualbox doesn't grab your mouse through hardware so that actually has nothing to do with usb. 

What do you see? What version of Virtualbox are you using? Do you have guest additions installed? Is usb support enabled in the VM's settings? 

To check the last shutdown the guest, click your Virtual Machine in the list of virtual machines, select settings, select USB in the left hand box, make sure enable USB is checked.

Also make sure you are in the group vboxusers, you can check if your in that group with this command from a terminal
```
groups
```

If you are not in that group add yourself like this, logout then log back in for the changes to take affect. You can copy and paste the code exactly.

```
sudo adduser $USER vboxusers
```

So to reiterate, in order of USB to work you must have Guest additions installed on the guest, you must have USB support enabled for the guest in it's settings, and your user must be in the group vboxusers.

---

### Post by littleslayer15 on 2012-04-19
Sorry I do have guest addition installed I should have told you that so I didn't see the USB symbol in the bottom left corner. In my settings menu I don't have a USB option I only have
general, system, display, storage, audio, network, serial ports, and shared folders. When I type groups into terminal this is what is says
"adm dialout cdrom plugdev lpadmin admin sambashare"
and when I type the sudo adduser $USER vboxusers code this is what it says "adduser: The group `vboxusers' does not exist." so I am not sure if I am in a group or not. 
thank you for your help so far it is greatly appreciated.

---

### Post by jerome1232 on 2012-04-20
Do you have the OSE (Open source edition) installed? If you go to about->Virtual Box, what version does it say?

Virtualbox-OSE doesn't support USB, you need the proprietary version from Oracle. Installing from the repo's *should* get you the proprietary version. If that succeeds it will remove virtualbox-ose as they conflict.

```
sudo apt-get install virtualbox
```

If that just still gives you the OSE version, download the .deb from [HERE]("https://www.virtualbox.org/wiki/Linux_Downloads")

edit:

Once that is all said and done, try again, if it still doesn't work, check your groups again with the "groups" command. If you are not in vboxusers, add yourself, if it again tells you that the group doesn't exist you can create it with the following code, then rerun the previous command to add yourself to the new group. A logout/login is required for group changes to take affect.

```
sudo addgroup vboxusers
```

---

### Post by littleslayer15 on 2012-04-20
Sorry it took me so long to reply but I did have the OSE version installed, so I got the version you said to get (the command didn't work so I got it from the website.)Then I turned USB support on and added myself to the group but my flash drive and vita still don't mount in VB.

---

### Post by jerome1232 on 2012-04-20
You have to pass control to the virtual machine by right-clicking the little usb plug icon in the bottom right of the window.

---

### Post by littleslayer15 on 2012-04-20
It says no USB drives connected even thought Ubuntu clearly detects it. I have also safely removed the drive on Ubuntu (by right clicking on the icon in the my computer section) and that didn't work either.

---

### Post by jerome1232 on 2012-04-20
Have you rebooted since you added the groups? Perhaps try reinstalling guest additions as well (maybe they are different between the different versions of virtualbox)

Unfortunately I don't know how else to troubleshoot it, it should work, it does for me.

---

### Post by littleslayer15 on 2012-04-20
Well I am getting closer I only enabled USB support in VB I never told it to let my flash drive and vita work on it (which was stupid of me.) So now when I plug my flash drive in, the USB icon in the bottom right detects them and windows makes the sound when you plug something into the USB slot but the flash dive doesn't show up in the my computer section on windows.

---

### Post by jerome1232 on 2012-04-20
> **littleslayer15 said:**
> Well I am getting closer I only enabled USB support in VB I never told it to let my flash drive and vita work on it (which was stupid of me.) So now when I plug my flash drive in, the USB icon in the bottom right detects them and windows makes the sound when you plug something into the USB slot but the flash dive doesn't show up in the my computer section on windows.

Sometimes I have a weird issue with Win7 (not sure what version you are running) where I have to open Disk Volume Management and manually assign a letter to the partition.

Disk Volume Management can be found under Control Panel->Administration Tools->Computer Management->Storage->Disk Management.

---

### Post by littleslayer15 on 2012-04-22
My flash drive doesn't even show up there.

---

