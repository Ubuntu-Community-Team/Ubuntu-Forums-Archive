---
title: "How to burn a booting CD ?"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by Innernet on 2012-12-06
Hi
How to create/burn with Ubuntu a CD that will boot itself in a Windows machine ?  The CD drive is first bios priority to boot.

I have downloaded an **.exe** antivirus from 'Spyhunter' for a very infected Windows Vista machine. 
I suppose something else must be in the CD so that executable will run itself after power up, Is that right?

---

### Post by levlaz on 2012-12-06
I think this may be more of what you are looking for. 

[http://www.dedoimedo.com/computers/linux-av-cd.html](http://www.dedoimedo.com/computers/linux-av-cd.html) 

Its a LiveCD that should clear the viruses without having to boot into windows. 

If you run an Ubuntu Live CD  -- it will run ubuntu you will not be able to run any .exe inside of ubuntu for the purpose of removing a virus.

---

### Post by Innernet on 2012-12-06
Correct, I see your point levlaz.

The intention is not to boot into Windows in the ill machine; it is to run the virus/malware cleaner CD before its Vista operative system takes over.

For that, has to be a 'Live' or 'bootable' CD; not just an executable, as far as my little knowledge goes.  Please correct if this is wrong.

---

### Post by levlaz on 2012-12-06
Yes this is correct, however I think one of the Live Distributions in that link I gave would do a better job than ubuntu since they are specifically designed for this purpose, whereas ubuntu is designed to be a replacement for Windows or Mac.

EDIT: In other words, there is no reason to use your .exe antivirus at all -- the live distribution IS an anti-virus and should be able to take care of all of your issues.

---

### Post by Innernet on 2012-12-06
Sorry, lev, am not that smart.
I do not want any Ubuntu distribution live CD. I have a bunch already.

I want to make with an Ubuntu machine, a live cd with an antivirus .exe for a Vista machine in order to clean its problems.

I understand there is some way to fix a Windows machine by booting it with a live Ubuntu disc.  That is not possible for this particular complex and extensive problem, been suggested that only the 'Spyhunter' can take care of such infection, and prefer to follow that before trying other methods.

---

### Post by lisati on 2012-12-07
If you want a rescue CD, this should do the trick: [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by levlaz on 2012-12-07
> **Innernet said:**
> Sorry, lev, am not that smart.
I do not want any Ubuntu distribution live CD. I have a bunch already.

I want to make with an Ubuntu machine, a live cd with an antivirus .exe for a Vista machine in order to clean its problems.

I understand there is some way to fix a Windows machine by booting it with a live Ubuntu disc.  That is not possible for this particular complex and extensive problem, been suggested that only the 'Spyhunter' can take care of such infection, and prefer to follow that before trying other methods.

I understand what you are trying to do -- but you cannot do it. You cannot make a live CD that runs an antivirus that was made for windows (in this case your .exe file) 

EDIT: Bottom line -- you cannot make a live CD to Run "Spyhunter" it's impossible. 

You need a rescue CD as mentioned above -- What you are trying to do is going to be very difficult if not impossible using Ubuntu. A Live CD **is **a linux distribution -- that is the entire premise. You cannot do this with Ubuntu because by default Ubuntu does not come with any sort of software to clean up your windows machine. 

The best thing to do would be to download a Live CD of a distribution that was designed to be used as a rescue CD for broken windows machines. The one I linked to works well, so does the AVG one.

---

### Post by mastablasta on 2012-12-07
> **levlaz said:**
> You need a rescue CD as mentioned above -- What you are trying to do is going to be very difficult if not impossible using Ubuntu. A Live CD **is **a linux distribution -- that is the entire premise. You cannot do this with Ubuntu because by default Ubuntu does not come with any sort of software to clean up your windows machine. 
.
 
not impossible, just need a different antivirus tool. 
1. you (can) boot ubuntu live CD. this loads the linux operating system into RAM
2. you then install a linux verison of antivirus into this operating system (for example clamav, avira antivir for linux, avast for linux...). 
3. clean the infected drive with installed antivirus. 
4. reboot (remove the CD on shutdown, so you boto into windows OS)
 
but as suggested this whole procedure will be much easier with rescue CD that comes with antivirus preinstalled.
 
edit: if you boot from USB drive (stick), you can add persistance to the live OS. so that when you install the antivirus, it will stay there on the live CD on reboot. that way you can create your own rescue disk ;-)

---

### Post by levlaz on 2012-12-07
What he is trying to do is impossible. 

He wants to make a "Live CD" that runs his SpyHunter software which is a windows antivirus I am assuming. (since he says its an .exe) This would require installing Wine in Ubuntu Live, hoping that this spyhunter program works under WINE, and then hoping that it does what its supposed to once its there. Honestly, the whole idea just sounds like a big mess to me. :) 

Your method would work just as well as a "rescue CD" but what the OP wants to do is not currently possible as far as I know.

---

### Post by Mark Phelps on 2012-12-07
There are antivirus products available in ISO form, for free, that you download, burn the CD image -- and you can then boot from those and run the virus scans.  Ironically, these ISOs actually run different versions of Linux.

Couple that come to mind are Avira and Kaspersky.

---

### Post by Bartender on 2012-12-07
> **Mark Phelps said:**
> There are antivirus products available in ISO form, for free, that you download, burn the CD image -- and you can then boot from those and run the virus scans.  Ironically, these ISOs actually run different versions of Linux.

Couple that come to mind are Avira and Kaspersky.

+1

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/]("http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/")

Skip the Spyhunter thing.  I'd try Kaspersky if it was me.

If you're going to create the CD from a Windows PC, install ImgBurn.  It's an easily understandable program that's handy for creating bootable discs from .iso downloads.  Once you've created the bootable CD, pop it into the infected PC and boot from the CD.  It's important to be connected to the internet when you boot up the infected PC, because these anti-virus boot CD's will try to go online and get the latest definitions.

---

### Post by critin on 2012-12-07
> **Innernet said:**
> Hi
**How to create/burn with Ubuntu **a CD that will boot itself in a Windows machine ?  The CD drive is first bios priority to boot.

I have downloaded an **.exe** antivirus from 'Spyhunter' for a very infected Windows Vista machine. 
I suppose something else must be in the CD so that executable will run itself after power up, Is that right?

Burn the rescue disk mentioned in Post@               #[**6**]("http://ubuntuforums.org/showpost.php?p=12391966&postcount=6") with Brasero Disk Burner in ubuntu.  The rescue disk will boot/work on linux and Windows.  See operating systems here:

[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

Once the virus' are cleaned, you can install spyhunter into the windows directly to further clean and protect the running system.

---

