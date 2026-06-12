---
title: "Hybrid Card"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by coollmax on 2015-10-29
Hi all. I have hybrid card Intel and radeon hd 5650. My notebook hp pavilion 3152er
I cant switch cart to Radeon. I installed ubuntu 15.10.  Installed prop driver. But still work INTEL
How switch on Radeon card? Help please. With initial command not worked for me.

---

### Post by ajgreeny on 2015-10-29
The AMD fglrx driver does not work in 15.10 yet though it looks as if a solution can be had by using the proposed repos, but be warned that installing all the packages from proposed is asking for trouble.
See [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888) for the bug and solution, and perhaps try it by enabling proposed in software-sources, refreshing repos, installing just the fglrx driver plus any dependencies, then disabling proposed again.

No promises, but it is what I would try.
If it does not work and you can not get a GUI using the AMD card, you can uninstall fglrx and will be back where you started.

---

### Post by coollmax on 2015-10-29
Hi. Yes i am use this now [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)
I upload all new drivers. And fglrx too.
This is not worked for me. The same problem.
No way change card? I cant disabled in bios. Bios not support that option. Mayby any way ?

---

### Post by QIII on 2015-10-29
Hello!

As I said before, based on the model of your AMD GPU it is likely that yours is a muxed system.  If that is the case, you will not be able to use the AMD driver and switch between the Intel and AMD GPUs.

Since your BIOS gives you no choice to disable the Intel card (again, also likely because your graphics are muxed through the Intel GPU and disabling it would keep your graphics from working at all), the only likely option you have is to uninstall the fglrx driver and install vga_switcheroo.

This will not allow the use of the fglrx driver, so when you switch to the AMD GPU you would be running the open source Radeon driver.

If you would provide the manufacturer and model number of your machine, we might be able to do some research to find out if it is or is not a muxed system.

---

### Post by coollmax on 2015-10-29
Ok. Hp pavilion dv6 model 3152er. 
How install switcheroo in terminal??? Sudo and next???? 
And how switch with switcheroo?
linux be support hybrid system in next time??? Or good use Windows??? Because i work with Photoshop and Lightroom and 3dsmax. I think this be problem use Intel because need 3D.

---

### Post by coollmax on 2015-10-30
Can you help please. 
I try switch switcheroo and after I can't enter to desktop. Login page every time.

---

### Post by mastablasta on 2015-10-30
if you use windows based program the best thing to do is to use windows. plus obviously windows support your setup.

---

### Post by coollmax on 2015-10-30
You mean I need use Microsoft Windows? Or ??? No way to use Linux with to video card???

---

### Post by coollmax on 2015-10-31
Hi I use Ubuntu 15.10
my laptop hp pavilion dv6 3152er
have 2 cards. Intel and radeon 5650hd
how I can switch Radeon card and off Intel card? I need use Radeon for 3D. 
Or best way use Windows?

---

### Post by oldos2er on 2015-10-31
Threads merged. Please don't create duplicate threads, it dilutes the community's ability to help.

---

### Post by coollmax on 2015-10-31
Ok. 
So ? I have one way ? Use Windows? Be I can't switch Radeon. I need this card. Help any one please. I need work.....

---

### Post by coollmax on 2015-10-31
I try many other options how switch Radeon . But all not worked. Every time work intell card. 
Windows support perfect two card.. Cc

---

### Post by Vladlenin5000 on 2015-10-31
I think it has been answered already.

---

### Post by QIII on 2015-10-31
Most muxless systems will work with Intel/ATI hybrid systems out of the box.

Yours is muxed.  Nothing will change to make that work.  The OEMs are not going to fix it.

You may read about vga-switcheroo [here.]("https://help.ubuntu.com/community/HybridGraphics")

Again, however:  This will not work with the fglrx driver and you must use the open source Radeon driver.

Windows does not support hybrid graphics.  Microsoft does nothing to make it work. The OEMs of the hardware make sure their hybrid systems work with Windows.  They do not put the same effort into Linux.

There is no point in starting another thread to ask how to get this to work with the fglrx driver.  It simply will not, and that is the end of it.

---

