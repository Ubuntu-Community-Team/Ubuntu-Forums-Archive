---
title: "Stops booting after update"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by AwaitingUserInput on 2012-07-06
Hi everyone - I decided to give Linux a try after being a Microsoft/Windows guy since forever. I had problems installing onto a partition residing on my RAID striped harddrive, so decided to try running off of a 16 GB USB drive that I bought just for running Ubuntu.

My main OS is Windows 7.

I downloaded the 64bit Ubuntu 12.04 CD ISO and burned a live CD, which works fine. From there, I had the installer partition and install Ubuntu onto my 16 GB USB drive. I arranged the boot order in the CMOS to go to "USB-HDD" first and Ubuntu fired right up. I got a boot menu asking me if I wanted to run Ubuntu, memtest, Ubuntu in safe mode, a couple other things, or Windows 7. So far so good.

Once I was up and running in Ubuntu, I installed about 4 or 5 applications, as well as clicked "install all updates." The update manager was telling me there were 236 updates or something like that.

Once the update manager finished, it said I needed to restart to finish installing the updates, so I told it to restart and the computer went straight into Windows 7 without giving me the option of booting Ubuntu.

One other interesting thing is it takes forever for Windows 7 to start now. It's almost as if Windows is trying to make sense of the file system on the USB drive before finally giving up and presenting me with the login screen.

This is actually the second time I have installed to this USB drive only to have it go south on me shortly after getting it set up. The first time, I don't know what triggered the problems. This time, I'm pretty sure it had something to do with me installing all those updates.

I've been hearing for years from my friends how superior linux OSes are, and would really like to give it a fair shot. Unfortunately, just getting it installed and running is proving to be a problem. Any suggestions? Any questions I can help answer if you need more info?

---

### Post by AwaitingUserInput on 2012-07-06
OK so I found a person having a similar problem on these forums and it was recommended to them to use Boot Repair. 

These are the directions I followed:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I did that, ran Boot Repair and unfortunately, the Boot Repair app started putting files on the hard drives that I use to run Windows. My mistake was I just accepted the default and told it to run the "recommended repair." I'm trying to segregate all my Ubuntu stuff and keep it confined to my USB stick and not mess with my Windows drives.

Now if I leave the USB stick in the computer and get to the Ubuntu boot manager, if I choose to go to Windows 7 I get an error that tells me, "Boot Manager is Missing. Press control-alt-delete to restart."

If I turn on the computer without having the USB drive inserted, it goes into Windows 7 no problem.

So now my question is, how do I undo the changes that Boot Repair did to my hard drives?

EDIT: If I followed this procedure, would I get rid of any Ubuntu remnants from my hard drives?
[http://suite101.com/article/undo-ubuntu-dualboot-for-vista-a73383](http://suite101.com/article/undo-ubuntu-dualboot-for-vista-a73383)

---

### Post by drs305 on 2012-07-06
Please run the boot info script from Boot Repair and post a link to it. That output should show us what is happening with your system.

---

### Post by AwaitingUserInput on 2012-07-06
> **drs305 said:**
> Please run the boot info script from Boot Repair and post a link to it. That output should show us what is happening with your system.

I happened to save the Boot Repair Log, which I think is what you are looking for. I will try to attach it to this message.

Some explanation:
I have 2 RAID arrays controlled by the mother board.

One  is called "Striped" which is 2x320 GB hard drives in a striped array and where I installed Windows 7, my applications and so forth.

The other RAID array is a RAID mirror, and where I keep all my data. That array is called "Data" and consists of two mirrored 2TB hard drives.

Please let me know if it would be helpful to supply any more info, and thank you for the help.

---

### Post by drs305 on 2012-07-06
Thanks for posting the file. I don't use RAID so we'll have to wait for someone who does to interpret the information you provided. Hopefully such a helper will come across your thread soon.

---

