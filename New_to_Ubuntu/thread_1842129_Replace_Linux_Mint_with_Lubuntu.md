---
title: "Replace Linux Mint with Lubuntu"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2011-09-10
I am currently dual booting Ubuntu Lucid Lynx and Linux Mint.  I have played around with Mint for about a week and am ready to move on.  Can I (without a whole lot of trouble) merely replace Mint with Lubuntu.
When I popped the flash drive in and I got to the what do you want to do page, I had to choose do something else.  Then I was forced to look at the dreaded colored lines which are supposed to tell me how my computer is configured.  I simply want to install on sda6 which is where Mint is now.  How do I do that and do I have to screw around with where do I put boot and the swap file?  Will it use the swap file already created or will it create a new one?  I have attached a screenshot from gparted.

---

### Post by Terry of Astoria on 2011-09-10
I think what I would do is use "disk utility" or "partition editor" in Ubuntu to delete the partition upon which you wish to install lubuntu.
Then it will appear as "unallocated space" in the lubuntu installer. You can probably figure out where to go from there.
   Yes, I don't like the new partitioner in the installer, either. It used to be so much clearer and easy to use. . .

---

### Post by mike555 on 2011-09-10
You might want to use the live gparted to delete swap sda7 ,and the space before it ,then expand sda6 to use those spaces , then format ext4 ....... then install onto sda6 and it will automatically use the swap you have left.(you only need one for all Linuxs), oh, in gparted you might need to turn swap off if the live cd or usb is using it before deleting it.

---

### Post by Rex Bouwense on 2011-09-11
Thanks Terry and Mike.  Mission accomplished.  I don't know why I get apprehensive every time that I have to deal with gparted.  It is really very simple but I know that I can really bork the sytem with a wrong click.

---

### Post by XubuRoxMySox on 2011-09-11
Don't feel bad! Repartitioning a hard drive was once a skill that only the geekiest of geeks could attempt! GParted makes it easy and safer, but it's no less scary, even for those of us who may have done it a few times.

---

### Post by Rex Bouwense on 2011-09-11
I am 2 for 3 when it comes to using gpated correctly.  The first time I used it I lost everything I had on the hard disk.  No biggie, there wasn't much on it.:D

---

### Post by candtalan on 2011-09-11
> **Rex Bouwense said:**
> I am 2 for 3 when it comes to using gpated correctly.  The first time I used it I lost everything I had on the hard disk.  No biggie, there wasn't much on it.:D

Consider getting to know something like clonezilla live CD - it allows imaging of either partitions or whole disc over to images on an external usb drive for safe keeping. It does other things too but I find the images facility fairly straightforward and  valuable.

---

### Post by Rex Bouwense on 2011-09-11
Thanks.  It didn't help, me being all sure of myself either.

---

### Post by oscarivera9 on 2011-09-11
> **candtalan said:**
> Consider getting to know something like clonezilla live CD - it allows imaging of either partitions or whole disc over to images on an external usb drive for safe keeping. It does other things too but I find the images facility fairly straightforward and  valuable.
[B]Yes indeed,
Clonezilla is great![/B]

			 		   		 		 		> Don't feel  bad! Repartitioning a hard drive was once a skill that only the geekiest  of geeks could attempt! GParted makes it easy and safer, but it's no  less scary, even for those of us who may have done it a few times.
**GParted is also awesome!**

The thing about both Clonezilla and GParted is that you have to have patience with them.  At least that's what I do.  When I'm about to use either one of those two essential tools I plan in advance so as to give myself plenty of time and not feel rushed.

---

