---
title: "Problem Installing Dual Boot with Vista"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by zxcvbnm2 on 2008-05-16
This is an Acer computer.  For some reason it came with the disk partitioned into C: and D: which are each 111gb.  Both partitions are mostly empty. 

It seems like the installer only gives two choices:  repartition the disk, or wipe out the original OS and single boot Ubuntu.  Since I want to keep Vista and dual boot, I chose the repartition option.

At the part where the installer is ready to repartition the disc, it seemed to indicate that it would give 91% to the Ubuntu partition (there was a field that said 91%).  I thought that was a bit greedy, but since it there was no obvious option to change that, I decided to go along with it.  So I proceeded.  

Then the installer said that there was not enough room.  I had to abort the install.

Obviously there is plenty of room because I have a total of 105 gigs available between the two partitions.

How do I resolve this and get Ubuntu installed?

Thanks for any replies.

---

### Post by jimmy the saint on 2008-05-16
The way I did it was to go into vista and resize the vista partition using its built in disk tools.  I cant remember how exactly to do that because I got rid of vista very quickly after that.  once you do that, the ubuntu installer shoudl be able to simply use the empty space that you cleared up.  
Let me know how this works for you!

---

### Post by alzie on 2008-05-16
Here is a tutorial to dual boot with vista:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I think this will help you

---

### Post by zxcvbnm2 on 2008-05-16
Thanks.  That sounds like the way to do it.  

I will have to try it later because I just decided to return this computer and get something else with more expansion options (the one I'm returning has only two memory slots (both used but totaling only 1 gig of ram), two serial ATA slots (both used on the HD and DVD) and one IDE.

I will be back.

---

### Post by ChrisMaybury on 2008-05-16
Hey there, I found the tutorial provided some time ago and I've been attempting to free up enough space on my hdd to install. However when i go to shrink my partition it gives me only a possible shrink of 199 mb, so leaving me with little room for an install. there is however 20 GB free disk space. 
What can i do?:(

I don't fancy wiping the hdd like i did with this laptop. Its my girlfriends

---

### Post by jimmy the saint on 2008-05-17
Chris,
Vista will not let you shrink its partition past what it deems to be a reasonable size.  Who knows how it figures that out.  You could use gparted, but I still prefer Partition magic for some reason (guess I just used windows for too long to let everything go at once).  This will bypass windows habit of trying to do your thinking for you.  I am not sure if partition magic works in vista, and I have heard that gparted causes issues with vista partitions, but I didn't have any problem myself.  I would obiviously recommend imaging the vista partition before you do anything to it just in case.  Acronis works well for me on the windows side.  I don't know what to use for imaging in ubuntu.

---

### Post by Sef on 2008-05-17
> I still prefer Partition magic for some reason

Partition Magic and GNU/Linux tend not to get along.  Besides GParted, you can use [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php").

---

