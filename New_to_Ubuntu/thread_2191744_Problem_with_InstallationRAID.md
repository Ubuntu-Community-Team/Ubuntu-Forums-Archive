---
title: "Problem with Installation/RAID"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by kyle.mattson88 on 2013-12-04
Hello!

I'm very new to Ubuntu and have run into an issue during installation (Server 12.04.3). To keep things simple I'll give you a quick overview of what I'm looking to do. I will have 1 SSD and 4 HDD installed in my "server". Ideally, I'd like to Install only Ubuntu to the SSD and create a RAID 10 with the other 4 HDDs. I've attempted to run the installation via CD and Flash Drive, but after I finish configuring my partitions and am about to finish the installation, I get a prompt stating that there was an error during installation. Like I've stated, I'm very new to this, but am eager to learn more about Ubuntu, but seem to be at a wall right now. I've tried searching via Google/Youtube/ubuntu wiki, and did not find any solutions that I could find. If anyone could point me in the right direction, I would greatly appreciate it. If there is any additional information that you need to help provide an answer, let me know and I'll post it. I'll be keeping an active eye on this thread for the next hour or so.

Thank you in advance for any advice you may have for me!

---

### Post by andyfied on 2013-12-04
Hello and welcome to Ubuntu!

Does the prompt give any additional details? Are you just setting up the partitions on the SSD for now?

---

### Post by r-senior on 2013-12-04
Additional suggestion ...

Did you check the MD5 sum on your downloaded ISO? Or did you try and download again?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kyle.mattson88 on 2013-12-04
Thanks for the quick replies :D
@andy - I'm attempting to install the OS to the SSD and configure the RAID for the other 4 HDDs.
@rsenior - Verified the MD5. Downloaded multiple times and tried burning to a CD, a DVD, and a Pendrive.
Update: I believe I completed the installation, but immediately after reboot, prompted me to a blank screen with a blinking cursor in the upper left of the screen. Then my monitor fades and can no longer see the blinking cursor. I'm fairly certain I can attribute the fading part of it to the monitor. The remaining issue is that it did seem to finish the install, but is unable to boot. :(

Edit: I'm thinking that GRUB may not have been installed correctly? 
Hitting CTRL + ALT + F1 doesn't do anything either.

---

### Post by kyle.mattson88 on 2013-12-04
Well don't worry guys, got it figured out on my own. Thanks for the attempt.

---

### Post by r-senior on 2013-12-04
What was it? Somebody might search and end up in this thread at some point.

---

### Post by kyle.mattson88 on 2013-12-05
The Installation didn't play well with Integrated graphics for [COLOR=#444444][FONT=arial]NVIDIA GeForce 6150 Chipset. If other users happen across this, try adding a Video card and see if that resolves the issue. Worked out for me.[/FONT][/COLOR]

---

