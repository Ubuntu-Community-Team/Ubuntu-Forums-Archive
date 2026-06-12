---
title: "Laptop boots to Busybox v1.27.2 Help?"
date: 2018-11-17
forum: New to Ubuntu
---

### Post by mistermaggot4 on 2018-11-17
Hey, 
My laptop is a brand new LENOVO ideapad 330 with 8gb of ram and 1 tb harddrive. 
This is my first time using Ubuntu or Linux on a laptop, and i put it on my computer about a week ago.
Today while i was working on a project, my computer suddenly froze, so i restarted it and it keeps booting up to a bunch of text ending in: "BusyBox V1.27.2 (Ubuntu 1:1.27.2-ubuntu3) built in shell (ash)"

Ive followed a few tutorials online that supposedly fix what i am going through, but none of them work.

I will attach a photo of what i am seeing exactly.

I am new to Ubuntu and Linux, so i know basically nothing about it yet, which may be why nothing has worked so far. Could someone help me? This is very frustrating.


Thank you!

---

### Post by Impavidus on 2018-11-18
That's not an error I personally encountered in 12 years of using Ubuntu. Most likely you interrupted an upgrade when you rebooted, but there are some other possibilities. What happens is that at one stage of the booting process the initial ram disk (that's what initramfs stands for) is loaded, which contains enough of an operating system to load the rest of it from the hard drive. However, that's where it stops on your computer. You've got a built-in shell that an expert user can use to (hopefully) fix the problem, but that will be a bit hard for you.

So let's first get some more diagnostics. Do you still have the live disk you used to install Ubuntu? It's a great tool to keep. Use it to run [Boot Repair](https://help.ubuntu.com/community/Boot-Repair) and create a boot info summary. Show us the link and we may know more.

---

### Post by mistermaggot4 on 2018-11-18
I used live-usb to try and install Boot Repair, but that led me to another problem:

For some reason I can't install Boot Repair. I've followed several different tutorials for doing so but they all lead to the terminal saying: 'Unable to locate package boot-repair".

I've included a picture of my terminal so you can see all that i typed in.
 
What do i do now?

---

### Post by angisky on 2018-11-18
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This page has install instructions. It's not on the default repositories so you need to add it. Additionally it says there's a boot-repair disc that you can download and flash to a usb or burn to a disc and it'll contain a live environment that already contains boot-repair so you don't need to go through the process of installing it.

---

### Post by Impavidus on 2018-11-19
Better install it from the repository in the Ubuntu live session. I read that the boot repair disk has an older version.

You split the first command in two parts. It should be```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```all on one line. You hit enter in the middle. That won't work.

---

### Post by mistermaggot4 on 2018-11-19
Thank you! I got boot repair to work. It gave me an address with information. I'll paste that down below:

[http://paste.ubuntu.com/p/kfggQGNr69/](http://paste.ubuntu.com/p/kfggQGNr69/)

I don't know what any of thos means, but is there a solution to getting my laptop working again, and is there anything i cam do to avoid problems in the future?
Thank you guys so much!

---

### Post by Impavidus on 2018-11-19
It appears you've got an encrypted system. Other than that everything shows as normal. I suspect you hit the reset button while writing to the encrypted file system, leading to file system corruption. I've no personal experience with encrypted file systems. Maybe someone who has knows some tricks to recover something, but I wouldn't hold my breath.

---

### Post by mistermaggot4 on 2018-11-19
Since my laptop is so new, i dont have much on it and am not too broken up about losing what i have saved. If i reinstalled the OS on my computer, would that restore things to normal?

---

### Post by angisky on 2018-11-19
Yeah just don't enable encryption the next time around. It'll be easier to troubleshoot when something comes up.

---

### Post by Impavidus on 2018-11-20
Reinstalling will work.

The downside of encryption is that it gets very hard, if not impossible, to recover from filesystem damage or a lost password. If you think there's an increased risk that this laptop gets stolen (like, you often take it with you out of the house and sometimes leave it unattended for a few moments) or if it contains highly sensitive data (like, you're a doctor and it contains medical records), you should encrypt the system. But for most of us it's not needed.

---

