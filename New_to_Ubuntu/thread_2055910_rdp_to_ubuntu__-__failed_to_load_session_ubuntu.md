---
title: "rdp to ubuntu  -  failed to load session ubuntu"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by fachhoch on 2012-09-10
I am able to login through ssh , I want  to rdp to ubuntu  its failing with failed to load session ubuntu.
I am a new bee with linux.Please advice how to troubleshoot.

---

### Post by lah7 on 2012-09-10
Assuming you're using **xrdp** for RDP, you could try configuring the session that is used:

Quoted from: [https://gist.github.com/2229643](https://gist.github.com/2229643)
> Enabling Windows style RDP server in Ubuntu in easy.

Steps:
1. sudo apt-get install xrdp
2. cd ~ 
3. echo "gnome-session --session=gnome-classic" > .xsession
4. sudo /etc/init.d/xrdp restart

You can use a different session types for the gnome session:
ubuntu
gnome-classic
gnome-fallback
ubuntu-2d

I use XRDP, and I'm sure this will do what you are looking for.

---

### Post by fachhoch on 2012-10-17
> **lah7 said:**
> Assuming you're using **xrdp** for RDP, you could try configuring the session that is used:

Quoted from: [https://gist.github.com/2229643](https://gist.github.com/2229643)


I use XRDP, and I'm sure this will do what you are looking for.

the session menu appears , but  copy/paste   is now working?
file explorer does not differentiate between file and folder everything looks same these are two issues I see , but not sure what more issues it has ? 
is there a   fix ?

---

