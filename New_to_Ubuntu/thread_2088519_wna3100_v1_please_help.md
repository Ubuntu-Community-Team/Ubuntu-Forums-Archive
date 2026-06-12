---
title: "wna3100 v1 please help"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by lurch618 on 2012-11-26
I can't get the driver to open with ndiswrapper here is what i get please help.  root@bt:~# ndiswrapper -i /root/desktop/bcmwlhigh5.inf couldn't open /root/desktop/bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. root@bt:~#  I have also found two different drivers and have tried them both bcmwlhigh5.inf and bcmwlhigh6.inf getting same results with both

---

### Post by DuckHook on 2012-11-26
Did you activate the root account instead of using sudo? Because ndiswrapper installer is looking for the driver in the root Desktop directory (/root/desktop/bcmwlhigh5.inf) which is probably not where you placed it (more likely, /home/your_name/desktop/bcmwlhigh5.inf where "your_name" is your system user name).

Try instead:

```
cd ~/Desktop
```

or wherever you placed the driver before trying to install with:

```
sudo ndiswrapper -i <DRIVERNAME>.inf
```

This link covers the use of ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Windows_driver](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Windows_driver)

On a more fundmental note, it is usually better to use native Linux modules before resorting to Windows drivers using ndiswrapper. Does Linux not recognize your hardware? have you tried to locate native Linux modules first? From the cryptic Windows name of the driver, I would guess that it is some Broadcom wireless wifi adapter. If so, then there are native Linux modules available for it, although they are no longer part of the kernel This link for instructions might help:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

To determine your exact broadcom chipset, type:

```
lspci -vvnn | less
```

that's two "v"s and two "n"s

Look for a section titled "network" and either "controller" or "adapter". This will usually tell you the chipset. By installing the proper Linux module, you will avoid a lot of future headache and potential trouble spots from shoehorning in a Windows driver. After all, although ndiswrapper is a well written kludge, it still remains a kludge.

---

### Post by sandyd on 2012-11-26
> **lurch618 said:**
> I can't get the driver to open with ndiswrapper here is what i get please help.  root@bt:~# ndiswrapper -i /root/desktop/bcmwlhigh5.inf couldn't open /root/desktop/bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. root@bt:~#  I have also found two different drivers and have tried them both bcmwlhigh5.inf and bcmwlhigh6.inf getting same results with both

Are you using 64bit ubuntu?

As far as I know, it doesn't really work under x64 ([http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989))

but, someone mentioned in the middle that these instructions worked for them in x64 [http://forums.linuxmint.com/viewtopic.php?f=42&t=97610](http://forums.linuxmint.com/viewtopic.php?f=42&t=97610) .

---

