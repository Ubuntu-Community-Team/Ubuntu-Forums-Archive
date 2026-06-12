---
title: "system keeps freezing- help!!"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Matt26 on 2008-05-30
in the past few days my ubuntu 8.04 system has frozen up completely a couple of times- to the point of no mouse movement, HDD activity, nothing at all responds- i have no choice but to hit the restart button on my PC case.  i have no idea why this is happening, and i have not installed any new hardware recently.  i have installed the latest recommended and critical updates, reconfigured my installation of vmware server 1.0.5 (since it decided to stop working all of  sudden the other day) and changed/added some of the startup items in my System/Preferences/Sesssions section, but that's it.

i know these kind of issues are normally difficult to troubleshoot- i've run into enough of them with Windows in the past- but i was hoping someone might have an idea as to what the culprit is here.

any help is appreciated.

thanks.

---

### Post by skymera on 2008-05-30
I'm not sure what is causing it, sorry.
Someone else may know.

But your keyboard may respond still, instead of hitting the restart button, or holding the power button for magical 5seconds try this:

Hold: ALT + SYSRQ (Print Screenbutton) Whilst holding press in this order: REISUB

That will perform a safe shutdown.

---

### Post by Matt26 on 2008-06-03
thanks for the suggestion- it did work a few times, however i am still having random system freezes, and they seem to be more frequent now- i have had at least 3 occur in the last couple of days, within hours of each occurrence.

i have changed back all the settings i can think of that have recently been updated (turned off auto-login, restored all session items that start up automatically, turned off custom session startup items for FF, Pidgin and Thunderbird and turned off my XP VM that i have set to start up with Ubuntu) but nothing has worked so far.. i have noticed a variation in the freezing of my system as well recently, where instead of no response from any part of the system at all, i can move the mouse pointer, but nothing responds when i click on it (this has also happened a few times in the past).

i don't know what else could be happening at this point to cause this issue- is there some sort of restore feature in ubuntu that would allow me to set the system back to a certain date (like Windows Restore points)?

if anyone has any other suggestions i would really appreciate it.

thanks.

---

### Post by Golem XIV on 2008-06-03
If you have the LiveCD on hand, try running a memory check overnight.  Another thing to look into is the possibility of overheating.

---

### Post by Daveg4otu on 2008-06-03
Have you recently (or ever) opened the case and cleaned out the dust and cat hairs etc.

The Heatsinks on the CPU, Chipset and Graphics cards need particular attention - as well as any vent slots, case fans etc.

Install  the CPU/System monitor Xsensers ...check voltages- +3.3/+5 /+12 should all be within +/- 5% of nominal- a failing PSU can cause  this type of problem

---

### Post by _sphinx_ on 2008-06-03
@Golem XIV 
I have one question though it not related to the thread but I am really curious to know about it. When I did the following:
> Hold: ALT + SYSRQ (Print Screenbutton) Whilst holding press in this order: REISUB
My laptop restart just at the moment I press the last 'B'(without any time lag). I want to asked is it really safe to use this thing in daily practice.

---

### Post by Golem XIV on 2008-06-03
> **_sphinx_ said:**
> @Golem XIV 
I have one question though it not related to the thread but I am really curious to know about it. When I did the following:

My laptop restart just at the moment I press the last 'B'(without any time lag). I want to asked is it really safe to use this thing in daily practice.

Um, it wasn't me, it was skymera :-)

In any case, yes, the B will reboot the system.  The keystrokes do the following:

R tells the X server to release control of the keyboard
S syncs the disks (forces write of any cached information)
E sends all processes but init the term singal
I sends all processes but init the kill signal
U remounts all filesystem read-only
B reboots the system

The mnemonic for this sequence is
**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring

You should allow a few seconds between each keypress.

---

### Post by Matt26 on 2008-06-04
i have been reading a number of posts from different forums from people having similar issues as this one and it appears that the issue may be related to the use of bit torrent clients and high volumes of network traffic while using the client (i use deluge) on  various ubuntu platforms and releases.  i am almost certain that every time i have had a freeze occur i was running deluge, so i tried restarting my PC yesterday and did not start deluge this time.. and when i checked my PC this morning it was still running.  so i'm hoping that when i get home tonight i will find that it is still running *fingers crossed*.

anyone know how this might be remedied if this is indeed the case?

---

### Post by Matt26 on 2008-06-05
well i guess i spoke too soon- a few hours ago (after having run for a couple of days freeze-free) my PC froze up again completely... no mouse movement, so i guess i can't say that it was a bit torrent issue at this point.

does anyone know how i can track all the services and resource usage on my PC in real-time?  there must be something that is peaking to the point of causing things to crash like this.

thanks.

---

### Post by stalkier on 2008-06-05
I have been having the same issue with freezes. This did not happen with 7.10, only with the recent 8.04. Even with all the current updates it still freezes. I thought maybe it was related to not having enough DDR, however I recently just upgraded to 1.5GB and it still freezes from time to time. I just hit the restart button and go about my business.

---

### Post by sgloom on 2008-06-06
I have same problem. My mouse and keyboard freezes when DVD drive is working (reading or writing) and sometimes at random points in time. And I can only press reset (reboot) button  when it happend. This problem is absent in Ubuntu 7.10.
I have Ubuntu 8.04 (kernell 2.6.24-16/17/18 ); Athlon XP 1700+; ATI Radeon 9550 (128MB); 120 GB IDE (NTFS); 40 GB IDE (FAT,NTFS,EXT3); DVD-ROM Optiarc AD-7200A

---

### Post by Matt26 on 2008-06-06
if i recall correctly, my issues also started when i upgraded to 8.04... i wonder if this means that there is something wrong with some of the files or settings that were updated?  very strange either way...

---

### Post by sgloom on 2008-06-06
Is your mouse PS/2 ? Does your machine become completely freezing or keyboard and mouse freezes only (programs still executing)?

---

### Post by Matt26 on 2008-06-06
my mouse and keyboard are wireless, but the receiver connects to the PC with a PS/2 and USB connector for the keyboard and mouse respectively.

most of the time the entire system freezes to the point where nothing at all responds- not even mouse movement- in some of these cases i am able to perform a safe reboot using the Alt+Print Scr+REISUB method, other times that won't even work and i have to hit the restart button on my PC case.

in a few cases the system freezes up to the point where i can at least move the mouse around, but nothing will respond to a mouse click.

---

### Post by _sphinx_ on 2008-06-06
Thanx of the information...

---

### Post by Matt26 on 2008-06-06
after doing some googling and reading a few more posts on this issue, it appears from what i am reading that most people (if not all) are using some form of wireless network connection that is active/enabled when these crashes occur- my setup also includes a wireless setup- does anyone else have a wireless setup in their situation?  i am thinking there is a possibility that variable wireless performance could be causing this issue (or at least possibly having a bearing on the issue).

i am going to try setting up a wired connection from my PC to my router and modem when i get home after the weekend and see what happens, i'll post an update once i see how things go.

---

### Post by gnatman on 2008-06-06
I am not using anything wireless. Mine used to just freeze occasionly, when it does, I get 2 verticle lines in the lower right side of screen. They are about 1/2 in apart, and 2-3 inches long. Earlier I turned it on, tried to do updates,got an error that said I had to manually update, but before I could do anything, it froze. It was first time turning it on today.
Help anyone?

---

### Post by Matt26 on 2008-06-09
i left my PC running for about 3 days and it was still responding when i came back- with only deluge running.  as soon as i went to open FF (which was trying to load about 6 tabs from it's previous session) it crashed within seconds of the browser trying to load the tabs-again with no mouse response and Alt+PrScr+REISUB didn't work, interesting...

i am starting to wonder if this is an app-specific issue or a wireless issue like i have been reading about.

---

### Post by signseeker on 2008-06-09
You should also check your power supply. They sometimes die for no apparent reason.

---

