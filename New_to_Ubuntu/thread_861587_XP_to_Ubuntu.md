---
title: "XP to Ubuntu"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by sbalick on 2008-07-16
I am attempting to install Ubuntu onto an older system of mine that I built several years ago (OK ancient dinosaur, in these contexts).  It is an AMD 900MHz with 512MB RAM and a 250GB HD - I forget which version of the Via chipset that is on the MB.  Windows is getting klunky and I am looking forward to something better that isn't a resource hog... hence Linux.  This is still a good machine and suits all my purposes.

But I digress...  I used Unix in school about 10 yrs ago and only needed it for mail, ftp and a bit of Xterm stuff at the time.  I now need to relearn Linux for work and this seems to be a good way to do it.  :)

I have downloaded both versions of the install image and attempted to run Live CD without success.  I have been searching over the forums for the past 2 days and all that has been reported to do was use the alternate text version of the install - it seemed to clear up any issues with everyone, well, except mine.  In both cases, my system reboots, asks me which OS to use (XP or Ubuntu).  I am then prompted to "Escape to the menu".  At which point, I select the Live CD version as I haven't done any backups yet to see if I even like the interface, structure etc.  The screen clears and a flashing cursor appears at the upper left hand corner of the screen, and there it sits ad infinitum.... (and beyond)...

Any suggestions?


Additional:  There are so many posts indicating that CD's might be corrupt/bad/incorrectly burned.  How is it that you can check?  I have seen on some other posts that inferred there is a disk check utility just after the system boots.  This would indicate that it is part of the BIOS.  Am I correct in this or is there some other method to check???

I left my system running last night and to what do my wondering eyes ... no difference (bumming).  I am really interested in running this OS as an option to Windows.  Where else can I check to see what might be causing me problems.  I wish I could provide more information as to what my system is trying to do, but I am left with a blank screen.

Sincerely,
Hoping for better

---

### Post by adewale on 2008-07-16
Hmm why not check the cd for defects. I had a similar experience with a different distro, only for me to realize later that the cd was bad. I didn't run on my desktop neither on my sister's laptop also. Then i tried making an iso out of the cd and it gave errors.

---

### Post by sbalick on 2008-07-16
Well, success and failure.  I used InfraRecorder to make the .iso out of the CD I burned earlier (with InfraRecorder).  I would assume from the success I had in that app that my image was good.  But where does that lead me from here?

At what point is HW now supported on most flavors of *buntu or Linux at all?  Is it possible that my system is too much of a relic?

---

### Post by Het Irv on 2008-07-16
I don't see any problems, but I am confused about what you did.  Have you actually installed Ubuntu on your computer?  Do you still have Xp on the computer?

---

### Post by sbalick on 2008-07-16
As I understood it, the Live CD didn't have to be installed, it just loaded the kernal from the CD into RAM and ran from there.  That assumption going forward (I know this brews trouble), I burned the .iso image to a CD and booted from that CD.  Am I missing something?
... stranger things have happened...

edit:  I still have XP on the system, nor did I actually install Ubuntu on it either.

---

### Post by alienexplorers on 2008-07-16
DOwnload the .iso file from Ubuntu.  Use InfraRecorder to burn the .iso to the CD.  Do not just copy the .iso to the CD as a DATA burn.  It must be burnt as an .iso....  From there you can insert it in you CD drive and reboot.  It should then start loading Ubuntu.

---

### Post by Het Irv on 2008-07-16
Okay, I was just trying to clear it up for me, and yes, you are entirely right about the way it works.

When you boot to the CD does a menu pop up asking what language and then it gives you a few options?  If not then I don't thing your CD was burned correctly

---

### Post by sbalick on 2008-07-16
I believe that is what I did.  I think it verifies after the burn, and I do indeed have a menu window appear when I load the CD.  This window has 3 buttons:  demo and full installation, install inside windows, and learn more.  I have been selecting Demo and full installation.  When the PC reboots, I select the Live CD demo.  After that, the screen clears and stalls for 20 mins+.

---

### Post by logos34 on 2008-07-16
> **sbalick said:**
> At which point, I select the Live CD version as I haven't done any backups yet to see if I even like the interface, structure etc.  The screen clears and a flashing cursor appears at the upper left hand corner of the screen, and there it sits ad infinitum.... (and beyond)...

So you're able to boot the live cd but it goes to flashing cursor when you choose the first option (try out ubuntu)?  Is that where you are?

---

### Post by sbalick on 2008-07-16
Exactamundo.

---

### Post by Het Irv on 2008-07-16
> **sbalick said:**
> I believe that is what I did.  I think it verifies after the burn, and I do indeed have a menu window appear when I load the CD.  This window has 3 buttons:  demo and full installation, install inside windows, and learn more.  I have been selecting Demo and full installation.  When the PC reboots, I select the Live CD demo.  After that, the screen clears and stalls for 20 mins+.

Are you sure you burned as an .iso not data.  I think it will still work in windows even if you burned it wrong.  Also can you check your bios to make sure your computer is set up to boot to CD?

---

### Post by sbalick on 2008-07-16
Alienexplorers mentioned the same thing.  I guess to limit confusion, I will explain the process I have been using when I burn the image.  From within InfraRecorder, I select "Burn Image..." from the Actions menu.  I select the .iso file that was downloaded and use Verify the disk after writing.  I have been burning them at 8x and my media and recorder are rated far beyond that.  I have burned 3 images so far, just to double check - 2 of the desktop version and one of the alternate version.  Nothing balks at me afterwards.  I figure it should be OK.

I hope that is correct.....  ??   :|

---

### Post by Het Irv on 2008-07-16
Okay, yeah you got that part right.... uhhh hmmm.

Not sure, have you tried a different Download (if you can, I realise thats a big deal if you are on Dial-up or the like).

Other than that I am not sure.

---

### Post by sbalick on 2008-07-16
Downloading another copy isn't too big of a deal.  I have high speed.  I will give it a try, certainly.  Thanks for your time.  :)

I am still open to suggestions....

---

### Post by AndrewEsther on 2008-07-16
What is the read speed on your dinosaur's cdrom? I ran into something along these lines when installing xubuntu on my laptop, and I wound up having to use the option to install without booting into it first (oem install, or something like that I don't remember the exact option) because my cdrom simply could not read fast enough. It took an hour to do anything once it finally booted into xubuntu, which itself took almost 2 hours

---

### Post by sbalick on 2008-07-16
It is a Plextor PX-708A capable of 40x CD read speeds.

---

### Post by lisati on 2008-07-16
<an aside>BTW: some Live CDs pop up a window that gives you a chance to install Windows versions if you put the CD in while Windows is running. That can be a clue that the CD was burned correctly.</an aside>

---

### Post by Blahblah54 on 2008-07-16
Is it freezing before it gets to the screen where you have the options "Try Ubuntu without changing your computer, Install Ubuntu, etc."?

---

### Post by pi.boy.travis on 2008-07-16
One of my machines takes almost an hour to boot from the live CD.  It displays all manner of weird flashing things before actually booting.  It has 1GB ram, it must be a weird graphics card to configure.

---

### Post by sbalick on 2008-07-16
For each of you:

lisati & blahblah54: If I load the CD while still in Windows, the CD does start to run and I am presented with a selection of three items, as you indicated, blahblah54.  (I think I may have mentioned this one in an earlier post).

pi.boy.travis:  I suppose I will try and wait longer.  I don't see any activity on the screen nor at the prompt for typcially 20 mins.

It seems like everything is telling me the CD is burned correctly.   So, I will take some advise and wise words from many scriptures, texts and otherwise more experienced individuals in this world and 

BE PATIENT....           otherwise, I am still on the path.

This post is starting to read like some sort of Dear Abbey or sumpin'... but I am still looking for clues.  I will leave the system on overnight to see what happens, so tune in next time on the same 'bat' channel...  :)

UPDATE...  Rest of story:  I left the system on overnight without success.  I am doing some more hunting on help.ubuntu.org to try and install the system on an external USB HD.  Hopefully this will lend some success.  I am still open to suggestions on why it won't work as described by so many.

---

### Post by ddrichardson on 2008-10-24
This doesn't sound like a bad burn, this sounds more like a problem with an odd ACPI configuration on the motherboard. Are there any options in the BIOS relating to power management?

Booting with the -noapic option is often useful - did you say you got the CD Menu?

---

### Post by cleatus on 2008-10-28
:) Hi! You computer should run ubuntu fine. Are you using an onboard video card or are you using an add on card thru pci or agp? I had to install ubuntu thru onboard card and then install drivers for my add on video card before being able to get anything except blinking cursor ´hang´. Try this using onboard video card to install ubuntu. Hope this helps a bit....keep trying it is really worth it!!!:biggrin:

---

