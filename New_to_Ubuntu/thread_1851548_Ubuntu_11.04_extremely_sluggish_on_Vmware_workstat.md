---
title: "Ubuntu 11.04 extremely sluggish on Vmware workstation 8"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by nadeemk on 2011-09-28
Hi,

I just installed Ubuntu 11.04 on VMWare Workstation 8. I have a relatively newer machine however Ubuntu seems to be running rather sluggishly on it. Moving/resizing windows is slow and jittery, opening new tabs in Firefox takes forever, opening basic things like software update center takes upto a few seconds.  I don't think its my machine since its very new (specs below.)

Any leads on what could be going wrong?

I gave the virtual machine40GB of diskspace and 2GB of RAM. 

My host machine specs are:

Thinkpad T520 running Windows 7 Home Premium (i5 2.5Ghz, 4GB RAM, 320GB HDD, Intel HD Graphics Card.)

---

### Post by Dangertux on 2011-09-28
Did you install vmware tools on the guest operating system? They tend to be really sluggish if you don't do this first. Instructions here : [http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html)

---

### Post by krtica on 2011-10-17
I have same laptop as you. I solved many VM issues by going to BIOS and enabling advanced virtualization in Security section.

---

### Post by nadeemk on 2011-10-22
Thank you Dangertux and krtica. Both your suggestions helped tremendously and now Ubuntu is humming perfectly on my vmware workstation.

---

