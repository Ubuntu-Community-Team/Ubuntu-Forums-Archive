---
title: "Quad booting question...m"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by malinman100 on 2013-05-16
Hey :) So I have a conundrum for you guys, 

I have just built a system from the ground up and at the moment I only have one 500gb HDD as my SSD and 1TB Hard drive wont come for a while (Shipping problems grrr). 
I want to get this system up as I desperately need it for college this is why I cannot wait to install windows first.

Does it matter if I connect this HDD and install my chosen OS' onto it (Ubuntu, Mint and Fedora) and then when my other drives come install windows on the SSD and use the 1 TB as a shared drive for everything.... 

Will this work or does windows need to be on a specific drive (The first drive). I know I will probably have to play around with GRUB as well since windows doesnt play nice with other OS'. Or do I? since their on seperate drives....  

Hope you can help :D Thanks.

** Side note:  My system DOES support EUFI so any help for the easiest solution is apprieciated.

---

### Post by AmandaLovatt on 2013-05-16
I did this as well and it doesn't matter, all you need to do after installing Windows is to recover the GRUB which is easilly done with a LiveCD. All I did was [follow this page]("https://help.ubuntu.com/community/Boot-Repair") and you're good to go.

PS: I always did the Easy Repair and it worked fine.

> - [boot your computer on a Ubuntu live-CD or live-USB.]("https://help.ubuntu.com/community/BootFromCD") 

- choose "Try Ubuntu" 
- connect internet 
- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type: 

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update- Press Enter. 
- Then type: 

sudo apt-get install -y boot-repair && (boot-repair &)- Press Enter

---

### Post by malinman100 on 2013-05-16
So this will work across all my drives? :)

---

### Post by AmandaLovatt on 2013-05-16
I can't answer that since I've never used more than a drive. But I guess you can install Windows at one drive and UBuntu at another, thus the only thing needed is to select on you BIOS which device you want to boot from.

---

### Post by malinman100 on 2013-05-16
Man im confused lol thanks though you've helped quite a bit  :) will research this further.

So is there a way to fix the booting a 
system across multiple drives?

---

### Post by Mark Phelps on 2013-05-16
When you installed Ubuntu to the HDD, it installed GRUB as well.

When you get the SSD, do the following:
1) Disconnect the HDD
2) Connect only the SSD
3) Install Win7 to the SSD
4) Reconnect the HDD and set the system to boot from it
5) Boot into Ubuntu
6) Once in Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config file and add an entry for the Windows loader.

When you reboot, you should get a GRUB menu.

---

### Post by malinman100 on 2013-05-16
Omg thank you so much :D if this works your amazing lol :D

---

### Post by oldfred on 2013-05-16
I have 4 drives with different versions of grub in each. I still have my XP install that used to have a Windows boot loader. But let most recent install default to sda as I am not booting XP anymore.

You need to pay attention to the new UEFI vs. BIOS issues. All that is really important is that both systems need to be either UEFI or both BIOS. And how you boot install media is how it installs. 

Windows only boots from gpt partitioned drives with UEFI. Or with UEFI from gpt drives.
Ubuntu will boot from gpt partitioned drive with UEFI or BIOS. If hard drive will never have Windows you can use gpt, but do not have to.

I would keep Windows as sda or when you get that drive be sure to plug it into the first SATA port on motherboard and change BIOS to boot that drive before installing. Otherwise Windows may try to put its 100MB  boot partition on which ever drive is set as first to boot from BIOS.

---

### Post by malinman100 on 2013-05-17
Okay so if I use a temp hard drive that has windows on it as the first Drive.. then when my new SSD comes can I just wipe the old HDD and reinstall windows on the SSD or will the drive structure not change?? So will that HDD ALWAYS be sda or will it change to sdb? Sorry for all these questions Im new to linux...

---

### Post by oldfred on 2013-05-17
I find that Linux reports drives in SATA port order normally. But mixed SATA & IDE may not always be reported the same. And I skipped a port and sometimes my flash drive is in that location (I think from cold boot) and sometimes my flash drive is sde.

BIOS always reports boot drive as hd0 to grub, so grub will use it as hd0. When I chain load to other MBR it matters which drive I boot from. But generally boot is hd0 and the rest are in port order from motherboard.
Not sure if same in UEFI or not.

Because drives do change device order that is why Ubuntu changed to use UUID for grub & fstab mounting. UUID should not change unless you reformat a partition. So you can get consistent booting. When they used device or /dev/sda and you changed drives around you almost always had boot issues.

---

### Post by malinman100 on 2013-05-17
Okay, so figures out I have windows 7 on a drive.. is there any way to "migrate" it to another drive?

---

