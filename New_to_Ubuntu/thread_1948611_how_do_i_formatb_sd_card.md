---
title: "how do i formatb sd card"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by tobythedog on 2012-03-28
hi can someone please tell me how i format an sd card on xubuntu please afraid i cannot work it out

---

### Post by carl4926 on 2012-03-28
If it's showing in the file manager - Is there no right click > Format option?

Or try Gparted

---

### Post by papibe on 2012-03-28
Hi tobythedog.

As carl4926 suggested, the first step is check if the card is recognized and automounted.

If it isn't automounted, it still may be recognized in the background. Run in the terminal the command:
```
sudo fdisk -l
```
To see if it is visible.

You can also check 'Disk Utility'. There, it is also very easy to format the card.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by tobythedog on 2012-03-28
i have used the disc usage anylyser and it shows that a small part of the card has something on it and the rest is empty however i cannot find anything on it when i look , maybe i am looking wrong , the card has been used in a sd dvr camera , i plug the usb into the computer and it recognises the unit and mounts ok saying its mounted automatikly it then opens the file manager and it cannot see anything on it , is there some other way of looking that might work better

---

### Post by papibe on 2012-03-28
I think you are getting closer ;)

Use '**Disk Utility**' (not Disk Usage Analyser) to check its format, partitions, etc, and eventually format it if you want.

Regards.

---

### Post by tobythedog on 2012-03-28
where can i find the disc utility as all i can find is disc usage analyser

---

### Post by audiomick on 2012-03-28
The small part that is showing as used is possibly some administrative function of the file system. If the file manager shows it as empty, it is empty.

If you really want to format it fresh, the disk utility is an easy option.

---

### Post by papibe on 2012-03-28
> **tobythedog said:**
> where can i find the disc utility as all i can find is disc usage analyser

My bad: Disk Utility is not installed by default on Xubuntu.

Got the 'Software Center' and install it there.

Sorry for the confusion.
Regards.

---

### Post by mike555 on 2012-03-28
might be better to install gparted , you will probably need it later anyway ...... just when you use it be sure you format the right area , if you format the wrong partition or hard drive that would be bad.....

---

### Post by tobythedog on 2012-03-28
the sotware centre says disk utility is installed , however i cannot work out how to acess it , could it be its only for gnome desktop and not for xubuntu, do i need something different for xubuntu

---

### Post by papibe on 2012-03-28
Try this: press Alt+F2 to run a command. Paste this into the dialogue box:
```
palimpsest
``` 
Tell us how it goes.
Regards.

---

### Post by tobythedog on 2012-03-30
still no luck seems really strange to me that there is no installed software to do this on xubuntu its should be very simple thing to do . i have put gparted on but cannot run it as it says only root can use it , it seems a bit drastic to use this as it can do serious damage if used wrongly , shurly there must be a simple program that can do this , anyone any other ideas please as i really do need to format this card

---

### Post by roger_1960 on 2012-03-30
Hi

Try in terminal opened by CTR+ALT+T
> 
gksudo gparted
and then your password

---

### Post by tobythedog on 2012-03-30
just tried the palimpsest in terminal and this is working great it opens the disk utility it unfortunatly looks like my card is knackered as it cannot format it also tried on a friends windows pc and this cannot format it eather. 
is there some way i can set my pc up so i can use the disk utility without having to use terminal please.as i have been unable to get to it without terminal

---

### Post by tobythedog on 2012-08-11
problem was a naff brand new sd card , now in the bin .

---

