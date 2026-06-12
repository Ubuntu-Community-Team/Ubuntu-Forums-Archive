---
title: "How to install ATI drivers"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by loseby on 2008-09-18
Have downloaded them and when I click on them I get this message

"Could not open the file /home/bill/Documents/ati…ller-8-8-x86.2.x86_64.run.
edit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

---

### Post by northern lights on 2008-09-18
Are you certain you need to install this particular driver.
Is there no option under "System > Administration > Hardware Drivers"?

---

### Post by sloggerkhan on 2008-09-18
installing the binary from ati's website is more complex than click and run. If this is your first time with a linux system, I suggest system>admin>hardware drivers
and put a check mark in the ati driver box.

While you will not have the absolute most up to date drivers, it is simpler than installing yourself.

If you still want to install yourself, you need to make the file as executable and run with admin permissions. be sure to use --help or such to lookup the proper --buildpkg ubuntu/gutsy or similar tag to use to build *.deb files with the installer. To do this, you may have to use synaptic to add some dependencies, forget what they are. Once you have *debs, it's click and run, and if you want to grab the latest driver in the future it's as simple as sudo buildpkg ubuntu/whatever && sudo dpkg [install option, forget the letter it is] *.deb in directory you're in. If you search these forums or phoronix.com's forums, you will find more detailed instructions. The ubuntu wiki is also a good source.

---

### Post by loseby on 2008-09-18
I have tried the hardware option before and it caused major problems so upon reinstall I am staying away from that  option.  Have tried using EnvyNG but it wouldnt recognise my video card ( 4870 ) and using the manual option resulted in more errors so thats why I ended up downloading the latest drivers. 

Was hoping for an easy option in installing the latest drivers.......actually I find it surprising that installing is such a bugger

---

### Post by northern lights on 2008-09-18
Please post the output of ```
sudo lshw -C display
```Thank you.

---

### Post by sloggerkhan on 2008-09-18
> **losbey said:**
> I have tried the hardware option before and it caused major problems so upon reinstall I am staying away from that  option.  Have tried using EnvyNG but it wouldnt recognise my video card ( 4870 ) and using the manual option resulted in more errors so thats why I ended up downloading the latest drivers. 

Was hoping for an easy option in installing the latest drivers.......actually I find it surprising that installing is such a bugger

Installing ati drivers is easy, but probably not for a new linux user.
And yes, with a 4870 you do need newest drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%20Ubuntu%208.04%20(Hardy)%20with%20ATi%208.443.1-1%20and%20above%20binary%20drivers)

has the basics.

Make sure you purge any other ati fglrx driver install previous to installing the latest one.

---

### Post by loseby on 2008-09-18
> **northern lights said:**
> Please post the output of ```
sudo lshw -C display
```Thank you. 
*-display UNCLAIMED     
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0

---

### Post by northern lights on 2008-09-18
> **losbey said:**
> product: ATI Technologies IncThat's just horrid. Not even chipset info...

Since you've revealed that in a post in between anyhow, [this thread]("http://ubuntuforums.org/showthread.php?t=878709") might be an interesting read.

---

