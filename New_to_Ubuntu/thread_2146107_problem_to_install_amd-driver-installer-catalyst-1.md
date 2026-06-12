---
title: "problem to install amd-driver-installer-catalyst-13.3-beta3-linux-x86.x86_64.run"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by Tjkhan on 2013-05-17
what should i do? additional drivers are not helping at all. Please let me know how can i install amd-driver-installer-catalyst-13.3-beta3-linux-x86.x86_64.run
Thank you

PS: code will be helpfull

---

### Post by dino99 on 2013-05-17
follow that howto : [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Tjkhan on 2013-05-17
thanks dude :)

---

### Post by Mark Phelps on 2013-05-17
> **Tjkhan said:**
> what should i do? additional drivers are not helping at all.
This is usually the best way.  What do you mean by "not helping at all"?  If you are not being offered any additional drivers, then forcing an installation of them could hose up your display!

What make and model is your video chipset? If you don't know, run the command "lspci" (without the quotes) and look for the line containing VGA.

What version of Ubuntu are you running?

---

### Post by Tjkhan on 2013-05-17
its ati 7770. i m using [SIZE=2] Ubuntu 12.04 LTS
still its not working. when I press .run its starts to install but at the end, failed. 
after I installed [/SIZE]additional drivers, everything massed up. 
[IMG]http://s14.postimg.org/ycpi354gx/Screenshot_from_2013_05_17_23_43_18.png[/IMG]



**After this **



[IMG]http://s16.postimg.org/u2mjy1rqt/Screenshot_from_2013_05_17_23_46_16.png[/IMG]

I tried but that massed up everything

[IMG]http://s12.postimg.org/zbzee3gfh/Screenshot_from_2013_05_18_00_01_06.png[/IMG]


I am using dual monitor and i dont know what to do. can u help?

---

### Post by Mark Phelps on 2013-05-17
OK, understand now.  Looks like you're only being offered Beta drivers, and from experience, the post-install version nearly always fails.

If I were you, I'd follow the directions to remove the fglrx drivers and see if you can get the dual-monitor support without them.  I'm using the default Radeon drivers and get dual-monitor support just fine.

Link:  [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Tjkhan on 2013-05-20
> **Mark Phelps said:**
> OK, understand now.  Looks like you're only  being offered Beta drivers, and from experience, the post-install  version nearly always fails.

If I were you, I'd follow the directions to remove the fglrx drivers and  see if you can get the dual-monitor support without them.  I'm using  the default Radeon drivers and get dual-monitor support just fine.

Link:  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks for the help. But I am not getting 3D support. Example when i  start MUnity, That says "Your Ubuntu 12.04 is running in 2D mode and  many features will not available.
Should I install "amd-catalyst-13.4-linux-x86.x86_64.zip" ?
Is it a good idea? Or which additional driver is should activate from three below? 
[IMG]http://i1278.photobucket.com/albums/y504/tjkhan1/driver_zpsc124a67b.png[/IMG]

---

### Post by Mark Phelps on 2013-05-21
What I recommend is the following:
1) using the link I provided, remove the fglrx drivers and reboot.  When that happens, Ubuntu should install the default Radeon drivers.
2) Go to the AMD site and download the non-beta drivers for your card. Link is:  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")
3) Read the FAQ at the AMD site about how to install the drivers.  I've found the best option was the one that created the .deb files.

---

### Post by Tjkhan on 2013-05-24
Thank you [**[COLOR=#000000]@Mark Phelps[/COLOR]**]("http://ubuntuforums.org/member.php?u=311399") Problem solved. Using 13.04 and everything is going so well! Thanks mate

---

