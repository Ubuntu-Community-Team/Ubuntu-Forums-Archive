---
title: "VNC or teamviewer?"
date: 2018-05-01
forum: New to Ubuntu
---

### Post by JesterDev on 2018-05-01
I am attempting to connect two computers so I can remotely control one of them that does not have a monitor via remote desktop. I want to be able to login via remote desktop as well.

I've been trying to hours to get something, anything working. So far Reamviewer (which I've used for years to help family) is currently the only thing that works. But I don't think I can login
via teamviewer unless I can get to to boot before login. Is that possible with Teamviewer?

Is there a simple guide I can follow for VNC other than teamviewer? Or any suggestions or other software?

---

### Post by Autodave on 2018-05-01
Not sure what your question is about logging in. I use Teamviewer across 8 machines. The one unattended machine is set in the BIOS to come back to life after a power failure. It requires a password and I can type that remotely and get the machine running again.

---

### Post by HermanAB on 2018-05-01
Both machines run the latest Ubuntu Linux?

If so, why not use ssh, it is already installed, just enable it.

SSH is the standard way to manage UNIX machines remotely and it can also be used to run GUI programs remotely.

---

### Post by sp40140 on 2018-05-02
You can configure TeamViewer so that you can log-in using it. It's in the settings.
It's handy if you want to connect from internet and also be able to use clients from different platforms.
If your destination is within local network, use NX/ssh. 
VNC is easy to configure as well. What specific problem are you having with it?

---

### Post by monkeybrain20122 on 2018-05-02
How about [nomachine]("https://www.nomachine.com/") or [anydesk]("https://anydesk.com/download?os=linux")? TeamViewer works but we are about to test nomachine at work since it apparently allows multiple users to simultaneously login (with a paid license)

---

### Post by sp40140 on 2018-05-02
just FYI 
NX is from nomachine :
[https://en.wikipedia.org/wiki/NX_technology](https://en.wikipedia.org/wiki/NX_technology)

---

