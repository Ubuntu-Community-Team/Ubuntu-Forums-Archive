---
title: "trying 'recovery' mode way to try to fix this error"
date: 2018-02-22
forum: New to Ubuntu
---

### Post by fixlaptop on 2018-02-22
this is the error after the computer/os starts

starting version 232 ERROR '/dev/disk/by-label/' did not show up after 30 secs. sh: can't access tty: job control turned off

and stuff you're likely familiar with after it


when you turn on computer
it has a black box title
gnu grub ver 2.02 it says

one of the options is sys setup
nothing in sys setup works
meaning that it goes to black screen empty
then back to the black box title

when you select one of the adv options, there's an option for recovery mode
and it does the same thing as the error but just with no 'error' at the start of it

it ends on 
[rootfs ]#

and it has a blinking
_
next to it
 

[B]maybe there's something to type to fix this entire thing?

[/B]
im not technical, please show things in steps

please ask any clarifying questions that would definitely help fix this


--

---

### Post by alexandari on 2018-02-22
What have you done prior to seeing this? Any updates, installs? This error means that Ubuntu cannot locate or boot from your disk, due to a reason.

---

### Post by fixlaptop on 2018-02-22
> **alexandari said:**
> due to a reason.

nothing, never really used the laptop, there was some update error, dunno, one time last year or over, and now it's just like this

but anyhow what's the reason shown by the error? 

and just how to fix it? like what could be done?

what's usually done when it comes to these problems? 

im sure they have 10-points of diagnostics or w/e they do to fix these things

is there something to type into the black screen thingy, and then its all fixed?

---

### Post by fixlaptop on 2018-02-22
i have a < 2gb usb if there's something that can be on it to fix everything?

i should say these things tho:

* it's not dual-boot, this is the only os on it

* there's no way to get into that thing call 'bios'

* none of the 'shortcuts/hotkeys' on the laptop works when starting up the os

* i think maybe it's been disabled by linux or something, i dunno

before there was win10 on it, and everything was completely fine, everything works including 'buttons you press upon start'

---

### Post by leunam12 on 2018-02-22
If the hard disk died there is nothing that you can press and/or type to fix it, you have to replace the drive. So, I would start by checking the HDD's health. Can you boot to the live session from USB? There is a utility called "Disks" that allows you to check the disk's condition.

---

### Post by deadflowr on 2018-02-22
Double check with boot-info.
[https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

You can use the Ubuntu installation media that you used to install Ubuntu to run a live session (Use the Try Ubuntu option) and then download the boot info packages.
Then just copy the url of the paste it shows and copy that into this thread.

---

### Post by fixlaptop on 2018-02-22
> **leunam12 said:**
> Can you boot to the live  session from USB?

could you explain why you think it can?

is a usb suppsoe to start when you put it in or something?

if so, let me know

if not, then why would the laptop be able to start from the usb?

i had say that you cannot access bios

but the answer is no, you cannot start from usb cos you can need to access bios or something i think???

> **leunam12 said:**
> If the hard disk died

does that error say that? im asking what the error means

are there any good reasons or causes that you think the hard disk died? is that what the black screen means?



> **leunam12 said:**
> I  would start by checking the HDD's health

how do you do this? im 100% sure the hard drive is compeltely fine

i already say that win10 was completley fine on that laptop

> **deadflowr said:**
> boot-info.

huh? 

i dont think this can be done, please see above

is anything else that can be done?

would the laptop start from an external cd drive? or no??

i need to know if it would, if not then i know an external cd drive would not work

---

### Post by deadflowr on 2018-02-22
> i dont think this can be done, please see above
How'd you install Ubuntu?

---

### Post by fixlaptop on 2018-02-23
someone else did it

also before there was win10 on it, and everything was completely fine, everything works including 'buttons you press upon start' 

i already say that win10 was completley fine on that laptop


--

what now?

is anything else that can be done?

would the laptop start from an external cd drive? or no??

i need to know if it would, if not then i know an external cd drive would not work

---

### Post by QIII on 2018-02-23
Hello!

Which Release of Ubuntu did you install?

---

### Post by fixlaptop on 2018-02-23
i didnt install it

someone else did it

2016


--

what now?

is anything else that can be done?

would the laptop start from an external cd drive? or no??

i need to know if it would, if not then i know an external cd drive would not work

---

### Post by leunam12 on 2018-02-23
Hard disk failure is one of the most common problems in computers, a hard drive that works today may not work tomorrow. 
I have fixed a lot of computers in my life and the two main problems with computers are: 1-Overheating (mainly on laptops) and 
2-Hard drive failure. your system is complaining that it cannot find a certain drive, so the first step is to check the drive's health 
even if you are 100% sure that there are no drive problems.

The reason you cannot enter BIOS is because there is a "quiet" boot setting enabled in BIOS and it skips the POST messages that you
usually see at the beginning. 
If you have a Lenovo check to see if it has a separate button to enter the BIOS settings (some Lenovo's do). If you don't have that button,
then, one way to enter the BIOS is to unplug the laptop, remove the battery and press the power button for 45 seconds. Then, put the
battery back on the computer and plug it in and press the power button; most of the times this will allow you to see the POST
messages that tell you what to press to enter BIOS and temporary boot menu.

If you know what key to press to enter BIOS what you need to do is press power button and immediately start pressing
that key, since you only have a couple of seconds to do it and no warning on your screen.

You can boot from USB if you have a bootable USB drive, this is not intended to be a permanent solution, it is just used to install
the operating system and fixing and diagnostics. If you are successful booting from USB or DVD drive and you check your hard drive
and it has no problems, then, the next step is to run the boot-info as suggested above and post the results. Somebody will be able to
tell you what is going on and how to fix it.

---

### Post by QIII on 2018-02-23
2016 is not an Ubuntu release.

Can you ask the person who installed it what release was installed?

The fact that it is prompting at rootfs leads me to suspect that whatever was installed, it was installed with encrypted LVM (Logical Volume Management) and  the kernel is unable to access or pass control to the filesystem starting at /.

At this point we are in the dark without more information.  We can only provide guesses if you are unable to provide basic information about your system.  You further run the risk of being taken as willfully obtuse and losing the good will of those who would help.

Please stop repeating the last four sentences of your posts.

---

### Post by QIII on 2018-02-23
Further thoughts:

Are you able to enter the bios setup by tapping or holding the F2 key during startup?

[This user guide]("http://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-17r-n7110_setup%20guide_en-us.pdf") might be helpful.

Judging from some research on the web, which is always a good idea before one comes to a Forum unprepared, I suspect that you would be able to boot from your optical drive, but booting from USB appears to be problematic.

If your system is set up as an encrypted LVM, it is unlikely that you will be able to complete an installation without the encryption credentials.  However, if the prior installation used non-encrypted LVM, [this thread]("https://askubuntu.com/questions/228136/how-to-remove-all-lvs-vgs-and-partitions-on-all-drives-before-installing-12-04") might be of value even though it is specifically about Ubuntu 12.04.

I also suspect that you are somewhere near Mountain View, California.  Given the area, I think you could easily find a local LUG (Linux User Group) that, having physical access to your machine, could be of help.  Please take the time to attempt to find one.

---

