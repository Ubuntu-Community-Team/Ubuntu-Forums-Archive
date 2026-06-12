---
title: "Changing Computer Name"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by laurielegit on 2008-11-10
Ok this is in absolute beginner talk for a reason. It's just a simple question: How do I change the name of my computer. Its currently Laurie-desktop but I want to rename it Fredrick. I googled this dilemma and it came up with a result but it didn't seem to work. Any help would be appreciated.

Thanks,

Laurie

---

### Post by th89 on 2008-11-10
System->Administration->Networking
Select the General tab. Enter the name of the computer in the Hostname field.
Click OK, close all open applications and reboot.

Hope this helps!
(Originally found on [http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm))

---

### Post by laurielegit on 2008-11-10
> **th89 said:**
> System->Administration->Networking
Select the General tab. Enter the name of the computer in the Hostname field.
Click OK, close all open applications and reboot.

Hope this helps!
(Originally found on [http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg26t2.htm))

I don't have a networking option. all i have in administration that is related to networking is network tools. I'v checked the menu editor and is very definatly not there. I am using 8.10 by the way

---

### Post by anystupidname on 2008-11-10
As far as I know a reboot isn't necessary.

To set it permanently:
```
sudo echo "NewName" > /etc/hostname
```

To set it temporarily:
```
sudo hostname NewName
```

---

### Post by th89 on 2008-11-10
Ah, sorry. My bad. Didnt check it out first. :P

> **Malac said:**
> In a terminal:
```
sudo hostname <whatever>
```To make this permanent edit hostname file with:```
gksu gedit /etc/hostname
```
**Do the same to /etc/hosts otherwise you will have sudo issues**


Hope that works better.

DO NOT DO JUST THIS - See above bold:
> **anystupidname said:**
> 
To set it permanently:
```
sudo echo "NewName" > /etc/hostname
```


---

### Post by laurielegit on 2008-11-10
Well I tried both methods and it worked so I dont know who to thank, so I'd better thank both of you :) thanks

---

### Post by anystupidname on 2008-11-10
> **th89 said:**
> Ah, sorry. My bad. Didnt check it out first. :P

Hope that works better.

DO NOT DO JUST THIS - See above bold:

@th89: Thanks for the info, I've never experienced this. Care to enlighten me? 

> **laurielegit said:**
> Well I tried both methods and it worked so I dont know who to thank, so I'd better thank both of you :) thanks

@laurie: you're welcome

---

### Post by Iowan on 2008-11-10
If you change the hostname, you may also need to change /etc/hosts file (the 127.0.1.1 line)- otherwise **sudo** complains.

Sorry, my bad... Missed this part:> Do the same to /etc/hosts otherwise you will have sudo issues

---

