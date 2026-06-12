---
title: "HP 430 Ubuntu Install"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by Andrew Jeyaraj on 2012-07-28
Hi 
I have quite a peculiar problem.I recently acquired an HP 430 Notebook(Specs Below). It has a single C: partition with Windows 7 installed and 2 other partitions.

100 mb System 
14GB Recovery

I shrank the C: partition and made another one to install ubuntu.

During the install i chose to specify partitions manually. However Ubuntu's partition manager only shows me 2 partitions of roughly 220 each(500 gb hard drive).And when i install it on any one of the partitions my windows doesn't work.
Ive been forced to do a factory reset at least 3 times now.

What could the problem be?

Intel Core i3 2.3o Ghz
4Gb R.A.M
500 GB Hard Disk

---

### Post by Finnicella on 2012-07-28
Usually HP have 4 primary partions 
1 - System is the boot of 7
2 - C where there is windows
3 - Recovery
4 - HP TOOLS
I think this is the problem.
You must delete one partition. I have an HP and after saving the file inside the partition I deleted HP TOOLS.
I hope that this is the solution of your problem.
Sorry for my english.
Bye.  :)

---

### Post by Andrew Jeyaraj on 2012-07-28
Hey
Thanks for the reply. So when you deleted HP_Tools partition did everything work smoothly with ubuntu? And could you advise me as to how i can shrink my C: drive beyond 200 GB.

Regards

---

### Post by mastablasta on 2012-07-28
> **Andrew Jeyaraj said:**
> Hey
Thanks for the reply. So when you deleted HP_Tools partition did everything work smoothly with ubuntu? 

you can't have more than 4 primary partitions which is the reason you are having priblems to boot the OS.  since HP mkaes 4 primary partitions for that stuff they add.

> 
And could you advise me as to how i can shrink my C: drive beyond 200 GB.


you need to defragment the driver first. a couple of times then, do some checkdisk and then try to reduce it again.

---

### Post by Finnicella on 2012-08-01
Hi,
yes, after I deleted HP_Tools partition, everything work smoothly with ubuntu.

On Windows, go to Control Panel -> Administrative Tools-> Computer Management, at this point on the left side of the screen click on Disk Management and will appear all the partitions of your HDD.
Select the one you want to resize and with the right mouse button select 'Shrink Volume'.
Wait a few seconds and it tell you what is the space that you can reduce and confirmation. It not give you all the free GB because of fixed files of windows.

**_Do not use GParted because it can cause problems_** windows must be resize with windows tool.

I hope that what I wrote is clear.
Bye

---

