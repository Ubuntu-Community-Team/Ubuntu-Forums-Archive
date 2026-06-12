---
title: "Ubuntu won't start"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by bedpotato on 2012-02-23
Hello! I had to re-install Ubuntu yesterday because my hard drive broke and I had it replaced. It booted up fine at first and I've had two or three normal sessions on my laptop but now suddenly when turning it on it won't get to the Ubuntu screen. After coming up with the options of starting up Ubuntu normally or starting in recovery mode etc, I click enter to choose Ubuntu from those options, but it just says this on white writing on a black screen:

BusyBox v1.18.4 (Ubuntu 1:1.28.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

What does this mean?

Why won't my computer start?

Does it mean I have to reinstall Ubuntu - AGAIN? :(

Please can somebody tell me what to do? Thank you!

---

### Post by yeats on 2012-02-23
Are there any log messages that appear before you're kicked into BusyBox (there usually are)?

---

### Post by bedpotato on 2012-02-23
I don't think so. I think it just says as stated above.

---

### Post by bedpotato on 2012-02-25
Please can somebody help?

---

### Post by Jake5 on 2012-02-25
I had a similar issue with a .iso disk that i failed to check before i installed.

I suggest taking a good look here:[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

and make sure you did it right...Not assuming that you didn't, but stuff happens.

---

### Post by Carterclan on 2012-02-25
When you are in the Grub boot-loader menu try booting using a previous version if there is one listed.

---

### Post by mapes12 on 2012-02-25
This may help:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bedpotato on 2012-02-26
Thanks everyone, but I don't know what grub or boot loading or .iso means. I am a  BEGINNER.

Can anyone please explain in simple terms what the funny message means, and what I need to do to fix my computer? 

Thank you. :)

---

### Post by rbowen1 on 2012-02-26
> After coming up with the options of starting up Ubuntu normally or starting in recovery mode etc,

Select the recovery option and post what happens.

---

### Post by bedpotato on 2012-02-27
I don't know what recovery mode is or does. 

I still don't know what the message on my screen means or what BusyBox means, either, nor why my computer won't start.

I'm grateful to people who're trying to help by replying to this thread  but you're overlooking the fact that I'm a BEGINNER. Please can somebody help me? I need somebody to talk me through what I have to do, rather than assuming I know how to do things already. I would be very grateful for your help. Thank you! :)

---

### Post by audiomick on 2012-02-27
> **bedpotato said:**
> Thanks everyone, but I don't know what grub or boot loading or .iso means. I am a  BEGINNER.

Firstly, what is wrong is that either grub is broken or the computer can't find the spot on the drive that it is supposed to be booting form. I think the former, because I think you get a different error message when it can't find the drive.

So what is:
Grub, boot-loading, boot loader.

The computer has to be booted to start. The term comes from the concept of "pulling yourself off the ground by your own bootstraps." The computer has to tell itself to be a computer in order to start. That is all you need to know about that for now. If you want more info, search a bit in the internet. I'm not trying to brush you off, but it is a wide topic that you can leave for another day.

A boot loader is a small program that is stored on a part of the hard drive that the computer looks at first thing when you turn it on. The boot loader tells the computer "the operating system is over there". When you only have one operating system installed, be it Windows or Linux, you probably wont even notice this happening because there are no choices to be made.

Grub is a boot loader. When you have a dual boot, be it Windows and Linux, or multiple Linux installs or whatever combination, Grub shows a menu that lets you choose which install you want to boot into. 

If you only had Ubuntu installed, you would probably not have seen the Grub menu, as Ubuntu hides it when it is only a single install. You can make it show quite easily, but I am not sure how. I think you have to press shift, but I have practically never had to do this, so I don't remember.

Busy box is what comes up when grub fails to boot properly. It provides you with some tools with which you may be able to repair what is wrong. I can't help you with that, as I have no idea how it works.

An .iso is a file that is ready to be burned to a CD. The file that you use to create an Ubuntu CD is an .iso

Recovery mode is one of the options in the Grub menu. If is a "safe" mode of Ubuntu that should always be able to boot. I've never used that either, sorry.

There was a reference to an old kernel in one of the posts. In the course of time, your system is updated. New Kernels come along pretty regularly. The kernel is the very heart of the Linux sytem. When a new kernel is installed, the old one is not removed. The old kernels are available in the Grub menu. It can happen if something breaks that an older kernel witll still boot when the newly installed one is broken.

If you haven't already, I would suggest reading that link to the article on "boot repair". I think it is likely that there is some help to be had there.

---

### Post by bedpotato on 2012-02-29
Thank you for taking the time to write such a long reply to me, audiomick. 

I  wasn't asking for someone to explain all the terminology being used; rather, for someone to help me without using it (at least without assuming I know what it means). Knowing what all those words mean will not fix my problem.

Please can anyone just talk me through how to make the funny message on the screen go away, and how to make Ubuntu come back?

I will go and read those links you mentioned in the meantime, and see if I can find any solution there.

Edit: the link seems to be about using a software program. I can't use a software program, because my computer won't start. That's the whole point...

:(

Please someone help me! Would it work to re-install Ubuntu?

---

### Post by bedpotato on 2012-03-01
SOLVED!!!

Thanks to a very kind and patient user via PM.

You know who you are. :)

---

### Post by epicer on 2012-03-03
> **bedpotato said:**
> SOLVED!!!

Thanks to a very kind and patient user via PM.

You know who you are. :)

Hey mate I have same problem you had can you tell me how you solved it thanks

---

### Post by bedpotato on 2012-03-06
For anyone else with this problem, I have now posted the instructions I received on epicer's thread here:

[http://ubuntuforums.org/showthread.php?t=1935163](http://ubuntuforums.org/showthread.php?t=1935163)

---

