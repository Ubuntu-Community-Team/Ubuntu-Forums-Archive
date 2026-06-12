---
title: "A walkthrough for booting and installing from USB?"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Vance14 on 2012-06-13
I am a complete newbie to all of this.  I have a computer that will no longer start in Windows and I would like to install Ubuntu (which I am installing now) from a USB key and then use that as the sole OS.  One of my reasons is to get at the files on the computer, the other is to just see what Ubuntu is like. 

Is there a walkthrough from "I have it on a USB" forward?

---

### Post by black veils on 2012-06-13
firstly, if you are just wanting your files, you can access them from the live usb **without** installing. there should be a  home icon or some sort of computer/file manager link on the desktop, double-click it to open. locate your windows partition from the left pane, then locate your personal files from within those windows files. copy and paste to another usb flash drive/external hdd/or try to zip things and upload to some online storage website, though they will have a file-size limit.

as for installing, remove all external media except the ubuntu live usb. you will see something like this [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

its also best you have a wired internet connection for the install process.

---

### Post by Vance14 on 2012-06-13
Ah, with the USB plugged in, I don't have change the BIOS at all?

---

### Post by irv on 2012-06-13
> **Vance14 said:**
> Ah, with the USB plugged in, I don't have change the BIOS at all?

With the USB stick plugged in, does it boot from it? If not you will have to set it to boot before your Hard Drive in the BIOS.

---

### Post by anewguy on 2012-06-13
It may be what you are already doing, but try using unetbootin on another PC that will boot to create the bootable USB installation.  You have the option of specifying the amount of space to allocate to persistence - keeping setting and some data over boots.  Unetbootin simply makes a "livecd" like version on a flash drive.

BTW - if you don't know - you can't just copy the installation(livecd) disk to the flash drive - you need to use one of the tools so it boots correctly, etc..

As black veils pointed out, you can run off the live media - be it CD or flash - and copy the files you need to save to another flash drive - and while it shouldn't be a problem, you need at least 2 usb slots to do so - 1 for the OS flash and 1 for as many flash drives or external devices you need to back up to.

Dave ;)

---

### Post by Vance14 on 2012-06-13
OK, so it is not as easy as I hoped.  I can't just copy the file I downloaded onto a USB key, then plug that into the computer and turn it on.  I figured that was too easy. 

So, what I need is truly a step-by-step, what I will need to at least get access to my existing files.  If you assume I know nothing, you will not be far from the truth.  I will likely be doing this tomorrow morning.

---

### Post by Rex Bouwense on 2012-06-13
Here is a very nice How To.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by wilee-nilee on 2012-06-13
It is very easy once you know how, booting a thumb is the same as a disc. You would either set the bios to boot the usb first, or use the per-session boot menu out side of the bios.

The per-session  on my setup is triggered with the f12 being held down as soon after you power on as possible, during the bios screen where it may actually tell you the key or key prompts, as well as the bios key prompt.

I never reset my bios I always use the per-session myself. 

You can find out the key prompts on the web with your computer model or in the manual for it.

Google per-session boot with the model, if needed.

---

### Post by Vance14 on 2012-06-13
Thanks guys, that information should get me going.  I will check back tomorrow and let you know how it goes!

---

### Post by black veils on 2012-06-14
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by Vance14 on 2012-06-14
OK, before I saw that link to unetbootin, I followed a link on the walkthrough to Lili USB Creator, and that is finishing up now.  It looks like I won't be able to try this until the morning.  I want to make sure that booting in Ubuntu using this USB key won't wipe out any data on the system, correct?  I have now found out that there IS essential data on the computer that we did not get Carbonite to backup, so that part is important.

---

### Post by Rex Bouwense on 2012-06-14
If you boot from the flash drive (or CD for that matter) you will not make any changes to your system unless you install it.  Booting to a live CD is an easy way to see if your hardware will run the OS.  Enjoy.

---

### Post by Vance14 on 2012-06-14
> **Rex Bouwense said:**
> If you boot from the flash drive (or CD for that matter) you will not make any changes to your system unless you install it.  Booting to a live CD is an easy way to see if your hardware will run the OS.  Enjoy.

OK, so I just have to make sure I run it live, and not install it.  I assume it will give me prompts at the boot on this point.

Once I get all the data I need, I think I will install it, I have been wanting to play with Ubuntu for a while now.

---

### Post by irv on 2012-06-14
It sounds like you are well on your way to becoming a Ubuntu Linux user. Once you do this you will see all the fun you been missing out on. I did this back in 2005 and I find I don't miss Windows one bit. In fact I don't think I will ever go back to using it on a daily bases. I can do everything I want in Ubuntu plus much more because of the great software out here. I am not a gamer, but many games are coming to Linux.

---

### Post by firekage on 2012-06-15
> **irv said:**
> It sounds like you are well on your way to becoming a Ubuntu Linux user. Once you do this you will see all the fun you been missing out on. I did this back in 2005 and I find I don't miss Windows one bit. In fact I don't think I will ever go back to using it on a daily bases. I can do everything I want in Ubuntu plus much more because of the great software out here. I am not a gamer, but many games are coming to Linux.

I did the same thing more than year ago. My friend was trying to convince me to try linux for more than 5 years. He succeded. I'm happy linux user - not because of stability because sometimes there are problems (that can be solved) but because of approach, because of software and my laziness - yes, that's right. Installing software in Ubuntu is so much easy that it's hard to belive! Also, it's much faster than on Windows.

There is something more - in linux world there is such saying:

"one tool for the job" - that's right! One good tool for the job (but it can have many front end like smplayer), and for an example, because of this i can watch movies in different players using one keyboard settings, i don;t have to learn each time i use new software! It's the same for different movies. Also, if i don't know something about software than...

man <software> 

and there is everything! Also, GUI in Linux is more fascinating, more user friendly, more advanced and just better! 3d, cairo, compiz, eye candies and much more!

Do you often work with text? Yes? Than what about fonts? They are much better (antialiasing?) on Linux than on Windows.

One more thing - terminal! Yes, if something is messed up we can fix it without rebooting! For an example - X crashed. So...let's restart X in terminal! Works!

---

### Post by Rex Bouwense on 2012-06-15
> **Vance14 said:**
> OK, so I just have to make sure I run it live, and not install it.  I assume it will give me prompts at the boot on this point.

Once I get all the data I need, I think I will install it, I have been wanting to play with Ubuntu for a while now.

When you boot from the flash drive you will be prompted to choose to try it without making a change to your computer.  That is the option that you want.  You will be running it from the flash drive.  Once it has fired up you will need to mount the partition that your data is on so you can copy it to a CD, another flash drive, or a whole bunch of floppies if you still use them.

---

### Post by Vance14 on 2012-06-15
> **Rex Bouwense said:**
> When you boot from the flash drive you will be prompted to choose to try it without making a change to your computer.  That is the option that you want.  You will be running it from the flash drive.  Once it has fired up you will need to mount the partition that your data is on so you can copy it to a CD, another flash drive, or a whole bunch of floppies if you still use them.

OK, I have it up and running in Ubuntu (off the USB drive), how would I go about mounting the other partition?  Do I need additional software for that?  Would I be able to install additional software on the USB-only OS?

---

### Post by irv on 2012-06-15
Just open your home folder and open the partition on the left and it will mount it and open it.
[ATTACH]219754[/ATTACH]

---

### Post by Vance14 on 2012-06-15
> **irv said:**
> Just open your home folder and open the partition on the left and it will mount it and open it.
[ATTACH]219754[/ATTACH]

Wow, that was just too easy!  Thanks!

---

### Post by Rex Bouwense on 2012-06-15
> **Vance14 said:**
> OK, I have it up and running in Ubuntu (off the USB drive), how would I go about mounting the other partition?  Do I need additional software for that?  Would I be able to install additional software on the USB-only OS?
No you do not need additional software.  Looks like you already have the other information.

---

### Post by irv on 2012-06-15
> **Vance14 said:**
> Wow, that was just too easy!  Thanks!

Sometimes a picture is worth a thousand words.
Most things are easy in Ubuntu Linux.

---

### Post by Vance14 on 2012-06-15
OK, a follow up question.  If I actually install the OS, will I still have access to that partition with the old files?

If not, I will just pull all of it off onto a hard drive and then install since I really want to use this extra machine to mess around with Ubuntu!

---

### Post by Rex Bouwense on 2012-06-15
It depends upon how you install.  When you select install, you will be asked how do you want to install?
1, Along side Windows.
2. Use the whole disk (this will erase everything on the hard drive).
3. Something else.
If you select along side Windows (or words to that effect) you will end up with a dual boot and will still be able to boot into Windows if you can do that now.  However, I always recommend that all data be backed up before doing that because you never know what can happen and you might end up losing data.  So any data that you do not back up is just data that you can afford to lose.
If you choose use the whole disk you WILL lose your data because it will be overwritten.

---

### Post by Vance14 on 2012-06-15
> **Rex Bouwense said:**
> It depends upon how you install.  When you select install, you will be asked how do you want to install?
1, Along side Windows.
2. Use the whole disk (this will erase everything on the hard drive).
3. Something else.
If you select along side Windows (or words to that effect) you will end up with a dual boot and will still be able to boot into Windows if you can do that now.  However, I always recommend that all data be backed up before doing that because you never know what can happen and you might end up losing data.  So any data that you do not back up is just data that you can afford to lose.
If you choose use the whole disk you WILL lose your data because it will be overwritten.

OK, perfect. Since it won't boot into Windows anyway, I might as well just use the whole disk.  I can easily copy all the relevant files out first.  Thanks!

---

### Post by Rex Bouwense on 2012-06-15
Have fun Vance14.  :popcorn:

---

