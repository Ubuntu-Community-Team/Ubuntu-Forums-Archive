---
title: "Trying to figure out how to add network printer."
date: 2014-11-10
forum: New to Ubuntu
---

### Post by Rob_Halverson on 2014-11-10
Okay, I figured out how to make a bootable usb.  I am a Xubuntu user now!  But can't find the "Sharp MX-M260N" choice when trying to add network printer.  Any tricks welcome.

---

### Post by deadflowr on 2014-11-10
Perhaps try using the cups browser interface
Open a browser and type
```
localhost:631
```
It'll open the cups interface.
Go to Administration, then click on Add printer.
Does the printer show up in Discovered Network Printers?

---

### Post by pfeiffep on 2014-11-10
> **Rob_Halverson said:**
> Okay, I figured out how to make a bootable usb.  I am a Xubuntu user now!  But can't find the "Sharp MX-M260N" choice when trying to add network printer.  Any tricks welcome.If you know the printer IP address you may choose manual in adding a Network Printer.

---

### Post by Mike_Walsh on 2014-11-10
> **Rob_Halverson said:**
> Okay, I figured out how to make a bootable usb.  I am a Xubuntu user now!  But can't find the "Sharp MX-M260N" choice when trying to add network printer.  Any tricks welcome.

Hallo, Rob.

I've just been setting up this exact same process myself. My main workhorse, running Ubuntu 14.04, has my Epson printer attached to it.....and I've just set my old Dell laptop, running Puppy Linux, up to print from it.

You say you're trying to setup network printing. Are you wanting to set things so that two or more machines will print from the same printer? From the sound of things, you haven't set your printer up to work with any machine yet. You'll need to get your printer working with one machine first, which will be the 'host'; you will then need to set things up for your second machine, the 'client', to work with the 'host' machine via CUPS. The client machine will also need setting up with the correct driver for your printer, as will the 'host' itself.

We need a little bit more detail first. You've given us the details for your printer; but it would help to know what your machines are, and what operating systems they're both running. Two Linux machines will require a different procedure from one Linux and one Windows machine.

Regards,

Mike.

---

