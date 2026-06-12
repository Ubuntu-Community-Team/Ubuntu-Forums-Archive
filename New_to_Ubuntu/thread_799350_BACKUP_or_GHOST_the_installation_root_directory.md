---
title: "BACKUP or GHOST the installation root directory"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by rraj.be on 2008-05-18
In windows i used to use symantec ghost to make my complete windows installation along with many essential softwares into a restorable dvd image....\


is there any such thing with Ubuntu...

because i frequently install Ubuntu  in many computers ....

many of my college mates are just introduced to linux and ubuntu and hence could any one get me a suitable solution for this......

because installing and upgrading the packages is really a  time consuming thing...

please help me

---

### Post by wolfen69 on 2008-05-18
[Partimage]("http://www.partimage.org/Main_Page") 

it may be in the repos, not sure.

---

### Post by evilc on 2008-05-19
Have a look at remastersys, you can make a backup of your system or a installation disc.Both can run as liveCD.

---

### Post by Sef on 2008-05-19
Also Check out [Clonezilla]("http://www.clonezilla.org/").

---

### Post by autocrosser on 2008-05-19
All of the ideas above are nice---but they require software to work----

Take a look at: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

For a NON-software way to backup & restore all or part of your system using a simple .tar file & a very simple bit of scripting--I've been using it from when the post first came out & it works a treat!!!

I've been musing about making a cron task with this info--to just backup my /home on a weekly basis.

---

### Post by hyper_ch on 2008-05-19
I backup automatically using rsync... installation is done with an install script that installs all my preferred applications and then copy config/data files back :)

---

