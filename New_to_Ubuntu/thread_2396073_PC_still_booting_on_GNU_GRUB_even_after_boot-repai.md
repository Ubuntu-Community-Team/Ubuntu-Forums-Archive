---
title: "PC still booting on GNU GRUB even after boot-repair"
date: 2018-07-10
forum: New to Ubuntu
---

### Post by mohamedsouleimanepiro on 2018-07-10
I have an issue on my Asus. After I runned boot-repair on USB live, after rebooting the same message of Grub GNU 2.0 appears "minimal bash like-line editing is supported..."

I don't know what to do,

Here is the link [http://paste.ubuntu.com/p/D9JQcvy33S/](http://paste.ubuntu.com/p/D9JQcvy33S/)

The message says "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!", but I don't know how to do that.

Thank you,

---

### Post by oldfred on 2018-07-10
If you turn off UEFI Secure boot, but leave UEFI on, can you boot Ubuntu entry or the UEFI OS entry in UEFI boot menu. Also try with flash drive unplugged.

Do not turn on BIOS/CSM/Legacy boot mode, you still want UEFI boot mode.

Did you change something as install now in sdc, says you installed to sda.
But you show no sda, and sdb is your flash drive.

---

### Post by mohamedsouleimanepiro on 2018-07-11
Hello,




Thank you for your answer,



I changed boot option priorities and  now it shows [ATTACH=CONFIG]280350[/ATTACH]  and [ATTACH=CONFIG]280349[/ATTACH] here is  advanced page for Sata  drive.[ATTACH=CONFIG]280352[/ATTACH] and I turned  off secure boot as per here [ATTACH=CONFIG]280351[/ATTACH] but I still  get grub menu. "leaving UEFI on" (is there an option for that or does it  mean to not turn pc off?).

When I plug the USB I get this [ATTACH=CONFIG]280353[/ATTACH]


Also I am writing this post from a live USB  session.






[ATTACH=CONFIG]280349[/ATTACH][ATTACH=CONFIG]280350[/ATTACH][ATTACH=CONFIG]280351[/ATTACH][ATTACH=CONFIG]280352[/ATTACH][ATTACH=CONFIG]280353[/ATTACH]

---

### Post by oldfred on 2018-07-11
Often better to have UEFI fast boot off as it may not give time to press any boot keys. It assumes no system hardware or software change and immediately starts system booting. Normal boot goes thru process of checking what hardware you have and write that info onto drive for operating system to use.

Are you getting:
grub>

Then can you manually boot, change example with gpt8 to actual partition with your install?
       grub> set root=(hd0,gpt8)
grub> configfile /boot/grub/grub.cfg

---

### Post by leunam12 on 2018-07-11
If I have fast boot enabled on my PC's BIOS it will do the same thing, I get the grub> prompt so I keep it off all the time.

---

### Post by mohamedsouleimanepiro on 2018-07-11
Thank you @Oldfred and @leunam12 for your precious help,


Disabling fast boot and secure boot in UEFI has solved the issue after I reinstalled distro. 




Have a nice day,

---

