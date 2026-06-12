---
title: "help"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by noobman29 on 2013-03-17
hi posted earlyer about compatability issues well ther resolved got the packages now just one more thing i knw vista has partioning issus i have 2 harddrives so first i thought seprate drive duel boot would be good but after further readiing and security updates as well as support for my x-fi hd usb dac ending im actualy hinking of removeing vista and going full linux ubuntu 12.04 iv used open suse 12.2 and ubuntu 12.04 inthe past and liked them both im a noob becaus when it comes the terminal i dont know my but from a hole in the ground but have done several full installs before of linux but never duel i wont own a windows pc or mac this whould be my only computerso iguess what im asking is whats everyone think should i do a full install or risk the problems of duel boot

---

### Post by trundlenut on 2013-03-17
try a live cd and see if everything works (sound, networking, graphics etc) and if it does and you don't need windows for some particularly arcane piece of software then go for it.

If you have an external hard drive or similar take an image of the hard drive with clonezilla before you start so if it all goes wrong or you cange your mind you can just put windows back.

---

### Post by noobman29 on 2013-03-17
im gonna use wubi and migrate it later i have heard horror stories about duel booting vista and my x-fi hd dac isnt supported so i need vista for music playback but can safley surf with ubunu now that vista wont update and noone knows why or how to fix it

---

### Post by fantab on 2013-03-18
> **noobman29 said:**
> im gonna use wubi and migrate it later i have heard horror stories about duel booting vista and my x-fi hd dac isnt supported so i need vista for music playback but can safley surf with ubunu now that vista wont update and noone knows why or how to fix it

There are no "horror stories" about dual booting Windows Vista with Ubuntu. They both dual boot perfectly well. The only catch is that Windows Vista must be ideally installed on the FIRST PARTITION of your First HDD. WUBI is for people from Windows trying to figure "what is Ubuntu?". It in not a recommended way to install Ubuntu.

You say you have two Hard Drives (HDD), right?

Then I suggest that you install Ubuntu on the HDD where Vista is not installed. After successfully installing ubuntu you edit your BIOS settings to boot HDD on which ubuntu is installed to boot first. This way you can not only boot both Ubuntu and Windows, you retain your Windows MBR, Boot-loader intact.

If you have any more doubts then shoot...

---

### Post by Adi Krishnan on 2013-03-18
I've installed dual boot a lot of times with Windows 7 and everytime I wanted to remove Linux the best way I found was formatting the entire hard disk. Once I also deleted the Linux grub loader without removing windows using some complex task but it froze the partition I had done for Linux.

Bottomline: If you go for dual boot, be sure you keep it there for as much as you can.

Alternatively, you could install VMWare or VirtualBox and run your iso image on it. This is best since you can play around and remove very quickly without touching your Windows settings. But I hope your RAM and HDD can support this.

Cheers!

---

### Post by noobman29 on 2013-03-18
thanks adi i didnt think of that thats exatly what i will do my pc is a duocore w. 4gb of ram and i keep it clean and fantab you are right wubi is a very bad idea it has glitches in it i couldent deal with after first reboot i got a scrambled screen and had to turn off and back on again well thanks guys

---

