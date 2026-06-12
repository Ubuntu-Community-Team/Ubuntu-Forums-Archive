---
title: "Re: Problems Mounting DVD drive/burner"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by Heaphy on 2012-05-27
Hi, I'm having issues with my DVD drive too and not sure how to fix it.
I am also a bit new to the wonderful world of linux - running ubuntu 12.04

I have tried following the instructions on this thread but it seem fruitless for me.

When typing in
```
 wodim --devices 
```

I ended up recieving this message.
```
 heaphy@heaphy-Not-Specified:~$ wodim --devices
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation. 
```

Also when previously typing in: cd /dev and then: ls
I got the following...
```
 heaphy@heaphy-Not-Specified:~$ cd /dev
heaphy@heaphy-Not-Specified:/dev$ ls
agpgart          net                 sdb1      tty24  tty57      ttyS30
autofs           network_latency     sdb2      tty25  tty58      ttyS31
block            network_throughput  sdb5      tty26  tty59      ttyS4
bsg              null                sdb6      tty27  tty6       ttyS5
btrfs-control    oldmem              sdc       tty28  tty60      ttyS6
bus              parport0            sdc1      tty29  tty61      ttyS7
char             port                sdd       tty3   tty62      ttyS8
console          ppp                 sdd1      tty30  tty63      ttyS9
core             psaux               sg0       tty31  tty7       uinput
cpu              ptmx                sg1       tty32  tty8       urandom
cpu_dma_latency  pts                 sg2       tty33  tty9       usbmon0
disk             ram0                sg3       tty34  ttyprintk  usbmon1
dri              ram1                shm       tty35  ttyS0      usbmon2
ecryptfs         ram10               snapshot  tty36  ttyS1      usbmon3
fb0              ram11               snd       tty37  ttyS10     usbmon4
fd               ram12               stderr    tty38  ttyS11     usbmon5
fd0              ram13               stdin     tty39  ttyS12     v4l
full             ram14               stdout    tty4   ttyS13     vcs
fuse             ram15               tty       tty40  ttyS14     vcs1
hpet             ram2                tty0      tty41  ttyS15     vcs2
input            ram3                tty1      tty42  ttyS16     vcs3
kmsg             ram4                tty10     tty43  ttyS17     vcs4
log              ram5                tty11     tty44  ttyS18     vcs5
loop0            ram6                tty12     tty45  ttyS19     vcs6
loop1            ram7                tty13     tty46  ttyS2      vcsa
loop2            ram8                tty14     tty47  ttyS20     vcsa1
loop3            ram9                tty15     tty48  ttyS21     vcsa2
loop4            random              tty16     tty49  ttyS22     vcsa3
loop5            rfkill              tty17     tty5   ttyS23     vcsa4
loop6            rtc                 tty18     tty50  ttyS24     vcsa5
loop7            rtc0                tty19     tty51  ttyS25     vcsa6
loop-control     sda                 tty2      tty52  ttyS26     vga_arbiter
lp0              sda1                tty20     tty53  ttyS27     video0
mapper           sda2                tty21     tty54  ttyS28     zero
mcelog           sda5                tty22     tty55  ttyS29
mem              sdb                 tty23     tty56  ttyS3

```


Any ideas of how to help?

---

### Post by Sef on 2012-05-27
Copied thread to ABT.

---

