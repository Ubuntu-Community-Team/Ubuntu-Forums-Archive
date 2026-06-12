---
title: "Here's what happened..."
date: 2011-11-22
forum: New to Ubuntu
---

### Post by U-boo boo on 2011-11-22
Hi, all.
 
I was having a problem on my notebook, which was running Windows 7. While googling for a solution, I read a post on a forum that suggested using Ubuntu to fix the problem.
 
Thinking that Ubuntu was a fix-it utility,and not realising that the poster was being facetious, I downloaded Ubuntu to a USB drive and plugged it into my notebook.
 
Nothing happened, so I tried it in this desktop computer.
 
A process began, taking quite a long time. I let it run, not having any idea that it was, in fact, installing a Linux system on my computer!!!!!! My computer was running Windows XP, which I want to keep. Part way through this process, I aborted it and removed the USB drive.
 
Unfortunately now, when I start the computer, the boot process pauses and I am asked to select an OS, (Windows XP or Ubuntu). I select Windows, and it loads. But this is a nuisance. 
 
The one time that I experimentally selected Ubuntu in the boot-up screen, I got a message and Ubuntu couldn't load. I guess that's because I aborted the installation process.
 
Anyway, to get to the point, I'd like to ask, how the heck do I remove that fragment of Ubuntu so that I don't have to select my OS every time I boot up? 
 
More importantly, how do I remove it ***without formatting my drive and reinstalling XP*** all over again. I've had to do that a few times before, and I'd really like to avoid doing it again!  
 
***Any*** help will be very much appreciated! [-o< 
 
Thanks.

---

### Post by pierreyy on 2011-11-22
hello,

this is a guide that takes you through the process 

```
 http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/ 
```good luck


if you have questions about the terminology or whatever heres another link 

```
 www.google.com
```

---

### Post by grahammechanical on 2011-11-22
There are somethings that I do not understand and I would like you to explain.

1) Where did you download this Ubuntu from?

2) Was it Ubuntu.com?

3) Did you not read the instructions?

4) Ubuntu on a USB stick will not load unless you have set your machine to boot from USB stick before booting from hard disk and then you also need to boot the machine with the USB stick in drive. Is this what happened?

5) Ubuntu will not install unless you choose to install it and to do that you have to use the down arrow key to move the selection from Try Ubuntu Without Installing to Install Ubuntu.

6) Once you have started the install process you have to answer questions and click Next to continue. You always have the the option to cancel the install until you get the the section where you make the final choice to install.

7) So, I ask how the heck did you manage to mess up your system?????

I just want it made clear that Ubuntu will not mess up the system without considerable help from the computer owner.

Regards.

---

### Post by LegendaryBibo on 2011-11-22
So did you install Ubuntu? It wouldn't have installed unless you clicked on the install button. Otherwise it would have just been a LiveUSB running.

---

### Post by bluexrider on 2011-11-22
You need to fix the MBR Master Boot Record

Here's How:

[LIST=1]
[*] [Enter Windows XP Recovery Console]("http://pcsupport.about.com/od/fixtheproblem/ss/rconsole.htm").
[*] When you reach the command prompt (detailed in [Step 6]("http://pcsupport.about.com/od/fixtheproblem/ss/rconsole_6.htm") in the link above), type the following and then press **Enter**. 
 **fixmbr**
[*] The fixmbr utility will write a master boot record to the [hard drive]("http://pcsupport.about.com/od/componentprofiles/p/p_hdd.htm")  that you're currently using to boot into Windows XP. This will repair  any corruption or damage that the master boot record may have.
[*] Take out the Windows XP CD, type **exit** and then press **Enter** to restart your PC. 
  Assuming that a corrupt master boot record was your only issue, Windows XP should now start normally.
[/LIST]

---

### Post by Rubi1200 on 2011-11-22
Posting the results of the boot info script would also give us a better idea of what is where on the system and make offering solutions easier.

There is a link at the bottom of my post with instructions.

---

### Post by U-boo boo on 2011-11-24
Sorry, folks, I didn't get email notifications of these replies. 
 
I have fixed the problem to my satisfaction. I simply edited the Windows BOOT.ini file by deleting the line referring to Ubuntu. Now my machine boots straight to Windows.
 
 
@pierreyy: FYI, I found this forum by doing a Google search in the first place, thank you.....................................

---

### Post by lolpenguin on 2011-11-25
I think you installed Wubi...
Go to Add or Remove Programs and uninstall Ubuntu from there.

---

### Post by mastablasta on 2011-11-25
> **lolpenguin said:**
> I think you installed Wubi...
Go to Add or Remove Programs and uninstall Ubuntu from there.
 
 
he interrupted the install half way thoguih. it likely left plenty of stuff on the disk that needs to be cleaned. he should have waited until install was done and then do an uninstall.

---

### Post by mlentink on 2011-11-25
> **mastablasta said:**
> he interrupted the install half way thoguih. it likely left plenty of stuff on the disk that needs to be cleaned. he should have waited until install was done and then do an uninstall.

But not even a Wubi install starts by itself... So I suspect user error here.

---

### Post by lolpenguin on 2011-11-25
> **mlentink said:**
> But not even a Wubi install starts by itself... So I suspect user error here.

It didn't start by itself, s/he started it manually. To clean up all the junk, delete all of C:\ubuntu if the uninstall hasn't

---

### Post by U-boo boo on 2011-11-26
Guys, thanks for your help. I'm good, now. 

  Yes, it was user error. It happened because I read a facetious, cryptic, (snip) comment on another forum, and took it as genuine. My bad.

  Cheers.

---

### Post by Rubi1200 on 2011-11-28
Glad you got things worked out in the end :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

