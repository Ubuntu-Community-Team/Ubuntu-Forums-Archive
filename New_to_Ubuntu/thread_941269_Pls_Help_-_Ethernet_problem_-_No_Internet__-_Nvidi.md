---
title: "Pls Help - Ethernet problem - No Internet  - Nvidia nForce Controller"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by ZhuaSD on 2008-10-07
Hi, sorry to bother but I can't figure this out after searching and trying just about everything I can.  I am a newbie and really need a hand.

I have a Nvidia nForce Networking Controller for my ethernet.

I installed Hardy for the first time about a month ago, got a dual boot system with XP.

I used the Network GUI to configure my NIC.  The GUI has a bug in it, you set up the pppoe connection and then try to check it and it doesn't stay checked basically 95% of the time, but eventually it did stay checked, and everything worked.

But the connection would drop sometimes, and at first I was able to get it going again by reconfiguring everything again and getting through the bug I mentioned above.

This last time it dropped (two days ago) I just couldn't get it going by using the same methods.  

So I tried using pppoeconf in terminal to configure it.  When the configuration through the GUI is completely disabled, the pppoeconf dialog works, or at least says it does.  But still no internet.  When the GUI-configured setup is just temporarily disabled the pppoeconf does not work, it can't communicate with the eth0 device, and says it cannot continue.

Anyway I have searched here and at the nvidia site, downloaded drivers, uninstalled things (nvidia's own instructions, they basically tell you to uninstall all of the nvidia (graphic) drivers if you run ubuntu!!), and basically done everything I can aside from burning incense and chanting to wake up the internet gods.  If you think that will help then let me know!!  ;-)

Its harder because nvidia has a real branding problem.  Too many products all combined together, too many softwares and so on. nForce is a suite of products or some such monsense.

I have a GeForce 4000 chipset.  The driver name for this eternet  controller is forcedeth.

I downloaded two driver packages from nvidia, 1.77.80 and 1.23, I think 1.23 is newer.  But 1.23 unpacks into a whole bunch of different flavors of Linux and I don't know which one to choose, there is no ubuntu, so I haven't yet.  And the 1.77.80 is a .run file that needs to run in terminal with root permission.  I have tried to create a launcher for that but so far failed.  I click on it and it opens a terminal and then says it cant run because no root permission, click ok to close.

My brain is a little frazzled at this point so I will keep it simple and not say too much now.

I will say that when I go into network manager, when I choose eth0 or ppp0, and then click configure, it always says interface does not exist, be sure its supported properly.  Somehow I think that's important.

Anyway thanks in advance!!  I will really appreciate some input!!

---

### Post by iansane on 2008-10-08
for the .run files, you have to use sudo.

```

sudo nvidia_file.run

```

Then enter your password when prompted.

I  have all nvidia and luckily it works with the past 4 distributions of ubuntu but I know from installing the nvidia.run for my video card it was a real pain.
Had to drop to root shell and do "sudo telinet 3" then "sudo file.run" then still other problems but just to make the point, be ready for it to be a pain to install and research it some more first to make sure you use the right driver. Read nvidia's instructions carefully and ask specific ubuntu questions if it doesn't make sense which in my recolection, it doesn't. Provide a link to the driver page and maybe someone can help with it.

Sorry I can't tell you which one cause I have no clue since mine works.

---

### Post by ZhuaSD on 2008-10-08
Ok thanks iansane I will try.  I tried to use sudo for the file but I thought I needed another command like 'run' and couldn't find it. The launcher looked like a solution but I couldn't make it work either.

EnvyNG made the video drivers easy.  So no problem there, although now they are all uninstalled because nvidia told me to.

Anyway I will report back, and if anyone else has any advice, I am all ears...

---

### Post by ZhuaSD on 2008-10-08
Nope, that didn't work, command not found.

Off to research setting up launchers with root privileges so that I can launch this driver pack.

Any more advice is still welcome!

---

### Post by ZhuaSD on 2008-10-08
Bump

---

### Post by houbysoft.xf.cz on 2008-10-08
Yes, the command must work. The thing you probably did wrong is that you haven't cd'd to the correct dir. When you open a terminal, it is by default in your home dir. So, if, for example, your files are on your Desktop in a folder named "test", you must execute this in terminal:
```

cd Desktop/test

```
then you can run
```

sudo nvidia_file.run

```.

If you still don't know how to do that, just post the exact location of the nvidia_file.run.

Hope this helps.

---

### Post by ZhuaSD on 2008-10-08
Ok thanks for that, I understand.  I will try that soon.

I made some progress last night, getting closer to a solution. I have an older nvidia chipset so that complicates things a little.  

I will post here when I figure it out or get stuck again.

Thanks again!!

---

