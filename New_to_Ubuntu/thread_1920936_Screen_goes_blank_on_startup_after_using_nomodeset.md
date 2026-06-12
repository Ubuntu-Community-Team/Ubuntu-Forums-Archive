---
title: "Screen goes blank on startup after using nomodeset to install"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by graydon77222 on 2012-02-05
Hi I am new to Linux and I wanted to use my laptop to try Linux out full-time when I am not at home since I only use my laptop for note taking and some light coding.

So I downloaded the install files and when I went to install the screen seemed to turn off. So I looked on-line to see if I could locate a fix to my problem. Eventually I found that pressing shift at the install let me use a nomodeset option which made the screen work and I was able to install. But when I reset the computer at the end of the ubuntu 11.10 install the screen wouldn't work again. So I went searching and found I could edit a grub file and put nomodeset in the spot where quite splash or something was located, but this didnt seem to work.

I have now resorted for asking for help in my own thread, and would appreciate any help I could get.

Here is a link to my specific laptop model:  [http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/321957-321957-3329744-64354-64354-5082212-5170080.html?dnr=1](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/321957-321957-3329744-64354-64354-5082212-5170080.html?dnr=1)

---

### Post by mastergkage on 2012-02-06
Suaswe give me this installation advice when i encounter the same problem as yours I hope this works on you too

1. boot into a LiveCD/USB environment and opt for Try Ubuntu
2. once in the live desktop environment, go to Terminal and type in

Code:
sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom

3. click Install Ubuntu and run through the install as normal

then after the restart everything went well

---

### Post by graydon77222 on 2012-02-06
I tried to do that but when I pressed try ubuntu the screen went blank. And then when I tried to do try ubuntu with nomodeset it brought me to some black command line screen. And on this screen I typed your thing in, but since I was stuck on this screen I had no way to install.

---

### Post by 2F4U on 2012-02-06
Did you run 

sudo update-grub

after editing the grub configuration? Else the change is not permanent.

---

### Post by graydon77222 on 2012-02-06
> **2F4U said:**
> Did you run 

sudo update-grub

after editing the grub configuration? Else the change is not permanent.

Where do I do that? And for what change in the grub?

---

### Post by graydon77222 on 2012-02-06
I was searching on google when I came across this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777)

Is it impossible to get Ubuntu working correctly with my laptop?

---

### Post by mastergkage on 2012-02-06
Try using the last LTS support of ubuntu.

---

### Post by micxploed on 2012-02-21
I think I have the same problem as you, at first I installed ubuntu 11.10 via usb, all went well until i entered the password to log in and all I got was a blank screen. This has to do with the video card or graphics card. Like you said, hold shift upon booting to bring up grub menu then hit, "e". this will bring you to an editable page to where you replace "quite" and "splash" with the correct command that fits your video card, "mine was, "pci=noacpi". Then I reboot, sigh in and the problem seemed to be fixed but the next step is to manually change AND SAVE this from the inside. Sorry but I dont know how to change and SAVE from the inside of the os, im trying to do that now. your supposed to open grub to edit the text but i dont know how. please let me know if you fix this.

---

### Post by roelforg on 2012-02-21
> **graydon77222 said:**
> I was searching on google when I came across this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777)

Is it impossible to get Ubuntu working correctly with my laptop?

May i note that that bug relates to beta versions?

Also,
try CTRL-ALT-F1, if you get console:
than it does boot, it just won't start Xorg (try posting /var/log/Xorg.0.log)
if it won't, post the content of dmesg

FYI: update-grub regenerates grub's config

---

