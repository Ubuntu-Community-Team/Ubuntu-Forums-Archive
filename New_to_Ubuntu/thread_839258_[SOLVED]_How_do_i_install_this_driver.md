---
title: "[SOLVED] How do i install this driver?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-24
Hi,

I'm having problems with internet dropping out and found this:

[http://people.redhat.com/csnook/atl2/](http://people.redhat.com/csnook/atl2/)

How do i install the driver or patch?

Thanks a lot..

---

### Post by hyper_ch on 2008-06-24
download the file, unpack it, read the instructions

---

### Post by hopelessone on 2008-06-24
perhaps you should download it and realize there are none b4 comments...so many times you do this hyper_ch...lol...

i can only do a  ./make

---

### Post by hyper_ch on 2008-06-24
> **hopelessone said:**
> perhaps you should download it and realize there are none b4 comments...so many times you do this hyper_ch...lol...

i can only do a  ./make

why should I download it to help you? Isn't it your job to give me the info that I need to help you? I don't see any mentioning of you having downloaded it and no install instructions found ;)

---

### Post by hopelessone on 2008-06-24
i meant no offense..

as i said i can't figure out how to install the drivers and or patch..

redox@redox-pc:~/atl2-2.0.4$ make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/redox/atl2-2.0.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/redox/atl2-2.0.4/atl2_main.o
  CC [M]  /home/redox/atl2-2.0.4/atl2_hw.o
  CC [M]  /home/redox/atl2-2.0.4/atl2_ethtool.o
  CC [M]  /home/redox/atl2-2.0.4/atl2_param.o
  LD [M]  /home/redox/atl2-2.0.4/atl2.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/redox/atl2-2.0.4/atl2.mod.o
  LD [M]  /home/redox/atl2-2.0.4/atl2.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
redox@redox-pc:~/atl2-2.0.4$ sudo make install
make: *** No rule to make target `install'.  Stop.
redox@redox-pc:~/atl2-2.0.4$ make install
make: *** No rule to make target `install'.  Stop.
redox@redox-pc:~/atl2-2.0.4$ 


any help appreciated..

---

### Post by pedro_orange on 2008-06-24
Umm...it's just a simple makefile.

I downloaded it. Unpacked it. Made my CWD to that. and typed make.

Magic.

---

### Post by hopelessone on 2008-06-24
pedro_orange - thanks...what do i do after ./make?

---

### Post by dwhitney67 on 2008-06-24
I assume that you have already asked for help on the network issues, right?  You are building kernel drivers, of which you don't seem to have a clue how to deal with them, yet you are 110% certain that you need this "patch".

I suspect we will be see a post from you in the near future about "I messed up my kernel, and now I can't get up!".

Anyhow, have you opened the Makefile to see what entry-points it supports?  You've already stated that "install" doesn't work; perhaps
```
$ sudo make modules_install
```

Let it be known that once you do this, that any kernel update coming from Ubuntu will have to be ignored, since now you have deviated from what they provide.  Or in the future, you can accept the new kernel from Ubuntu, then perform (if necessary) the same steps you are doing now to add this patched driver.

Btw, this is the location where the atl2.ko kernel driver should be stored:
```
/lib/modules/`uname -r`/kernel/drivers/net/atl2
```

---

### Post by hopelessone on 2008-06-24
> **dwhitney67 said:**
> I assume that you have already asked for help on the network issues, right?  

Yes

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/147639)

[http://ubuntuforums.org/showthread.php?t=838223](http://ubuntuforums.org/showthread.php?t=838223)

[http://ubuntuforums.org/showthread.php?t=826324](http://ubuntuforums.org/showthread.php?t=826324)

---

### Post by dwhitney67 on 2008-06-24
Ok.  So, did the "modules_install" work?   ---- Edited:  Nevermind, "modules_install" will not work.

If not, you have another choice... you can manually copy the driver (atl2.ko) to the appropriate location (as mentioned in my previous post).  I recommend that you first make a backup copy of the existing atl2.ko kernel driver before overwriting it.

P.S.  A reboot will be required after modifying the kernel.

---

### Post by hopelessone on 2008-06-24
dwhitney67 - thanks very much for the info...much appreciated...it's late and will resume this tomorrow..

cool without your post it would ave taken all day as i was googling the wrong things...

---

### Post by hopelessone on 2008-06-24
Ok,

if theres no driver there named atl2.ko

```
/lib/modules/`uname -r`/kernel/drivers/net/atl2
```

Do i just copy it there n reboot and all will be well?

Thanks..

---

### Post by hopelessone on 2008-06-24
Well how about that...theres a Debian version aswell in the repos...

Doh..

---

### Post by dwhitney67 on 2008-06-24
> **hopelessone said:**
> Ok,

if theres no driver there named atl2.ko

```
/lib/modules/`uname -r`/kernel/drivers/net/atl2
```

Do i just copy it there n reboot and all will be well?

Thanks..
Ha... that's funny.  You're right; there isn't an 'atl2' directory.  Apparently Ubuntu is lagging behind the curve on that.  My Fedora 9 system, which is running kernel 2.6.25.6-55.fc9.i686 has it.  When I checked my Ubuntu system, which uses kernel 2.6.24-18-generic, there isn't an atl2 directory.

No worries... you can create it yourself using mkdir.  Then copy (or move) the atl2.ko module into that directory.  You will need to blacklist whatever driver your system is currently using (atl1 perhaps?), and instead use atl2.

Blacklisting of module is done in /etc/modprobe.d/blacklist.  This is a file where entries look like:
```
blacklist atl1
```

Then in /etc/modules you would add atl2.  My /etc/modules looks like:
```
loop
lp
sbp2
fuse
```

At the end you would add atl2.

---

### Post by hopelessone on 2008-06-25
OK cool thanks...

How can i tell that it is installed and working? 

Thanks again..

---

### Post by dwhitney67 on 2008-06-25
> **hopelessone said:**
> How can i tell that it is installed and working? 

Well, after you install the atl2 driver from Synaptics, I recommend that you do a reboot.

Then, you can test if the atl2 driver has been loaded by:
```
$ lsmod | grep atl2
```
If the result shows atl2, then the driver is loaded.  But that doesn't mean it is in use!

Right-click with your mouse on the Network Manager applet, and select "Connection Information".  This should pop-up a window indicating which driver is being used by the network connection.

---

