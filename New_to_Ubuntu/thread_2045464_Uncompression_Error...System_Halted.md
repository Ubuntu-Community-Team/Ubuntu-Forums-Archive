---
title: "Uncompression Error...System Halted"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by carldhickman on 2012-08-21
Hi all...I have installed PuppyLinux & Ubuntu on laptops. I am now trying xubuntu on my oldest laptop, a Toshiba Satellite S1800-700...but am have trouble running from the DVD image...I get the GRUB menu and when I choose a a linux option I then get 'Uncompression Error...System Halted' and then have to turn off. The laptop is running 256 RAM & has winMe installed. I have checked other Linux live CD/DVDs that I used in other laptops & I get same error...can anyone help?????

---

### Post by mcduck on 2012-08-21
I'd say that's probably because you don't have enough RAM to run the live environment.

The system requirements for 12.04 recommend at least 512MB of RAM, and if I remember right at least 384MB is required to sue the live-CD. You might have better luck using Lubuntu, or doing the install with the Alternate CD (or with Minimal Install CD and then adding some lightweight desktop afterwards).

---

### Post by sandyd on 2012-08-21
[crunchbang]("http://crunchbanglinux.org/") comes to mind.

Extremely light.

You could replicate the same effect by installing Ubuntu Minimal, then adding openbox.
I wouldn't expect the PC to be capable of running something as heavy as firefox though. Maybe opera or even chrome.

---

### Post by carldhickman on 2012-08-22
Okay...I managed to get Lubuntu to install using the Alternate Install CD...it did everything it was supposed to and completed the installation process without falling over or reporting any errors. GRUB installed fine. Problem I now have is that it hangs on boot-up with the LUBUNTU logo and the dots underneath...and goes no further. Any ideas???? Or am I flogging a dead horse. Should I try an older LUBUNTU release. (I could not get Crunchbang to load at all, or WattOS). Is this a memory issue? Or a graphics issue that is preventing it from loading? It did run WinMe fine before I attempted this, but this has now been wiped with the Lubuntu install.

---

### Post by carldhickman on 2012-08-22
Or should I try the MiniOS install of Lubuntu or would that be a world of pain for no gain????

---

### Post by carldhickman on 2012-08-23
Sorted - running WaryPuppyLinux and the laptop runs now....

---

### Post by Resistent on 2012-11-13
I tried to install Ubuntu with the Wubi Installer. 

Rebooting, I got the "Uncompression Error...System Halted" message.

The problem was: The harddisk was adjusted to "compress to save space" as I could see in Windows Explorer. (properties of harddisk). This affected also the Ubuntu folder on the harddisk. After I unchecked "compression" for the Ubuntu folder in Windows Explorer, I could restart and landed at the "Bash promt". Then I installed Ubuntu with Wubi installer again, and it worked (because Windows did not compressed the Ubuntu folder on the harddisk).

---

