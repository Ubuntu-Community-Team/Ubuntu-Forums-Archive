---
title: "How do I get a GUI for my server?"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by blacktwain on 2012-05-10
So I just threw Ubuntu server onto my new microserver and I am trying to get a GUI on it.  So far whenever I try to install anything it gives me:
"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package "

I'm brand new at this so any help on how to get this set up would be appreciated.

---

### Post by QIII on 2012-05-10
What are you typing when you try to install?

---

### Post by blacktwain on 2012-05-10
sudo apt-get install ubuntu-desktop

---

### Post by blacktwain on 2012-05-10
It is failing to fetch the URLs when I type in sudo apt-get update 

I have added 
"deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main" to "sudoedit /etc/apt/sources.list"

---

### Post by QIII on 2012-05-10
Could you

```
cat /etc/apt/sources.list
```

and make sure the main repository is there and not commented out?

---

### Post by blacktwain on 2012-05-10
They look fine, I assume the # signs are comments.  Universe and multiverse are active

---

### Post by blacktwain on 2012-05-10
Does it need to be connected to the internet?  It is indicating that it is failing to fetch URLs when I try to update

---

### Post by wlraider70 on 2012-05-10
Once you add the GUI like gnome to Ubuntu server it is essentially the desktop version. The most significant difference is the GUI, I've never come across a package that required server or desktop.

You might try webmin, that is once you get your internet connection fixed.

Can you ping google?

---

### Post by blacktwain on 2012-05-10
It says "unknown host"

---

### Post by blacktwain on 2012-05-10
I'm trying to connect through my router.  Is there a way to gain internet access that way or should I plug my ethernet directly into my modem?

---

### Post by ammofreak on 2012-05-10
Hi ):P
I would plug into the modem first to eliminate possible problem(s) with router. If you are successful, then I would try via the router next. All of this is assuming you have the source correctly configured & network configurations right on your computer.

---

### Post by blacktwain on 2012-05-11
plugging directly into the modem didn't work.  How do make it detect my router/connect through my router?

---

### Post by ammofreak on 2012-05-12
Hi ):P
Try following: Ctrl+Alt+t for terminal. Then nano /etc/network/interfaces. Assuming you did not set a static IP, you should see an IP within the range given by your router. If not, then you have a problem with the router, or the wiring to your computer. Are you able to ping your router? On your router, can  you see a WAN IP?

---

