---
title: "&quot;About this computer&quot; and &quot;System settings&quot; don't pop up"
date: 2016-01-07
forum: New to Ubuntu
---

### Post by roy18 on 2016-01-07
I have been using Ubuntu for two years, or so. Recently, when I click on "About this computer" or "System settings," nothing happens/pops up.

Maybe related: Firefox has been getting "jammed up" kind of often recently (requiring me to turn the computer off).

Thanks for looking,

Roy

---

### Post by coldraven on 2016-01-07
This might be a good time to do a back-up of your important stuff! 
Then check your hard drive for faults. Run the "Disks" utility and in the top right corner find the "SMART data and self-tests". 
 What version of Ubuntu are you using? See here for instructions: [https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by Bucky Ball on 2016-01-07
Which release are you using? When was the last time you did an update?

---

### Post by blade4 on 2016-01-07
If you're on ubuntu 14.04 and above , try running this in the terminal : 

```
 unity-control-center 
```

else , try this : 

```
 gnome-control-center
```

If nothing happens then some of the files used by the settings program may have been corrupted or removed. You can reinstall the settings feature from the ubuntu software center to fix this.

---

### Post by roy18 on 2016-01-07
> **blade4 said:**
> If you're on ubuntu 14.04 and above , try running this in the terminal : 

```
 unity-control-center 
```

.


OK,

Thanks all.

I am running 14.04.3

I did the above command, and was informed I needed to load the unity control. That fixed the problem I posted.

BTW, the disk check indicated the disk was OK with one bad sector.

Roy

---

