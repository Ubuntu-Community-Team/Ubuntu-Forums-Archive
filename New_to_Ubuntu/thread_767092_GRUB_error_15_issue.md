---
title: "GRUB error 15 issue"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-25
Recently, before 8.04, I had 7.10 installed on a other partition on my computer. Would look something 

like this.

Sata:
80 Gig (Windows XP Pro)

IDE Channel 1:
250 Gig (Game Drive)
160 Gig (Storage Drive)

IDE Channel 2: 
120 Gig (Ubuntu)

I formatted the Ubuntu Partition so that I could upgrade from 7.10 32bit to 8.04 64bit.  After my 

install of Ubuntu 8.04 I would get to the GRUB loading screen and get a GRUB Error 15.  I would go to 

the GRUB menu and now i dont see my install of windows xp...

Anyone know anyway i can get my windows back and also keep my installation of Ubuntu??????

Any help would be much appreciated.

---

### Post by TeoBigusGeekus on 2008-04-25
Post us the contents of your menu.lst file
```
sudo gedit /boot/grub/menu.lst
```

along with the results of

```
sudo fdisk -l
```

---

### Post by dtrot55 on 2008-04-25
I think i fixed the issue...seems that after i did all that my hard drive boot orders were messed up....I went in and messed with the boot orders and now i can get to my windows and ubuntu...thank you for your help...i will keep your code in mind if i have this issue and switching boot orders doesnt work.

---

### Post by dtrot55 on 2008-04-25
Well actually i went back and switched my drives again and GRUB still doesn't recognized my windows installation...but if i just switch the boot sequence i can get to windows or ubuntu...so i guess thats alright..but  i will do you code just so i can figure it out once i get back from work.

Thanks

---

