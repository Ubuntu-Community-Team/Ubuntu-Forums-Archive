---
title: "start-up script to detect when external media is plugged in"
date: 2014-04-17
forum: Programming Talk
---

### Post by IAMTubby on 2014-04-17
Hello,
 Is there a start-up script or something which I can edit, so that it detects when my pendrive is plugged in.

Basically, when I plug-in my pendrive, I want the system to detect that and then call another program which I have written, instead of me manually running the program from the terminal after the pendrive is plugged-in.

Thanks.

---

### Post by mikewhatever on 2014-04-17
Check out this: [http://askubuntu.com/questions/25071/how-to-run-a-script-when-a-specific-flash-drive-is-mounted](http://askubuntu.com/questions/25071/how-to-run-a-script-when-a-specific-flash-drive-is-mounted).

---

### Post by IAMTubby on 2014-04-17
> **mikewhatever said:**
> Check out this: [http://askubuntu.com/questions/25071/how-to-run-a-script-when-a-specific-flash-drive-is-mounted](http://askubuntu.com/questions/25071/how-to-run-a-script-when-a-specific-flash-drive-is-mounted).
Thanks mike for the reply. But I still have some trouble getting it to work.

I checked the output of the lsusb -v command, and it's as follows
```

Bus 002 Device 007: ID 8564:1000
Device Descriptor:
  bLength                18
  ..
  ..
  idVendor           0x8564
  idProduct          0x1000

```

So I created a new file as follows
```

IAMTubby@IAMTubby-Inspiron-1545:/etc/udev/rules.d$ ls
100-persistent-transcend.rules  70-persistent-cd.rules  70-persistent-net.rules  README
IAMTubby@IAMTubby-Inspiron-1545:/etc/udev/rules.d$ cat 100-persistent-transcend.rules 
**ACTION=="add", ATTRS{idVendor}=="0x8564", ATTRS{idProduct}=="0x1000", RUN+="/home/IAMTubby/Desktop/run.sh"**

```

My script is as follows
```

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat run.sh 
sleep 10
touch transcendfile.txt

```

I tried removing and inserting the pendrive few times, but the script doesn't seem to run as suggested by the ps output.

Please advise.
Thanks.

PS : Please find attached the output of my lsusb -v command. Have highlighted the details for my pendrive in blue which is **8564:1000**

---

### Post by steeldriver on 2014-04-17
Double check the IdVendor and IdProduct fields using the udevadm attribute walk instead of lsusb - it may be subtly different (e.g. minus the 0x prefix)

```

udevadm info -a -p  $(udevadm info -q path -n **/dev/sde**) | less

```

where you have replaced **/dev/sde** with the block device file of your device

---

### Post by mikewhatever on 2014-04-17
How about ATTRS{idVendor}=="8564", ATTRS{idProduct}=="1000" instead of ATTRS{idVendor}=="0x8564", ATTRS{idProduct}=="0x1000"?

---

### Post by steeldriver on 2014-04-17
^^^ that's exactly what I'm hinting at (but verifying with udevadm would be a good step imho)

---

### Post by IAMTubby on 2014-04-17
> **steeldriver said:**
> Double check the IdVendor and IdProduct fields using the udevadm attribute walk instead of lsusb - it may be subtly different
steeldriver, thanks for the reply. But I'm still not able to get it

> udevadm info -a -p  $(udevadm info -q path -n **/dev/sde**) | less where you have replaced **/dev/sde** with the block device file of your device
To find the block device file, I did a mount and got the output as **/dev/sdb1 on /media/Transcend type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)**

I then ran the command **udevadm info -a -p  $(udevadm info -q path -n [B]/dev/sdb1**) | less[/b]

However, the output I get is same as before. Please find the required part of the output below
[b]ATTRS{idVendor}=="8564"
    ATTRS{idProduct}=="1000"[/b]

Please find attached the entire output.

---

### Post by IAMTubby on 2014-04-17
> **mikewhatever said:**
> How about ATTRS{idVendor}=="8564", ATTRS{idProduct}=="1000" instead of ATTRS{idVendor}=="0x8564", ATTRS{idProduct}=="0x1000"?
mike, just tried that, but doesn't seem to work.

---

