---
title: "Latest Updates clobbered my system"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by AnimalMagic on 2008-06-24
Just ran the latest updates and I am now unable to connect to the network/internet. Ubuntu is running as a virtual machine under VmWare and I have run the Vmware-Config script and rebooted, but no network connection.

Can anyone explain how to revert back to the previous version?

---

### Post by Beatinu on 2008-06-25
Same problem here. No error messages, network interface is up but simply no connectivity.

I wonder how I'm supposed to install the fix without internet access :-S Always good to have an USB stick at hand.

---

### Post by AnimalMagic on 2008-06-25
I ended up reinstall vmware tools which seems to have solved the issue. Would like to know how to revert to the previous version though...

---

### Post by bumanie on 2008-06-25
I'm not in front of a ubuntu machine at present, but what you need to do is get rid of the latest kernel that doesn't work for your setup. Open synaptic and type kernel into search. Scroll down to the linux-image-header and look for the one with the latest kernel (ie the one with the highest number). Click on it and choose completely remove. Then in terminal > sudo update-grub then > sudo apt-get install update. Do this at your own risk.

---

### Post by AnimalMagic on 2008-06-25
Thanks for that. I've made a note for the next time :-)

---

