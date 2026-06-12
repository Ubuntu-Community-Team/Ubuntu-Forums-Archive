---
title: "Help with partitions."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Ciju on 2008-09-19
Hello, I am new to Linux, Ubuntu and this forum. I want to say that its much better than windows vista already, and I just got it. My problem is, that I only want to keep windows vista for games and other minor things I cannot run on Ubuntu so then I got a few questions: 

~I have a 500GB HD (approximately) and when I partitioned (with the help of a friend) a part for Ubuntu I made Ubuntu only 50 GB big. Now after reading around a bit and seeing just how much more secure Ubuntu is, I want to use it as my main OS and my main HD. By this I mean I want to make my Vista partition (being C://:confused: ?) to 50GB and make the other 450 GB for my movies, pictures and other personal things on my Ubuntu. So in the end I will only be using Windows for games ( GuildWars, Counter Strike, etc.) My question is can I reformat just Vista ( clear it all) and then make it only 50Gb and **add the rest to my already existing Ubuntu without formating Ubuntu in anyway?**If so, how can I do it the easiest way? Please keep in mind that I am VERY new to Ubuntu (Gnome) but I find my way really easily throughout Windows.

P.S. I use Ubuntu Gnome so I didn't know what to put for the Prefix, Ubuntu or Gnome.

-Thanks a lot, Eric.

---

### Post by zxscooby on 2008-09-20
Vista includes a tool for resizing partitions. I would use 
it to shrink the windows partition and then format the free 
space.

---

### Post by Ciju on 2008-09-20
Once I partition the windows, will it get rid of all the content? And once I do partition it to a smaller size, then how can I take the space I just too out of it and attach it to my Ubuntu?

---

### Post by Shazaam on 2008-09-20
No need to format. Use the Vista partitioner to shrink Vista to the size that you want.
This is a default Ubuntu install, correct? No separate /home partition?
After using Vista's partitioner to shrink Vista set your pc so it boots to cd first and then boot the Ubuntu livecd. Start the Partition Editor (System>Administration>Partition Editor). When it opens highlight the Ubuntu partition. Choose "Resize/Move". A box will open with a bar at the top that has arrows on either side. Move the left one down. Click "Apply" Since you have a largish hard drive it might take a while.

---

### Post by Locutus_of_Borg on 2008-09-20
boot into vista
defrag your hard drive
run all disk management utilities you have (disk cleanup etc)
now choose volume management under computer management, and choose to resize your volume, shrink it as much as you can
reboot into ubuntu
open gparted (install if you dont have it)
create a new partition out of the newly created free space
format it to ext3
when that finishes, create a directory ~/storage (make it whatever you want)
edit /etc/fstab and have that new partition mount at /home/username/storage

---

