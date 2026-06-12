---
title: "Power Supply Failed"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by Rich42 on 2012-05-22
Have Dell 2400 Dimension PC 1Gb Ram OS Ubuntu 11.10 

Fitted with Graphic card Verto nVidia GeForce 6200 256MB DDR2 PCI DVI VGA TV-Out  

The PSU failed I presume.

1/  PSU shutdown without warning I was using the net the time.

PSU green power light was pulsing amber.

2/ Tried restart, which failed 1st & 2nd time. After 1 hour tried again, booted up in safe mode (I think) Ran Memory test as this was one of the options. PC failed after about 30 mins.

3/ Replaced 1Gb Ram. same thing happen.

4/ Replaced PSU. PC started but have Errors.
One of which was /dev/sda1: UNEXPECTED INCONSISTENCY;

5/ PC screen said RUN fsck MANUALLY

6/ I did a number of things but can't remember all.
PC seam to be working.

Please advise if there is anything I should DO or Check.

thanks
Richard

---

### Post by ammofreak on 2012-05-22
Hi ):P

When you turn on the computer do you hear any beeps. If so, how many?

Also: did you run fsck? I would use something like: fsck -a /dev/sda1.

PS: I hope you have backups...

---

### Post by Rich42 on 2012-05-22
No noise or bleeps were heard.

Sorry not sure exactly what I did, but did run repair option when in safe mode.

There were a number of things going on the screen, did say that there some errors were found and that some fix had been done.

I tried to write it all down, but screen changed before I could, sorry.

And it is working now, I am typing this on it now.


I did not run fsck as far as remember. Should I?

Thanks for quick response

Richard

---

### Post by Rich42 on 2012-05-22
Here is some of what wrote:-

[38.094918] Adding swap on /dev/sda5. Priority:-extent: 1 across 1461876k

fsck from util-linux 2.19.1
/dev/sda1:Inodes that were part of a corrupted orphan link list found.

/dev/sda1:UNEXPECTED INCONSISTENCY;
Run fsck MANUALLY
(i.e., without  -a or -p options)

mountall:fsck/[394] terminated with..............

That all I wrote them screen changed

---

### Post by buzzingrobot on 2012-05-22
If the power supply had completely fried, you would not have been able to do anything, of course. The fact that you could start up after an hour suggests you might, perhaps, have an overheating problem. In any case, you need to find out what that amber light means.

Fsck checks for and repairs file system inconsistencies.  These are often caused by an improper shutdown, which is what you had. Ubuntu runs it by default when the system boots, but it seems to be telling you to also run fsck manually, which you ought to do.

[EDIT:  Oops.  Just noticed you replaced the FSU. The fsck should get you back to normal (fingers crossed).

---

### Post by Dave_in_MD on 2012-05-22
> **buzzingrobot said:**
>  The fact that you could start up after an hour suggests you might, perhaps, have an overheating problem. In any case, you need to find out what that amber light means.

[EDIT:  Oops.  Just noticed you replaced the FSU. The fsck should get you back to normal (fingers crossed).

Amber on a Dell is indicative of motherboard or memory failure.  It didn't POST and generally the fans go to full speed.  I concur with the heat diagnosis check all fans, power supply, CPU, video card and case as populated.  Also check that the fins on the CPU heat-sink are not clogged.

---

### Post by kieferonline on 2012-05-22
Could it be that your system is overheating? Have you been doing any overclocking? Do you have any special program that controls fan speed? If the computer starts fine after a good rest, maybe it's because it cooled down--just a thought. Excessive dust could be a factor too.

---

### Post by Rich42 on 2012-05-23
All the fans (2 in OLD PSU) (presume faulty) run at constant speed and I not notice any change.

No over-clocking or any games have been ever used on this PC.

I had only be running the PC for about 30 min when it failed. The day before it was running at least 2 hours and no problem.

All fans and fins are clean, they were cleaned only a few weeks ago.

Since the PSU has been changed not problem has occurred. 

Note before PSU the RAM was also changed

I am the a retried TV engineer, so I have worked with electronics for over 50 years.

I think that it could be a overheating in the PSU or an intermitant fault open circuit (O/C) or short circuit (S/C) in PSU.

---

### Post by Rich42 on 2012-05-23
Please advise How-To run fsck Manually

I assume in terminal, it said on screen to

Run fsck MANUALLY
(i.e., without -a or -p options)

Do I have to add anything?

Thanks again for your help

Richard :confused:

---

### Post by oldfred on 2012-05-23
Run e2fsck on all Linux ext formated partitions.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s)
# to see format and partitions:
sudo blkid -o list

#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

