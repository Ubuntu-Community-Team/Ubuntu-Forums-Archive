---
title: "How to delete secondary OS"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by tcbarr on 2012-10-23
Hi All,

I have windows 7 as my primary and a partition with Mint. I want to delete mint and install Ubuntu (I had Ubuntu 11.10 on my last computer and I prefer it). I am a compunoob and dont want to mess anything up, I imagine it cant be too hard but couldnt find any resources after searching for an hour or so...

Thanks!

---

### Post by Paqman on 2012-10-23
When you run the Ubuntu installer it will give you a few options about what you want to do to the existing stuff on the drive. You can select "Do something else..." and pick the current Mint partition as the target for the Ubuntu install.

Alternatively, delete the Mint partition using Windows or the tool Gparted that's on the Ubuntu disk/USB, then when you install tell it to install into that free space.

Take the opportunity to back up your Windows partition, just in case. You can never have too many backups.

---

### Post by tcbarr on 2012-10-23
Thank you kind sir/madam. I am trying the installer method (didnt used to have that when I previously installed Ubuntu). Here are 10 Internets for your speedy response!

---

### Post by tcbarr on 2012-10-23
So the installer only gives me the option to install on C: and D: and those are both of my windows HD spaces, it doesnt show my partitions...Soo, it doesnt look like that method will work, you say I should delete the partition? through the Windows program (forget the name atm)? I dont have a windows CD if to load with if I jack up the boot ( i did that once deleting a partition...).

---

### Post by aabed91 on 2012-10-23
You can't replace mint for ubuntu without lost your data.

the best solution is to delete the partition that contain mint from windows and make it free then install ubuntu on the same partition

---

### Post by tcbarr on 2012-10-23
So I deleted the old partitions and re formated but when I run the installer, it only show the C: drive as an option. hmmmm

---

### Post by tcbarr on 2012-10-23
As I suspected, I damaged the bootloader and am going into grub rescue when restarting. Burning 12.10 now so I can boot it via dvd...

---

### Post by will1982 on 2012-10-23
> **tcbarr said:**
> As I suspected, I damaged the bootloader and am going into grub rescue when restarting. Burning 12.10 now so I can boot it via dvd...

I heard people have been having trouble with 12.10.
If it doesn't work, I'd try 12.04.

---

