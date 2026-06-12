---
title: "Computer Shuts Off"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by nofacts on 2013-04-10
I have ubuntu 12.04 LTS

At sporadic times, my computer just shuts off - no warning.

It first happened after I installed and was using Handbrake. I tried using Handbrake a few times and it always shut down while it was running and never shut down at any other time.

I stopped using Handbrake.

Things were fine for a month or so, and then it started shutting down with no correspondence (that I can determine) to what I am doing. I can be typing a Libre Office document or an email and in an instant the screen is black and the computer off.

I got a new UPS thinking that might be the problem, but it does the same thing with the new UPS.

The next thing that comes to mind is the power supply, but before I start down the road of buying a new power supply and finding out that's not the problem, can anyone think of a way for me to troubleshoot the issue to determine the cause?

Thanks for the help.

---

### Post by blackbird34 on 2013-04-10
Is the computer getting too hot? or full of dust?

---

### Post by Derxst on 2013-04-10
Also, running a memory test wouldn't be a bad idea!

---

### Post by nerdtron on 2013-04-10
From your description, I think your computer might be overheating. If a computer reaches a certain temperature, it would automatically shut itself off to protect the internal components. As blackbird34 says, check your computer internal, maybe the fans or grill are full of dust. This may be a good time to clean them up.

---

### Post by nofacts on 2013-04-10
Thank you all for the ideas.

I removed dust a month ago so I don't think that's it, but will check. It's been in the 60's and 70's inside during this time, and I've had the side of the case cracked, but I will take the side completely off and make sure good airflow and see if it happens again.

I've found the instructions for doing the memory test and will also try that.

Thanks again.

---

### Post by nerdtron on 2013-04-11
> **nofacts said:**
> 

I've found the instructions for doing the memory test and will also try that.

Thanks again.

Reboot the computer and hold down the Shift key to pause at the GRUB bootloader choices. Choose the memtest option and press Enter.

---

### Post by Paqman on 2013-04-11
> **nofacts said:**
> 
I removed dust a month ago so I don't think that's it

Check all your fans are running, if you've been inside the case it's quite easy to dislodge a cable and have one of your fans stop. I did it myself a couple of weeks ago.

---

### Post by nofacts on 2013-04-11
All fans running. I did notice under the fan for the CPU there was dust on the paper accordion looking deal - heat disperser maybe - portions that were hard to reach due to the plastic fan on top. I worry about making things worse if I go 'too deep' but got what I could with dust lizard and then ventured forth with the duster spray can. Didn't relax until computer powered back on. So that is encouraging - I found some dust. Never know when the power off will occur so can't conclusively say it is is fixed.  Will see.

Nerdtron, I think you were speed-reading, maybe. I said I *did* find the instructions for doing the memory test, which were the same you've stated above. However, I tried it when I first powered the computer back on and did not get any GRUB. Just came up with the logon screen. Is it something that is supposed to happen after logon screen?

---

### Post by ppjdee on 2013-04-11
You have to be quick when it reboots, so it may take a few tries.

---

### Post by nofacts on 2013-04-11
I have ruled out dust as the problem. 

No luck with GRUB even if I hold down the shift key from before I power on until the logon screen. 

I assumed GRUB was part of the install, but when I went to see what version I have with
grub - install -v
i got the message
grub is currently not installed.

Does it need to be installed as an add-on to ubuntu? Will it overwrite or interfere with something if I install it?
thanks ...

---

### Post by jimafternoon on 2013-04-12
I had the same issue before. Boot Repair fixed it for me, maybe it can help you as well. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nofacts on 2013-04-12
You are talking about using Boot-Repair to get access to GRUB to test memory? It looks a little involved and dose say on one line it can make things worse. Is there an advantage to using Boot-Repair over command line install?

In case it matters - I don't have any other operating system on this computer - just ubunutu.

---

### Post by jimafternoon on 2013-04-12
Yes, I had the same issue as you (broken grub) and used Boot Repair to fix it, 

Boot repair couldnt be much easier....just open it and select the "recommended repair" button, and that's it.

---

### Post by nofacts on 2013-04-12
Nothing panning out so far.
Downloaded iso for boot-repair and created the disk.
Booted from it. It had a memory test - memtest86 V4.10 - ran for 2 hours, said everything ok - no failures.
Then ran the boot repair - it mentioned it was installing grub and said all went well.
When I logged back on, display colors had changed. They stayed changed for a couple minutes and then when I moved a window it went back to my usual colors.
I did the 'grub -install -v' again and it says the same thing it said before - that it is currently not installed.

So, I've ruled out memory as the problem but added more questions to the question of why my computer is shutting down.

Should grub have been installed when I installed ubuntu or is it an add-on?
Does the fact that I only have ubuntu and not multiple operating systems influence it showing up?
Could it actually be there and something is wrong with my command to see the version - it's telling me it's not there when it really is? But it doesn't show up when I hold down shift so I don't think it is there. Along with the message comes the suggestion to install it - was there a reason to use boot-repair to install it rather than installing it from the command line - e.g., do you have to not be running from the hard disk when you install?
Colors changing - could that be related to running the boot repair or is it just coincidence and this is first signal video card going south. Could video card be causing the system to power down?

The log from boot-repair is [http://paste2.org/PJH4MGVA](http://paste2.org/PJH4MGVA). It mentions 
fdisk and the boot sector having different locations for the start of sda1 – not sure what to make of that. It also says to have the bios boot on the 750GB disk. I checked the BIOS and the 750 disk is listed as first in boot order. In BIOS, disks look like:
 Ch1 M 750 one (has the OS on it)
 Ch 0 S extra disk
 
Thanks again for the help ...

---

### Post by zrdc28 on 2013-04-12
When you install ubuntu it will automatically write grub to the mbr for you! You can try "update grub" and see what that does it might 
solve your problems.

---

### Post by nofacts on 2013-04-15
"update grub" gives update: command not found.

But I think I will start a separate thread with all the additional questions that have come up with trying to follow suggestions.

Getting back to the original problem of the computer shutting off, suggestions were dust, heat, and memory. I've eliminated all 3 as possibilities. Next?

---

### Post by Nr90 on 2013-04-15
overclock/volt settings?

Can you run a live CD for a while and see if the problem still occurs?

---

### Post by deadflowr on 2013-04-15
My first thought on any time a computer suddenly shut off is loose heatsink.

A normal heatsink will have four brackets securely tight to the cpu, if any of those loosen up then it takes that much less heat away from the core.

---

### Post by Paqman on 2013-04-15
Could be any number of things, blown caps on mobo, dying power supply, etc, etc. I like the suggestion of running from the Live disk/USB for a while to try and conclusively rule out anything on the software side.

---

### Post by nofacts on 2013-04-15
Heat sink secure, but good thought.

Yes, I like the idea of running from the live CD also. Will do that.

---

### Post by Cheesehead on 2013-04-15
After booting from a sudden shutdown, look at logfiles: /var/log/dmesg and /var/log/syslog for clues. Since booting includes a lot of logging, you'll need to browse by the timestamps.
Post the couple minutes before shutdown here. (not the whole file, please)
If you're not sure how to do that, then attach (not paste) both files here.

---

### Post by gifford on 2013-04-15
The command is sudo update-grub.

---

### Post by zrdc28 on 2013-04-15
have you tried installing jupiter and using it cut back the cpu?

---

### Post by nerdtron on 2013-04-15
> **zrdc28 said:**
> have you tried installing jupiter and using it cut back the cpu?

I think the OP uses a dekstop. I don't think he will solve the issue by throttling his CPU. Using a desktop because of its powerful CPU is the whole point of using a desktop. Besides, he says the heatsink is fitted properly and the fans are working. That's enough to cool it off.

There is something there, hardware or software that is making the computer shut off randomly. We need to isolate the possibilities.

---

### Post by nofacts on 2013-04-17
Cheesehead, next shutoff I will look at those files.
gifford, it was the dash I was missing - thanks.

Will try to not be too confusing with too many side-paths. Slow getting back as had pipe burst in wall - right near computer of course - dryers had it too hot in most of the house, etc. Now the computer is in a room with its own AC and is plenty cool.

Back to business, I tried the live-cd, but the problem with that is I don't have access to email and all the extra programs I set up, so it ran but nothing much for me to do to put it through its normal paces. It ran for a few hours with no shutdown, but then that is not unusual. There is no consistency of time running and the shutdown.

Reboot after live-cd got a screenful of IO errors and I thought well ok, it's hardware, but then it booted up fine and has been running for a couple hours so far. I had the CD out before I hit restart, but maybe the switch from CD boot to hard drive boot somehow confused things.

This did make me wonder - is there a program that will do a direct copy of my hard drive to another hard drive or DVD to hard drive that will boot and run the same as the current drive, should it turn out that the drive crashes? 

In the meantime I'm waiting for the shutdown so I can look at those files, and backing up every time I change a file.

---

