---
title: "Remote desktop from Kubuntu to WinXP"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Martyn Thompson on 2008-06-08
Hello pros,

My mother is used to using XP. Obviously, she has occasional problems for two reasons:
1) She is my mother
2) She is running Windows XP

I would like to be able to use remote desktop in order to help my mum out from my own home. I am using kUbuntu. But also have Gnome installed so could use either desktop...

I am sure that there will be a way this can be done - could you let me in on the secret and any (simple) HowTos in order to configure it. 

Thanks in advance,

Martyn.

---

### Post by Xerp on 2008-06-08
Most of it the work needs to be done on the remote (mother) end. You need to set her firewall to accept your connection, and have her machine set to accept "remote desktop". You may also have a NAT router to configure. You can then simply

rdesktop your.mums.ip.address

:)

This page may help when configuring her router:

[http://portforward.com/](http://portforward.com/)

This page has the setup stuff needed for XP:

[http://www.microsoft.com/windowsxp/using/networking/expert/northrup_03may16.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/northrup_03may16.mspx)

---

### Post by lisati on 2008-06-08
Check out "Gnome-RDP"

---

