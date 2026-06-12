---
title: "Lost grub &amp; MBR record and cannot recover it or boot"
date: 2017-04-01
forum: New to Ubuntu
---

### Post by norton62 on 2017-04-01
Hi Everyone
I am new ubuntu user and tried install Ubuntu on my machine on a single boot "ubuntu" only on my hard disk on a new AcireAspire ES 13 machine.
Once the install was complete i could not boot my machine and UEFI was missing.I switched to legacy boot, I have no master boot record or grub although the partition is there but empty.

I have used boot-repair and ran it several times but to no avail and cannot get this machine to boot.

Having ran boot-repair gave me a paste bin url to put on help forums it is [http://paste2.org/3LYWjxcE](http://paste2.org/3LYWjxcE) can anybody help.

Thank You

---

### Post by Geoffrey_Arndt on 2017-04-02
Just my 2cents . . . the simpler/cleaner way to run an Acer PC with Linux only is to do a "full-disk" install AFTER the Legacy mode has been enabled _**rather than before**_ and then try to back-fill.

Since you should'nt have any data worth saving yet, I would run a full re-install - - let the system take the entire drive space, and use ext4 file system instead of ext2 (yes, even on mmc & ssd devices).

Keep secure boot off (not enabled) (with Legacy mode it should be so already).

Be sure to use the "something else" option during the first part of the install, and to let system install grub2 to sda (not sda1 or 2).

---

### Post by oldfred on 2017-04-02
If an UEFI install, Acer has a unique requirement of setting a Supervisory password in UEFI and enabling "trust" on the ubuntu/grub .efi boot files from within UEFI.
That is a better option than many other systems offer (really do not offer) for UEFI boot.

You also need to make sure you have newest UEFI from Acer. Some older theads mentions downgrading UEFI, but newer ones say newest UEFI from Acer works.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by cwmoser on 2017-04-03
I could not get Ubuntu 16.04 to run after installing on my HP8200.
I disabled UEFI too.  It would run properly in test mode, install correctly, but would not boot after installing.
So, I went with Linux Mint Mate 18.2

Later, some googling makes me think that I needed to add some options on the Kernel entry in Grub.
This is what I found:

Boot problem, hangs on boot
Add the following to the kernel in Grub:
nomodeset xforcevesa
&#8230; if the above does not work, boot to the live USB thumb drive and:
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
sudo boot-repair

---

