---
title: "Installation problems"
date: 2017-03-24
forum: New to Ubuntu
---

### Post by aris-ko on 2017-03-24
Hi,
I just installed ubuntu 16.04 on my VAIO SVF15 (dual boot with windows 10) and i have 3 problems.

1)There is no option "wifi" where i can connect to the internet through wifi. The only way to connect is by using Ethernet cable. 
2)The screen is flickering and it's not stopping
3)And most important, if i boot windows for 1 time then the laptop will always boot windows. There is no option to choose between Ubuntu and Windows.

Any help will be appreciated because i have no clue.
Thanks in advance :)

---

### Post by RobGoss on 2017-03-24
Hello and welcome, I'll try to answer at  least two questions for you

If I can remember correctly you should have a switch on that **VAIO** to turn on your **WiFi**, I remember installing Ubuntu on at least two machines like that and I had to turn the WiFi on in order for the WiFi to be detected once that was done my WiFi worked as it should

Second, If you are not seeing the GRUB menu it's because you did installed Ubuntu correctly, most likely your Windows 10 is installed in **UEFI** and you installed Ubuntu in Legacy mode

OldFred, has some great tips on UEFI and how to over come it
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

More UEFI information
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

How to dual boot Windows and Ubuntu 
[http://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi)

---

### Post by aris-ko on 2017-03-25
Thanks for the reply.

1) I disabled the secure boot and still cant enter the GRUB.
2) Concerning the wifi, the only way to turn it on is through settings. There is no special key on my keyboard for turning on/off the wifi.

---

### Post by RobGoss on 2017-03-25
> There is no special key on my keyboard for turning on/off the wifi

No, there should be a slider in the front bottom of that machine to turn on the WiFi this should allow you to turn WiFi off or on there is no special key on the keyboard

---

### Post by yancek on 2017-03-25
Take a look at the Ubuntu documentation at the site below which explains the requirements for dual-booting windows 10/Ubuntu using UEFI.  Are the steps indicated what you did?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When you click the network icon in the upper right of your Desktop, is wifi enabled?  You should be able to add/edit from there.

---

### Post by aris-ko on 2017-03-26
First of all thank you for your replies.

1) I connected to the Internet via Ethernet cable and then i managed to download drivers for the wifi. Now I'm able to use wifi.
2) I have followed the instractions from [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) but i still have a problem. After the end of installation i have to restart my PC. When restart is finished, I'm able to see the GRUB menu and choose between Windows and Ubuntu. If i choose Windows then I will never be able again to see the GRUB menu and my PC will alwaya boot Windows. I have turned off the secure boot and fast startup but still no solution.

---

### Post by RobGoss on 2017-03-26
> If I choose Windows then I will never be able again to see the GRUB menu and my PC will alwaya boot Windows. I have turned off the secure boot and fast startup but still no solution. 

Sounds like you've installed Ubuntu in MBR / Legacy mode and Windows is installed it UEFI

Is your machine UEFI? these questions are most important if you're trying to dual boot your system

Take a look at Oldfred's UEFI tips as I see you already installed Ubuntu on your system [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) please make sure you have a full understand how this is done to prevent damaging your Windows's installation

---

### Post by aris-ko on 2017-03-26
I fininally managed to get the GRUB menu (I ran a boot-repair) and almost everything works fine now. My screen is flickering now. Any ideas?

---

### Post by RobGoss on 2017-03-26
You might want to start another **thread** for the screen flickering issue in the mean time this may help your new issue [https://ubuntuforums.org/showthread.php?t=2061180](https://ubuntuforums.org/showthread.php?t=2061180)

---

### Post by Geoffrey_Arndt on 2017-03-26
What's the graphics system?   If nvidia or ati, you will need to use the dash button (top left on panel) and search for "additional drivers" program.    Start it and see if the hw prober finds additional drivers in the repos for your gpu.

---

