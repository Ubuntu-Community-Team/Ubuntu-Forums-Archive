---
title: "Install PCI Firewire Card"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by dmulkearns on 2008-04-23
This is a newbie question, I have the beta for 8.04 running on my desktop computer, I just installed a startech PCI card and nothing happens.. I can't tell for sure but I assume it's not recognized.

How can I check ?
IF this card does not work which one will ?

Thanks
Dave

---

### Post by phidia on 2008-04-23
For PCI cards it's good to do a search linuxquestions.org has a hardware database as do the Ubuntu community docs.

You can open a terminal and type dmesg or lspci -v the latter probably will be easier to read since dmesg will give you lots of system stuff to wade though.

Sometimes a 1394/firewire drive isn't recognized because of the filesystem that's on the drive-so why do you think it isn't working-what are you seeing or not seeing that you want to?

---

