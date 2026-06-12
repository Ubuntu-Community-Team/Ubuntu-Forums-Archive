---
title: "help me! PLEASE!!!!"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Bridget on 2008-06-05
seriously needs help!!!

My CD drive is broken and I downloaded ubuntu from online and got an icon on my desktop but it is saying windows is not recognizing how to open the iso file or something like that. Can anyone tell me how I can get Ubuntu WITHOUT using a CD?!?!?!?! PLEASE HELP ME!!!!!!

---

### Post by Dr Small on 2008-06-05
You probably burnt the ISO incorrectly. The ISO should be burnt as a 'image', not a file.

---

### Post by Victormd on 2008-06-05
Well, you can install it using the WUBI feature, but without a CD drive, you'll need to install a virtual drive, such as [daemon tools]("http://www.disc-tools.com/download/daemon"), and mount your ISO file.
Download Daemon tools lite, install and reboot. Then an icon will appear on your task bar and you can right click that icon, select "mount image" and browse to the file you downloaded. Now windows will recognize the ISO file as a CD and you'll be able to install ubuntu. Keep in mind that During the install, if windows looses control of the virtual device, ubuntu will not finish the installation. Though I seriously doubt this will happen, just thought I'd mention it... :)

Good luck!

---

### Post by Bridget on 2008-06-05
It was but I am not sure what to do now! I double click on it and nothing happens! Before it was asking what I wanted to use to open it! Now it doesnt do anything!

---

### Post by utsuprainfra on 2008-06-05
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

I used to use loadlin.

---

### Post by Bridget on 2008-06-05
Honestly computers is not my thing I am a nurse! Medical jargon is my language! Everything you just said was another language to me! I am such a beginner when it comes to this stuff!

---

### Post by Bridget on 2008-06-05
What option do I use on there?! Thanks by the way!

---

### Post by bikinguy77388 on 2008-06-05
Briget,

if you just want to get ubuntu going the easy way...google "wubi" download the program
Click on it..it will download ubuntu. Select the type of ubuntu you want..make a few easy selections and just sit back..installs it on windows in a virtual drive. You dont need a cdrom at all.

Hope this helps
bikinguy

---

### Post by Bridget on 2008-06-05
Thanks!!!!!

---

### Post by starcannon on 2008-06-05
[LIST]
[*]Don't Panic
[*]Don't forget your towel
[/LIST]

The file you downloaded is a special kind of file known as a disk image.

You need to find or choose a piece of software that is capable of recording (burning) a disk image to a cd. 

Simply dragging and dropping the file onto a cd will not do.

You need something that will "write image to cd" or some verbage equivalent to that.

When your done you will have a bootable install cd.

I would suggest and recommend that you try a wubi install for your first try, after you burn the "cd image" you will then be able to see the files that are contained in the image by loading the cd in the tray, one of them is a "wubi installer" use that for now, at least until you get your feet wet and are ready to move on to bigger and geekier things.

GL and use google, if you are a Nurse then you obviously know how to do research (my wife made it through A&P) and that is 9/10's of the battle to becoming good at computer related tasks.

*ignore my grammar, i know its terrible*

---

### Post by Victormd on 2008-06-05
> **starcannon said:**
> 
You need to find or choose a piece of software that is capable of recording (burning) a disk image to a cd. 

Simply dragging and dropping the file onto a cd will not do.

You need something that will "write image to cd" or some verbage equivalent to that.

From what I understood, she does not have a CD rom, so she'll have to use a virtual drive to install...

---

### Post by Lord Xeb on 2008-06-05
Bridget, I am not trying to be mean or insult you, but WOULD YOU STOP WITH THE '!'s NOW!!!! This is not as dire as you make it out to be. What are you trying to achieve with the Ubuntu Do you want to do a complete install of it and wipe windows from your machine, or do you want to dual-boot (which means you are running two operating systems on the same computer, or kinda like a car that it a hybrid, Run windows (the gasoline engine) if you want power and compatability with most of the programs out there, or run Ubuntu (the electic motor) if you want to have speed and efficentcy)? A virtual machine is a virtual "computer" It is were you run a seperate OS on virtual hardware. It is like someone running a small car inside a big one. 

You can find out how to set up Wubi [here]("https://wiki.ubuntu.com/WubiGuide").

Just give Ubuntu 8 GB of space and you should be set. Also, set the location to C:. Once you are done with that, it will ask you to restart then select Ubuntu at the boot menu. 10-15 minutes later, you have an install of ubuntu.

---

### Post by Lord Xeb on 2008-06-05
No, not neccessarily. She can use Wubi to dual-boot between Ubuntu and Windows.

---

### Post by ramjet_1953 on 2008-06-05
I'm probably stating the obvious here, but why don't you get the PC along to a repair shop and have the CD ROM drive replaced?

In the long run you are going to be having all sorts of dramas without it, so bite the bullet and have it repaired.

Regards,
Roger :cool:

---

### Post by starcannon on 2008-06-06
> **Victormd said:**
> From what I understood, she does not have a CD rom, so she'll have to use a virtual drive to install...

Doh! yeah your right hehe, in that case she needs something to mount that puppy with...

---

### Post by starcannon on 2008-06-06
> **Lord Xeb said:**
> No, not neccessarily. She can use Wubi to dual-boot between Ubuntu and Windows.

+1 for Lord Xeb's suggestion of a wubi install, it'll use the iso as well.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Victormd on 2008-06-07
> **starcannon said:**
> Doh! yeah your right hehe, in that case she needs something to mount that puppy with...

Yeah... :)
That's why I suggested daemon tools under windows... it's free and works like a charm...

---

