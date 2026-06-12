---
title: "How to recover my lost hard disk space ?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by chaitanyamisal on 2008-05-10
Hi, 
   I tried my hand with Ubuntu yesterday. I downloaded 7.10 and burned the ISO image on CD to make it live CD. I booted from CD and installed  it on my external hard drive partition. 

At the end of installation process I got an fatal error where the installation was not able to write to boot/grub.

After reading a few threads on the ubuntu forum, I checked the 'boot' flag in manage flags settings for the selected hard drive for installation. 

I tried to reinstall again (after selecting the installation drive again, this time the drive I wanted to use allowed me to select the amount of space to use for the installation, unlike for the first time wherein I had to select the whole external drive partition ) but, the installation did not start again.

I restarted the computer and booted windows from main hard drive. When I went to My Computer on windows, I was able to see following drives: 
C: --> My computer Hdd 
Z: --> Partition on my external hard drive, where I tried to        
       install the Ubuntu
Y: --> Other partition on my external hard drive (untouched)

Z drive was supposed to be 100GB but it did not show any size information, instead when I clicked it asked me to format it. I formatted the drive and it showed the size of only 45GB. I lost all other usable space.

Q: How do I recover my lost space on external hard drive. I believe I the windows is not able to read ext3 filesystem which I tried to install for Linux on the partition. 

I am desperately trying to recover my lost disk space and make  it usable through windows. :confused:

Could anyone of you please let me know what should I do ? :(

Thank you in advance.

---

### Post by Malta paul on 2008-05-10
If you only wish to use Windows you can restore your system with your Windows disk (If you have one) or use a partition program such as 'Partionmagic'
If you want to duel boot Ubuntu with windows you could try the 'Alternate disk' 
Check out:  [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Good luck :)

---

### Post by chaitanyamisal on 2008-05-13
Malta Paul, 
           
           Partition magic is a paid software, instead I did following and solved the problem, 

1. Boot using Ubuntu CD 
2. System  --> Administration --> partition editor 
3. Unmount the disk partition which needs formatting 
4. Format the hdd partition by selecting the format option. 

Thanks and regards,

--CM

---

### Post by SlappyPappy on 2008-05-13
Pretty slick! Well played sir.....  :)

---

