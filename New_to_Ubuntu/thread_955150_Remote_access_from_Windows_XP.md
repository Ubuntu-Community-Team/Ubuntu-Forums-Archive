---
title: "Remote access from Windows XP"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by goulies on 2008-10-21
Hey all,

I recently setup an Ubuntu server so I could run Oracle XE. Everything is running properly and I couldn't be more happy with the product. Now that everything is setup I want to remove my monitor and other components from the machine so I can use them elsewhere.

What products can I install on the server so I can remote into the machine from my laptop(Windows XP) So I can occasionally perform updates and make changes. I am a PL/SQL / ApEx developer so I do not have much experience with remoting into other machines and or configuring that sort of product.

Thanks,

Tyson Jouglet

---

### Post by bodhi.zazen on 2008-10-21
You have several options. 

If you want a graphical connection you can try a vnc server or freenx.

If you want a command line you can use ssh (and putty on windows).

---

### Post by cgkades on 2008-10-21
i dont think you can run vnc on ubuntu server because there is no desktop WM installed. you're best bet is to install and set up ssh if it's not already there

---

### Post by bodhi.zazen on 2008-10-22
> **cgkades said:**
> i dont think you can run vnc on ubuntu server because there is no desktop WM installed. you're best bet is to install and set up ssh if it's not already there

Yes you can, you just need the right vncserver.

vnc4server will do this for example.

---

### Post by goulies on 2008-10-22
> **bodhi.zazen said:**
> 
If you want a graphical connection you can try a vnc server or freenx.


Do you know of any documentation i could read to accomplish this?

---

### Post by bodhi.zazen on 2008-10-22
> **goulies said:**
> Do you know of any documentation i could read to accomplish this?

Yikes, the Ubuntu wiki page *was* good, but it looks like it is undergoing major re-organization.

[https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH)

Here is a little something I wrote up.

[http://ubuntuforums.org/showthread.php?t=541656](http://ubuntuforums.org/showthread.php?t=541656)

This one is also nice :

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

