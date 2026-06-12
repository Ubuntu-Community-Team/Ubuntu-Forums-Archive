---
title: "GRUB error 22 need major help!"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by kuxpac383 on 2008-06-08
When I try and boot up my laptop I get the following error message "Error 22". This happened probably because I went into my parition magic and erased a parition that held GRUB on it.  The way I had it before was I was dual-booting XP and Ubuntu 8.04. Well I wanted to resize my ubuntu parition.  It was broken down into three. There was my home parition 20gb, swap which was another 1GB and and the third which was 2GB and I believed had the GRUB loader on it.  Well I was told in a previous thread that I didn't need this 2GB parition anymore. So i deleted it and expanded my home filesystem.


How do I fix this? Or am I totally screwed? I can't even use my laptop at this point.  I am on a friends computer.

---

### Post by kuxpac383 on 2008-06-08
anyone?

---

### Post by dmj99 on 2008-06-08
If you deleted all the partitions except home and swap, I think that means you deleted linux.  IMHO, your looking at a re-install.

---

### Post by meierfra. on 2008-06-08
Try this:

Boot from the Ubuntu LiveCD, open a terminal and type

```
sudo grub
```

and the grub prompt type:


```
find /boot/grub/menu.lst
```
("l" is a lower case "L")
the output should be

(hd0,5)

In the following I assume that it  was (hd0,5).  If it wasn't, replace all the (hd0,5)'s by the actual output. 

At the grub prompt type:

```

root (hd0,5)  
setup (hd0)
quit 
```


Reboot.  The grub menu should appear.  

Select Ubuntu. Press ``e'' instead of ``enter''. At the new screen press
``e'' again. Change 

root (hd0,6)

 to  

root (hd0,5)
  
Press ``enter'' and then ``b'' to boot.


This should boot you into Ubuntu. Once you successfully booted into Ubuntu
you need to make these changes permanent. Open a terminal and type


```
cd /boot/grub
sudo cp menu.lst menu.lst.bu
gksudo gedit menu.lst

```

Look for the line 

#groot (hd0,6)


and change it to

#groot (hd0,5)

Save the file. In the terminal type

```
 sudo update-grub
```


Reboot and hope for the best.

---

### Post by kuxpac383 on 2008-06-08
Well I am going to run system recovery CD recreate the deleted parition and see if that helps.  If that doesn't I will boot from the Live CD. Anyone else have any ideas?

---

### Post by bumanie on 2008-06-08
Boot live cd and post output of > sudo fdisk -l That will give a read out of which partitions are still in tact. Things may not be as bad as you imagine - time will tell.

---

### Post by kuxpac383 on 2008-06-08
I will try that after I run this system rescure CD. Do you believe if I re create the deleted parition that will fix it?  What I did was delete the parition that contained GRUB.  It was a 2gb ex3 parition.  So what I am doing is creating it again through Gparted using the system rescue.

---

### Post by kuxpac383 on 2008-06-08
Ok, now it gives me Error 15....Ideas?

---

### Post by bumanie on 2008-06-08
This may help; > sudo fdsik -l (that's a lower case L) via the live cd. Please post result.

---

### Post by kuxpac383 on 2008-06-08
ok i don't have a Live CD, so I am creating one now. Will post results.

---

### Post by kuxpac383 on 2008-06-08
> **bumanie said:**
> This may help;  (that's a lower case L) via the live cd. Please post result.

Question.  What does that do exactly? I am curious for future reference.

---

### Post by kuxpac383 on 2008-06-08
Thank you all! I got it working again!

---

