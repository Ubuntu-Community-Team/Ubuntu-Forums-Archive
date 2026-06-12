---
title: "GRUB, Ubuntu, Windows 8 UEFI which to pick?"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by Aonarch on 2013-05-13
So...  I have had one hell of a time dual booting Ubuntu and Windows 8 on my Lenovo Y500.  I first had to set the BIOS to Legacy mode, with legacy booting first.  Then I was able to install Ubuntu 13.  But in order to boot to Windows I had to go back to the BIOS and set it back to UEFI mode.  

So I used a live disk on Ubuntu, downloaded boot-repair and ran it on automatic.  I am now able to boot both Ubuntu and Windows 8 on UEFI mode.  

But...  What are all of these options and which one do I pick?  The Windows 8 loader does not work, but the other Windows options do.

How do I get the Windows 8 loader to work properly?  

[IMG]https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-ash3/942142_4815958833046_287824410_n.jpg[/IMG]

---

### Post by oldfred on 2013-05-13
Does the one you have highlighted work? That one should work even with secure boot on. It was created by Boot-Repair and Boot-Repair also renamed the Windows efi file as many computers were modified to only boot Windows. But Ubuntu/grub has the Microsoft secure boot key & signed kernel, so Boot-Repair renames the shim to be Windows to make it really boot grub & then from grub boot the backup Windows file as you have hightlighed above.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

You can turn off os-prober until grub fixes its bug. And if you want to rename or remove entries in 25_custom you can.
      
 # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub
Or one liner
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub 
sudo update-grub
# Edit descriptions used by Boot-Repair or remove entire boot stanza
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

---

### Post by Aonarch on 2013-05-13
Odd, now my Ubuntu will not boot.  I haven't changed a thing yet.  

Off to trouble-shoot that!

---

