---
title: "internet works throught terminal, not from firefox?"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by fenghc on 2014-08-03
Hi All, I'm running 14.04 LTS version.  I ran a VPN script and ruin the internet.  Terminal is working, as I can use apt-get update.  But I cannot use firefox to browse any internet.  only for local wifi hotspot.  Any suggestion is much appreciated.  Thanks a lot.

---

### Post by fenghc on 2014-08-03
wlan0 ip address 192.168.1.255/25, brd address 192.168.1.255. scope gloabl wlan0


Is it normal?

---

### Post by sandyd on 2014-08-03
Please post the output of
```
route -n
```

---

### Post by fenghc on 2014-08-03
destination   gateway          Genmask            flags   Metric   Ref Use Iface
0.0.0.0         192.168.1.1      0.0.0.0          UG   0     0      0    wlan0
192.168.1.0   0.0.0.0         255.255.255.0    U  9   0   0     wlan0

---

### Post by fenghc on 2014-08-03
Thanks for any hints.

---

### Post by fenghc on 2014-08-03
firefox and thunderbird don't work. Terminal is ok for internet.

---

### Post by sandyd on 2014-08-03
From the terminal output, the VPN script isnt working properly.

What script are you using?

---

### Post by fenghc on 2014-08-03
i don't know. It is from our company. It said all thing is ok after install vpn.  but I cannot use internet any more. After rebooting the machine, i cannot use firefox and thunderbird.

---

### Post by fenghc on 2014-08-03
how to reset the network or uninstall vpn?

---

### Post by fenghc on 2014-08-03
i checked the vpn from a Mac. I only can get information for Mac now. 



     Click to dial: VPN (Virtual Private Network) Split Tunnel Access

When you use Network Access for the very first time on a remote system, a small java applet is loaded and starts the installation process.

You must have administrative priviledges on the remote computer to install the Network Access client-side components.

Depending on the browser configuration and the OS version, the installation process occasionally fails.

If the installation process fails

    Download the necessary components manually, using the link below. Normally, when the package is loaded, it is unarchived automatically, and the package installer, which is a standard part of the Mac OS X distribution, starts the installation process.
    If the installation does not start automatically, double-click the SSLVpn.pkg.tgz file in your Finder window, then double-click the SSLVpn.pkg.tar file that is created, and finally double-click the resulting SSLVpn.pkg file. The client components are installed in /Library/Internet Plug-Ins directory as a plug-in file F5 SSL VPN Plugin.plugin and a bundle f5_sslvpn.bundle.
    If you use Safari, restart your browser after the plug-in installation.

To un-install client components, just remove the plugin and the bundle from the remote system.

---

