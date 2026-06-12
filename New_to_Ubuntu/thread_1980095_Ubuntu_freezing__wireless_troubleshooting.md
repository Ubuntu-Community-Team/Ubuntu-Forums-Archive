---
title: "Ubuntu freezing / wireless troubleshooting"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by adfgvx on 2012-05-14
Hello everyone,

I have tried to run both Ubuntu 12.04 and 11.10 on my computer, and both freeze when the splash screen is about to change to the desktop. When I first installed 12.04, everything worked fine, but after a few reboots, it now freezes permanently on the splash screen. 11.10 does the same thing.

Because these two versions won't work, I had to revert back to 10.04. It works perfectly, except it will not detect my wireless network. The only way I can connect to the Internet is by wireless, and since that doesn't work, I cannot access the Internet. When 12.04 was working, I could access my wireless Internet. I can also access the Internet in Windows 7 on the same computer.

Here are the results of sudo lshw -C network:

```
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d0200000-d0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d0100000-d013ffff ioport:2000(size=128)
```

Can anyone help me solve either or both of these problems? I would really like to be able to use Ubuntu again, and I cannot until I can either access the Internet in 10.04 or get 12.04 to run without freezing.

Thank you!

---

### Post by HiImTye on 2012-05-14
boot into 12.04
at the login screen, hit ctrl+alt+f1
enter
```
sudo apt-get install gnome-shell gnome-session-fallback
```
once that has completed, issue
```
sudo /etc/init.d/lightdm restart
```
now it should take you back to the login screen, hover over the box for your name and then click the little gear. select either Gnome or one of the other Gnome options

that should bring you to a usable desktop, which will tell us that Unity is having problems, if not, then that tells us it is something else

---

### Post by numand on 2012-05-14
@adfgvx, could you give outputs of ```
sudo rfkill list
lspci 
dmesg | tail -n 40
``` commands.

How much RAM has this computer got?

Have you tried to start Ubuntu with boot options? Especially with "nomodeset" parameter?[1] 

[1] [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by adfgvx on 2012-05-14
Thanks HiImTye! Now I can use Ubuntu again! :)

---

