---
title: "Dvd rom not mounting"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by stuart.mullett on 2014-06-29
Trying to get my dvd rom drive to open in ubuntu 14 04. if i go into disks it is listed there ,insert a dvd/cd into drive it shows up in disk but have no way of opening the dvd/cd. Model IDE-DVD ROM 6116(HD24). The dvd/cd burner work ok  and shows on the launcher. Any ideas new to ubuntu so be gentle

---

### Post by netgooroo on 2014-06-29
So, you are able to see DVD/CD media in the drive but, you are not able to access it? 

This sounds like a user rights issue to me. If you can see the disk but, are not able to access it, IE: have read/write privilages, you don't have the right permisions set up on the drive. 

You might try right clicking on the CD/DVD drive in your / folder and see what it says under properties on the Permissions tab.

---

### Post by stuart.mullett on 2014-06-29
How do i get  to permissions tab

---

### Post by yancek on 2014-06-29
What happens when you click the DVD icon in the launcher?
It should show under the /media directory, probably with a UUID number and if you have multiple partitions, you will just have to click on them to find which is the DVD.  You right-click the icon, and select Properties and then the permissions tab.

---

### Post by stuart.mullett on 2014-06-30
DVD icon does not show in launcher

---

### Post by yancek on 2014-06-30
Is there anything on the DVD?  When I put a blank DVD in the drive, the icon shows up in the left panel.  Same if I put a DVD with data on it.  The difference is that if there is data on it, it will also show up in the /media directory and you can open it there and navigate.  So what exactly is the problem.  You just want the icon showing in the panel or you cannot access data, or both?  Did you previously have the icon and maybe selected unlock from launcher?

---

