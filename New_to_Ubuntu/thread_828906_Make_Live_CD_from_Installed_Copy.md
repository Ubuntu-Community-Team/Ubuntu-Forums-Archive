---
title: "Make Live CD from Installed Copy"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Henrywantstobeapenguin on 2008-06-14
Hello there, 

I have installed Ubuntu, wiped XP and thus deleted my method of making a live CD. Is there an automated way to do it from Ubuntu? As I want to install it on another computer but have lost the disk!

thanks

Henry

---

### Post by dracayr on 2008-06-14
just download the image from ubuntu.com and double click it :P

dracayr

---

### Post by misfitpierce on 2008-06-14
If you are referring to making an Ubuntu disc I would just suggest downloading another copy from [http://www.ubuntu.com](http://www.ubuntu.com) . :) Im not sure exactly how to make a copy from what your running. I know there was a program but I forget the name.

---

### Post by philinux on 2008-06-14
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

You can make one using this. Just make sure the files to be use equate to less than 4.7 gb of a standard dvd.

---

### Post by Henrywantstobeapenguin on 2008-06-14
Dear Philinux, Misfitpierce and Dracayr

Thanks very much for the responses - I will certainly try the link and if I can't make it work then I will just bite the bullet and dl a new copy. Just the 700 mb iso is a bit of a mission on this 512k connection. 

Henry

---

### Post by Joeb454 on 2008-06-14
You can still burn disc's in Linux :) I'm guessing you're running Ubuntu 8.04, so you can go to Applications &#8594; Sound & Video &#8594; Brasero Disc Burning

You can then burn the disc from there :)

---

### Post by Cariboo1938 on 2008-06-16
> **philinux said:**
> [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

You can make one using this. Just make sure the files to be use equate to less than 4.7 gb of a standard dvd.

I have installed Ubuntu 8.04-amd64 (Linux karibu-desktop 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux) 
and I recently had 49 updates installed. Now I want to use "remastersys" to make a new, customized Live CD.
I know remastersys could be used with Ubuntu 7.10, LinuxMint.
Could I use it for the 8.04 release?

---

### Post by avtolle on 2008-06-16
Yes

---

### Post by Cariboo1938 on 2008-09-01
> **avtolle said:**
> Yes
No, because it doesn't work for the 64bit version of ubuntu 8.04!
and it seems that none of the Ubuntu devs is interested to solve the issue with the remastersys dev, alias Fragadelic.:(

---

### Post by Cariboo1938 on 2008-10-13
> **philinux said:**
> [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

You can make one using this. Just make sure the files to be use equate to less than 4.7 gb of a standard dvd.

Hello,
I'm back to this issue....I have installed Ubuntu 8.04-amd64 and I recently had more than 50 updates installed. Now I want to use "remastersys" to make a new, customized Live CD to save all these updates. This is kind of important to me because I'm on slow Dial-Up connection and update take for ever.
I'm an average computer user (Office, Gimp, Video, Music, Internet) and I would like to downsize my installation to fulfill the "less than 4.7 gb" condition. 
How can I figure out what packages I don't need....and  
I could uninstall.:confused:

---

### Post by philinux on 2008-10-13
Just exclude any large files/directories in your home partition.Back these up separately.

My root partition is currently using 3.7gig. Well within the limit.
But home is using 27 gig.

---

### Post by Cariboo1938 on 2008-10-13
> **philinux said:**
> Just exclude any large files/directories in your home partition.Back these up separately.

My root partition is currently using 3.7gig. Well within the limit.
But home is using 27 gig.
Thanks Phil...:)
Did you ever use 'Remastersys' for creating a Live CD?
Actually there is the 'Dist' option when running Remastersys which automatically excludes the /home partition.
How did you figure out the size of your  system?
I have separate partitions for /, /boot, /home, /usr, /var.

---

### Post by philinux on 2008-10-13
Yes it works a treat.

Just use admin>system monitor

click the file system tab. All will be revealed.

Edit Prefs and tick show all file systems.

---

### Post by Cariboo1938 on 2008-10-13
Thanks Phil...
I found it ...(see attachment)

Do you have Ubuntu 8.04-amd64 (kernel 2.6.24-19-generic x86_64 GNU/Linux) installed? 
(I used 'uname -a' in terminal to get the above info). 

So, what you are saying is, that I only have to add up the 'Used' column to figure out how big the total data amount is?

---

### Post by Cariboo1938 on 2008-10-15
> **Cariboo1938 said:**
> No, because it doesn't work for the 64bit version of ubuntu 8.04.....


Ooops,](*,)
 
**[COLOR="Red"][SIZE="3"]I was so wrong with this statement....[/SIZE][/COLOR]**
I apologize....
It works great...see [HERE]("http://ubuntuforums.org/showthread.php?t=947720")

---

### Post by Cariboo1938 on 2008-10-15
> **Cariboo1938 said:**
> No, because it doesn't work for the 64bit version of ubuntu 8.04.....


Ooops,](*,)
 
**[COLOR="Red"][SIZE="3"]I was so wrong with this statement....[/SIZE][/COLOR]**
I apologize....
It works great...see [HERE]("http://ubuntuforums.org/showthread.php?t=947720")

---

