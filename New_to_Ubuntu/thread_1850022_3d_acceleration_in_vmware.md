---
title: "3d acceleration in vmware"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by linuxfreak003 on 2011-09-25
I'm running 10.04 and I was hoping to be able to install windows 7 in vmware player to be able to play a couple games(and never have to restart the computer again..) but it tells me that 3d acceleration is not supported. I've tried some other fixes but i think they might be outdated. At least they haven't fixed it on mine. I was hoping someone might be able to help me here..

** I guess maybe I should let you know that I have an intel based graphics card.(yeah, wish it was Nvidia..)

---

### Post by wildmanne39 on 2011-09-25
Hi, 3d is supported on virtualbox I know for sure but it will not play games well no virtual machine will.
Thank you

---

### Post by linuxfreak003 on 2011-09-28
Ok Thanks. I guess I'll try virtualbox.. I'm hoping to find something.. I don't think warcraft 3 would take too much though so maybe it will work... any games for linux yet that are like age of empires or warcraft, etc.?

---

### Post by wildmanne39 on 2011-09-28
Hi, I am not sure when it comes to games I do not play any games on the computer, here is a link for games on ubuntu.
[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/) 

Even though virtualbox has 3d support it does not play games very well, but you can use wine or playonlinux I believe both of those play warcraft well if I remember right.
Thank you

---

### Post by linuxfreak003 on 2011-09-28
Awesome. Something's gotta work :P

---

### Post by Dangertux on 2011-09-28
VMware supports 3d acceleration by installation of vmware tools, however it may or may not be enough to play games at any decent frame rate. 

You may wish to look into something like Wine or play on linux.

As far as vmware goes without vmware-tools you will find your 3d acceleration very poor, if it is even supported. VMware tools is a free package, however it has to be installed in the guest OS after the installation of the Operating System.

Instructions here [http://www.vmware.com/support/ws5/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws5/doc/new_guest_tools_ws.html)

---

### Post by wildmanne39 on 2011-09-28
Hi, your welcome!

---

### Post by linuxfreak003 on 2011-09-28
> VMware supports 3d acceleration by installation of vmware tools, however it may or may not be enough to play games at any decent frame rate. 

You may wish to look into something like Wine or play on linux.

As far as vmware goes without vmware-tools you will find your 3d acceleration very poor, if it is even supported. VMware tools is a free package, however it has to be installed in the guest OS after the installation of the Operating System.

Yeah I have vmware-tools installed it looks like they might not support my intel-based graphics card.

---

### Post by Dangertux on 2011-09-28
Yeah I've never had a whole lot of luck with them either, and I have a radeon graphics card. :-/

---

### Post by collisionystm on 2011-09-28
> **wildmanne39 said:**
> Hi, 3d is supported on virtualbox I know for sure but it will not play games well no virtual machine will.
Thank you

It will play Starcraft and Quake 3D!!

---

### Post by collisionystm on 2011-09-28
Oh and Vmware Workstation claims to be able to play Steam games such as half life 2. It is on their website.

---

### Post by linuxfreak003 on 2011-09-29
I was tempted to try vmware workstation and see if that would work. I tried virtualbox. I still have to get it all set up everything. So I'm still working on it right now... 
> Yeah I've never had a whole lot of luck with them either, and I have a radeon graphics card. :-/
Yeah I kinda wish I had an Nvidia graphics card.. as far as I know they seem to be the best in compatibility with linux..

---

### Post by wildmanne39 on 2011-09-29
Hi, in virtualbox you will use there video card driver, and where I could not install 11.10 ubuntu with there driver it let me install 11.10.

I set up the cube and effects on ubuntu in virtualbox using there driver and it worked as good or better then with the nvidia driver my card uses.
Thank you

---

