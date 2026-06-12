---
title: "edit grub on raid 0 results in &quot;offline member&quot; state"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by piadex2 on 2014-09-12
Dear Forumers,

I have successfully created an Ubuntu-Windows 7 dualboot system. My only problem is that I want Windows be the default option.
When I use simply "grub customizer" it kills my raid 0 array. My system says after "custimizer"-ing grub "no arrays" and my hdds are "offline member"s. All my work is ruined.
So the question raises:
how to do the grub modding properly when I have working raid0 array?

Thank You for Your help in advance.

piadex2

---

### Post by oldfred on 2014-09-13
Have not used grub customizer.

But you should be able to copy 40_custom to 06_custom so it is first in processing order and copy the Windows boot stanza that os-prober creates into 06_custom. If that works turn off os-prober so you do not have the duplicate entries.

              
 sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom

 gedit /boot/grub/grub.cfg
#and copy into grub_default  here:
gksudo gedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by piadex2 on 2014-09-13
hi,

are these commands going to work on my system? may I just type them blindly?
I am asking because I have just begun to use Ubuntu and I am using fakeRAID0 array.
Thank You.

piadex2

---

### Post by oldfred on 2014-09-13
Typos are often a major issue. Better to just copy & paste if you can, either directly from here or copied to a text file.
Only if not running Ubuntu, then you may not have gedit and need to use a different editor that your version has.
I think all versions of Ubuntu, Kubuntu, Xubuntu etc have the command line editor nano which then you start with sudo not the graphical gksudo that you use for gedit or any graphical app where sudo is required.

I left of one command that after any edit of grub config files you have to run this to get grub.menu updated with changes.
sudo update-grub

---

### Post by piadex2 on 2014-09-13
New experiences!

It is not the grub customizer that kills my raid (sets my hdd-s into "offline member" state).
Totally powering off my PC that kills the array.
Well, when I am live-CD-ing in and saying "sudo apt-get install dmraid" then restart system (reboot) everything works fine.
Of course I do not want to play this live-CD-ing all the time when I switch my PC on.

Please help.
Thank You for Your help in advance.

piadex2

PS: I have already changed the battery in the motherboard and updated the motherboard's ROM to the newest possible.

---

### Post by oldfred on 2014-09-13
You should just install dmraid once, into your working system. 
But to install that correctly you may have to chroot into system or use Boot-Repair.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by piadex2 on 2014-09-13
Dear oldfred,

There is no info on how to make boot-repair install the "dmraid".
You mentioned chroot-ing. How to do that? May be that would be the easiest.

I have the old gigabyte ep45-dsr3 motherboard. It is not an UEFI one.
Hope it is not a problem. What do You think?

Thank You for Your help in advance.

piadex2

---

### Post by oldfred on 2014-09-13
That should not make any difference.

I just have not used any RAID, so do not know any details.

       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)


 Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
      
 [URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup
[/URL]
 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

### Post by piadex2 on 2014-09-13
Dear oldfred,

Thank You for Your reply.

I refrase my question: let us forget about the raid for a moment. Just look at the ubuntu installation. How to add a software (in this case dmraid) to the boot ... system? So there is a grub, there is a software (dmraid) how to make them be together?
Thank You for Your precious help in advance.

piadex2

---

### Post by oldfred on 2014-09-13
Many with RAID have a separate /boot partition that is outside of the RAID. 
But with grub2 you can load RAID drivers and grub will directly boot from a RAID partition. It is just that it used to be that you installed RAID with the server version or back with 12.04 the alternative installer. But Desktop installer has not included RAID drivers. And they discontinued the alternative installer and said later they would add RAID back in to the Desktop. I believe some have reported that they can get RAID working with Desktop, but have not seen that it is official for fully supported yet.

From a Desktop live installer run Boot-Repair. Just for now just provide link from the report, do not run auto fix. Sometimes autofix does not work, and manual fix using Boot-Repair Advance mode is better.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by piadex2 on 2014-09-26
Dear oldfred,

First of all: sorry for being away for so long there was a lot to do...
So You state that this problem can be solved using Boot-Repair's Advanced mode. BTW I will soon provide The report.
Thank You.

piadex2

---

