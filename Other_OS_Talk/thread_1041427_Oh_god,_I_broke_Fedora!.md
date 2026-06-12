---
title: "Oh god, I broke Fedora!"
date: 2009-01-16
forum: Other OS Talk
---

### Post by liamnixon on 2009-01-16
It seems so.

Not sure how to fix this, but I just installed Fedora on my laptop today and after updating it won't even boot into it!  When I try to boot into the 2.6.29-0.38rcl.git4.fc11.i686 kernel, I get this:

Starting udev: Loading /lib/kbd/keymaps/i386/qwerty/us.map.gz

devadm settle timeout of 180 seconds reached, the event queue contains:
  'sys/devices/platform/pcspkr'  [946]
  'sys/devices/platform/i8042/serio1/input/input6/mouse2  [945]
  'sys/devices/platform/i8042/serio1/input/input6/event6'  [944
  'sys/devices/platform/i8042/serio1/input/input6'  [943]
  'sys/devices/pci0000:00/0000:00:1f.3'  [931]
  'sys/devices/pci0000:00/0000:00:1f.0'  [900]
  'sys/devices/pci0000:00/0000:00:1e.0/0000:0c:04.3'  [898]
  'sys/devices/pci0000:00/0000:00:1e.0/0000:0c:04.2'  [897]
  'sys/devices/pci0000:00/0000:00:1e.0/0000:0c:04.1'  [896]
  'sys/devices/pci0000:00/0000:00:1e.0/0000:0c:04.0/pci_bus/0000:0d'  [895]
  'sys/devices/pci0000:00/0000:00:1e.0/0000:0c:04'  [894]
Wait timeout.  Will continue in the background.           [FAILED]

And then it hangs, but I guess the big "[FAILED]" says that.

---

### Post by liamnixon on 2009-01-16
And then when I try to boot the 2.6.27.5-117.fc10.i686 kernel everything flies pretty quickly so I don't have time to catch anything.  The only thing I can find is that something called 'libssl.so.7' is missing or was never installed.  Perhaps I can install it through a live cd of some sort?  I'll try it in a minute.

---

### Post by Noblacktie on 2009-01-16
You're running the **2.6.29 kernel?** 

Where did you get that? The F10 kernel is 2.6.27, so if you somehow managed to load something that tells Fedora you're running the .29 kernel I expect that many dependencies will be borked. 

What did you use to update? yum or PackageKit?

---

### Post by Kinetic Being on 2009-01-16
[double post]

---

### Post by Kinetic Being on 2009-01-16
If you're using the 2.6.29 kernel then either you got a development version, or something is messed up with your kernel...The latest released kernel (released on Christmas I think) is 2.6.**28**

Maybe a new (stable) kernel will fix it. 

Fedora probably has a way to compile and install the kernel automatically, but I've never used Fedora...

Its really not that hard to compile your kernel...just download the source to /usr/src/ change the symbolic link on /usr/src/linux to the new kernel then cd to the /usr/src/new-kernel-version and run make menuconfig and choose your options though an easy menu with explanations of every option, then do make && make modules_install and cp arch/i386[this may be different]/bzImage [one space] /boot/name-your-kernel and then edit your GRUB menu to point to the new kernel....

I always thought that compiling the kernel would be hard, but if you just use menuconfig and read the help on stuff you don't understand, its really easy...

---

### Post by smartboyathome on 2009-01-17
The "fc11" means he's testing Fedora Core 11, people, not 10. I think you should report this to the fedora forums, so they know of this breakage in their test version. ;)

---

### Post by jrusso2 on 2009-01-17
When you said you wanted to use Fedora I thought you meant the Fedora 10 which is buggy enough and not the non release Fedora 11.

---

### Post by ghindo on 2009-01-17
Breakage is kinda to be expected if the final release isn't for another couple of months :popcorn:

---

### Post by Sorivenul on 2009-01-17
> **smartboyathome said:**
> the "fc11" means he's testing fedora core 11, people, not 10. I think you should report this to the fedora forums, so they know of this breakage in their test version. ;)
+1

---

### Post by liamnixon on 2009-01-17
I posted this over on the Fedora forum, so they should know.  I might post something again, though.

Yeah, I didn't mean to use the fc11 kernel and it didn't hit me for a while that "fc11" meant exactly that.  I can be a tad retarded.  I suppose I didn't weed through the updates enough or something (or should I use them at all)!  Oh well, I reinstalled it with the rawhide repo disabled (not sure when I enabled it anyway) and is working fine except for a few issues which I'm trying to work out.  I could've told anybody that I'm not nearly knowledgeable and far too absent minded to fix any sort of large-scale crap like that.

Whoops!  Screwing stuff up is how I learn.  :)

---

### Post by liamnixon on 2009-01-17
> **Kinetic Being said:**
> If you're using the 2.6.29 kernel then either you got a development version, or something is messed up with your kernel...The latest released kernel (released on Christmas I think) is 2.6.**28**

Maybe a new (stable) kernel will fix it. 

Fedora probably has a way to compile and install the kernel automatically, but I've never used Fedora...

Its really not that hard to compile your kernel...just download the source to /usr/src/ change the symbolic link on /usr/src/linux to the new kernel then cd to the /usr/src/new-kernel-version and run make menuconfig and choose your options though an easy menu with explanations of every option, then do make && make modules_install and cp arch/i386[this may be different]/bzImage [one space] /boot/name-your-kernel and then edit your GRUB menu to point to the new kernel....

I always thought that compiling the kernel would be hard, but if you just use menuconfig and read the help on stuff you don't understand, its really easy...


Thanks a lot for the help!  I already reinstalled last night it though.

I have no business testing new and experimental stuff (which I didn't mean to anyway).

---

### Post by Sunshine128 on 2009-02-01
Just a quick note here.

Reporting bugs on / about fedora should be done on the fedora project communication page rather than the fedora forum.   The bug *might* be seen buried on the forum ... but it *will* be seen in bugzilla. 

However, thanks for the effort!

Fedora 10 is rock solid here now, but there were a few, shall we call them "adventurous," moments when an upstream update broke packagekit early on in the relaease.

---

