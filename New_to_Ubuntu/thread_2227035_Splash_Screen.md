---
title: "Splash Screen"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-30
Hello all

I had a similar problem, as did many others with NVIDIA cards in Ubuntu. The Plymouth Splash Screen does not show correctly and instead some kind of raw font is displayed. I've managed to fix it and details are under this thread: [http://ubuntuforums.org/showthread.php?t=2223463](http://ubuntuforums.org/showthread.php?t=2223463)

However like Ubuntu, a Lubuntu machine of mine has the same problem. Does anyone know if the same fix would work? Is the Lubuntu splash also called Plymouth?

Thanks

---

### Post by steeldriver on 2014-05-30
The plymouth packages for Lubuntu are 

```

plymouth-theme-lubuntu-logo - plymouth theme for Lubuntu
plymouth-theme-lubuntu-text - plymouth text theme for Lubuntu

```

I think

---

### Post by Drowz0r on 2014-05-30
What I mean is, in Ubuntu the splash screen isn't working because hwinfo isn't in the default depository. To install hwinfo you need:

1. libhal1_0.5.14-8_amd64.deb
2. libhd16_16.0-2.2_amd64.deb
3. hwinfo_16.0-2.2_amd64.deb

...depending on if you're on 32 bit or 64 bit.

This only effects NVIDIA users. I'm curious as to if this would work for Lubuntu as well, seeing as it's an Ubuntu flavour.

---

### Post by bapoumba on 2014-05-30
So reading your other thread and around a bit, I guess you have to install these packages from some other repo or a ppa ? Not using nvidia here, or any third party repo.
```
bapoumba@SonyBlue:~$ apt-cache policy libhal
N: Unable to locate package libhal
bapoumba@SonyBlue:~$ apt-cache policy libhd
N: Unable to locate package libhd
bapoumba@SonyBlue:~$ apt-cache policy hwinfo
hwinfo:
  Installed: (none)
  Candidate: (none)
  Version table:
```

[https://launchpad.net/ubuntu/saucy/amd64/hwinfo](https://launchpad.net/ubuntu/saucy/amd64/hwinfo)

Now, /etc/init/plymouth-splash.conf shows the following, if this is of any help to you ..
```
# plymouth-splash - Show the splash screen
#
# plymouth must be started ASAP to avoid racing with gdm, but the splash
# screen can't be spawned until our framebuffer is available.  Wait for the
# video device to be available before showing the screen, or, if udevtrigger
# finishes without finding any video devices, bring up the fallback text
# interface.
# We also *should* wait for the filesystem to be up because of the libraries
# being used from /usr/lib, but this would cause a circular dependency if
# any interaction at all is required for mounting a filesystem; so these libs
# need to be moved to /lib instead.

description	"userspace bootsplash"

start on (started plymouth
          and (graphics-device-added PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udev-fallback-graphics))

exec /bin/plymouth show-splash

```

---

### Post by Drowz0r on 2014-05-30
Ah, I don't quite get it...

I just tried the ubuntu fix for lubuntu and it worked though... figured I can always format the machine if it goes wrong heh.

Thanks anyhoo.

---

### Post by bapoumba on 2014-05-30
Is this for the same user or the same partition that you fixed it for Ubuntu ? That would make sense as you already installed the packages. If on a different partition or a different machine, then I do not know. A basic lubuntu install with no fancy whatever do not provide these packages :)

---

### Post by Drowz0r on 2014-05-30
Yeah completely different machine.

I have four computers, two with dedicated NVIDIA cards which had the problem. The other two did not have NVIDIA cards and did not have this problem. One was an Ubuntu machine and one was a Lubuntu machine.

Exact same fix for each, although the Lubuntu needed the 32 bit files while Ubuntu needed the 64 bit, because of their respective hardware.

---

