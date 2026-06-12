---
title: "Gateway MC7801u laptop hibernate/start-up issues"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Stargazer989 on 2008-12-01
(Ubuntu 8.10, Intrepid Ibex)
Every time I boot up from hibernate or start up from shut down, it says boot fail and then starts back up a second time, successfully booting that time. well this time i'm running in low graphics mode. i really want to use the hibernate function. i have the swap space (4.8gB(bigger than it should be but i have the space)) so swap shouldn't be the problem.

any ideas ?

[My Laptop]("http://www.gateway.com/systems/product/529668195.php")

please and thank you.

---

### Post by Stargazer989 on 2008-12-01
i've googled but found no solutions to this problem. seems it too new to be widely found.

---

### Post by Stargazer989 on 2008-12-03
24-hour rule, right ?

*bump*
*bump*
*bump*

---

### Post by Stargazer989 on 2008-12-25
out of my time using ubuntu i don't think i have had to restart or hard shutdown ubuntu this many times... my desktop faired better than this.

i can't be using this laptop knowing that it may just seize up and sputter out on me.

I am using Ubuntu 8.10 64bit.

any **answers** ?

---

### Post by Stargazer989 on 2008-12-26
*bump*
*bump*
*bump*

:(

i may start trying other Linux Distros... i don't want to though. <3 ubuntu and how it works. i'm none too thrilled with how most other Distros restrict so much stuff. i really don't want to switch. :(

---

### Post by scandido on 2008-12-26
I would guess it's not an issue with hibernate specifically as it is occurring on all of your start-ups. I would look at the logs from your start-up and see if there are any obvious errors. You can do this by typing "dmesg" at the command prompt or "dmesg &> bootup" to put the output into a text file. If you do not see anything unusual or are unable to tell if there is anything unusual (I probably wouldn't be able to find anything unless it is obvious), post the output of that log in this thread and perhaps someone more knowledgeable will be able to diagnose the problem.

---

### Post by Stargazer989 on 2008-12-26
couldn't attach the bootup copy... so here: [bootup.txt]("http://adam.pcriot.com/r/bootup.txt")

can this help the freezes DURING usage ? or is there a command that could log errors from <program.name.here> and actively log it so that when a crash/freeze comes along i could find out ?

***EDIT: this is fresh-install bootup... sorry. i was going to return the laptop but the <:D><:D> manager said no. so, um, i'm updating now and i will get a copy of bootup after a crash/freeze.

---

### Post by Stargazer989 on 2008-12-26
i found a couple of errors:

> [   13.789063] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.SMRD] (Node ffff88013fa39c00), AE_TIME
[   13.789173] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT1.UPBI] (Node ffff88013fa3b900), AE_TIME
[   13.789240] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT1._BIF] (Node ffff88013fa3b8c0), AE_TIME
this was after i restarted (after i updated...)
so far i haven't been able to get in normal mode... always Low-graphics mode.

---

### Post by Stargazer989 on 2008-12-27
ok... so i've gone to sleep and woken and turned on the laptop... seems the above error is there as well. either that or i'm reading the same file *deletes file* ... nope, that error is there now for 2 boot ups. any solutions or is this even a notable error ?

---

### Post by scandido on 2008-12-27
Sorry, I can't comment on the specific messages in your logs. (I'm just not knowledgeable enough.) However, regarding your question about usage logs, this page explains what logs are available

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Also, if you launch an application from the terminal, it will often report back status to the terminal window. This might help you diagnosing problems with a particular program.

Good luck.

---

### Post by Stargazer989 on 2008-12-27
um, since i did a fresh-install all seems calm so far... but the resolution isn't top... it's still low-gfx. i'm supposed to be seeing 1366x768 but i am only looking at 1024x768. :(

just did a reboot... ubuntu booted cleanly.. going to install my programs and i'll update this read as things happen.

thanks.


~stargazer989

---

### Post by Stargazer989 on 2008-12-27
i may have spoken too soon... only about an hour after i made that last edit on that last post... ubuntu decided to seize up. :( i think it's because i inserted my flash drive, it has that u3 thing on it.

---

### Post by Stargazer989 on 2008-12-27
i've been asking for help in General help for nearly as long as i've had the laptop(about a month)... [http://ubuntuforums.org/showthread.php?t=999255]("http://ubuntuforums.org/showthread.php?t=999255") i am using 64bit but i don't know if it's AMD. it's most likely Intel.

anyone have an answer ? i've been facing this for some time now. :(

on an unrelated side-note... is there a program where i can watch which way my data is going/coming from ? like if i were uploading, i would want to know which program is uploading and if i were downloading what program or what the IP is from where i'm downloading.

---

### Post by p_quarles on 2008-12-28
> **Stargazer989 said:**
> i've been asking for help in General help for nearly as long as i've had the laptop(about a month)... [http://ubuntuforums.org/showthread.php?t=999255]("http://ubuntuforums.org/showthread.php?t=999255") i am using 64bit but i don't know if it's AMD. it's most likely Intel.

anyone have an answer ? i've been facing this for some time now. :(

on an unrelated side-note... is there a program where i can watch which way my data is going/coming from ? like if i were uploading, i would want to know which program is uploading and if i were downloading what program or what the IP is from where i'm downloading.
Threads merged, as it just makes it difficult to track problems when the same topic is spread among several threads. 

Btw, Intel 64 bit and AMD 64 bit architectures are, for the desktop market, the same.

---

### Post by Stargazer989 on 2008-12-28
could you move this to Absolute Beginners ? i think there are more advanced ubuntu techies there helping people than in General Help. :)

please and thank you, in advance.

---

### Post by p_quarles on 2008-12-28
> **Stargazer989 said:**
> could you move this to Absolute Beginners ? i think there are more advanced ubuntu techies there helping people than in General Help. :)

please and thank you, in advance.
Done. :)

---

### Post by Stargazer989 on 2008-12-30
ok... I have a new theory... this laptop is the first in the line of upcoming Artificial Inteligence units... this version is the 'Child' version. this is what i think... or i may have just gone mad. 

anyways... the past 24 hours i've left my laptop on and going... **without** any issues. again, i think this laptop is an AI unit. :|

---

### Post by Norm24 on 2008-12-30
Suspend/Hibernate in Ubuntu basically doesn't work on the majority of laptops.Never has.

I've had Ubuntu on three different brands and its never worked properly.From Drake to Ibex,suspend/hibernate has been completely erratic.

I've accepted the fact that I have to shutdown after I'm done for the day.At least Ununtu loads a lot faster than Windows.

I'm hoping someday to be able to suspend a laptop under Ubuntu without worries.

---

### Post by morpheus01 on 2009-05-17
Thanks for that Norm24, good to know. I have been trying to fix hibernate on my Dell 640M; on and off for over 2 years. I thought it was something to do with downloading a driver myself and editing the xorg.conf file when I was setting up Edgy. 

Pity about this as it makes Ubuntu unfeasible for bunch of users with Windows partitions. It's just not worth rebooting and shutting down for looking up something quickly...

---

### Post by morpheus01 on 2009-05-17
Sorry to post this here but I just found a fix - for my issue at least. I did this by using the "dpkg reconfigure..." command to update the xorg file and remove my configured version (there have been driver updates installed since I needed to do that). However I have been dispointed to notice that booting from Hibernate doesn't have the time saving effect with Ubuntu that I thought it would. I also just noticed that booting Windows from shutdown is quicker on my machine than I thought it would be (I don't have alot of apps starting at boot up). See below... 


Ubuntu
Start from Shutdown
	1 minute 25 seconds
Start From Hibernate
	1 minute 25 seconds

Windows
Start From Shutdown
	1 minute 10 seconds
Start From Hibernate
	20 seconds

---

