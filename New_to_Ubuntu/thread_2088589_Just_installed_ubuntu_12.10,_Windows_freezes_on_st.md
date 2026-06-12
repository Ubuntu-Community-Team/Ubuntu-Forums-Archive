---
title: "Just installed ubuntu 12.10, Windows freezes on startup"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by AlyssaVS on 2012-11-27
I just installed ubuntu 12.10 alongside Windows 7 on my Sony VAIO. It works great. But now none of my programs will work in Windows. It's either horribly slow or just freezes and they won't open. I have waited as long as 20 minutes. It boots fine in safe mode and I can use some programs there. When I run "troubleshoot" it says that superfetch isn't working. The problem is that I can't restart superfetch in safemode. And I'm not even sure that superfetch is the problem. 
I installed ubuntu by downloading it from the website and burning it to a startup disc. I allowed the wizard to decide partition size and installed according to the prompts. My system is: SONY VAIO with Intel® Core™ i5-2450M CPU @ 2.50GHz × 4 and 5.9 GiB memory.
Do I have to recover windows to get it to work? (I saved everything and created a system repair disc before installing ubuntu)
Thank you very much in advance for your help.

---

### Post by AlyssaVS on 2012-11-29
Well I guess I'll try to find another site to help me. Not ONE reply. :(

---

### Post by audiomick on 2012-11-29
Don't be discouraged. It is an unusual problem. I've never heard of it, anyway.

That only thing that occurs to me as possible is that windows has been left with too little space to operate smoothly. 

The installer would have shrunk the partition if you hadn't already done so before the install. I suppose it is possible that some damage was done then, but it would be unusual. On the other hand, there is a lot of advice on the web to use the windows tool to shrink the windows partition before doing the Ubuntu install.

Anyway, how much free space does the windows partition have?

---

### Post by AlyssaVS on 2012-11-29
> **audiomick said:**
> 
Anyway, how much free space does the windows partition have?

I honestly don't remember and have no idea how to look for it now.

---

### Post by audiomick on 2012-11-29
Your Ubuntu works, right? And I assume you can access your windows partiton. So, boot into Ubuntu, click on the windows partition to access it and thereby mount it, then look for the system monitor (search in the dash). One of the tabs in there looks at the file system and should show you how much of the various partitions is used and how much free.

---

### Post by AlyssaVS on 2012-11-29
Yes it's working. And It's embarrassing but this is my first time ever using a Linux OS. I have looked but don't know where the "windows partition" is. It sounds like an easy step but I just don't know how to get to it. 

I'll look again... :redface:

Ok, I think I found it. 278.3 GB. Lol, not so bad ;)

---

### Post by westie457 on 2012-11-29
Use Gparted instead. If not already installed, in a terminal ```
sudo apt-get install gparted
```

When you run Gparted your Windows partition should be listed near the top of the window with size,used and free numbers.

Hope this helps.

---

### Post by audiomick on 2012-11-29
No need to be embarrassed. No one was born knowing how to use Linux. ;)

If you do as I said, i.e. look for an entry on the left pane of the file manager that is called "data" maybe, or maybe "os install" and click on that. When you get in there in the file manager, you may be able to identify it from the files in there as the windows partition.

Having done that, find the system monitor. You can search for it in the dash.

In there, on the tab that shows you the file system, there will most likely be a partition that is called / . That is the one that the linux system is on. If I am right and there is another one there, that is likely to be your windows partition.

This is a bit of a roundabout way to do this, and it is possible in a more direct way with terminal commands, but I don't know them off hand.

---

### Post by AlyssaVS on 2012-11-29
Ok, Ubuntu is 272.2 GB using 3.9 GB. Windows is 345.2 GB using 66.9 GB.

---

