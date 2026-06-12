---
title: "Xubuntu 12.04, How to install wvdial with no internet"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by Advait on 2013-11-16
Hi All,

I just successfully installed Xubuntu 12.04 on a friend's old XP Home laptop. For the installation I used an Xubuntu 12.04.3 ISO image burned onto a DVD. No internet is available for this computer. But I have another computer with internet. What is the best way to get wvdial installed on the old computer? I want to use a cellular modem on the old laptop.

Is it easy to install wvdial (and all its dependencies) from the Xubuntu 12.04 DVD? Or is it easier for me to download files using the other computer that has internet?

I'm a non-technical newbie so please keep that in mind when you reply. I'll need clear instructions. I searched the web and this forum and found lots of different instructions for different distros. So I want to make sure I have the right instructions for my situation and my distro (Xubuntu 12.04.3 ISO file burned on a DVD). Thanks,

Advait

---

### Post by Impavidus on 2013-11-16
Check these links:
[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)
[http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)

You can download the packages using the other pc and transfer them via usb drive. The first link may be the clearest and does certainly apply to your machine.

---

### Post by Advait on 2013-11-16
Ok, I went to the offline laptop, started Synaptic, searched for "wvdial" and it found nothing. Any ideas?

I've got wvdial installed on the online PC. The online PC is Ubuntu 12.04. Are all the wvdial files/packages/dependencies somewhere on my online PC? If yes, where? How do I know which files to copy?

I went to the Keryx page and it listed 4 files to download. Which one should I download?

Thanks,

---

### Post by howefield on 2013-11-16
The deb packages on your online machine would be found in..

/var/cache/apt/archives

---

### Post by Advait on 2013-11-16
Problem solved, but in a different way. On my other Ubuntu machines, Network Settings -> Mobile Broadband never worked for setting up my 3G cellular modem connection; only wvdial worked. On a lark I tried Network Settings on the Xubuntu machine. Surprise! It made the connection even though it never showed that it recognized the USB cellular modem. First thing I did was install wvdial. Now I'm doing a full update download and it seems to be a steady connection. I'm using Tata Photon+ in India. So something about Xubuntu (as opposed to Ubuntu) allows my 3G cellular modem to work using Network Settings.

If you know why this would be, let me know. Otherwise I'll just drop it in my big bulging bag of Unsolved Mysteries.

Thanks for your replies! 

Advait

---

