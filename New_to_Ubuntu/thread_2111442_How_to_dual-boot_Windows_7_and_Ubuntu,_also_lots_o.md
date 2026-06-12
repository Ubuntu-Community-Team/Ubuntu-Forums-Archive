---
title: "How to dual-boot Windows 7 and Ubuntu, also lots of other issues?"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by JayB1rd on 2013-02-01
Hello,

So I've only been working with/reading about Linux for about three days, so please feel free to correct me and tell me as much as possible.

Basically, my HP running Windows 7 (only) crashed a few days ago and I don't have any access to un-backed-up files. The goal of using Ubuntu was to get into my files, back them up on an external device, and then reboot my laptop to factory settings (or I might just completely switch to Linux because I'm starting to love it).

This is what I've already done:
-Used [this]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows") website to install Ubuntu version 12.10 [64 bit] on a USB
-Ran Ubuntu on my laptop

Here are my issues:

1. Ubuntu doesn't actually install on my laptop, every time I restart, I get a message that I'll be sent to a safe desktop because Ubuntu failed to restart. I can provide a picture of what this looks like if need be.

If it does go to the desktop, I've looked around, and there doesn't seem to be any kind of connection to the data on my Windows account, so it's just a blank slate. I downloaded WUBI and the .exe file won't open from my desktop or anywhere else I move it (I get a archive error).

If I click "install Ubuntu" and then press the power button, a pop-up comes up behind the "are you sure you want to shut down" or whatever page, helping me install Ubuntu. The problem is, as soon as it goes to reboot, I have to press F9 and reboot from Ubuntu all over again like nothing happened. I'm not sure what I'm suppose to be doing.

I don't know if I'm even doing this right, I basically want access to my Windows files through Ubuntu. Is this even possible? Am I incorrectly trying to install WUBI?

2. I just restarted on Ubuntu again, but now it claims not to be able to read my graphics card configuration, giving me some options, all of which take me to a non-editable b/w command page that doesn't do anything. I no longer have access to the blank desktop.

If you could help with any of these issues, I'd be super grateful, thank you!

Please let me know if I should provide pictures or more information.

---

### Post by offgridguy on 2013-02-01
I am not familiar with wubi, i do know it stands for windows , ubuntu, installer so i
suspect that without an operating windows system already installed, it's not going
to work.
I have always installed ubuntu alongside windows on it's own partition whenever i
dual boot with windows.

With the live USB, have you used the try ubuntu option?  Or only the install ubuntu
option?  The try ubuntu option should let you run ubuntu and give you access to
your windows files.

---

### Post by JayB1rd on 2013-02-01
> **offgridguy said:**
> I am not familiar with wubi, i do know it stands for windows , ubuntu, installer so i
suspect that without an operating windows system already installed, it's not going
to work.
I have always installed ubuntu alongside windows on it's own partition whenever i
dual boot with windows.

With the live USB, have you used the try ubuntu option?  Or only the install ubuntu
option?  The try ubuntu option should let you run ubuntu and give you access to
your windows files.


I saw the page that gave me the option between "try ubuntu" and "install ubuntu" once and I believe I clicked install because there was a note that said I could have ubuntu alongside Windows without any affect on my data. I'm not sure how to go back to that page.

---

### Post by rushikesh988 on 2013-02-01
just buRN the image of ubuntu in CD / DVD and boot from it .
then selet try ubuntu without changing my computer.

thats it ..

---

### Post by JayB1rd on 2013-02-02
Okay so I went back to that page and clicked "try ubuntu" but it reaches the end of the installation process, restarts the laptop, which doesn't give me the option to use ubuntu! So I have to go back to the desktop and reinstall ubuntu (inside windows, right?).

Also when it restarts, the laptop makes a very loud crackling noise...

---

### Post by Thee on 2013-02-02
Are you sure that everything with your hardware is alright? Seems like something is wrong with your hard drive. Can you boot into BIOS and check if everything is detected correctly? Maybe your Windows didn't just crash out of the blue...

---

### Post by fantab on 2013-02-02
> **JayB1rd said:**
> Okay so I went back to that page and clicked "try ubuntu" but it reaches the end of the installation process, restarts the laptop, which doesn't give me the option to use ubuntu! So I have to go back to the desktop and reinstall ubuntu (inside windows, right?).

Also when it restarts, the laptop makes a very loud crackling noise...

The "Try Ubuntu" option does NOT install Ubuntu on your machine. It only runs from CD/DVD/USB (that you have created). 

When you say "Try Ubuntu" at the end of it you WILL have a fully functional and working Ubuntu desktop. And this is not installed anywhere.  However you can do almost every thing that you would do from an installed OS. 

I hope we are clear so far.

Once you get to the Ubuntu desktop you can access your Windows partitions. And not only that, if you connected to internet, you can use Firefox as well.

If you need more help log into these forums from Ubuntu Desktop and we can take you further.

---

### Post by JayB1rd on 2013-02-02
> **Thee said:**
> Are you sure that everything with your hardware is  alright? Seems like something is wrong with your hard drive. Can you  boot into BIOS and check if everything is detected correctly? Maybe your  Windows didn't just crash out of the blue...

I'm actually pretty sure there's something wrong with my hardware,  which is why I'm trying to get my data off ASAP and reboot completely. I  took my laptop to an IT center a few days back, and I saw that the  person who was helping me used a Ubuntu USB and had access to my files  in Ubuntu, which is where I got the idea to dual-boot.

Also what specifically would I be looking for when I boot into BIOS?


> **fantab said:**
> The "Try Ubuntu" option does NOT install Ubuntu on your machine. It only runs from CD/DVD/USB (that you have created). 

When you say "Try Ubuntu" at the end of it you WILL have a fully functional and working Ubuntu desktop. And this is not installed anywhere.  However you can do almost every thing that you would do from an installed OS. 

I hope we are clear so far.

Once you get to the Ubuntu desktop you can access your Windows partitions. And not only that, if you connected to internet, you can use Firefox as well.

If you need more help log into these forums from Ubuntu Desktop and we can take you further.

Okay, that is clear, thank you, I do have a fully functional and working Ubuntu desktop. I am also currently using Firefox through Ubutu, but I'm not sure how to access my Windows partitions.

---

### Post by fantab on 2013-02-02
In the left side launcher you will see hard disk Icons, which are actually your Hard Disk partitions. They may not be labelled as C: or D: however, you can open them one by one after cliking on them.... 

If you are able to rescue your data then I suggest you save it somewhere other than your Hard Disk...
While you are with Ubuntu Desktop find a utility called "Disks", it will reveal more information about your Hard Disk.. on the top right corner you will see an icon like gears... click on it and choose to run SMART tests... 

Good Luck...

Edit: added a screenshot of "Disks".

---

### Post by JayB1rd on 2013-02-02
> **fantab said:**
> In the left side launcher you will see hard disk Icons, which are actually your Hard Disk partitions. They may not be labelled as C: or D: however, you can open them one by one after cliking on them.... 

If you are able to rescue your data then I suggest you save it somewhere other than your Hard Disk...
While you are with Ubuntu Desktop find a utility called "Disks", it will reveal more information about your Hard Disk.. on the top right corner you will see an icon like gears... click on it and choose to run SMART tests... 

Good Luck...

Edit: added a screenshot of "Disks".

I get an error after clicking all of the partitions:

Adding read ACL for uid 999 to `/media/ubuntu' failed: Operation not supported

This also happens when I try to "mount" the filesystem (is that what I'm trying to do?!) from the Disks page. I ran the SMART test, and it said everything is fine.

---

### Post by JayB1rd on 2013-02-02
Nevermind, I got it.

Thanks so much for your help, everyone!

EDIT: To get rid of the ACL issue, I typed this into terminal

sudo mkdir /media/$USER 
sudo chown $USER.$USER /media/$USER 

(help from [here]("http://askubuntu.com/questions/202630/cant-mount-any-partition-acl-error"))

and I was then able to access all of my partitions correctly.

---

### Post by fantab on 2013-02-02
We are glad that you could work it out yourself. Linux is all about that 'do it yourself'... mostly. :-)

---

### Post by offgridguy on 2013-02-02
:D> **JayB1rd said:**
> I'm actually pretty sure there's something wrong with my hardware,  which is why I'm trying to get my data off ASAP and reboot completely. I  took my laptop to an IT center a few days back, and I saw that the  person who was helping me used a Ubuntu USB and had access to my files  in Ubuntu, which is where I got the idea to dual-boot.

Also what specifically would I be looking for when I boot into BIOS? Since the person at the IT center had access to your files, hopefully you can too.  Probably confused you as you thought he was dual booting ,when in effect he was running ubuntu
from the USB drive.

I see i am a little late, glad it worked out for you.:D

---

