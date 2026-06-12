---
title: "Run dpkg"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Captain Cole on 2008-10-07
When I tried to run an update on Sys>Admin>Syn Pkg Mgr I received this error. How do I get rid of it & What is 'Superuser Privilege' ?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


cole@captain-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cole@captain-desktop:~$

---

### Post by dje on 2008-10-07
you're nearly there! prepend the command with sudo to give root privilidges:
```
sudo dpkg --configure -a
```

---

### Post by billgoldberg on 2008-10-07
> **Captain Cole said:**
> When I tried to run an update on Sys>Admin>Syn Pkg Mgr I received this error. How do I get rid of it & What is 'Superuser Privilege' ?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


cole@captain-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cole@captain-desktop:~$

Go to applications -> accessories -> terminal

enter

```
sudo dkkg --configure -a
```

press enter

enter password and press enter again

Let it run untill it returns to the prompt

---

### Post by Captain Cole on 2008-10-07
OK... Now I _really_ have a problem. This looked like it was working OK. When I re-booted to set the changes, the system froze up. It will not boot without the floppy. I believe the issue began when I downloaded some files I think were incorrect for Hardy... I have Gutsy 7.10 on my machine. Someone on the forum said it didn't make any difference in the download. Should I just simply upgrade to Hardy somehow ?

---

### Post by bapoumba on 2008-10-07
Did you mix hardy and gusty repos in your sources.list, or did you directly install a hardy file ?

---

### Post by Captain Cole on 2008-10-07
I downloaded a file which was for Hardy. I didn't think that looked correct !

---

### Post by bapoumba on 2008-10-07
> **Captain Cole said:**
> I downloaded a file which was for Hardy. I didn't think that looked correct !
Did you install it with dpkg ? which file was it ? Do you remember if there were dependencies coming along ?

---

### Post by Captain Cole on 2008-10-07
It was a file we downloaded to get an Ipod to work with Ubuntu/Gutsy... If you don't mind, Please take a look at this thread. I think you will see what happened.
[http://ubuntuforums.org/showthread.php?t=939080](http://ubuntuforums.org/showthread.php?t=939080)

---

### Post by bapoumba on 2008-10-08
Please post your sources.list:
```
cat /etc/apt/sources.list
```
and the error to:
```
sudo apt-get update
```

---

