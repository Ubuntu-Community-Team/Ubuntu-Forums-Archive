---
title: "Need to recover files."
date: 2015-10-03
forum: New to Ubuntu
---

### Post by jon_4 on 2015-10-03
I need to recover my files from the 316 volume on my laptop(home folder specifically). I was trying to use the terminal for the first time the other day (tried to install something called sh. files). The result of this is that i cant boot up again, its only a blank screen with a cursor. What i have tried is to boot from a cd> try ubuntu and then tried to open the home folder but i get "this location could not be displayed". What shall i do?

---

### Post by ian-weisser on 2015-10-03
You shall tell us, in as much detail as possible, exactly what you did...and the contents of that .sh file.
Link to instructions you followed, if any.
Every command you entered, in order...and the results.

---

### Post by jon_4 on 2015-10-03
There was a zip file containing folders and two sh. files. It contained ergonomic/ alternative keyboard layouts from colemak forum. [http://forum.colemak.com/viewtopic.php?id=1438](http://forum.colemak.com/viewtopic.php?id=1438)
The sequence i followed: extracted zip file in the download folder. and in terminal: cd Downloads/ -> ls -> cd dreymar_x-mod -> ls-> sudo chmod +x install-dreymar-xmod.sh, and then this message telling about a successful installation came on the terminal. I Did the same sequence with the other sh file. This is what i remember that i did, was kind of the first play i had with the terminal ever. Hope this is in sufficient detail.

---

### Post by ian-weisser on 2015-10-04
When you boot, at what point does the boot fail?
Do you see the manufacturer's logo?
Do you see the GRUB screen or prompt?
Do you see the Ubuntu splash screen?
Do you see the Login page?

Do you see any error messages, or mysterious or cryptic status messages or warnings?

Are any other OSs (like Windows) also currently installed on the machine?

---

### Post by jon_4 on 2015-10-04
If manufacturers logo means the HP logo i get at the beginning: Yes. After that this GNU GRUB menu shows up with the ubuntu, memtests and advanced options shows up(4 options in total). When i press ubuntu at top, or just wait the blank screen with the cursor shows up (is this what you call prompt?) There are no other OS installed on this Computer. after a couple of minutes the cursor became smaller, and messages were on the screen for about 15 seconds. Were not able to write down.(should i?)
As i was writing this a change happened as i waited ( i did not wait this long yesterday): the splash screen now shows up and it says: "Error were found while checking the disk drive for /." I also get the alternatives: F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery.

---

### Post by ian-weisser on 2015-10-04
Does your boot fail the same way every time?
A photo or written record of the error message may be very helpful. Certainly worth a try.
Depending upon the answers, your entire system may or may not be recoverable. Backing up your data is a very good idea before deeper investigation.

To recover your data:
1) Boot from a LiveUSB (*NOT* your HDD).
2) Plug in and mount another storage device.
3) Mount your /home on your HDD, and copy your data to the other storage.

---

### Post by jon_4 on 2015-10-04
It seems like the boot- up is somewhat inconsistent, and not the same as last time.
Is it ok to boot from a cd instead of an USB?
I think i managed to mount the external storage as well as thee 316 GB volume( used the disks application). I do the copy to... but get the same result as last time: Error while copying.

---

### Post by ian-weisser on 2015-10-04
It doesn't matter if your Live media is USB or CD. Whatever works and boots you into a stable environment without using the HDD.
 
> **jon_4 said:**
> It seems like the boot- up is somewhat inconsistent, and not the same as last time.
A system having intermittent trouble communicating with the hard drive implies a hardware fault.
If you're lucky, perhaps the hard drive data cable is merely loose or shorted.
If you're less lucky, perhaps your hard drive is dying or broken.
Or perhaps your motherboard.

Those are three possibilities - try to narrow them down: Check the data cable. Try the HDD in a different machine.

If your HDD is SMART-compatible (most are), install SMART tools from the LiveCD's Software Center and let it scan for drive errors (different from filesystem errors).

It's still possible to recover your data from a flaky/dying hard drive. It requires patience, and perhaps multiple tries. Prioritize - copy your most important data first.

Some members of local Linux User Groups are quite skilled at diagnosing and recovering data - might be worth dropping by a local meeting (if any) and letting a them try your drive from their machines. There are also commercial data-recovery firms, if the problem really is the hard drive.

---

### Post by mastablasta on 2015-10-05
if you manage to somehow backup the important data first then according to this:

> **jon_4 said:**
> 
As i was writing this a change happened as i waited ( i did not wait this long yesterday): the splash screen now shows up and it says: "Error were found while checking the disk drive for /." I also get the alternatives: F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery.

it might be able to repair the errors by default software (fsck). but do make the backup first.

if you have a place - then perhaps making an image is also good. even if data is corrupt the image will be made (of corrupt data). 

It really does point to a hardware error but then again there is a small chance it is a software one. ultimatebootCD has many tools needed for various disk and hardware diagnostics.

I had a similar thing occur to me upon update command. though the update went wrong but in the end it turned out the drive was damaged. i was able to partially recover the data - once though I managed to catch the drive before it failed. the boot cd showed imminent failure which was true as it didn't want to spin up always. cloned it just in time.

---

