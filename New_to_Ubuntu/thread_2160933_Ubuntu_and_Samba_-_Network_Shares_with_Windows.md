---
title: "Ubuntu and Samba - Network Shares with Windows"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by theedudenator on 2013-07-08
I am pulling my hair out on this one.
I have been reading and trying various things online.
Removed disabled all firewalls.

I have a Windows 7, Windows 8 and Ubuntu machine.
Windows 7 and 8 work fine with network shares.
I can ping each machine from Ubuntu and Windows
I can see my Ubuntu Media server from any other machine.
I can remote desktop from windows to the Ubuntu machine.
So I know they are all talking!!

I can not browse the windows network on the Ubuntu machine
I cannot access shares on the Ubuntu machine
I cannot access Ubuntu shares on the windows machines.

I reinstalled SAMBA, but I think it kept all my old settings.
Maybe I need to purge all of this???

Suggestions?

---

### Post by papibe on 2013-07-08
Hi theedudenator.

Make sure they are all in the same Workgroup (I believe some new Windows machines are not in WORKGROUP anymore but MSHOME).

Could you post the result of these commands?
```
sudo testparm

sudo smbtree
```
Regards.

---

### Post by theedudenator on 2013-07-09
I reinstalled Ubuntu and now it all works.

Now can't seem to get the USB 2 ports to work... USB 3 ports work fine...

> **papibe said:**
> Hi theedudenator.

Make sure they are all in the same Workgroup (I believe some new Windows machines are not in WORKGROUP anymore but MSHOME).

Could you post the result of these commands?
```
sudo testparm

sudo smbtree
```
Regards.

---

