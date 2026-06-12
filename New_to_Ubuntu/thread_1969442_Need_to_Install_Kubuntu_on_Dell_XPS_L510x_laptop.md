---
title: "Need to Install Kubuntu on Dell XPS L510x laptop"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by beepbeep2709 on 2012-04-30
Hi Guys,

I want to install Kubuntu on my Dell XPS L510x laptop (i5). I have worked on Linux for a while and after a lot of research, i found Kubuntu is the best distro which is catering my needs. Has anyone been able to install Kubuntu on the said laptop with all functionality available (meaning all the keys, sound, video et all). If yes, could someone guide me through it (if possible a doco if any). I just want to get rid of Windows 7 once and for all. Thanks..

---

### Post by Avaritia on 2012-04-30
Does alll the hardware work when you run the live cd?

---

### Post by beepbeep2709 on 2012-04-30
I am yet to get the installation running and was hoping for a way to get the installation done. Just wondering if anyone was able to install Kubuntu on the laptop without any problems.... i am yet to take a leap with the installation.

---

### Post by Avaritia on 2012-04-30
Burn Kubuntu to disc then restart computer and boot from it, when the menu pops up click 'Try Kubuntu', run it from CD so you can check what works before you install.

---

### Post by Curtis6767 on 2012-04-30
Follow Avaritia's advice. 

When you boot from the Live CD, you'll have the option to Try it. Do this before installing becasue Kubuntu will check for drivers and choose the correct ones. If you have problems, especially with your wireless connection, then you can wait and see if these issues are resolved before you take the plunge and install.

---

### Post by beepbeep2709 on 2012-04-30
Thanks guys...however, one question, if i install Kubuntu alongside Windows and give it a try, does that mean Kubuntu will load and install the drivers necessary for a working laptop? 
If yes, then i would give it a try installing Kubuntu rather than running it on live CD. That would give me a good idea on the functionality available on the laptop from the software. Correct me if i'm wrong guys... thanks.. :)

---

### Post by Curtis6767 on 2012-04-30
Click on the link below my signature that says "Read this before installing Ubuntu"

It will take you a few minutes to read but will save you headaches in the long run.

GL

---

### Post by beepbeep2709 on 2012-04-30
Thanks Curtis...made things a lot clearer...i will give it a try by installing Kubuntu on my laptop alongside Windows.... before going for a complete Linux environment... thanks again ! :D

---

### Post by beepbeep2709 on 2012-06-21
Hi Guys, 

I started this thread to get Kubuntu working on my Dell XPS L510X laptop and I have been running Kubuntu for a while now and below are few of my observations...

Overall performance - So far it has been a great ride on the new distro. This is my first time using any K(ubuntu) distro and i am happy with it so far and it has been an easy transition for me from Windows to Kubuntu. Although you need to get familiar with the new environment, the new applications etc, need to read about them and go through most of the forums to get it working as you need to. Overall a great Distro so far.

Peripherals (wifi, ports) - Most of the media buttons were activated during the install and i had not much to worry about buttons not working. However, i found the brightness button was not working and after a few searches found a solution to the problem. In case brightness button does not work you need to add the below line as a root user. 

echo 0 > /sys/class/backlight/intel_backlight/brightness 

Wifi didn't have much issues and worked perfectly fine. 

HDMI - I am having problems with my HDMI output though. I am not able to get hdmi working on my TV. I have been trying to search for solutions but to no avail. If anyone could help me out with it, would be great. 

Battery life with Kubuntu - I have not seen much of a difference in the battery life while using it. Its as same as Windows7 loaded on my laptop.  

Boot speed- Boot speed has been incredible. It takes less than a minute for me to start of my work. 

This is a first review so far as per my experience. once i have a strong hold on Kubuntu i will do a detailed overview on it.

Hope this helps someone.

---

### Post by blackbird34 on 2012-06-22
Great ! :D but then a lot of us love Ubuntu and Linux

Maybe you might like to talk about your laptop in[ this thread - the "**[B]Sticky:**[/B]                                      [other]                          **Laptop COMPATIBILITY List.**             "]("http://ubuntuforums.org/showthread.php?t=1543006") [link]
That way you can help others take the plunge, you mentioned some helpful details. 
(You could also mark your thread as solved)

Happy ubuntu-ing!

---

