---
title: "Ubuntu runs very slow !!"
date: 2018-11-08
forum: New to Ubuntu
---

### Post by legend2100 on 2018-11-08
Hi guys ...
               I am new to Ubuntu. I recently decided to let go of my windows and install Linux Os as the Main Os. I found many of my friends , colleagues , and other people in many 
               fields that tell me a lot about Linux and then i became admire of the idea to install it. After installing Ubuntu successfully and log in , i face a series & difficult problem 
               which is Ubuntu SLOW in everything . for example , to open a Terminal it take 5 to 6 seconds to open ! the OS doesn't run smoothly as i was told . Every program or even 
               a browser life Firefox take some to time to open and lagging . Also When typing on Keyboard it lags . I am very disappointed and I don't have another word to describe 
               the shock . Well i really want to solve this issue as soon as i can so i can discover Linux world . 

               Here the Specs of My Laptop : 
               System Manufacture & System Model : Dell Inspiron 15-3542
               Processor : Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz (4 CPUs), ~2.0GHz     L3 Cache Size : 4 MB
               BIOS : Legacy
               Memory : 8192 RAM DDR3
               Graphics & Display : Intel(R) HD Graphics Family  - Adapter String : Intel(R) HD Graphics 4400        
                                             Dedicated Video Memory : 128 MB  -  Shared System Memory : 1792 MB - Total Available Graphics Memory : 1920 MB
                                             
                                             Nvidia GeForce 840M      Memory :   - Size  :  2048 MB       - Type : DDR3       
                Screen Resolution : 1366 x 768 

                HDD Hard Disk  1 TB
               
                Well , i don't know if this information enough or not but pleeeeease Help me why Linux Os runs Slow 
                One of My friends told me to run this Command in the Terminal ( top ) and i did and then found that there are programs or services i don't really know but it consumes 
                all the CPUs  like Xorg and others .. also when i open Firefox it consume a lot of CPU .. i don't know why !! in general anything i open consume from 5 % to 20 %
                I will appreciate any Help and i will do anything to make Ubuntu fast as Windows 
                many told me that Ubuntu Should runs Super fast on your laptop and i also read that Linux is way faster than windows , then how ?
                my recent os Windows 8.1 Pro runs very smoothly without problems
                that's all guys i hope you help me solve this problem

---

### Post by TheFu on 2018-11-09
The integrated GPU on that system is weak.  If you want a faster experience, install and use a lighter DE rather than Gnome3 or Unity or KDE.  
XFCE, LXDE, Mate would be recommended.  You don't need to reinstall the OS, just logout, click the "gear", choose a different DE and login again.
Of course, a newer GPU would help.

For sharing specs, the **inxi -Fz** command is helpful. It provides the core data needed to be helpful.  For example, you didn't say which OS release.  The default GUI completely changed with 17.10 and later releases.

---

### Post by Autodave on 2018-11-09
Sounds like the Intel GPU only is being used and not the Nvidia. I, however, do not know how to make it use the Nvidia card: someone else will have to jump in here.

---

### Post by TheFu on 2018-11-09
> **Autodave said:**
> Sounds like the Intel GPU only is being used and not the Nvidia. I, however, do not know how to make it use the Nvidia card: someone else will have to jump in here.

Google found this: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If the system has a discrete GPU, definitely get that working. Even if you don't choose to keep using Gnome3 or Unity, the performance improvement would be significant with LXDE/Mate/XFCE too.

---

### Post by hennmann on 2018-11-12
My setup had similar problems of running slow, very slow at the log in screen where the cursor couldn't keep up to where I slid my rodent, the log in pass word was type one character every 3-5 seconds to let the sloth keep up and basically it was do a complete  system update, remove improper drivers of my GPU, and reinstall the proper drivers. What a difference including crashing of certain programs etc. is gone.

[https://ubuntuforums.org/showthread.php?t=2400219](https://ubuntuforums.org/showthread.php?t=2400219)

Drivers and software not updated brings a system down to it's knees

---

