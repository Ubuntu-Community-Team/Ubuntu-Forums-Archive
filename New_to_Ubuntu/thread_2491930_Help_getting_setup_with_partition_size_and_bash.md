---
title: "Help getting setup with partition size and bash"
date: 2023-10-25
forum: New to Ubuntu
---

### Post by bertha999 on 2023-10-25
Hi guys,

I've installed 22.04 as a duel boot, however on boot up the GNOME display manager fails to start and I think it's because the partition doesn't have enough space. If I log in using the advance start up options and repair and clean the disk, I can get in, but next time it fails again.

So, I've then tried to boot up using the boot disk with the goal of increasing the partition size by using the "try Ubuntu" feature, however, when I select the USB stick in the BIOS, I'm taken through to a limited version of bash and I don't seem to have anything in there.

I've looked through the drives (?) in the minimal bash I get, but I don't see linux or vmlinuz in any of the drives which list as hd0, hd0,gpt1, hd0,gpt2, hd0,gpt3 and hd0,gpt4 - there is also a bunch of hd1, but they seem to be related to windows.

I've then tried to find the partitions on Windows, but I can't, so I'm kind of stuck. I can't get into Ubuntu through the test version, can't find the partition via Windows or DOS and not sure what to do.

I'm running a Dell XPS 15 if that helps?

Thanks in advance :)

---

### Post by Bashing-om on 2023-10-25
Hello bertha999

Anew experience can be daunting - to say the least.

1)> 
 I think it's because the partition doesn't have enough space.


Let's not think but *KNOW* :D
In the installed operating system from terminal (crl+alt+t} run commands:
```

df -h
sudo fdisk -lu

```
where sudo requires your user's password - enter the pass word blindly as there is no response to the display when the PW is entered.
Show us the results here pasted between code tags - that retains formating:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

2) ouch - corrrupted medium ? Not likely as you have an install
> 
 however, when I select the USB stick in the BIOS, I'm taken through to a limited version of bash

Start the find-out process -
Boot the liveUSB;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> Here should be "check disk for defects" All good ?
else what next to check

3)
> 
find the partitions on Windows

Unless you have the tools installed on Windows - Windows will not see the Linux partitions. The above "fdisk" command will tell us the tale.

[INDENT]look, there are solutions
[/INDENT]

---

### Post by bertha999 on 2023-10-25
Thanks for the help.

Starting with point 2, unfortunately I can't get there - from the BIOS, as soon as I click on the USB boot it goes to the limited Bash screen and sudo isn't one of the commands I can use

However, if boot up the advance features I can get to a terminal and can run the commands from point 1 - see attached

So I can't get to the purple slash screen at all at this stage - I can format my USB and download Ubuntu again and try and boot back in to see if that works, but I'm kind of stuck as I've failed to login at all now.

Any thoughts?

---

### Post by Bashing-om on 2023-10-25
bertha999 - uh huh
"df" confirms what you thought - 100% used ... and Somethings taking up 62 Gigs ! Wow !!

Next up then is to find out what is taking up all the disk space and WHY.
As long as you are able to boot to a terminal in the install we can proceed.
In terminal run:
```

cd /
sudo du -sx * | sort -n

```
Here we go looking for what is hogging all your disk space.

[INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT]

---

### Post by bertha999 on 2023-10-26
Thanks Bashing-om, I've added a couple more pics, the first one is the result from the command you gave me and the second one is from me messing with your command which I think has given me a list of the smallest to largest files (because I saw that the "usr" folder was so large versus the other folders/files.

I should say, I've only just put Ubuntu on my machine in the last day or so and haven't yet installed any software, expect for Slack, that was in addition to what comes in 22.04.

---

### Post by Bashing-om on 2023-10-26
bertha999; Hey --

It is the /var/ directory that is so huge ! Is There an app that is running amuck and spamming the log file(s) ??

Go a step deeper and have a look/
```

cd var/
sudo du -sx * | sort -n

```

[INDENT]prepare to get ready to do some reading
[/INDENT]

---

### Post by Rubi1200 on 2023-10-26
Can you please copy/paste the terminal output and not use screenshots. It is hard for us to analyze like this.

When you reply, choose Go Advanced paste the output and then use # tags around the text.

It will make life easier for everyone and is a good way to also learn how to select terminal output.

Thanks!

---

### Post by bertha999 on 2023-10-26
Hey [COLOR=#000000]Bashing-om, haha, I thought that was the sum total of size and didn't even look at it :)

See attached the results, looks like the log files :([/COLOR]

---

### Post by bertha999 on 2023-10-26
I would if I could, they're not screen shots, they're photo's of the screen - I'm not in Ubuntu because it fails to boot up, I'm accessing the terminal through the Linux recovery and going into the terminal from there. Once I run the command I'm having to take a pic of the screen, reboot and then log into my Windows OS and add them to the forum.

---

### Post by yancek on 2023-10-26
Some serious problem with software as mentioned above which is creating massive log files.  One of your images above shows /dev/nvme0n1p7 is 65GB is size and contains 62GB of data.  This exceeds the allowed limit.  A Linux filesystem will have problems booting when it gets close to 95% full which your system has.

What are you using to try to access the system installed?  You indicate that you just installed Ubuntu, are you using the Ubuntu install media?  Do you have it set to first boot priority in the BIOS.  Not sure why you would be having problems booting it is it is the same USB you used to install?

Since you seem to be able to get to a terminal, go to the /var/log directory and delete log files.  You need to first create a mount point on the 'live' USB then mount the partition and navigate to the /var/log directory and delete files.  When booted to the 'live' Ubuntu USB, open a terminal and run:  sudo mount  /dev/nvme0n1p7 /mnt
Then change to the correct directory with:  cd /var/log and proceed to remove files with the rm command.  Need to use sudo to do this.  Make note of and report and errors or problems you have.

Just an FYI, 65GB is large enough.  My 20.04 I have had installed for over 3 years is 47GB and is less that 40% used.  Your problem is not the size of the partition it is some software that is incorrectly installed/configured which is creating these massive log files.

---

### Post by bertha999 on 2023-10-26
> **yancek said:**
> Some serious problem with software as mentioned above which is creating massive log files.  One of your images above shows /dev/nvme0n1p7 is 65GB is size and contains 62GB of data.  This exceeds the allowed limit.  A Linux filesystem will have problems booting when it gets close to 95% full which your system has.

What are you using to try to access the system installed?  You indicate that you just installed Ubuntu, are you using the Ubuntu install media?  Do you have it set to first boot priority in the BIOS.  Not sure why you would be having problems booting it is it is the same USB you used to install?

Since you seem to be able to get to a terminal, go to the /var/log directory and delete log files.  You need to first create a mount point on the 'live' USB then mount the partition and navigate to the /var/log directory and delete files.  When booted to the 'live' Ubuntu USB, open a terminal and run:  sudo mount  /dev/nvme0n1p7 /mnt
Then change to the correct directory with:  cd /var/log and proceed to remove files with the rm command.  Need to use sudo to do this.  Make note of and report and errors or problems you have.

Just an FYI, 65GB is large enough.  My 20.04 I have had installed for over 3 years is 47GB and is less that 40% used.  Your problem is not the size of the partition it is some software that is incorrectly installed/configured which is creating these massive log files.


Hey Yancek, yeah, it USB boot drive that I used to install Ubuntu 22.04 that I was using again so I'm not sure what was happening.

The way I was getting to the terminal was to go into recovery mode and there's an option for dropping the shell to the root (I'm new to Linux so that might not be an exact quote) - so I got access to the terminal without having to enter in any password security which also feels like a vulnerability, but anyways.....

I think I have it solved, for the time being at least.

What I did was;

cd /var/log
sudo sh -c 'echo > /var/log/syslog'

I then installed logrotate - although saying that, it could well of been there already. I then rebooted from the terminal and bang, I'm back in.

I checked the size of the files on the drive and everything was good and the log folder was reduced right down.

Lastly, I checked the updates and there was a Dell BIOS update that I've just flashed and I'll monitor it from here. Fingers crossed it's all good!

Thanks everyone for the help!

---

### Post by yancek on 2023-10-26
> I got access to the terminal without having to enter in any password  security which also feels like a vulnerability, but anyways..... 

That is standard and expected behavior if someone has physical access to a computer.  I don't do encryption but I imagine if the system on your hard drive was encrypted, you would need a password.  If a 'live' Linux system had a password, it would be available to anyone.  The iso files are downloaded by thousands of people and there can't be a separate password for each download.  A 'live' system is read only and creating a password when using it would not help as it could not be saved.  Don't let anyone have physical access.

---

