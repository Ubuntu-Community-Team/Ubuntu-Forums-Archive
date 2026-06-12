---
title: "usb module?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by gaarie on 2008-11-01
i need to let a module called usbcore.ko and ub.ko handle usb things plugged in. problem is, they were built for a 2.4.x kernel.

i think that's what causes them to return the error "invalid module format" when i run insmod.

my final goal is to have usb mount on /dev/ub* rather than /dev/sd*. can i convert these modules somehow? i googled for source but did not have much luck. is there a different way to do this?

can anyone point me to any other methods of achieving this? thanks!

---

### Post by Cypher on 2008-11-01
The USB module is part of the Kernel. What version of Ubuntu are you using and what Kernel version?

Run the command
```

lsb_release -a
uname -a

```

This will tell you the version of Ubuntu and the Kernel version. By default, a proper installion of Ubuntu will get you the right USB modules.

---

### Post by gaarie on 2008-11-01
> **Cypher said:**
> The USB module is part of the Kernel. What version of Ubuntu are you using and what Kernel version?

Run the command
```

lsb_release -a
uname -a

```

This will tell you the version of Ubuntu and the Kernel version. By default, a proper installion of Ubuntu will get you the right USB modules.

sure i have the right modules, but i need them to be handled by this specific driver and mount to /dev/ub*. it is possible that the default drivers might work IF i can tell them to mount here. i would like to know how both end results could be achieved if possible.

this build is only to run a closed source program. i am not worried about messing up my default drivers or anything.

i am rocking hardy heron (8.04.1) kernel 2.6.24.21-generic. i686. it says no LSB modules are available, if that helps at all.

can i rmmod the default usb drivers and insmod my new ones if i get them converted? i can do that with a script on startup.

thanks in advance!

---

### Post by Cypher on 2008-11-02
The USBcore doesn't actually use the /dev/sd* naming scheme. WHen you use USB Storage to be able to access Flash drives and other storage media, you go through the /dev/sd (SCSI naming layer) to access it.

Breaking the link being USB Storage and SCSI-layer is tough and probably nigh impossible.

If you wish to use an alternate /dev/ub* instead of /dev/sd*, then what you'd want to do is to just create symlinks frmo /dev/ub* to /dev/sd* as the devices are found during the driver loading.

---

### Post by gaarie on 2008-11-02
thanks for replying, i've tried symlinks (both ln and ln -s). they are deleted shortly after i create them, even as root.

i will try once more, but does anyone have other ideas?

---

