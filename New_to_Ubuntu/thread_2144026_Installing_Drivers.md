---
title: "Installing Drivers"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Jett Byrnes on 2013-05-10
Hello, everybody. 
I am very new to using Ubuntu and I don't really know much about any OS. I am trying to install my VGA drivers from a CD I recieved with my new laptop, but the autorun is an .exe file. I installed wine and tried to run it with that and I get a message saying the device isn't plugged in. I don't know what to do or how to install the drivers can anybody please help me.

(SORRY IF THIS IS WRONG SECTION)

---

### Post by QIII on 2013-05-10
Hello!

The drivers on that CD are likely for windows and will not work for Linux.

Could you tell us about the specifications of your machine?

Regards.

---

### Post by Jett Byrnes on 2013-05-10
Release 12.10 (quantal) 32-bit
Kernel Linux 3.5.0-17-generic
GNOME 3.6.0

Hardware
Memory: 3.5 GiB
ProcessorAMD C-30 Processor

System Status
Available disk space: 216.3 GiB

I copied  this straight from System Monitor. I don't know if this is what you were asking for.

---

### Post by Kojak Peg on 2013-05-10
Hi Jett
I'm a newbie too. Have you tried additional drivers in the system setting. If there are any driver there you can click enble

---

### Post by Jett Byrnes on 2013-05-10
There isn't any Additional Drivers option in system settings.
Also experiencing another problem my CPU is always 50%

---

### Post by Jett Byrnes on 2013-05-10
I found additional drivers. 
I found three listed drivers, which one should I choose for best preformance.
X. Org X server --AMD/ATI Display Driver Wrapper from xserver-xorg-video-ati(Open Source)
Video Driver from the AMD graphics accelerators from fglrx(Proprietary)
Video Driver from the AMD graphics accelerators from fglrx-updates(Proprietary)

---

### Post by gifford on 2013-05-10
Try the fglrx first, not the updates. Should work the best.

---

### Post by QIII on 2013-05-10
Hello again.

Right now the video driver you are using is the open source Radeon driver, which is the default driver to ATI graphics controllers for Linux.  

If you want to install a proprietary driver, install the fglrx driver and not the fglrx-updates.  The latter causes problems as often as it works.

But let's take a look first at what is taking up your CPU time.  Remember that the C30 is not a powerful processor, only just slightly faster than Intel's Atom -- and that only because it processes instructions in a different manner.

If you would, go to the terminal and type 

```
top
```

After the display starts, press Control-C to stop the updates.  Then highlight the text in the terminal and press Control-Shift-C to copy the text and paste it back here.

When you paste it, first click the pound symbol (#) above and then put your cursor between the two code tags.  



Thanks.

---

### Post by Kojak Peg on 2013-05-11
my knowledge of the drivers, in linux, begins and ends with additional drivers, I'm afraid. And I've never had any listed, so never actually used it. However a few other bits of interest are:

1)**install, "ubuntu restricted extras"** in the [B]software centre
[/B]
2)change the** mirrors** go to the** update manager** => **settings** => **ubuntu software**. Then click on the drop down menu called "**download from**" => then click "**other**" and select the **country you are** **in**. Then click "**select best server**"
  
3)also in **update manager**=>**settings**=> **ubuntu software**. **tick all the boxes** especially "**proprietary drivers of devices (restricted)**" 

4)also in** update manager**=>**settings**=>**updates**. "**Automatically check for updates**", click on drop down menu and select "**daily**"

5)underneath "**Automatically check for updates"** there is "**when there are security updates**", click on the drop down menu and select "**download and install automatically**"  

6)also in **update manager**=>**settings**=>**other software**. make sure all the boxes you want are ticked

Hope all that makes sense and you can follow in. There are some very good podcasts on youtube you can watch too. like 10 things to do after installing ubuntu

---

### Post by Mark Phelps on 2013-05-11
Linux is not Windows, meaning that one of the things you do NOT do is start hunting around for drivers soon after you install it.  The right drivers are downloaded and installed as part of the initial setup.  So, if you are seeing a desktop, and not encountering any display problems, you don't need to be installing other video drivers as the correct default Radeon drivers are already installed.

---

### Post by squakie on 2013-05-11
A big +1.  As you have found also, sometimes people think they should install Windows drivers to Wine - this is not the case.  Things like chipset drivers, wireless drivers, modem drivers, video drivers, etc., that normally come on disk either for the motherboard or as separate disks to use in Windows are not required nor will they work in Linux (okay, VERY rarely wireless drivers).  So, don't worry about installing the drivers, etc., that came with your PC and equipment in Windows.  Doesn't work - 2 completely different animals.

---

