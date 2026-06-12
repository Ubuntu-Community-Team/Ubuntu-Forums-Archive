---
title: "how to fix when we forget the password ?"
date: 2015-03-16
forum: New to Ubuntu
---

### Post by Rio_Charles on 2015-03-16
hi guys, can you all help me out ? i have a problem, it's simple.
when i want to upgrade & update my lubuntu, i typed sudo apt -get update && sudo apt -get upgrade. after that , ask my root password, i forget my password . may you all help me to find the solution ?

---

### Post by Rio_Charles on 2015-03-16
hi guys, can you all help me out ? i have a problem, it's simple.
when i want to upgrade & update my lubuntu, i typed sudo apt -get  update && sudo apt -get upgrade. after that , ask my root  password, i forget my password . may you all help me to find the  solution ?

---

### Post by TheFu on 2015-03-16
It isn't asking for the root password - it is asking for the password to the userid that was used to install the OS.
Ubuntu doesn't use the root account with a password.

So... just type in your "rio_charles" password on the machine.

---

### Post by sandyd on 2015-03-16
> **Rio_Charles said:**
> hi guys, can you all help me out ? i have a problem, it's simple.
when i want to upgrade & update my lubuntu, i typed sudo apt -get update && sudo apt -get upgrade. after that , ask my root password, i forget my password . may you all help me to find the solution ?

It is not asking for your root password - use the password you normally use to login to your system. The root account is by default locked for security purposes.

In case you've forgotten that one, see [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Rio_Charles on 2015-03-17
yeah, successfull. thank you

---

### Post by newb85 on 2015-03-17
+1.  That's one reason it's a good idea *not* to set your machine to log in without a password.  If you keep using it, you're more likely to remember it.  ;)

---

### Post by kerry_s on 2015-03-17
> **Rio_Charles said:**
> hi guys, can you all help me out ? i have a problem, it's simple.
when i want to upgrade & update my lubuntu, i typed sudo apt -get update && sudo apt -get upgrade. after that , ask my root password, i forget my password . may you all help me to find the solution ?

only choice is to reset it.
boot into recovery mode, if your grub menu don't show, tap escape or shift after your bios but before grub loads.
go into recovery(usually the 2nd option)->root
type: mount -rw -o remount /
type: passwd your-user-name


don't feel bad i forget mine all the time to many to remember, i write it down & forget where i put the paper. lol

---

### Post by coffeecat on 2015-03-17
Threads merged. 

Please do not cross post (post the same thing in different locations of the forum). It dilutes the community's ability to help, which is why it is against the forum rules.

---

