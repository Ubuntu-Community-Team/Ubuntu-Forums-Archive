---
title: "New printer proplems."
date: 2012-02-14
forum: New to Ubuntu
---

### Post by vagelism on 2012-02-14
Hell to all. 
I just bought a new printer SAMSUNG model ML-1670.
I did all the instructions found here:

[http://thejaswi.info/tech/blog/2011/09/10/installing-drivers-for-samsung-ml-1676-on-linux/]("http://thejaswi.info/tech/blog/2011/09/10/installing-drivers-for-samsung-ml-1676-on-linux/")

Here is a screenshot of the jobs that I send in my printer. 
They seem to get print but nothing happent.
Any idea on how to solve the problem?
Thank you!

---

### Post by SamsungService on 2012-02-16
I am sorry to hear that you are having problems setting this up. 

I have noticed that the link provided within this tutorial links to our Indian site, could you please remove this software from your machine and download and install the correct version from our Greece website, [www.samsung.com/gr/support]("http://www.samsung.com/uk/support").

I hope this resolves the issues you are facing, if you require any further assistance, feel free to contact our support team in your area.

---

### Post by vagelism on 2012-02-17
> **SamsungService said:**
> I am sorry to hear that you are having problems setting this up. 

I have noticed that the link provided within this tutorial links to our Indian site, could you please remove this software from your machine and download and install the correct version from our Greece website, [www.samsung.com/gr/support]("http://www.samsung.com/uk/support").



I hope this resolves the issues you are facing, if you require any further assistance, feel free to contact our support team in your area.

Can you please help me to do this? Because I dont know how to do it! Thank you!

---

### Post by mastablasta on 2012-02-17
Linux drivers for printers provided by Samsung are rubish. however someone fixed them and provided a PPA for Ubuntu & debian. have a look here: [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

---

### Post by vagelism on 2012-02-17
Thank you!

---

### Post by vagelism on 2012-02-17
> **mastablasta said:**
> Linux drivers for printers provided by Samsung are rubish. however someone fixed them and provided a PPA for Ubuntu & debian. have a look here: [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

I am lost!
So much information...for many models and also for scanners not only for printers.
My model is samsung ML-1670.

---

### Post by mastablasta on 2012-02-17
it is supported by these drivers.
 
Use the first post to install them. they should work. 
 
go here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
 
And then down the page to Adding PPAs
Follow the instructions. and add the ppa. this is the first "command" under item 1 in the post i linked to.
 
then copy the rest of commands found (item 2 and 3) in the first post: [http://ubuntuforums.org/showpost.php?p=2033542&postcount=1](http://ubuntuforums.org/showpost.php?p=2033542&postcount=1)
 
if you installed any unified drivers you need to remove them instructions are also there...
 
Once you add this repository, the drivers will then show in software center as various new packages. just use  *samsungmfp* to search for them.

---

### Post by vagelism on 2012-02-18
> **mastablasta said:**
> it is supported by these drivers.
 
Use the first post to install them. they should work. 
 
go here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
 
And then down the page to Adding PPAs
Follow the instructions. and add the ppa. this is the first "command" under item 1 in the post i linked to.
 
then copy the rest of commands found (item 2 and 3) in the first post: [http://ubuntuforums.org/showpost.php?p=2033542&postcount=1](http://ubuntuforums.org/showpost.php?p=2033542&postcount=1)
 
if you installed any unified drivers you need to remove them instructions are also there...
 
Once you add this repository, the drivers will then show in software center as various new packages. just use  *samsungmfp* to search for them.
 Visit the PPA's overview page in Launchpad and look for the heading that reads Adding this PPA to your system. Make a note of the PPA's location, which looks like:


ppa:gwibber-daily/ppa
???
I dont understand this at all!!! any clue on how to do it?
Thank you!

---

