---
title: "How to Remove Ubuntu 11.04 from Hard Drive-Have 12.04 Already Installed"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by sewbiz on 2014-07-14
I'm in a mess. Without going into too much detail, can someone tell me how I would remove my Ubuntu 11.04 from
one of the partitions on my hard drive? I am a beginner. Tell me also how to find the partition it is on. Please
tell me what to type in the terminal (command-line). It's complicated so won't go into it here or I may be sent
to another forum sub-category. : (    Thank you for your help.

I have a desktop with a dual-boot system. BIOS settings/Intel processor. Ubuntu 12.04LTS on system.

---

### Post by sudodus on 2014-07-14
Please get Boot Repair and ***create a BootInfo summary***, that you upload to make it available for us (normally done automatically). See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sewbiz on 2014-07-14
Sounds easy...but the problem is, I am using a laptop (Windos OS) to tell you of my trouble.
The computer I am having the trouble with is a desktop (both Ubuntu 11.04 and 12.04LTS on hard drive).
I did make a live CD/DVD-RW of the boot-repair disc and ran it. Now I can't log in as it does not
recognize my password. : (  A bigger mess now as I try to fix things on my own after reading
what is out there. I will run this new DVD I just made and try. Won't be able to auto anything.
Will have to type what I can see.

---

### Post by sewbiz on 2014-07-14
Doesn't do any good....it is now ignoring any changes to the boot order....running the newly
arranged boot things I suppose that boot repair fixes so now how do I get back to my old
settings (password to login). It is like because I did the "boot repair" install, now removed
my passwords. : (
I only get to the login page on the screen for Ubuntu 12.04LTS.   Just a mess I am in now.
Thank you for any advice.

---

### Post by sewbiz on 2014-07-14
I do have a terminal if that will help.

---

### Post by sudodus on 2014-07-14
OK, this might be simpler:

If either of Ubuntu 11.04 and 12.04LTS is working you can also

1. Tell us which operating system is running

2. Run these terminal commands and post the output

```
 sudo parted -l
```

... space minus ell

and

```
df
```

---

### Post by sudodus on 2014-07-14
***df*** will show the running system's root partition '**/**' and from that and the output of ***sudo parted -l*** we can conclude which is the other installed system.

---

### Post by yancek on 2014-07-14
In your other thread earlier, you indicated you could boot to one of the systems installed.  Were you able to run the 2 commands I suggested in your other thread before your machine became unbootable?  I explained their purpose in your other thread.  Sounds like your BIOS is acting up or else you forgot how to save changes?

---

### Post by oldfred on 2014-07-14
Boot-Repair would not change a password. And liveDVD or flash drive has no password with Ubuntu.

At most you may have changed default boot from one system with one password to the other system with a different password?  Or user name.
Or you forgot password. 
It also is case sensitive.

---

### Post by sewbiz on 2014-07-15
> **oldfred said:**
> Boot-Repair would not change a password. And liveDVD or flash drive has no password with Ubuntu.

At most you may have changed default boot from one system with one password to the other system with a different password?  Or user name.
Or you forgot password. 
It also is case sensitive.

It is GOOD NEWS to me that boot-repair can not change a password.
Let's forget about all the other threads. It is too confusing and I don't want to go backward to move forward.
I am not going to do another thing on my own anymore because I always end up making a bigger mess of things.

I am a beginner....but need expert help. It has been weeks of taking my time to fix this. I am reading the manual (so to speak)
to learn some things but not a tech wizard. Some get ticked off if you ask a question that sounds simple to them...but I do
need things "dumbed down" a bit.

I can't work on this again now for a few days. Grandma does a lot of babysitting lately, but very important to get my system
up and running again...need it for my job/business. Thank you for your patience with me! I use the same passwords as I have
for years....did not forget them. Especially...for the last many weeks of doing this. Maybe a break from this will help some.

---

### Post by sewbiz on 2014-07-15
> **sudodus said:**
> OK, this might be simpler:

If either of Ubuntu 11.04 and 12.04LTS is working you can also

1. Tell us which operating system is running

2. Run these terminal commands and post the output

```
 sudo parted -l
```

... space minus ell

and

```
df
```

Thank you...but until I can get my password problem figured out...I am not going to get far typing any commands.
Seems the teminal does not recognize my password anymore. Weird...and I didn't forget it.

Also...another weird thing that has happened (since I used the boot-repair disc) is that 11.04 is nowhere to be found anymore.
It always, no matter what I "select" boots into the 12.04 version. Maybe boot-repair got rid of 11.04 since it is not supported
anymore by cannological (or whatever it is called). I am only guessing.

---

### Post by sewbiz on 2014-07-15
> **sudodus said:**
> ***df*** will show the running system's root partition '**/**' and from that and the output of ***sudo parted -l*** we can conclude which is the other installed system.
   
Thank you....I will try this when I get the chance (when my password works). :(    I do appreciate your help!

---

### Post by sewbiz on 2014-07-15
> **yancek said:**
> In your other thread earlier, you indicated you could boot to one of the systems installed.  Were you able to run the 2 commands I suggested in your other thread before your machine became unbootable?  I explained their purpose in your other thread.  Sounds like your BIOS is acting up or else you forgot how to save changes?

You would have to tell me again what "2" commands. I recall.....I never found "both" of them.
I want to stay on this string of threads now (with this new title) and forget all others. It got too confusing.
Pretend I am starting fresh. But remember to consider the mess I am in so what would normally work for
some will not work for me:

1. My boot volume disc is 100% full now.
2. My Grub folder is missing IMPORTANT files (.mod and others) that I STUPIDLY deleted (while trying to make "space" on the boot volume instead of JUST REMOVING KERNELS)
3. Since running BOOT_REPAIR following well intentioned advice from others....I now can not sign into my desktop, or get permission for commands in the terminal. (Does not recognize my password anymore that I have used for years.)
4. I have Ubuntu 12.04LTS and 11.04 installed (yet can't find 11.04 anymore)
5. Can't boot from USB but it sees my "wireless mouse and keyboard" all on the same hub mount thing (it holds 7 ports)

Thank you for your help....I do appreciate your time!!!

---

### Post by oldfred on 2014-07-15
Can you boot a 12.04 live USB or DVD in live mode?
If so run Boot-Repair but do not run any fixes, but run the BootInfo report and post link it gives you.

---

### Post by sewbiz on 2014-07-21
I can boot a 12.04 DVD....not USB. But the problem is....it will not open to my desktop. I get the LOG-In screen for Ubuntu 12.04LTS ....I enter the password (which it recognizes I "assume") and then it just opens a terminal. That is all the further I get. I don't know what commands to type in after that to get past the log-in so it will open to my desktop. : (

I am making a live DVD of the boot-repair disc again but do believe I have already used it. I am making it from Windows 8.1. 
I put the boot repair disc in after changing the order of the boot to the DVD.....then restarted the computer. I get the Intel screen that shows the BOOT and BIOS menu keys...next my Log-in screen comes up....I type in my password....then I get the terminal....I typed in the terminal....sudo parted -l.....clicked "enter" (got a lot of info)....next I typed in 'df'...enter and got a lot of info. Do you want me to type all this info here? The one error message I got was: Error: /dev/sr0: unrecognised disk label

---

### Post by sewbiz on 2014-07-21
> **sudodus said:**
> OK, this might be simpler:

If either of Ubuntu 11.04 and 12.04LTS is working you can also

1. Tell us which operating system is running

2. Run these terminal commands and post the output

```
 sudo parted -l
```

... space minus ell

and

```
df
```

```
sudo parted -l
```

This is the output.....
```

Number Start       End       Size       Type           File System        Flags
1      63.5kB      500GB     500GB      extended                          boot
5      64.5kB      215GB     215GB      logical        ext4
6       215GB      334GB     120GB      logical        ext4
8       334GB      425GB     91.0GB     logical        ext 4
9       425GB      430GB     4248MB     logical        linux-swap(v1)
7       430GB      500GB     70.6GB     logical        ext4

Model: ATA WDC WD50000AAKS-0 (scsi)
Disk  /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number    Start     End        Size     Type           File System        Flags
1         1049kB    512MB     511MB     primary        ext2               boot
2          512MB    2511MB   2000MB     primary        linux-swap (v1)
3         2511MB    22.5GB   20.0GB     primary        ext4
4         22.5GB     500GB    478GB     primary        ext 4

Error: /dev/sr0: unrecognised disk label
```

```
df
```

This is the output.....
```

Filesystem        1K-blocks     Used        Available     Use%      Mounted on
/dev/sdb3          19222656     60216 96    12224424       34%      /
udev                2032880            4     2032876        1%      /dev
tmpfs                408040          844      407196        1%      /run
none                   5120            0        5120        0%      /run/lock
none                2040188           76     2040112        1%      /run/shm
/dev/sdb1            467367       465900           0      100%      /boot
/dev/sdb4         459082912    193499452   242263348       45%      /home
```

---

### Post by yancek on 2014-07-21
> I can boot a 12.04 DVD....not USB. But the problem is....it will not open to my desktop

What do you get from the DVD?  Black screen?  black screen with a blinking cursor?  Do you see any graphical user interface with any of the usual icons or the panel on the left?  Does it also just open to a terminal?

If you boot into 12.04 and get a terminal try typing:  startx  (needs to be all lower case and exactly as posted), hit the Enter key.  No harm in trying, it won't damage anything further although I'm not sure it will work.

> I am making a live DVD of the boot-repair disc again but do believe I have already used it
 
If you already have the boot repair on a DVD/CD just use that.  No need to do it again.

> I put the boot repair disc in after changing the order of the boot to  the DVD.....then restarted the computer. I get the Intel screen that  shows the BOOT and BIOS menu keys...next my Log-in screen comes up....I  type in my password....then I get the terminal.

I've never used the boot repair disc but I would not expect it to ask for a password?  Copying the output of the df -h and parted -l commands here would be a good idea.   If you get a GUI from the startx command, you should be able to post the output of the commands here.  If not it would probably be simpler to copy everything down then use your windows system to come here and post the information.

---

### Post by oldfred on 2014-07-21
I do not see any NTFS partitions, or no Windows.

Your sdb1 or /boot is 100% full. Generally with desktop computers better to not have a separate /boot. Server type installs or RAID or LVM may need a separate /boot.
You do have to regularly houseclean /boot as new kernels do not overwrite old. Unless you manually delete them it just keeps filling up.

You should be able to get to a desktop with the liveDVD. If only getting to the terminal even with Live installer it sounds like a video issue? 
What video card/chip(s) do you have.

You really want to use dpkg from your install to remove kernels. If you just delete them, then dpkg gets out of sync with what it thinks you have installed. But sometimes you have to delete as that is the only way.
Is this just the accumulation of kernels from 12.04 or is this install an update from an older version. dpkg would probably not have the old kernels from previous installs in its data.

When you say you are at a terminal is that in your install or in the liveDVD?
If in your install not liveDVD you can use dpkg to remove kernels.

       Determine your current kernel, you want to be sure not to delete it:
uname -a
uname -r
      
 cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example, in your case with 12.04 they may be 3.2 or later versions depending on which version of 12.04 you have:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic

I prefer to install synaptic and use it to remove kernels. But you need working desktop.
      
 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by sewbiz on 2014-07-21
> **yancek said:**
> What do you get from the DVD?  Black screen?  black screen with a blinking cursor?  Do you see any graphical user interface with any of the usual icons or the panel on the left?  Does it also just open to a terminal?

If you boot into 12.04 and get a terminal try typing:  startx  (needs to be all lower case and exactly as posted), hit the Enter key.  No harm in trying, it won't damage anything further although I'm not sure it will work.


 
If you already have the boot repair on a DVD/CD just use that.  No need to do it again.



I've never used the boot repair disc but I would not expect it to ask for a password?  Copying the output of the df -h and parted -l commands here would be a good idea.   If you get a GUI from the startx command, you should be able to post the output of the commands here.  If not it would probably be simpler to copy everything down then use your windows system to come here and post the information.

YES....read post #16...above yours. We must have sent our messages at the same time.

---

### Post by yancek on 2014-07-21
> YES....read post #16...above yours. We must have sent our messages at the same time. 		

Yes what?  Your last post seems to be in response to my earlier post in which I asked 5 separate questions and the answers to all of them could not be yes as they would be conflicting.

Did you get to a terminal on boot?  Were you booting from the hard drive to 12.04 or 11.04?  Did you try entering the startx command I suggested?  If so, what happened?  
Or, did you boot from the DVD and that is how you got the output you posted?

In your earlier post, you indicate that you were able to boot to a login screen.  You also indicate that you then enter a password and don't get the Desktop but do get a terminal.  If that is the case, you are booting something on the hard drive.  There is no login screen on the Live DVD as explained above.  There is also no password required on the Live DVD.  If you are getting a login screen and enter a password then following the suggestions by oldfred above should at least improve the situation.

---

### Post by sewbiz on 2014-07-23
> **sudodus said:**
> ***df*** will show the running system's root partition '**/**' and from that and the output of ***sudo parted -l*** we can conclude which is the other installed system.

sudodus...could you please help me? My messages are getting confusing again as others are trying to help and I find myself repeating my messages. I responded to what you suggested I do...by entering the two commands ```
df
``` and ```
 sudo parted -l 
```.  See my entries in #16 post here on this string of threads. I do appreciate so much your help.

Does it seem like I need to just buy a new processor or wipe my hard drive clean (if I could). I just want to get back to Ubuntu on my desktop. Can't even get in anymore.
Seems Boot Repair made things worse now for me. Can I remove whatever boot repair did? Ubuntu 11.04 is inoperable now even, and that was the one that at least got me
to use my desktop. I know it is no supported anymore, however.

---

### Post by sudodus on 2014-07-24
Yes, I'll try my best to help :-)

*Very important*: The first thing to do before starting to edit partitions or installing any new operating system is to ***backup*** your current system or at least your personal data (documents, pictures ...). And you should ***test*** the backup. Otherwise you don't know if it really works.

> **sewbiz said:**
> sudodus...could you please help me? My messages are getting confusing again as others are trying to help and I find myself repeating my messages. I responded to what you suggested I do...by entering the two commands ```
df
``` and ```
 sudo parted -l 
```.  See my entries in #16 post here on this string of threads. I do appreciate so much your help.

What we need to get clarified is *which system was running, when you ran **df** and created the output in post #16*.  That system is located in the partition **/dev/sdb3**. You tell us Ubuntu  11.04 is inoperable now. Does that mean the the other system, 12.04, was  running?

When that is clarified, and we know for sure, I can advice which partition can be re-used (formatted or merged with another partition).
> 
Does it seem like I need to just buy a new processor or wipe my hard drive clean (if I could). I just want to get back to Ubuntu on my desktop. Can't even get in anymore.
1. Next step *for me* would be to get details about your computer. Then we can discuss if it can run standard Ubuntu or maybe better some flavour like Lubuntu or Xubuntu. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. Next step *for **yancek* is probably that you try to reply with as much details as possible to their questions in previous posts.
> 
Seems Boot Repair made things worse now for me. Can I remove whatever boot repair did? Ubuntu 11.04 is inoperable now even, and that was the one that at least got me
to use my desktop. I know it is no supported anymore, however.

I'm sorry about Boot Repair. My intention (in post #2) was that you ***create a BootInfo summary***, not that you try to repair the system. I should have been more clear about that. But it is possible to make the booting work properly with or without Boot Repair. The BootInfo summary would still be a great help. It will tell us more than ***sudo parted -l*** and ***df***.

Finally, please try Ubuntu and the community flavours live (without installing) according to this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

and after that we know better what would be your best alternative.

---

### Post by sewbiz on 2014-07-24
> **sudodus said:**
> Yes, I'll try my best to help :-)

*Very important*: The first thing to do before starting to edit partitions or installing any new operating system is to ***backup*** your current system or at least your personal data (documents, pictures ...). And you should ***test*** the backup. Otherwise you don't know if it really works.

I have what I need backed up...all else is lost...too late....it was written over when I did a download, before I knew it would do that. Nothing I can't recover. Not serious.
Have my pics and videos backed up.

> **sudodus said:**
> 
What we need to get clarified is *which system was running, when you ran **df** and created the output in post #16*.  That system is located in the partition **/dev/sdb3**. You tell us Ubuntu  11.04 is inoperable now. Does that mean the the other system, 12.04, was  running?

I am guessing 12.04 because when I got to the log-in page on the computer...that is what it said at the bottom of my screen...."Ubuntu 12.04LTS"
I can no longer "find" 11.04 since I installed the BootRepair disc. 


Details about your computer: (I know I have put this in one of my other threads but not easy to find it...didn't take good notes.)
- Brand name and model.... Intel Corp.  DG41TX    Version: AAE78178-303   (My son built it for me.)
- CPU.....Processor Type: Intel(R) Celeron (R) CPU E3400 @ 2.60GHz   Intel 64 Architecture Capable
- RAM (size)....L2 Cache RAM   1024 KB     Total Memory  4096 MB (DDR3)
- graphics chip/card.....?????    (Where do I find this? My computer is a desktop.)
- wifi chip/card.....????? again....where do I find this info?
 More......  
Core Multiplexing Technology    CD/DVD Rom    (SATA: Optiarc DVI)
SATA Port 0    WDC WD5000AAKS (500.1GB)
Primary Slave:  Hitachi HDP725 (500.1GB)

> **sudodus said:**
> 
I'm sorry about Boot Repair. My intention (in post #2) was that you ***create a BootInfo summary***, not that you try to repair the system. I should have been more clear about that. But it is possible to make the booting work properly with or without Boot Repair. The BootInfo summary would still be a great help. It will tell us more than ***sudo parted -l*** and ***df***.

Don't think you or anyone in particular told me to do that. I did it out of desperation. Now I post
on a thread and wait a day or two for a reply before I mess with anything. It seems when I do I get in a deeper mess.


> **sudodus said:**
> Finally, please try Ubuntu and the community flavours live (without installing) according to this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

and after that we know better what would be your best alternative.

Will do but first things first and remember that I am not all that tech savy so dumb things down. I am a beginner in over my head.
I am very grateful for your help. I read what I can and see the glass half full all the time which makes me try too many things too soon
in hopes it is the FIX! Always hopeful.

---

### Post by sewbiz on 2014-07-24
> **yancek said:**
> 
Did you get to a terminal on boot?  Were you booting from the hard drive to 12.04 or 11.04?  Did you try entering the startx command I suggested?  If so, what happened?  
Or, did you boot from the DVD and that is how you got the output you posted?

In your earlier post, you indicate that you were able to boot to a login screen.  You also indicate that you then enter a password and don't get the Desktop but do get a terminal.  If that is the case, you are booting something on the hard drive.  There is no login screen on the Live DVD as explained above.  There is also no password required on the Live DVD.  If you are getting a login screen and enter a password then following the suggestions by oldfred above should at least improve the situation.

Thank you for you help. I am still learning how to do these messages so please be patient with me. I hear your frustration. I will try to be more clear. You are further advanced than I am. 

Everyday my situation changes so that is why there is so much confusion. Don't even read past posts.

This is what I do:

1. Turn on computer....open drawer for DVD...insert DVD of Ubuntu 12.04LTS...close drawer...Restart computer
2. Click F10.....enter password....get to "select boot device"....select SATA: Optoarc DVD RW AD-726OS
3. Click ENTER.....Ubuntu Log-In page opens 
4. Enter password....click enter.....up pops terminal...nothing else.
5. End of story.

I tried ```
 startx
```....output shown below:

X: user not authorized to run the X server, aborting.
X10: fatal 10 error 11 (Resource temporarily unavailable) on X server ":0"
after 7 requests (7 known processed) with 0 events remaining.

I can only boot from the DVD otherwise my computer has only a black screen that says:

grub rescue

Thank you for your help. I would understand if you did not want to bother anymore with me. 
I will continue on as I am that stubborn! : )
Have a good evening...do appreciate!!!

---

### Post by yancek on 2014-07-24
>  Click ENTER.....Ubuntu Log-In page opens 
4. Enter password....click enter.....up pops terminal...nothing else.

That's confusing as has been mentioned above, the installation medium (DVD) does not have a password.  You could try this when you get the terminal:

```
sudo grub-install /dev/sda
```

After typing that, hit the Enter key and watch for any output.  When you get back to the original prompt in the terminal type:

```
sudo grub-install /dev/sdb
```  Again, hit the Enter key and watch output.  When back at the prompt, reboot to test to see if you can boot without the DVD in the drive.  You will need to select one of the hard drives from 'select boot device'.  Try that and post back the results.

---

### Post by oldfred on 2014-07-25
Are you really booting DVD or is DVD not booting and BIOS is going to next in boot order and is defaulting to hard drive?
Then on hard drive you would boot into your install and need user & password?

This shows both the BIOS & UEFI boot screens that you get from a DVD or flash drive that is the live installer.
BIOS is the purple screen & UEFI is a grub menu.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If booting into your system and you only have one system installed, you do not get grub menu, but it just boots the one system installed. To get to grub menu with BIOS you have to hold shift key from BIOS until menu appears. With UEFI you usually use the escape key.

---

### Post by sudodus on 2014-07-25
I think you can try to get your installed system running, which is probably Ubuntu 12.04 LTS) in the partition **/dev/sdb3**. We are (at least) three persons trying to help, and one of us might find the key, that will solve your problem.

 I suspect there are problems with the driver for graphics or wifi. That is why I wanted to know what chips or cards you are have. Maybe you can ask your son about that.

-o-

But if you do not succeed after a fair effort, since you have backed up your important files, you might head for a fresh installation.

And before that installation, [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing]("http://ubuntuforums.org/showthread.php?t=2230389")

Try not only the newest version 14.04.1 LTS, but also the previous LTS version, 12.04, that you have installed. It should work live (booted from USB/DVD) at least with some boot options according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you have or can get a USB pendrive, it is a good idea to make a ***USB boot drive*** and install from it. I think it is easier and more reliable unless the computer is very old. Your computer is 64-bit capable, so it should be new enough to manage booting from USB. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 Otherwise you can try to burn new boot DVD disks. It is important to make it the correct way, not simply burning files into a data-DVD, but ***burn an image***.

---

### Post by sewbiz on 2014-07-27
> **sudodus said:**
> I think you can try to get your installed system running, which is probably Ubuntu 12.04 LTS) in the partition **/dev/sdb3**. We are (at least) three persons trying to help, and one of us might find the key, that will solve your problem.

 I suspect there are problems with the driver for graphics or wifi. That is why I wanted to know what chips or cards you are have. Maybe you can ask your son about that.

He will be home in a couple weeks so then I will ask him about it. I don't want him to worry about me right now. He is very busy at his job.

-o-
> **sudodus said:**
> 
But if you do not succeed after a fair effort, since you have backed up your important files, you might head for a fresh installation.

And before that installation, [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing]("http://ubuntuforums.org/showthread.php?t=2230389")

Try not only the newest version 14.04.1 LTS, but also the previous LTS version, 12.04, that you have installed. It should work live (booted from USB/DVD) at least with some boot options according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I will print this message and look into your suggestions.

> **sudodus said:**
> If you have or can get a USB pendrive, it is a good idea to make a ***USB boot drive*** and install from it. I think it is easier and more reliable unless the computer is very old. Your computer is 64-bit capable, so it should be new enough to manage booting from USB. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I have no luck booting from a USB...can't change my boot priority thing. It won't let me select anything even using the arrow keys. Only can change the boot menu page to DVD so that will boot first for me. Am I making sense?

 > **sudodus said:**
> Otherwise you can try to burn new boot DVD disks. It is important to make it the correct way, not simply burning files into a data-DVD, but ***burn an image***.

I figured that maybe that part is what I am always getting wrong but Windows (stinking) 8 does not show me that option "burn an image"....been looking everywhere how to do that (burn to disc using Windows 8....I had XP so knew that OS), yet the selection (burn to disc) does not pop up. The menu only allows me to select "send to" DVD...but NOT BURN to disc...or even the word "Burn" anywhere. However.... If I open the drawer for the DVD....and then look for the icon for the DVD (under "Devices and Drives") and right click on it... ONLY THEN do I see Burn as an option. So...I click on it (Burn to disc)...and (no surprise) I get a warning message " No files staged to burn. (NO Kidding!) Please add the files you want to burn to this disc, then try burning again." 

So....when I select the files and move them to the DVD when it is in the drawer...I can't select burn yet when the drawer is open and I select the icon ...I CAN select "burn to disc". It is pure frustration and insanity....WINDOWS. So this is my dillema. I will do my homework and look at the links you sent. I have already gone to many links "How to burn DVD/Windows" etc. but getting no where.

Thank you for your help though...I will get back to you in a few days. : (  Seems I am going in circles but maybe if I get the proper "BURN" we will have something.

---

### Post by sewbiz on 2014-07-27
> **oldfred said:**
> Are you really booting DVD or is DVD not booting and BIOS is going to next in boot order and is defaulting to hard drive?
Then on hard drive you would boot into your install and need user & password?

This shows both the BIOS & UEFI boot screens that you get from a DVD or flash drive that is the live installer.
BIOS is the purple screen & UEFI is a grub menu.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I am familiar with the Boot Menu screen and the Bios Menu screen. (Been to both far too often the last several weeks.)
By a process of elimination...my system only boots with the live dvd...to get me to the log-in screen. I just can't get beyond that to the desktop.

> **oldfred said:**
> If booting into your system and you only have one system installed, you do not get grub menu, but it just boots the one system installed. To get to grub menu with BIOS you have to hold shift key from BIOS until menu appears. With UEFI you usually use the escape key.

I get grub menu as my GRUB is messed up (missing files) thanks to my stupid mistake of deleting files when my Boot Volume Disc was 100% full.
My desktop is in Grub Rescue mode. But...if I can't boot into the desktop to fix grub...but there is a terminal on the log-in page I might be able to use,
how can I do anything to fix my boot? Clueless but thankful for everyone's help. Will check back in a few days as I have to walk away or I might
try again to do my own fix and be further in a mess.

---

### Post by sudodus on 2014-07-28
> **sewbiz said:**
> I can't select burn yet when the drawer is open and I select the icon ...I CAN select "burn to disc". It is pure frustration and insanity....WINDOWS. So this is my dillema. I will do my homework and look at the links you sent. I have already gone to many links "How to burn DVD/Windows" etc. but getting no where.

Thank you for your help though...I will get back to you in a few days. : (  Seems I am going in circles but maybe if I get the proper "BURN" we will have something.

There are tools for that purpose. You can use for example

[http://www.freeisoburner.com/](http://www.freeisoburner.com/)

[http://www.wikihow.com/Burn-an-ISO-File-on-Windows-7](http://www.wikihow.com/Burn-an-ISO-File-on-Windows-7)

---

### Post by sewbiz on 2014-07-30
> **sudodus said:**
> There are tools for that purpose. You can use for example

[http://www.freeisoburner.com/](http://www.freeisoburner.com/)

[http://www.wikihow.com/Burn-an-ISO-File-on-Windows-7](http://www.wikihow.com/Burn-an-ISO-File-on-Windows-7)

I did get Windows to Burn my file to disc...yet it did not work when I used it on my broken computer. The .iso file was ubuntu-12.04.4-dvd-amd64 but it seems to show up as something on my Windows 8 with an adobe reader avatar by it. It won't let me open it to see what is in it. 

> **sudodus said:**
>  				 				I think you can try to get your installed system running, which is probably Ubuntu 12.04 LTS) in the partition **/dev/sdb3**. We are (at least) three persons trying to help, and one of us might find the key, that will solve your problem.

 I suspect there are problems with the driver for graphics or wifi. That  is why I wanted to know what chips or cards you are have. Maybe you can  ask your son about that.

I will send my son an email. I will let you know if I hear anything. : (
Can I fix the problem whether or not I even have a graphics card or chip? Maybe this is why I could never use my webcam either.

Thank you for staying with me on this.

---

### Post by oldfred on 2014-07-30
If it is one large file, then it copied it not burned it as a bootable disk. You have to use tools to create a bootable disk which both extracts ISO and makes it bootable.

Windows by default does not show extensions. And since it may get things wrong, I always turned on extensions so I could really see what they are. Do not know how to do that with the newer Windows though.

You have some grahics chip or card, or else you screen would not work. 
What brand & model and we can look it up.

---

### Post by sewbiz on 2014-07-30
> **sudodus said:**
> 
 I suspect there are problems with the driver for graphics or wifi. That is why I wanted to know what chips or cards you are have. Maybe you can ask your son about that.

I got some info about mygraphics,sound,wifi are all built in to the motherboard...integrated.

From the [CODE] sudo lshw | less[CODE/]
4 series chipset DRAM Controller
width: 32 bits

4 series Integrated Graphics Contoller
Width: 64 bits

What other info do you need. I wrote down a ton of info.

Also....*firmware BIOS
capabilities: pci upgrade shadowing cdboot bootselect socket drom edd int13floppy 1200....etc.....etc....etc.
Let me know if this means anything.

> **sudodus said:**
> 
If you have or can get a USB pendrive, it is a good idea to make a ***USB boot drive*** and install from it. I think it is easier and more reliable unless the computer is very old. Your computer is 64-bit capable, so it should be new enough to manage booting from USB. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This never worked for me...the USB...I can make one but my broken computer won't see it in the order I want it to. Can't select this as an option on the boot menu.

---

### Post by sudodus on 2014-07-31
You are on the right track with

```
sudo lshw | less
```

I think you have Intel graphics, but I am not sure yet. Intel graphics is usually working, so that would be good news.

 Please find the corresponding piece of text, copy and paste all of it into reply (and put it within code tags)

This is from a computer with nvidia graphics
           ```
*-display
                description: VGA compatible controller
                product: GF108 [GeForce GT 430]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8
```
or from another computer with Intel graphics
```
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:c2000000-c23fffff memory:b0000000-bfffffff ioport:4000(size=64)

```

---

### Post by sewbiz on 2014-07-31
> **sudodus said:**
> You are on the right track with

```
sudo lshw | less
```

I think you have Intel graphics, but I am not sure yet. Intel graphics is usually working, so that would be good news.

 Please find the corresponding piece of text, copy and paste all of it into reply (and put it within code tags)


Mine has Intel graphics
```
        *-display-:0
             description: VGA compatible controller
             product:4 series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:f140(size=8)

```

Thank you again for your support!

---

### Post by sudodus on 2014-07-31
You have Intel graphics, and i think it should work in most computers with most linux operating systems. I don't know if it is very new (4 series Chipset)?

> 3. Click ENTER.....Ubuntu Log-In page opens 
4. Enter password....click enter.....up pops terminal...nothing else.

Is this when you boot from CD?

'Terminal', do you mean a text screen?

What prompt is there (text in the last line)? What commands are available?

Try the boot option **text**:

The Ubuntu family desktop install drives can use [boot options]("https://help.ubuntu.com/community/BootOptions") (for example **text**) and can be installed using the standard installers. 

After selecting language you arrive at the main menu of the installer. Click on F6 
At the boot menu screen the options are 

[LIST]
[*]Try Ubuntu without installing (in the desktop installer but not in the alternate installer] 
[*]Install 
[*]... 
[/LIST]
With the **Try Ubuntu** choice high-lighted press F6. (This option needs less RAM than installing from 'Try Ubuntu') 

A menu with a number of options appears. The option 'text' is not there, so press Escape to close the list. 

Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'text' to the string **after** the two dashes. 

... quiet splash -- textPress return, and the live system will be loaded. Now let us see, if it works in text mode. 

-o-

On another track: What happens when you boot from the internal hard disk drive? How far do you get, what is shown on the monitor? Also a text screen, or a graphical desktop environment?

If also a text screen: what prompt is there (text in the last line)? What commands are available?

---

### Post by sewbiz on 2014-08-01
> **sudodus said:**
> You have Intel graphics, and i think it should work in most computers with most linux operating systems. I don't know if it is very new (4 series Chipset)?



Is this when you boot from CD?

Yes, when I boot from the CD 
> **sudodus said:**
> 
'Terminal', do you mean a text screen?
I was assuming it was a terminal...looks like a small black screen in the upper left corner of the log-in page. It says"
cathy@bethe: $ and then a prompt thing.
> **sudodus said:**
> 
What prompt is there (text in the last line)? What commands are available?

The usual commands are available. I seem to not be limited like the FULL BLACK screen when I turn on the computer.
That is just a text screen and I am limited. This screen responds to any commands I give it like before when my system
was working...that is why I call it a terminal.

> **sudodus said:**
> Try the boot option **text**:

The Ubuntu family desktop install drives can use [boot options]("https://help.ubuntu.com/community/BootOptions") (for example **text**) and can be installed using the standard installers. 

After selecting language you arrive at the main menu of the installer. Click on F6 
At the boot menu screen the options are 

[LIST]
[*]Try Ubuntu without installing (in the desktop installer but not in the alternate installer] 
[*]Install 
[*]... 
[/LIST]
With the **Try Ubuntu** choice high-lighted press F6. (This option needs less RAM than installing from 'Try Ubuntu') 

A menu with a number of options appears. The option 'text' is not there, so press Escape to close the list. 

Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'text' to the string **after** the two dashes. 

... quiet splash -- textPress return, and the live system will be loaded. Now let us see, if it works in text mode. 

-o-

On another track: What happens when you boot from the internal hard disk drive? How far do you get, what is shown on the monitor? Also a text screen, or a graphical desktop environment?

If also a text screen: what prompt is there (text in the last line)? What commands are available?

I will look this over later and try what you suggest. I am babysitting (11 month old grandson) and he is waking up.
But...I learned something new today after posting in a forum on Windows...maybe this will solve everything....

Been trying to figure out why I could not "burn my .iso file to DVD".Here was my post.... [SIZE=4]**[Re: My CD-Rom won't burn .iso file to DVD-RW disc]("http://forums.toshiba.com/t5/Windows-8-8-1/My-CD-Rom-won-t-burn-iso-file-to-DVD-RW-disc/m-p/601554#M5506") **[/SIZE]
  
  Here is the answer......

 Sounds like you probably installed another burner that  stole the association. To fix that, set the default application for the  ISO file type to File Explorer (explorer.exe). Follow the instructions  here. (see link below) Maybe this will help someone else.

  

    I did this so I am going to try to now BURN all those .iso files to DVD and see if I finally get something working. I will be in touch!

Got to run...thank you so much but stand by please...appreciated!!!!
[URL="http://community.spiceworks.com/how_to/show/12394-how-to-re-enable-iso-mounting-in-windows-8-file-explorer"]How to re-enable ISO Mounting in Windows 8 File Explorer

[/URL]

---

### Post by sewbiz on 2014-08-01
> **sudodus said:**
> 

Try the boot option **text**:

The Ubuntu family desktop install drives can use [boot options]("https://help.ubuntu.com/community/BootOptions") (for example **text**) and can be installed using the standard installers. 

After selecting language you arrive at the main menu of the installer. Click on F6 
At the boot menu screen the options are 

[LIST]
[*]Try Ubuntu without installing (in the desktop installer but not in the alternate installer] 
[*]Install 
[*]... 
[/LIST]
With the **Try Ubuntu** choice high-lighted press F6. (This option needs less RAM than installing from 'Try Ubuntu') 

A menu with a number of options appears. The option 'text' is not there, so press Escape to close the list. 

Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'text' to the string **after** the two dashes. 

... quiet splash -- textPress return, and the live system will be loaded. Now let us see, if it works in text mode. 

I am not sure what to type in the terminal to the Ubuntu text you are talking about. I never see that anymore now that it is installed. It
does not give me that option when I turn on the computer...it just goes to Ubuntu log-in page...or if you mean hit a key as it is loading.
I will check into this later.


> **sudodus said:**
>  On another track: What happens when you boot from the internal hard disk drive? How far do you get, what is shown on the monitor? Also a text screen, or a graphical desktop environment?

If also a text screen: what prompt is there (text in the last line)? What commands are available?

If I boot from the internal hard disk I get the full black screen and it says "grub rescue>"  
It is limited to what commands it will know.  I can do ```
 l 
```...that is about it...can't remember but does
not understand sudo or anything much after that. Useless!

I am missing Grub files I deleted....   .mod files in the grub folder...etc. then my screen went BLACK.  : (

---

### Post by sudodus on 2014-08-01
> **sewbiz said:**
> I am not sure what to type in the terminal to the Ubuntu text you are talking about. I never see that anymore now that it is installed.
does not give me that option when I turn on the computer...it just goes to Ubuntu log-in page...or if you mean hit a key as it is loading.
I will check into this later.

I mean that you boot from CD again, then you get these boot options in a simple way and can do experiments, for example with the boot option **text **until you find something that works reasonably well. After that you can start working with the installed system.
> 
If I boot from the internal hard disk I get the full black screen and it says "grub rescue>"  
It is limited to what commands it will know.  I can do ```
 l 
```...that is about it...can't remember but does
not understand sudo or anything much after that. Useless!

I am missing Grub files I deleted....   .mod files in the grub folder...etc. then my screen went BLACK.  : (

You might be able to repair your installed system from a live system (booted from CD/DVD/USB). You can also backup important personal files (if there are such files in the computer now). Maybe it is easiest to re-install the system (easier than to find what is wrong, which files are missing and copy them back).

---

### Post by yancek on 2014-08-01
>  Maybe it is easiest to re-install the system (easier than to find what is wrong, which files are missing and copy them back). 		

From the OPs earlier posts, she mistakenly deleted all the .mod files from the /boot/grub directory rendering the system unbootable - because the icon for the .mod files looks like musical notes.  sdb1 is a boot partition which is where these files would need to be copied to.  Unfortunately, post 16 of this thread still shows that partition 100% full.  Partitiion 1 on sda is an Extended partition and four logical partitions plus a swap.  Hard to tell which is the / or /boot or if there is a boot partition on that drive.

I think it would be easier to reinstall if she can get a bootable medium.  Someone more familiar could probably copy all the .mod files back to /boot/grub.

---

### Post by oldfred on 2014-08-01
Having a separate /boot always makes it a bit more complex. And you have to maintain that by delete kernels regularlly (which you should do anyway). But once full it is difficult to houseclean as you cannot boot. And just deleting them puts them into root's trash and that can be difficult to houseclean, so partition remains full. 

If housecleaned to make room a full uninstall & reinstall of grub using Boot-Repair would work and is relatively easy.

But I have to agree that a new install at this point may be easier. But then good backups before erasing anything on system are also required. But those should be part of any users use of a system whether Ubuntu or Windows.

---

### Post by sewbiz on 2014-08-02
> **sudodus said:**
> 

Try the boot option **text**:

...Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'text' to the string **after** the two dashes. 

... quiet splash -- textPress return, and the live system will be loaded. Now let us see, if it works in text mode. 



Good news...hopefully. I made two dvd's "successfully BURNED!!! Now...hoping they are both the right .iso file.
Boot repair disc and Ubuntu-12.04.4-dvd-amd64.iso.

I got the screens up that I had to get to in your instructions above. One question though...do I type after the two
dashes the following?

```
text...quiet splash --text 
```

Thank you everyone for great work on this so far! I am finally feeling positive.

---

### Post by sewbiz on 2014-08-02
> **oldfred said:**
> Having a separate /boot always makes it a bit more complex. And you have to maintain that by delete kernels regularlly (which you should do anyway). But once full it is difficult to houseclean as you cannot boot. And just deleting them puts them into root's trash and that can be difficult to houseclean, so partition remains full. 

If housecleaned to make room a full uninstall & reinstall of grub using Boot-Repair would work and is relatively easy.

But I have to agree that a new install at this point may be easier. But then good backups before erasing anything on system are also required. But those should be part of any users use of a system whether Ubuntu or Windows.

Thank you oldfred...my son warned be about this when we first set things up. I should have called him to help me through removing kernals on my own but he is very unaccesible so being impatient I had to try things on my own. I was doing great until I started messing with the grub folder. I do understand now quiet well why things went south as they did. Maybe my experience in the school of hard knocks will help someone else one day. All is not lost...you learn more from mistakes that you make. I appreciate your help!!!  (READ POST 42...good news is coming.)

---

### Post by sewbiz on 2014-08-02
> **sewbiz said:**
> Good news...hopefully. I made two dvd's "successfully BURNED!!! Now...hoping they are both the right .iso file.
Boot repair disc and Ubuntu-12.04.4-dvd-amd64.iso.

I got the screens up that I had to get to in your instructions above. One question though...do I type after the two
dashes the following?

```
text...quiet splash --text 
```

Thank you everyone for great work on this so far! I am finally feeling positive.

Ok...this is what I typed after the two dashes```
text quiet splash --text
```

Success...it got me to this black screen (text screen) that says:

Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.11.0-15-generic x86_64)
*Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
ubuntu@ubuntu:~$_       (the cursor is blinking)

I will wait on your help for the next move. Thank you so much....ever grateful!

---

### Post by oldfred on 2014-08-02
You are in the live installer's command line.
Did you have to boot with text boot parameter or can you boot into the desktop gui?

Boot-Repair is not gui based, but text based.
You should be able to install it to live installer. Since it is just the live installer running in memory from DVD, you have to reinstall if you reboot.
Is Internet working as that is requried for Boot-Repair to work. If so you can add Boot-Repair.
You may need to boot in recovery mode or second boot option and choose the terminal with Internet access.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)


And if you can get into Boot-Repair run the advanced options and complete uninstall and reinstall of grub.
If still running the 11.04 version it may not work as that is very obsolete and repository is closed.

Have you all your data well backed up?

---

### Post by sudodus on 2014-08-03
> **sewbiz said:**
> Good news...hopefully. I made two dvd's "successfully BURNED!!! Now...hoping they are both the right .iso file.
Boot repair disc and Ubuntu-12.04.4-dvd-amd64.iso.

I got the screens up that I had to get to in your instructions above. One question though...do I type after the two
dashes the following?

```
text...quiet splash --text 
```

Thank you everyone for great work on this so far! I am finally feeling positive.

Almost correct, there should be a space between the dashes and the word text

```
text...quiet splash -- text 
```

***Edit***: Now we know that it works without the space too :-)

---

### Post by oldfred on 2014-08-03
You can also do this if you can get to install mode.

 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

You have to be sure not to tick the format box and choose same format as is current / (root) partition. All system files & settings are overwritten, but any data you have added should be preserved. Since settings will revert to default you may have to reconfigure any custom changes you made. And if you installed additional programs you will have to reinstall those.

---

### Post by sewbiz on 2014-08-03
I am totally illiterate, ignorant and clueless as to what to do next. What do I put in the command line so my program
can now be fixed (grub) and so it will boot to the hard drive, not dvd and actually OPEN my desktop?
I need everything idiot proof. I am still just a beginner. I will be patiently waiting some direction from the experts.

Should I just use my boot repair disc that is now correctly "BURNED" to my dvd and let it fix things for me? Is
that how it works? I just don't want to proceed using only a "guess" on my part because something is not clear.
I don't want to cause more damage. I am a bit shy at this point.

---

### Post by sudodus on 2014-08-03
1. Please start by answering oldfred's questions as detailed as possible! Read all his posts and try to reply to all of them. Right now you can start with post #45

 2. Try what he suggests and report the result!

Otherwise we don't know what is happening and can't give relevant help.

---

### Post by sewbiz on 2014-08-03
> **oldfred said:**
> You are in the live installer's command line.
Did you have to boot with text boot parameter or can you boot into the desktop gui?

I don't know what "text boot parameter" is?
I don't know what "deskto gui" is?
If you can please dumb down your replies I am happy to answer your questions. I feel I am going
in circles and answering questions repeatedly that have already been explained.

I put in the dvd that I just BURNED...the .iso file (12.04 LTS....) This is the first time it worked properly with me.
I set the computer to boot to dvd...which it did and I got the messages I described in post # 44

> **oldfred said:**
> 
Boot-Repair is not gui based, but text based.
You should be able to install it to live installer. Since it is just the live installer running in memory from DVD, you have to reinstall if you reboot.

This to me means I can install the boot repair then.

> **oldfred said:**
> 
Is Internet working as that is requried for Boot-Repair to work. If so you can add Boot-Repair.

If my internet were not working I would not be using this forum. My laptop is set up next to my "broken" system.

> **oldfred said:**
> 
You may need to boot in recovery mode or second boot option and choose the terminal with Internet access.

These suggestions mean nothing to me. I don't know what you are telling me to do. "Choose the terminal with the Internet access"????
I guess the following shows me what to type in the terminal in order to do this. If you get too technical I get lost. Sorry, not a tech wiz 
although most Linux users become quite computer savy...I am in the infantile stage.

> **oldfred said:**
> 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)


Why yannubuntu? I have Ubuntu. Is the command what I should use?

> **oldfred said:**
> 
And if you can get into Boot-Repair run the advanced options and complete uninstall and reinstall of grub.
If still running the 11.04 version it may not work as that is very obsolete and repository is closed.

So I assume I "select" these at some point (options you suggest)....complete uninstall...and reinstall of grub.
Guess I have work to do.

> **oldfred said:**
> Have you all your data well backed up? This again is a question answered in a 
previous post.

---

### Post by sewbiz on 2014-08-03
> **oldfred said:**
> You can also do this if you can get to install mode.

 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

You have to be sure not to tick the format box and choose same format as is current / (root) partition. All system files & settings are overwritten, but any data you have added should be preserved. Since settings will revert to default you may have to reconfigure any custom changes you made. And if you installed additional programs you will have to reinstall those.

The way you try to explain things to me is way over my head oldfred...too many things at once that you tell me to do. Not helpful. Sorry. 
Please idiot down your recommendations to me.
I have to do this using baby steps. I know you and sudodus are getting frustrated with me. I can't work on this daily, hourly or regularly...just
when I get a chance and I am as frustrated as you...also, learning how to properly enter codes on these text boxes...etc. I get yelled at a lot...still
learning but getting angry is not helpful. I do appreciate and will install boot repair and get back to you if I have any luck. I am sure you would
both like to close this post.

---

### Post by sudodus on 2014-08-03
I'll start replying, but I have to leave your most difficult issues for oldfred to take care of. So expect better explanations from him.

> > **oldfred said:**
> You are in the live installer's command line.
Did you have to boot with text boot parameter or can you boot into the desktop gui?
I don't know what "text boot parameter" is?

There can be many boot parameters, for example **nomodeset**. Now we are talking about **text** as in this example
```
...quiet splash -- text
```
> 
I don't know what "desktop gui" is?

It is when you don't have a text screen only, but a 'normal' screen where there are windows of programs, and there can be pictures, videos etc. GUI means 'graphical user interface'.
> 
If you can please dumb down your replies I am happy to answer your questions. I feel I am going
in circles and answering questions repeatedly that have already been explained.

As long as you are going in circles forwards and not backwards there is hope ;-)
> 
I put in the dvd that I just BURNED...the .iso file (12.04 LTS....) This is the first time it worked properly with me.
I set the computer to boot to dvd...which it did and I got the messages I described in post # 44

[COLOR=#006400][SIZE=4]OK, this is good.[/SIZE][/COLOR] :KS

Did you try also ***without*** adding that word 'text' (the boot option **text**)? If not please try and tell us the result!
> 
> **oldfred said:**
> 
Boot-Repair is not gui based, but text based.
You should be able to install it to live installer. Since it is just the  live installer running in memory from DVD, you have to reinstall if you  reboot.

This to me means I can install the boot repair then.

***Yes*** (but I thought Boot-repair is gui based).
> 
> **oldfred said:**
> 
Is Internet working as that is requried for Boot-Repair to work. If so you can add Boot-Repair.

If my internet were not working I would not be using this forum. My laptop is set up next to my "broken" system.

I think oldfred means if the*** computer with problems*** can connect to the internet.
> 
> **oldfred said:**
> 
You may need to boot in recovery mode or second boot option and choose the terminal with Internet access.

These suggestions mean nothing to me. I don't know what you are telling  me to do. "Choose the terminal with the Internet access"????
I guess the following shows me what to type in the terminal in order to  do this. If you get too technical I get lost. Sorry, not a tech wiz 
although most Linux users become quite computer savy...I am in the infantile stage.
 
At the grub menu, the top line is the standard choice. Then there are 'Advanced options' - select that, and you get a new menu, where you can select 'Recovery mode'.

If you do not get any grub menu, *directly when you boot*, press the left Shift key [in BIOS] or maybe the Escape key [in UEFI]
> 
> **oldfred said:**
> 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)


Why yannubuntu? I have Ubuntu. Is the command what I should use?

It is the user name of the guy who made Boot Repair.

And yes, write these commands exactly like they are line by line into a text screen or a terminal window. Finish each line with the Enter key.
> 
> **oldfred said:**
> 
And if you can get into Boot-Repair run the advanced options and complete uninstall and reinstall of grub.
If still running the 11.04 version it may not work as that is very obsolete and repository is closed.

So I assume I "select" these at some point (options you suggest)....complete uninstall...and reinstall of grub.
Guess I have work to do.

Yes
> 

> **oldfred said:**
> Have you all your data well backed up? This again is a question answered in a 
previous post.

Please tell us anyway, it is hard to find in this long thread. We don't want you to run risky commands without a good backup :-)

So if you don't have a good backup yet, we should focus on that now. It can be done in text mode.

---

### Post by oldfred on 2014-08-03
Is this from your broken system?
 ubuntu@ubuntu:~$

If so run each of these in the terminal.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)

The broken system needs Internet not your working system?
graphical user interface (GUI) is the point and click desktop where you use mouse to launch apps, but can open a terminal.
[http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)

---

### Post by sewbiz on 2014-08-03
> **sudodus said:**
> 

Did you try also ***without*** adding that word 'text' (the boot option **text**)? If not please try and tell us the result!

The only place I get....with the boot repair in the tray....is to the BOOT REPAIR Screen now and the log in page.
It wants a password and does not recognize mine. I am lost.

***The****** computer with problems*** may or may not be able to connect to the internet. I never get past the login page to get
me to the desktop. Before it went into grub rescue mode it could.

> **sudodus said:**
> At the grub menu, the top line is the standard choice. Then there are 'Advanced options' - select that, and you get a new menu, where you can select 'Recovery mode'.

If you do not get any grub menu, *directly when you boot*, press the left Shift key [in BIOS] or maybe the Escape key [in UEFI]
I remember this screen at one time weeks ago. When I get to recovery mode....then what?


> **sudodus said:**
> So if you don't have a good backup yet, we should focus on that now. It can be done in text mode.
I have a good back up. All I need saved to USB.

---

### Post by sudodus on 2014-08-03
Some more replies inline:
> 
> **sudodus said:**
> 

Did you try also ***without*** adding that word 'text' (the boot option **text**)? If not please try and tell us the result!

The only place I get....with the boot repair in the tray....is to the BOOT REPAIR Screen now and the log in page.
It wants a password and does not recognize mine. I am lost.

***Press Enter*** because I think it needs no password, if you are talking about the system booted from DVD.
> 
***The****** computer with problems*** may or may not be able to connect to the internet. I never get past the login page to get
me to the desktop. Before it went into grub rescue mode it could.

> **sudodus said:**
> At the grub menu, the top line is the standard  choice. Then there are 'Advanced options' - select that, and you get a  new menu, where you can select 'Recovery mode'.

If you do not get any grub menu, *directly when you boot*, press the left Shift key [in BIOS] or maybe the Escape key [in UEFI]
I remember this screen at one time weeks ago. When I get to recovery mode....then what?

[COLOR=#006400]*oldfred* wrote: > Is Internet working as that is requried for Boot-Repair to work. If so you can add Boot-Repair.
You may need to boot in recovery mode or second boot option and ***choose the terminal with Internet access***.[/COLOR]
> 
> **sudodus said:**
> So if you don't have a good backup yet, we  should focus on that now. It can be done in text mode.
I have a good back up. All I need saved to USB.


That's great :-) We need not worry about backup, so you start using Boot Repair.

---

### Post by yancek on 2014-08-03
In an earlier post, you indicated that you booted what you weren't sure was the DVD or the installed system.  You said that you saw a screen which had:  Welcome to Ubuntu 12.04...  at the top.  When I boot the Ubuntu 12.04 CD in text mode, that is what I see.  Below that is another line beginning with Documentation.... and below that is:  ubuntu@ubuntu~$.  If you see that you are using the DVD and not the installed system.

In another earlier post, you said you booted and what you saw for a prompt was:  cath@bethe~$.   That is a user name on your installed system so you can boot the DVD and were able (at least once) to boot to one of the installed systems.

One curious thing I saw on another post is that an Extended partition sda1 was set as boot?  You have 5 logical partitions on that drive one of which is swap.  I don't know what's on that drive.  Your second drive has the boot partition on sdb1 and the root filesystem on sdb3.  The sdb1 partition shows that it is 100% full so that must be the problem partition, the one you began deleting files from including the .mod files in grub.  There really isn't any reason to delete files from the grub directory.  They are all very small files and won't give you much space, usually 2-4kb.   As an example on my 12.04 installation, the entire grub directory is 4.2MB, the boot directory is 81.0MB.  The point of this is if you have a separate /boot partition, then deleting from the boot partition old kernels is the way to go.  The problem as stated by OldFred is having a separate /boot partition unless it is really large and they need to be bigger all the time.  And as you can see, deleting all the .mod files didn't make any difference as your boot directory after deleting them still shows 100% full.

I've never used Boot Repair so can't give you any advice on how to use that.  I'm not sure that it will do what you need, which is removing kernels/initrd files from your boot directory and also copying back all the .mod files deleted.

> When I get to recovery mode....then what?

When you see Recovery mode on the boot screen, use the down arrow on the keyboard to highlight it and hit the Enter key.  The purpose of this is just to see if it will boot and maybe boot to a graphical interface.  It seems pretty unusual that the Boot Repiar would ask for a password but, then again I've not used it.  Maybe someone else can explain that.

---

### Post by sewbiz on 2014-08-03
> **oldfred said:**
> Is this from your broken system?
 ubuntu@ubuntu:~$

yes...the ubuntu@ubuntu:~$ was from the broken system after I did something but now I could not tell you as
like sudodus said...this thread is getting too long. I fear you won't be able to help me. My son will be home
on Thursday and sure he may fix it in lickity split he is such a GEEK, yet, not so sure. Please don't give up on
me...I only have tonight and Wed. to fix it. Would love get get it up and running. STRESS!

> **oldfred said:**
> If so run each of these in the terminal.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)

I did this already...earlier.

> **oldfred said:**
> The broken system needs Internet not your working system?

You are not going to believe this but I have the internet and I have a desktop. While waiting for you the boot repair disc must have
worked. I put in my dvd with the 12.04.4 LTS on it and things opened up differently but I just ignored everything...then I got the
grub screen I think and it gave me choices but I let the time run out on the page that they had all the languages to choose...english
was already highlighted so I just ignored everything and then my desktop just appeared before my eyes...with my folders and all my stuff.
I clicked on the firefox icon and the internet opened. I remember telling the screen (before all this) to check my disk for repairs...all is well.

BUT.....now I come to choose install. Do I have enough room to just install for the time being alongside the other Ubuntu 11.04 and all my
other things? Can I remove 11.04 later and then fix anything else later if I install 12.04.4 LTS alongside? I can't believe I am IN....you will
be glad to be rid of me. Appreciate request for a bit more help if you are avail.

Can I create or resize partitions myself or choose multiple partitions for Ubuntu? (This is another option for the install.)  Eventually I will go 
to another flavor.

---

### Post by sewbiz on 2014-08-03
I think I won't try the third option....way over my head (create or resize partitions) for the install.

I am now erasing my entire hard drive and installing Ubuntu 12.04.4LTS so unless I have any more boot issues after this
THANK YOU SO VERY MUCH FOR ALL YOUR TIME AND HELP.

I hope one day I can do the same for another Ubuntu/Linux user.
It would be interesting to see the ratio of guys to gals because I think we both have a different way of
communicating and explaining things. Wonder if woman to woman would have been easier for me and
less frustrating for you. I have an IT "gal" when I was a Windows user and I understood her very well.

But....I AM GRATEFUL and it was worth the wait as I will always be a Linux user! Now hubby can have
his laptop back. Hope you don't have to hear from me again about "THIS ISSUE"!

---

### Post by sewbiz on 2014-08-03
NO FIX!!!
I guess it was too much to hope for. I am missing something.
I did a complete "erase my disc and install Ubuntu 12.04.4 LTS"...and no, my files were not in the folders I saw on the desktop icons. I do have
a backup of them though. They were empty folders before the install. Just looked like it on the desktop.
My system only boots with the DVD so how to make it boot to the hard disc or was it not really an install? I don't get it.
Without the disc I just get still the grub rescue text screen. : (

The disc keeps spinning, not sure what is going on...my programs come up when I click on them. Printer works when I try
to print a document (and it is NOT a wireless printer) which means my port works...so maybe my USB's  should. Yes,
my computer SEES my devices. So...maybe it is something I have to type into a terminal to make the system boot to
my hard drive. Is that the chroot thing I heard about in reading the "manual"? I have to do some research. I will get
back in a couple days.

---

### Post by oldfred on 2014-08-03
If booting from Live installer, reinstall boot repair and run the BootInfo report. Post the link it gives.

---

### Post by yancek on 2014-08-03
If you were finally able to boot the Ubuntu 12.04 on your hard drive, why did you erase the entire disk and reinstall, since you already had it installed?  Or am I mis-reading what you said and you were just able to boot the DVD finally.

Did you use the DVD and select to Erase disk and install?  Did it run to completion?  Did you get a message after the install telling you it was completed and to reboot?  
Did you accept all the defaults for the installation?  If the answers to all the above are yes, then it should be installed and you will need to change the boot priority in the BIOS to boot from whichever hard drive you installed to.  You had two identical drives so no one else will know which, try different options.  You will need to do this to boot from the hard drive.

---

### Post by sewbiz on 2014-08-06
> **yancek said:**
> If you were finally able to boot the Ubuntu 12.04 on your hard drive, why did you erase the entire disk and reinstall, since you already had it installed?

I erased the hard drive because I also had installed on it Ubuntu 11.04...also my son made it with many partitions should I ever want to use windows on it. It was just such a messed up disc I wanted to start FRESH. I only wanted 12.04.4 LTS on the hard drive. ALL MY files are backed up.

  > **yancek said:**
> Or am I mis-reading what you said and you were just able to boot the DVD finally.

Out of frustration...and many weeks of loss of work hours I need because of this computer problem I am having, I just thought this would be easier.
Not knowing what the H double hockey sticks I am doing and having to depend on so many helpful people in the Ubuntu community and relying on
the "manual" that is out there, sometimes I have to see what I can do to experiment and move forward in the meantime. This was my decision.


> **yancek said:**
> Did you use the DVD and select to Erase disk and install?  Did it run to completion?  Did you get a message after the install telling you it was completed and to reboot?  

Yes, I used the DVD and selected to just ERASE everything on my disc and reinstall. It installed to completion and it told me it was done and to reboot which is 
what I did....yet without the disc in the disc holder...does not boot to the harddrive. (My grub needs fixing...as I stupidly removed files I should not have when I got the warning message my boot volume disc was getting full....once it was 100% full, I started manually removing files...but did do some research first. I was getting positive results until I messed with the GRUB folder.) Here I am repeating myself again after weeks of posting.

> **yancek said:**
> 
Did you accept all the defaults for the installation?  If the answers to all the above are yes, then it should be installed and you will need to change the boot priority in the BIOS to boot from whichever hard drive you installed to.  You had two identical drives so no one else will know which, try different options.  You will need to do this to boot from the hard drive.

YEP...I have to change the boot priority in the BIOS! All you are saying is most likely CORRECT. I just need an IDIOT instruction how to do this from a terminal.
I need to know the commands. I will research when I get the chance. I can't sit at my computer all day and play with this as I have other obligations and appointmens so if I don't answer or reply right away don't get ticked off. I check every couple days what is my next move.

Thank you for your help. I do appreciate.

---

### Post by sewbiz on 2014-08-06
> **yancek said:**
> In an earlier post, you indicated that you booted what you weren't sure was the DVD or the installed system.  You said that you saw a screen which had:  Welcome to Ubuntu 12.04...  at the top.  When I boot the Ubuntu 12.04 CD in text mode, that is what I see.  Below that is another line beginning with Documentation.... and below that is:  ubuntu@ubuntu~$.  If you see that you are using the DVD and not the installed system.

In another earlier post, you said you booted and what you saw for a prompt was:  cath@bethe~$.   That is a user name on your installed system so you can boot the DVD and were able (at least once) to boot to one of the installed systems.

One curious thing I saw on another post is that an Extended partition sda1 was set as boot?  You have 5 logical partitions on that drive one of which is swap.  I don't know what's on that drive.  Your second drive has the boot partition on sdb1 and the root filesystem on sdb3.  The sdb1 partition shows that it is 100% full so that must be the problem partition, the one you began deleting files from including the .mod files in grub.  There really isn't any reason to delete files from the grub directory.  They are all very small files and won't give you much space, usually 2-4kb.   As an example on my 12.04 installation, the entire grub directory is 4.2MB, the boot directory is 81.0MB.  The point of this is if you have a separate /boot partition, then deleting from the boot partition old kernels is the way to go.  The problem as stated by OldFred is having a separate /boot partition unless it is really large and they need to be bigger all the time.  And as you can see, deleting all the .mod files didn't make any difference as your boot directory after deleting them still shows 100% full.

I've never used Boot Repair so can't give you any advice on how to use that.  I'm not sure that it will do what you need, which is removing kernels/initrd files from your boot directory and also copying back all the .mod files deleted.



When you see Recovery mode on the boot screen, use the down arrow on the keyboard to highlight it and hit the Enter key.  The purpose of this is just to see if it will boot and maybe boot to a graphical interface.  It seems pretty unusual that the Boot Repiar would ask for a password but, then again I've not used it.  Maybe someone else can explain that.

Hi Yancek,
Please don't look backwards too far in the posts...only two or three. It is not helpful for me. Things change every couple days as I am trying "SOMETIMES" on my own to fix this by reading the manual. Forgive me for being proactive moving toward my own solution as I understand it. I am not as advanced as the rest of you that are helping me.
I can't take the time to tell you what I did and what I saw and why I did it...unless it is something I did more recent.

---

### Post by oldfred on 2014-08-06
Sounds like we are starting all over again. 
It gets hard to fix issues when the issues keep changing. 

If the purpose of doing some different things is to learn that is great, but if just randomly doing things withour learning what to do or not do does not help in trying to solve issues.

You should be able to from BIOS or one time boot key choose what to boot. On my system BIOS is f2 and one time boot key showing what is available to boot is f12, but that varies by vendor.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

And if you now just have one system installed, it should boot automatically, grub will not appear unless you force it and it should boot.
If installed in BIOS mode, you can get to grub menu by holding shift key from BIOS start until menu appears. If UEFI you may need to press the escape key.
Can you get to grub menu?

---

### Post by sewbiz on 2014-08-06
> **oldfred said:**
> Sounds like we are starting all over again. 
It gets hard to fix issues when the issues keep changing. 

If the purpose of doing some different things is to learn that is great, but if just randomly doing things withour learning what to do or not do does not help in trying to solve issues.

You should be able to from BIOS or one time boot key choose what to boot. On my system BIOS is f2 and one time boot key showing what is available to boot is f12, but that varies by vendor.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)



I have BIOS not UEFI.
Seems because my GRUB is broken...I will never be able to boot to hard drive.
Also....it seems even though I think something went well...I am mistaken.
Without a live dvd in the drawer I continue to get grub rescue prompt on a black screen.
I can't make changes in BIOS.
When I get the boot menu screen up (F10) on my system I can change the boot order so the live dvd will boot.

I ran the boot repair disc again but never get to anything I could report. It too must not be working as I thought.
Got to fix GRUB. Should I now install Grub 2 to fix grub?

Going in circles because I have three people telling me things I don't fully understand. I am told to do something
but not where or explicitely how. Baby steps please. I do appreciate.
I fear this thread is getting too long and I will loose you. : (

> **oldfred said:**
> And if you now just have one system installed, it should boot  automatically, grub will not appear unless you force it and it should  boot.
If installed in BIOS mode, you can get to grub menu by holding shift key  from BIOS start until menu appears. If UEFI you may need to press the  escape key.
Can you get to grub menu?

When I am in Grub rescue and type ```
 l 
``` I see all the partitions I always had on my hard drive. I think I did not
erase my hard drive after all or I think I would see a change on it. When I was going to reinstall Ubuntu 12.04.4 LTS and erase my disc it
told me it was going to remove partitions. I am clueless what I now have on my computer that is broken.

I think this is why I have to fix GRUB.    ???????

---

### Post by sewbiz on 2014-08-06
Reminder....my grub is broken (files missing in grub).
Reminder...my boot volume disc is 100% full....maybe why I can't boot to it.

Should I do the chroot thing?
Should I try to fix grub.
Can't boot to hard disc drive.
System is in grub rescue still.

Boot repair dis does not fix anything.
System can get onto the internet.
All my files are backed up.

---

### Post by oldfred on 2014-08-06
From Live installer on broken system can you run Boot-Repair?
If you reboot you do have to reinstall it as live system does not save anything.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)



And do you get to screen shown that has recommend repair and create boot info report. Do not run repair.
Then click on create boot info summary.

---

### Post by sudodus on 2014-08-06
> **sewbiz said:**
> ...

Going in circles because I have three people telling me things I don't fully understand. I am told to do something
but not where or explicitely how. Baby steps please. I do appreciate.
I fear this thread is getting too long and I will loose you. : (
...

I will stay silent and not disturb the process unless you ask me directly :-)

---

### Post by sewbiz on 2014-08-07
> **oldfred said:**
> From Live installer on broken system can you run Boot-Repair?
If you reboot you do have to reinstall it as live system does not save anything.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)



And do you get to screen shown that has recommend repair and create boot info report. Do not run repair.
Then click on create boot info summary.

I only get the screen with the pic of the person jumping in the air. 
There is the title in the center of the screen that says Lubuntu (name of the developer I was told).
I have sat still and waited many minutes...if not hours leaving the screen alone while I multi-task on my other computer
yet nothing happens.

Yes....I always have to reinstall everything as you say....nothing gets saved.
My computer does not function without a live disc in it.

---

### Post by sewbiz on 2014-08-07
> **sudodus said:**
> I will stay silent and not disturb the process unless you ask me directly :-)

Appreciate your understanding.

---

### Post by sewbiz on 2014-08-25
My son built my computer. After weeks and weeks of trying to figure out why anything anyone told me of steps to take did not work, I found out why.
My home built computer had two hard drives but the one that I thought had the issues, was not the correct drive. Usually the A drive has all your system
files on it and the B dirve is your back-up. Mine was reversed for some reason. In another thread and another post, one person mentioned which drive
my files were on but it didn't connect with me what that had to do with anything, being new and not of full understanding.

STEP ONE.......know which hard drive the files are on that you want to fix. 
Because I now have all my files restored but on my A drive and newly installed Ubuntu 14.04-Trusty Tar, with the help of my son making sure the
partitions on the disc were set up correctly, I am now back up and running. I will mark this as solved and most of what all my good friends here
suggested should have "worked" for me but did not because only my hard drives were not set up initially in a typically set up order.

Thank you...I love being a Linux user!

THIS IS SOLVED but not finding where I am suppose to "add" that.

---

