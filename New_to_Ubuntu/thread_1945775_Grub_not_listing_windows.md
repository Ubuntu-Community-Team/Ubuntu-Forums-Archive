---
title: "Grub not listing windows"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by p3thead on 2012-03-23
Hi I got three harddrives two 250gb and a 500gb and yesterday I installed windows on a raid 0 with my two 250gbs and today I installed Ubuntu on my 500gb drive but grub ain't showing the windows as a boot option, I've tried sudo update-grub2 but it just lists the regular :

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done

How do I get my windows onto the list?

---

### Post by Cheesemill on 2012-03-23
How was your Windows RAID setup? Hardware, software, built into the motherboard?

If it's a softraid then you may be out of luck with getting grub to recognise it.

---

### Post by p3thead on 2012-03-23
It's built into the motherboard

GA-870A-UD3 if it matters.

---

### Post by Cheesemill on 2012-03-23
If it's built into the motherboard then it's probably not hardware RAID, instead it's probably what's known as softraid, where the motherboard does some of the work and the Windows drivers do the rest. I really don't fancy your chances of getting grub (or linux in general) to recognise the array.

Saying that, I don't actually have any personal experience with such a setup so hopefully someone who does will prove me wrong.

---

### Post by oldfred on 2012-03-23
I do not know RAID, but saved these links.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

---

### Post by p3thead on 2012-03-23
Thanks for the links they were very helpful, however I finally solved the problem with the help from this link: [http://www.linuxquestions.org/questions/linux-hardware-18/dmraid-ich10r-raid10-raid-set-was-not-activated-785597/](http://www.linuxquestions.org/questions/linux-hardware-18/dmraid-ich10r-raid10-raid-set-was-not-activated-785597/)

Just had to run

sudo apt-get install dmraid
sudo dmraid -ay
sudo update-grub2

And then it added windows to the grub list.

---

