---
title: "cant connect to aMSN??"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ra2008 on 2008-08-05
hi,,
my internet connection works fine.but i cant connect to aMSN since today morning.
any hints?
Thanks

---

### Post by Tony Flury on 2008-08-05
MS have changed their protocols - you need to install 0.97.2 (if you can) I am struggling with the same.

---

### Post by halitech on 2008-08-05
mine is working fine and I'm still on the old version

---

### Post by raedbenz on 2008-08-05
mine wasnt working but i fixed it by removing the old one using synaptics.
ans i installed from aMSN website using Tcl/Tk84 installer and works fine

---

### Post by jamesrfla on 2008-08-05
Using pidgin and didn't have any problems signing into MSN. :)

---

### Post by ra2008 on 2008-08-05
i have solved it as well. but when i pclick "go to inbox " i get this:
```
mozilla $url
```
i checked "preferences" --> "others" iand i have in browser section "mozilla $url" is it correct or not?
thanks

---

### Post by whitethorn on 2008-08-05
Hi if you want to try a new MSN program, give galaxium a try, it looks pretty nice and it allows you to use your Messenger Live Profile. Screenshots, and howto install are on the homepage

[http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

---

### Post by ra2008 on 2008-08-05
> **whitethorn said:**
> Hi if you want to try a new MSN program, give galaxium a try, it looks pretty nice and it allows you to use your Messenger Live Profile. Screenshots, and howto install are on the homepage

[http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

hi am trying t install galaxium. it asks about "mono". am trying to install it from its webiste. am typing this command " apt:mono-runtime" and says that mono exists in my machine. but when i try to install galaxium it says i need mono. 
Thanks

---

### Post by raedbenz on 2008-08-05
> **ra2008 said:**
> i have solved it as well. but when i pclick "go to inbox " i get this:
```
mozilla $url
```
i checked "preferences" --> "others" iand i have in browser section "mozilla $url" is it correct or not?
thanks

HI,,
try to check Preferences --> Others. there should be in browsers:
"firefox $url" instead of "mozilla $url"

cheers;)

---

### Post by rfdeshon on 2008-08-05
I just had this same issue as well, here is the step-by-step of how I fixed it:

1) Remove old amsn
```
sudo aptitude purge amsn
```
2) Install TCL/TK 8.5 and TLS
```
sudo aptitude install tcl8.5 tk8.5 tcltls
```
3) Download the TCL/TK 8.5 package from the amsn website
4) Install amsn
```
cd /path/to/download
chmod +x amsn-0.97.2-1.tcl85.x86.package
sudo ./amsn-0.97.2-1.tcl85.x86.package
```
5) Launch amsn, it will have to do some more configuration at this point, be patient!

---

### Post by Superkoop on 2008-08-05
[http://www.getdeb.net/search.php?keywords=amsn](http://www.getdeb.net/search.php?keywords=amsn)

getting it from getdeb would be really easy also, there are a bug or two in there, but it's the simplest, and it works.

---

### Post by Adri2000 on 2008-08-06
The simplest still is to use the official packages. Enable -proposed (only hardy and gutsy for now) and update amsn. Disable -proposed then.
See [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)

---

### Post by raedbenz on 2008-08-07
nice to have the full steps..
for me actually TCL/TK 8.5 didnt wirk . so i used TCL/TK 8.4.
cheers

---

### Post by Corvair on 2008-08-07
Adri2000,

Thanks for the tip.
I can now launch amsn on hardy 64 bit.

---

