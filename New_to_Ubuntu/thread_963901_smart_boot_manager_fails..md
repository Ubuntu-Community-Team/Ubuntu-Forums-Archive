---
title: "smart boot manager fails."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by robert shearer on 2008-10-30
I am trying to make a boot floppy using smart boot manager so I can boot from cd rom.  I am using the tutorial here... 
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

I copy the sbm.bin file from the Ubuntu live cd to my desktop and then 

```
cd Desktop
```
And
```
sudo dd if=sbm.bin of=/dev/fd0 
```

The command is executed,the floppy has activity and the terminal reports...
blunder@ubuntu:~$ cd Desktop
blunder@ubuntu:~/Desktop$ sudo dd if=sbm.bin of=/dev/fd0 
[sudo] password for blunder: 
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 86.8254 s, 17.0 kB/s
blunder@ubuntu:~/Desktop$ 


When I mount the floppy it is named"SMART BTMGR "but is empty!
Opening properties shows,  539kb used,contents=nothing, and filesystem = msdos

When I try to just drag and drop the smb.bin to the floppy it says error
1.4Mb is available but 1.4Mb is required.


It seems the smb.bin file is bigger than 1.4Mb but it is made for a boot floppy.?

What am I doing wrong??

---

### Post by louieb on 2008-10-30
After running the **dd** command the boot floppy is ready.  You won't see any files on it in the file browser -  thats normal. 

Just put it in the floppy drive and reboot the computer. If your floopy drive is 1st in the boot order SBM should come up.

---

### Post by robert shearer on 2008-10-30
Hmmm, tried that on two machines now with no result.

The floppy has activity then a pause and then the hard drive boots on one and the other goes to a blank screen(no hard drive.  I'm trying to boot from a live cd hence the need for the boot floppy.)

Tried 3 floppys made on two different machines.So comes back to the smb.bin file which shows as 1.4 MB (1474560 bytes) in the properties window but the floppy it makes shows as 539kb in it's properties window.?

---

### Post by caljohnsmith on 2008-10-30
I'm not sure why you're having problems with Smart Boot Manager, but I thought I would mention that I've used SBM successfully from a floppy using that same procedure you used. The reason why the floppy appears empty is because Smart Boot Manager lives in the MBR (Master Boot Record) of the floppy and in the next couple dozen sectors after it; so you won't see any data on the floppy. Are you sure the BIOS on those computers is set to boot the floppy drive before any other drives? That's something to check if you haven't all ready.

And just out of curiosity, what do you need SBM for? There are many boot loaders available, and it might be there is another solution for your situation.

---

### Post by stweat on 2008-11-04
Try This...Go to \/ for instructions.
[http://louboldt.com/ilinuxsbm.htm](http://louboldt.com/ilinuxsbm.htm)

Had similar problem with sbm.bin
1.38 1.44
Used sbm.img  with  RawWriteWin.exe
 and worked for Me to boot cd......

---

### Post by robert shearer on 2008-11-05
> **caljohnsmith said:**
> 

And just out of curiosity, what do you need SBM for? There are many boot loaders available, and it might be there is another solution for your situation.

I was trying to get an old compaq laptop ( that won't boot from cd in bios) to boot using the Thinstation cd. I was hoping that I could boot the smb floppy and have it hand off to the cd, boot Thinstation which would then connect to my Edubuntu box.

Managed to get the Thinstation to boot using another compaq (twin of the first) lappy that does boot from cd but it doesn't recognise my pcmcia Ethernet card so using smb would not have helped anyway. Sigh.:neutral:

What I am trying to do is recycle an old lappy (pentium mmx 233Mhz/96Mb Ram) to use as a dumb terminal in a room where low noise is a priority.

I had hoped to connect it via Ethernet to something like Edubuntu which seems to set up the thinclient environment by default. (anything else is beyond me)

---

