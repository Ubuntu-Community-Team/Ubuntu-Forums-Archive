---
title: "&quot;Waiting For Network Configuration&quot;"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by palmgrower on 2013-12-29
After completion of 13.10 installation, during reboot, screen reads "Waiting for network configuration", which after a while switches to "Waiting up to 60 more seconds for network configuration" and eventually "booting system without full network configuration". And the sreen reads "reporting crash something..." and it hangs there. 

Google search shows that I need to get into /etc/network/interfaces and remove:
iface eth0 inet dhcp
hwaddress ether 00:........

But I cannot get into /etc/network/interfaces because PC hangs. Is there anything I can do?
Thanks.

PS: I have hardwired PC to router. I was able to download from network during 13.10 installation. NO network card.

---

### Post by Kevin McCready on 2013-12-30
try booting from a usb installation. I find unetbootin best

---

### Post by Impavidus on 2013-12-30
I once had that same error message, just after upgrading from 10.04 to 12.04, and it was solved by reducing /etc/network/interfaces to just```
auto lo
iface lo inet loopback
```However, the computer booted OK, except there was no networking, which had to be started manually. In your case, booting from a live disk should work, maybe booting into recovery mode and dropping to a root shell works too.

---

### Post by palmgrower on 2013-12-30
Thanks.
My old PC does not have USB boot option.
But I will try live disk.

---

### Post by palmgrower on 2013-12-30
I have graphics incompatibility and am still in line command mode. How can I access and edit /etc/network/interfaces from line command? Thanks.

---

### Post by Impavidus on 2013-12-30
Sounds unrelated, but having network to fix your graphics problem may be handy.

To edit /etc/network/interfaces from the command line, use```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
sudo nano /etc/network/interfaces
```The first line isn't really necessary, but it gives you a backup of the old file, in case something goes terribly wrong. If you're in recovery mode, you're root already so you can omit the sudo. nano is a simple terminal-based text editor. It uses ctrl-<some key> for commands. The available commands are shown at the bottom of the screen. Alternatively, you can use a different terminal-based text editor, but if you don't know one, use nano as it's the only one for which you don't have to study the manual.

---

