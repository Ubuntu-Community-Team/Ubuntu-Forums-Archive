---
title: "No permission to external hard drive with all my phd research... gulp"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by KShark000 on 2013-03-23
Hi Guys,

I installed Ubuntu 12.04 today to recover data from my computer after Windows was caught in a start-up loop. I was able to pull all the important files off of my hard drive (running Ubuntu as a trial from a CD) and put them onto an iomega external hard drive. I then wiped my computer and installed Ubuntu 12.04 permenantly, as I was fed up with Windows. Now I am trying to transfer the files from my external hard drive back onto my computer, but am getting a message that I do not have permission to access the drive. I am guessing that I must have had it set to read / write or something incorrectly when I transferred my data in the first place. 

Does anyone know how I might be able to gain permission?  I am afraid to mess with the formatting as this drive contains a year and a half of my graduate research backups.

Thank you very much for your help in advance!

K

---

### Post by blackbird34 on 2013-03-23
Well the fast way to check if they're alright might be to open Nautilus as root 
```
gksudo nautilus
```
But this probably will not solve your problem as you will still have the same permissions issues with the actual files. I suppose if you **copy them over** to your computer hard drive you can have a go at getting the permissions right on the copied folder without worrying about messing up. 

I had a look for you and this post [here]("http://serverfault.com/questions/35076/need-to-fix-file-permissions-in-a-users-home-directory") may help you sort it out - although i'm not sure how much you know about Ubuntu so don't hesitate to ask back.

---

### Post by coffeecat on 2013-03-23
A root nautilus file browser might be an answer to getting your files, but before you try this we really need more information. What filesystem is on the Iomega drive? Did you format it yourself or is it as it came when you bought it? Plug the drive in, let it be automounted and post the output of these two terminal commands:

```
sudo fdisk -lu
mount
```

---

### Post by KShark000 on 2013-03-23
Thanks guys, I solved my immediate problem. I actually went back and launched temporary Ubuntu from the CD again, and it magically allowed me to access my files. It won't let me move them to the hard drive however, so I am just slowly clouding everything.

I will mess around with Nautilus and see if there is any way to gain permission via your reccommendions, and let you know what works.

Thanks again!!

K

---

### Post by coffeecat on 2013-03-23
> **KShark000 said:**
> I actually went back and launched temporary Ubuntu from the CD again, and it magically allowed me to access my files. It won't let me move them to the hard drive however, so I am just slowly clouding everything.

With respect - you are. The UID of the live session "ubuntu" account is 999, whereas the UID of your home folder in your 12.04 HD installation will be 1000, which is why you ran into a permissions error when you tried to copy to there. You really need to post the information I suggested. If the live CD can read your Iomega drive, but your permanent 12.04 installation cannot, then there is a mount issue or a permissions issue that needs to be identified. Magic is not involved.

> **KShark000 said:**
> I will mess around with Nautilus and see if there is any way to gain permission via your reccommendions, and let you know what works.

If you mean a root nautilus, then I strongly suggest you do not - at least not yet. It may be needed, but it would be much better to see exactly what is going on.

**EDIT**: and if you do post the output of fdisk and mount as I requested, please do so from the permanent 12.04 installation. Posting that information from the live CD session would be pointless.

---

### Post by KShark000 on 2013-03-23
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **KShark000** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12570127#post12570127") 				
 				I actually went back and launched temporary  Ubuntu from the CD again, and it magically allowed me to access my  files. It won't let me move them to the hard drive however, so I am just  slowly clouding everything.


> **coffeecat said:**
> With respect - you are. 

Haha, sorry, I guess my wording was ambiguous. By "I am just slowly clouding everything" I meant I am slowly sending all my data to cloud storage. Not, I am slowly confusing the situation.  I am going to have to wait until all my cloud transfers finish, and then I will switch back to the UID = 1000 Ubuntu and post the info you requested. 

K

---

