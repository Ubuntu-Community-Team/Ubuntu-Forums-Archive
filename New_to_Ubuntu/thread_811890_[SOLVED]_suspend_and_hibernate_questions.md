---
title: "[SOLVED] suspend and hibernate questions"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-29
is there a way to log what is happening when i suspend or hibernate?
a log file just for suspend and/or hibernate or a way to start it from the terminal so i can see any errors?

my laptop (dell xps m1210) used to suspend quite will but would hibernate and never wake..

now after i have been messing with pulse audio and some other things it will not do either. it just gives a warning beep and tells my it failed to suspend or hibernate and i should look at the help guide.

thanks for any pointers.

nutz

---

### Post by KingTermite on 2008-05-29
How much free space do you have on your drive? Were you close to capactiy and put much closer recently?

Just a thought because hibernations takes quite a lot of space to save the system state. I think its on the order of hundreds of megabytes.

---

### Post by philinux on 2008-05-29
Try this it worked on my desktop.

On pressing the power button I was back on in seconds and no login.

opened all the windows I had running.

sudo pm-hibernate

I'm making a launcher for it.

Using the normal quit then hibernate would lock my system up. REISUB only fix

---

### Post by kamitsukai on 2008-05-29
id be interested in getting either of those working...and i have 2gig's of ram and a 3gig swap but still no luck

---

### Post by nutpants on 2008-05-29
pm-suspend worked for me, sadly i lost my usb yet again coming back up. but that happened from time to time before ..

i still have laptop screen issues trying to reboot after a suspend (the screen fills with vertical lines, i think it has to do with my nvidia card and the refresh rate)

pm-hibernate seems to save fine but i just get a normal boot up sequence as far as i can tell.. 

i have 2 gigs of ram and a 3.5 gig swap file and lots of free space in my partitions.  

nutz

---

### Post by sayakb on 2008-05-29
I too have the USB problem after waking from suspend. (Thought that 'twas only on Thinkpad, but I'm wrong, my HP got *infected* too!!!)

---

### Post by philinux on 2008-05-29
> **nutpants said:**
> pm-suspend worked for me, sadly i lost my usb yet again coming back up. but that happened from time to time before ..

i still have laptop screen issues trying to reboot after a suspend (the screen fills with vertical lines, i think it has to do with my nvidia card and the refresh rate)

pm-hibernate seems to save fine but i just get a normal boot up sequence as far as i can tell.. 

i have 2 gigs of ram and a 3.5 gig swap file and lots of free space in my partitions.  

nutz

Thats odd like I said before it looks like a normal boot but I was back to my desktop with windows open in seconds and no login.

---

### Post by hufferd on 2008-05-29
> **nutpants said:**
> is there a way to log what is happening when i suspend or hibernate?
a log file just for suspend and/or hibernate or a way to start it from the terminal so i can see any errors?

my laptop (dell xps m1210) used to suspend quite will but would hibernate and never wake..

now after i have been messing with pulse audio and some other things it will not do either. it just gives a warning beep and tells my it failed to suspend or hibernate and i should look at the help guide.

thanks for any pointers.

nutz


I would love to get it working on my system as well - I'm not using a laptop but I can't get either to work on my desktop system.   The system hangs after suspend  and hibernate

:confused:

---

### Post by nutpants on 2008-05-29
> **LinuxIsInnovation said:**
> I too have the USB problem after waking from suspend. (Thought that 'twas only on Thinkpad, but I'm wrong, my HP got *infected* too!!!)

im working around my usb problem not powering on by having a launcher run "lsusb" which bring my usb back working 98/100 times
(and i dont even notice that my laptop usb has no power when my devices are pluged into a powered usb hub)

nutz

---

### Post by pfeels on 2008-05-29
I'm having the same problem, my desktop (Dell XPS 410) suspended fine until recently after I download updates ... It's something you just have to have, the ability to suspend ...

---

### Post by Tom--d on 2008-05-29
Use the Linux kernel -16 *the updates update it to -17 

then suspend and hibernation works :) (as for me)

---

### Post by nutpants on 2008-05-29
> **Tom--d said:**
> Use the Linux kernel -16 *the updates update it to -17 

then suspend and hibernation works :) (as for me)



i am suspending as well as i did before with  sudo pm-suspend...

i dont like the idea of downgrading my kernel to "fix" a bug..

that sounds a little too....WRONG...


nutz
ill upgrade to fix a bug but not downgrade.
this is not microsloft.... newer should mean better.. not just bigger and more money.

---

### Post by pfeels on 2008-05-30
Code:

sudo apt-get install startupmanager

Then go to System > Admin > StartUp-Manager

Default OS to > Ubuntu 8.04, kernel 2.6.24-16-generic

this worked for me ... tom and logas idea

---

### Post by helmut_hed on 2008-06-02
Nutpants, to your original question, the main way of exposing what's happening in suspend/resume is through the "pm_trace" facility:

sudo su
echo 1 > /sys/power/pm_trace

Once the suspend fails you can look through the output of "dmesg" for things like this:

[222978.660000] PM: Preparing system for mem sleep
[222978.660000] Disabling non-boot CPUs ...
[222978.660000] Stopping tasks ... done.
[222978.996000] Suspending console(s)
[222978.996000] sd 12:0:0:0: suspend
...
and hopefully this will give you an idea what's happening.

For even more information, try this:

echo 8 > /proc/sys/kernel/printk

before trying your suspend.

I'm not aware of any special file that gets suspend/resume information, but these commands will give you more in the regular system logs.

Good luck,
Jeff

---

### Post by nutpants on 2008-06-03
my suspend and hibernate problems seem fixed with the new kernel update today.

Ubuntu 8.04, kernel 2.6.24-18-generic

seems to have fixed the problems


nutz

---

