---
title: "Trouble installing Ubuntu. Please help!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Felliph3 on 2008-05-15
I am trying to install Ubuntu on my laptop however I get to step 3 where I choose a keyboard configuration and when i hit proceed the partitioner loads to 66% and freezes or goes all the way and nothing happens. The mouse shows loading but the popup window of the "loading partioner" dissappears once it hits 100 or it just freezes and stays there at 66%. The whole thing works, mouse and keyboard but i just cant get to the next screen(step 4). I dont know whats wrong.

---

### Post by overdrank on 2008-05-15
> **Felliph3 said:**
> I am trying to install Ubuntu on my laptop however I get to step 3 where I choose a keyboard configuration and when i hit proceed the partitioner loads to 66% and freezes or goes all the way and nothing happens. The mouse shows loading but the popup window of the "loading partioner" dissappears once it hits 100 or it just freezes and stays there at 66%. The whole thing works, mouse and keyboard but i just cant get to the next screen(step 4). I dont know whats wrong.

HI and welcome, have you check the cd for errors and you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If you are dual booting with windows you may want to defrag windows a couple of time. Could you give us some system specs also?

---

### Post by Felliph3 on 2008-05-16
> **overdrank said:**
> HI and welcome, have you check the cd for errors and you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If you are dual booting with windows you may want to defrag windows a couple of time. Could you give us some system specs also?

Thanks. Once i booted from the CD there was the UBUNTU screen with 4 or 5 options that went something like this:try ubuntu without doing anything to pc,install ubuntu,check disk for errors and load from frst hard drive. The first time i booted it  choose to check cd for errors and it scanned and i got no errors. So i proceeded to install linux and It worked fine however I wasnt sure which drive my D:\ drive was on the partitioner so i just quit and chose "try ubuntu without doing anything to pc" and it loaded ubuntu fine, i then found out that my D drive was under the name of dsc5 or something like that, i dont know. So i went to the install button but it wouldnt go to the partioner(step 4). It would just stay loading on step 3. The disc wasnt spinning when it was loading, just when i hit proceed and it would stop 20 seconds later and just sit there as if it was loading step 4.

I want to keep windows on C:\ and load linux on D:\

D is a 45GB hard drive built in, and C is another 45gb hard drive.

The pc is an Acer Aspire 5000 series with AMD Turion 64 bit,running windows XP SP2 1.60 Ghz and 896MB of ram. Thanks for the help. I have come up to this screen a few times but with an error msg. [IMG]http://garamchai.frivologs.com/gc_images/Screenshot4_of_6.png[/IMG]

Right now i dont even know how I can get that error again.

---

### Post by Felliph3 on 2008-05-16
This is the screen i get when i load the cd:
[IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus02.png[/IMG]

---

### Post by kesman on 2008-05-16
Hi! You could de-fragment the disks first in windows, and then boot back to ubuntu liveCD. In there, open up partition editor from system-menu and erase the whole D-partition you have and leave it unpartitioned. Then try the installation again. Also consider using the alternate install cd, it's text based and will work on almost every computer and it's a lot faster too.

---

### Post by Amstell on 2008-05-16
defragging windows on a separate hard drive doesn't really make sense.

checksum the disk.....instead of going to the installer do a check of the disk to make sure it is correct....

that is usually what it is....

---

### Post by kesman on 2008-05-16
Read the posts. He already checked it.

---

### Post by Amstell on 2008-05-16
My mistake, sorry kesman

I want to say I've had that happen to me on 7.10 before when I first tried to install it.  It would pause on the install, but it only happened once....

---

### Post by Felliph3 on 2008-05-16
I tried it a few more times and nothing. I cannot get my wireless network to go while on the live cd, i get something that says that my B43 drive isnt working really quick when its loading the live cd but it goes away within 1 sec. Maybe thats the reason it wont install. I dont know. Im wiping out my D drive and hope that will fix the problem. It just will not go to step 4. Why!!!?I will try the alrernate isntall cd!

---

### Post by Felliph3 on 2008-05-17
I managed to install it aftter i fomatted my second drive. Thanks everyone

---

