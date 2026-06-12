---
title: "Installer"
date: 2020-02-17
forum: New to Ubuntu
---

### Post by cuddy29772 on 2020-02-17
Right … 

I’m trying to use the Terminal commands* — listed [here]("https://ubuntu.com/download/iot/installation-media") — to turn a USB flash drive into an Ubuntu installer.

I’ve had to enable the root account on the relevant machine in order to do so.

However?

Having done so the Terminal tells me that — as the file is not in a gzipped format — create the installer.

Where do I get the gzipped iso file?

If they are no longer produced, how do I turn the iso files into a gzipped file?

OR what terminal commends do I need, to make the process work?

For some reason, balenaEtcher doesn’t worker on these file.



*        On 1 21” iMac running macOS 10.15.3

---

### Post by CelticWarrior on 2020-02-17
The file is probably corrupted.

And why are using 32-bit?

---

### Post by yancek on 2020-02-17
> Where do I get the gzipped iso file?

The gunzip command in the post is where you get it, the command should create it as  that's the purpose of running the command and the second part (the dd) is to write it to the usb.  Never seen this before but I don't use a Mac.

---

