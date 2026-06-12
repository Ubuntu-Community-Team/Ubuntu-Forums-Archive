---
title: "Error while installing Ubuntu 20.04 LTS"
date: 2020-06-16
forum: New to Ubuntu
---

### Post by lelol123 on 2020-06-16
I have a usb drive with a live installation of ubuntu and want to install it on another usb drive as a fixed one so it can store data on it. It works just fine throughout the process and the partitioning works too but then during the installation itself the same error keeps coming up. I couldn't find any solutions on the internet, so I hope someone here can help me. I'm fairly new to ubuntu (not to linux in general, i have a little knowledge but never worked with ubuntu so yeah). That's the error that keeps coming up:

```
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e.g. happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
```

Thanks in advance for any help

---

### Post by harrychen0314 on 2020-06-17
Hi,
```
[COLOR=#000000][FONT=&amp]XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e.g. happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)[/FONT][/COLOR]
```
This should not cause ubiquity to crash or abort installing, could you please provide more information? If the installer did not crash or abort, just ignore this "error" since it's ok (I've seen this couple times and it's actually a warning, not an error).

---

### Post by lelol123 on 2020-06-17
Well I let it run for hours ignoring it and it did some other things but then stopped and the bar doesn't move at all and nothing happens anymore so i don't know. I don't really know what more information to give as I'm not that experienced with ubuntu. What information might help you?

Thanks

---

### Post by TheFu on 2020-06-17
The Try Ubuntu environment runs using userid 999.
A typical Ubuntu install has the first userid 1000.

That's my guess for the error.

If you want to use a flash drive for Ubuntu AND have persistent storage, there's a special way that things have to be setup. **mkusb** can create that setup.  With mkusb, you can setup an install to run using an ISO, plus NTFS and EXT4 extra storage for persistent stuff.  [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)  There's a PPA by the author, Sudodus. He's active in these forums and there are lots of threads about the tool.  My first time using it was last night, more out of curiosity than need.  Over USB2, it took about 10 minutes.  Over USB3, it took about 2 minutes.  I did the 2nd install after seeing what my choices caused to happen.  "usbstorage" is code for "NTFS".  "Persistent Storage" is ext4 just for Ubuntu. There's a slider to chose how to split those using all the extra storage on the flash drive. 100% will be used, but we can choose 5% for NTFS and 95% for ext4.  Or 50/50 or whatever mix you like.

The problem with these ISO Try Ubuntu methods is that the ISO is read-only. The persistent storage becomes an overlay and will keep changes, but reports say that eventually the persistence will fail.  The link above has more information about that. As always, backup anything you can't lose. Daily or weekly, depending on the importance of the data.

Linux really wants to boot from a specific SATA/USB/IDE port and from a specific partition on the end of that port.  The installer has steps to address that problem, but an installed Linux doesn't. If every system you use has EFI and a EFI boot manager you can access, then this shouldn't be too hard to specify the EFI boot to use.

---

### Post by lelol123 on 2020-06-17
Oh okay I see

I'll try it tomorrow and look how that turned out, thanks a lot for the help : )

---

