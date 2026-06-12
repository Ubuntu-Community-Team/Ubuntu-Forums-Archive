---
title: "ubuntu won't install"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by greggregington on 2012-07-16
While running the live CD it gives the option to install it.

I select the option to "try something else" and go to the partition table.

When I select the 20gb partition I set up it says "no root file system" or something along those lines, and that I would need to correct the problem to proceed. Not sure why it gives me this error message when selecting a partition.





***Solved the issue***

Ubuntu apparently won't let you install on a pre-made  partition. Had to delete the partition I made for Ubuntu then create one from my existing C partition. Might be something from the new release because the videos I watched all looked different from the setup I was going through. So if there are any new people installing Ubuntu that read this post don't pre-make the partition before installing, it wont work and gives you the option to make the partition when you choose to install along side windows.

---

### Post by necromonger on 2012-07-16
go here [http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

---

### Post by deadflowr on 2012-07-16
When you go into the try something section and set up your partitions. I think the selections are new change and delete. pick change and the screen will show whatever partition you selected with two dropdown menus on the right, the top is the filesystem type ie, ext4,ntfs,brtfs,etc,etc. the lower dropdown menu will allow you to select what the partition will be, whether /(root), /home, or any of the other options. when set click ok and it will load the something else partition page. Now it should have the root set.

---

