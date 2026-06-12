---
title: "Installing Wine"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by jwfrancss on 2008-06-26
I just got an Ubuntu VM appliance up in VMWare Player and I'm trying to install Wine. But the installation manager is asking for my Administrator password. Can anyone tell me what the default for this is please?

JF

---

### Post by Elfy on 2008-06-26
Your password is the one you use to login.

If you use it in a GUI you get some representation, but if you use it in a terminal it is invisible.

---

### Post by jwfrancss on 2008-06-26
But I didn't use a password to login - in fact I didn't login at all. When the VM booted I just got a Desktop up.

I've hit another snag - when trying to access a share on my XP host machine. A program called Nautilus wants to access my KeyChain(?) and it's asking for a password which I don't know!

---

### Post by Elfy on 2008-06-26
I'm a bit confused here then - I only used vmware once preferring vbox.

Is there a ubuntu installation running in the vm, how are you trying to install wine.

Could you post a scrnsht perhaps.

---

### Post by jwfrancss on 2008-06-26
I'm just using this link in Firefox

apt://wine from a page on Wine HQ.

The Synaptic Package Manager seems to start OK, but then asks me for my Administrator password.

---

### Post by Elfy on 2008-06-26
try opening a terminal - in accessories and installing from there

```
sudo apt-get install wine
```

---

### Post by jwfrancss on 2008-06-26
OK - I've got it - it's ubuntu. The Wine install is proceeding now.

Thanks for the replies :-)

---

### Post by Elfy on 2008-06-26
Excellent - can you mark thread as solved please

and welcome to the forum :D

---

