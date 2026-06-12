---
title: "DVD drive not booting"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by rdd85 on 2014-04-10
I have ubuntu 12.4 installed on my PC. I wanted to put a different  distro on the computer but the computer does not boot from the DVD. I  have made sure the BIOS is set and I even hit the del key after POST to  select the boot device, and all the screen does is go black for about  2-5 minutes and boot to the HD as normal. I am not sure what other info  would be helpful but let me know and I will post whatever is needed. I  think the drive is mounted but I dont know for sure.

---

### Post by Mark Phelps on 2014-04-10
That sequence means your PC does not see the DVD as bootable.  To confirm the disk is OK, you need to try it in another PC to see if that will boot from it.

---

### Post by rdd85 on 2014-04-11
I have already done this with several different Linux/BSD distros as well as a windows Vista install disk on my laptop, primary desktop and this computer. This computer is the only one that will not boot any of these.

---

### Post by QIII on 2014-04-11
Pull a DVD player from another computer and try it.  Given what you have told us, if a different DVD on that computer does not work I would suspect the motherboard.

---

### Post by rdd85 on 2014-04-11
Before I do this, how can I confirm that the drive is actually mounted? Is there a cmd to list all mounted media devices and drives?

---

### Post by QIII on 2014-04-11
Issue the command

```
lsblk
```

in the terminal.

You should get something like this:

[ATTACH=CONFIG]251921[/ATTACH]

sr0 at the bottom is my DVD with a Fedora DVD with the install iso.

If you get no mount point and the default size of 1024, it is not being read.

If you do not see sr0, the DVD device is not being detected.

---

### Post by echotech2 on 2014-04-11
FWIW, I was having problems booting from a USB stick or DVD on an older machine, BIOS dated 2006. On one reboot I happened to notice the statement "This AHCI version supports Hard Drive and CD-ROM only".  Disabling AHCI and DVD boots OK.

---

### Post by su:bhatta on 2014-04-11
Which distro are you booting and did you checksum the iso for defects?

---

