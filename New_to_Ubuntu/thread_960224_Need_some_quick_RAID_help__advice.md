---
title: "Need some quick RAID help / advice"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Zeph79 on 2008-10-27
Hey everyone.   I am a total linux noob.  This is my first attempt at linux officially but I have tinkered with it a bit in the past.  Im setting up a file server using the ubuntu desktop version.   

I have 3 hard drives in this computer.   1 is a 500GB drive for the OS (I know, its overkill but its the only one I had).   Then I have 2 1-TB drives which I plan to create the fileshares on.  

This is going in a government building with multiple departments.  What I want to do is create a folder for each departement and then put passwords on those folders so they are kept private.  On the windows XP workstations, I will make a batch file that runs on startup to map a drive to the folder for that particular department.


The installation isn't a problem.   The problem is setting up the 2 1-TB drives to do RAID1 (Mirroring).   The motherboard doesn't do hardware RAID so that is why im putting the OS on one drive, and then hopefully I can find a way to tell Ubuntu to mirror the other 2 drives and use that for my data.  

Can anyone point me towards a utility or an apt-get line of code that will help me out?   I really like this ubuntu linux but I have a lot to learn so please be precise in your replies.   Thank you for your time.

---

### Post by lukjad on 2008-10-27
Have you considered using RAID 5? From what I hear, it's faster and makes a better use of space.

---

