---
title: "operating system to fit theses requirements"
date: 2008-05-25
forum: Other OS Talk
---

### Post by markp1989 on 2008-05-25
I just ordered a computer with the following specifications 
cpu: 866mhz, Pentium 3 
ram: 128mb
Hard disk: 20gb

Im planing on using this to play videos stored on a NFS server, all of which are .avi

must have support for ATI remote wonder



I am currently in 2 minds.

Geexbox, becuase i know this can access NFS shares, i just dont know how. 
 
or

Ubuntu CLI Install, then add packages i need, basicaly a limited graphical environment. with a media player starting on login.

What of these 2 choices do you think would be best (or suggest others) 

And If option 2 is selected what packages shall i install to meet there requirements 


Thanks for any help given

MarkP

---

### Post by Cap'n Skyler on 2008-05-25
[http://movix.sourceforge.net/](http://movix.sourceforge.net/)

---

### Post by meborc on 2008-05-26
i would go with ubuntu cli+fluxbox and then run elisa multimedia center at startup (elisa might not run on such a bad hardware, but it does not hurt to try)

you can of course try different things and see what is best for you... it is not like you are going to have to pay for the OSes... so download away :)

---

### Post by markp1989 on 2008-05-26
> **meborc said:**
> i would go with ubuntu cli+fluxbox and then run elisa multimedia center at startup (elisa might not run on such a bad hardware, but it does not hurt to try)

you can of course try different things and see what is best for you... it is not like you are going to have to pay for the OSes... so download away :)

I think for elisa you need to have accelerated graphics, if there is somthing similar to alisa that doesnt require accelerated graphics it would be perfect 

it wont be here till some time in the week, so i have a few days to decide

---

### Post by mips on 2008-05-26
> **markp1989 said:**
> I just ordered a computer with the following specifications 
cpu: 866mhz, Pentium 3 
ram: 128mb
Hard disk: 20gb


If you popped more ram into that pc, say 512MB total, it will run most things just fine. I just tried Ubuntu 7.10 on P3 550Mhz, 384MB ram and it ran ok although a bit slow. A lighter distro/WM would cruise on it.

---

### Post by Bungo Pony on 2008-05-26
I agree that you should boost the RAM on it. I've got a PC with the same specs as yours, except with 1G of RAM in it. It ran Fiesty very well, and it's now happily running PCLinuxOS. Plays video without any problems.

---

### Post by markp1989 on 2008-05-26
Im not sure what ram it has, but when it gets here i will look in to upgrade it.

This may sound like a stupid question, but is it posible to run the geexbox front end on a ubuntu base?

---

### Post by Bungo Pony on 2008-05-26
Isn't GeexBox built with MythTV? Because apparently you can get it to run on Ubuntu, but I myself have given up on that one. I found it a real pain to get working, but then again that was back in Gutsy, and getting ANYTHING to work in Gutsy was a real pain.

---

### Post by mips on 2008-05-26
> **markp1989 said:**
> Im not sure what ram it has, but when it gets here i will look in to upgrade it.


I suspect it might use PC100/133 ram if we consider the age of the cpu. Anyway, let us know what you find out.

---

### Post by markp1989 on 2008-05-27
it arived today, i just tried to install geexbox on , and it runs fine, only problem is , i am having trouble mounting NFS 

i added the this ```
10.0.0.99:/media/torrent /mnt/torrent
```

to /etc/nfs and it hasnt worked, dos any one know why this is?

thanks Mark

Edit: worked after first time, but after i turn geexbox off and on again, it doesnt work

Edit 2: seems fine now, currently using geexbox to play dvd

Computer works perfectly, best 20 pound i ever spent

---

### Post by ch_123 on 2008-05-27
> **mips said:**
> If you popped more ram into that pc, say 512MB total, it will run most things just fine. I just tried Ubuntu 7.10 on P3 550Mhz, 384MB ram and it ran ok although a bit slow. A lighter distro/WM would cruise on it.

I think 384MB would be more than enough to run a simple WM environment, as described by markp. 512MB would only be needed to ensure happy operation with GNOME or KDE.

---

### Post by markp1989 on 2008-05-27
I went with geexbox in the end, i found out how to mount NFS shares using it, it does exactly what i wanted, and is extremely light.

Thanks for the information given. 

attached a pic of it, they computer in question is under the sky box, definitely  worth what i paid.

im thinking of setting up the geexbox machine to boot over the network, so i can remove the hard drive from it, but all the pxe server tutorials i have looked at talk about setting it up as a dchp sever aswell, but i have a router to do that for me. 

when i get some more money i may set up a ubuntu box with elisa for use as a media player.

---

