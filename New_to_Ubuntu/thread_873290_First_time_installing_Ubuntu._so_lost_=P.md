---
title: "First time installing Ubuntu. so lost =P"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by koongoo on 2008-07-28
Well, I have 2 laptops that I wish to install Ubuntu onto. So I requested  a Live CD, but in the mean time I downloaded the Ubuntu file and Burned it onto a CD using a program I was recommended called InfraRecorder. after the File was burned onto my cd I put it into my drive and booted from the CD. the Ubuntu main screen came up with the options to start without changing windows or to install, etc. when i tried to install it would freeze up like it was doing something then a thing would pop up saying "I/O error"  with the option to click ok.after clicking ok it returns to my normal boot menu. what do i do?

not sure if this has anything to do with it but everytime i tell my laptop to boot from the menu to boot on windows normally or last working settings, I get blue-screened.

---

### Post by kool_kat_os on 2008-07-28
do a check cd for defects

---

### Post by Dougie187 on 2008-07-28
Did you check the integrity of the cd?

Its in the boot menu for it. If you choose it, then it will tell you if the cd is ok or not.

---

### Post by kool_kat_os on 2008-07-28
> **Dougie187 said:**
> Did you check the integrity of the cd?

Its in the boot menu for it. If you choose it, then it will tell you if the cd is ok or not.

hey...thats what i said :)

except in a more descriptive way

---

### Post by silent contender on 2008-07-28
How old are the laptops?  Unlikely, but sometimes the motherboard/BIOS has problems (happened to me once).

---

### Post by koongoo on 2008-07-29
hey,I guess i forgot to mention that but it also came up anytime i tried to do anything.Even the check CD. 

(thanks though guys)

---

### Post by alienexplorers on 2008-07-29
Try downloading the Alternate CD and burn the .iso to disk.  Try booting from that to load Ubuntu.

---

### Post by koongoo on 2008-07-29
ok. everytime since the first Ubuntu CD I burned they keep burning wrong. my cd says there are no bites left to use and that it is full but there is nothing on the CD. this has happend 5 times now. what the heck do i do?

---

### Post by kdb424 on 2008-07-29
It might be best to wait for the CD to get there. I requested a 32 and 64 bit ubuntu desktop, and they sent me a 64 bit ubuntu server, and a 64 bit kubuntu desktop. lol. Hope that they don't do that to you.

---

### Post by Kevbert on 2008-07-29
Once you've downloaded the alternate CD (text based install) have you performed a [[COLOR="Red"]hash check[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") on the ISO file ?  Also have you tried burning the CD at the slowest speed possible (to minimize errors) ?
Next check the CD for errors and then perform a memory test from the install menu (it's possible to have memory problems even with PCs that seem to run fine with windows).

---

### Post by Bucky Ball on 2008-07-29
Try booting from a cd you know to work. Does it work? If so, restart, rethink about your burning process. Maybe even download Ubuntu Hardy 8.04 iso again (there is a torrent file which is quicker). Reburn that image to another cd using a different burner to the one you have been using and try again.

You say nothing about the specs of the laptop. Make sure you are downloading the correct iso (there are several). The one you want is either desktop i386 or desktop amd64 (from memory). There are alternate cds but don't see why this is not working.

If the laptops have little memory (below 512 realistically, although the specs given are different) you may want to give Xubuntu a go. Designed for lower end machines (which were of course higher end 5 years ago!).

If the cd you know to boot doesn't boot, your optical drive is screwed and it is a hardware problem.

Good luck with it all ... :)

ps; and as kevbert says, always check the new ubuntu boot disk for defects before you do any installing ... :)

---

### Post by candtalan on 2008-07-29
> **koongoo said:**
> hey,I guess i forgot to mention that but it also came up anytime i tried to do anything.Even the check CD. 
(thanks though guys)

That sounds bad. One obvious problem is that the CD drive is not working properly, because at least you would hope that the cd check would *run* ok, and maybe find errors. Maybe though, the burned image on the media is very poor. 
iso images like this have to be byte perfect, you do not get (I think) the same sort of error correction that happens when you create your own CD like audio or documents. Any error in burning to the media is a problem, maybe you have a -lot- of burning errors. You would not notice these on other cd actions.

Try burning a cd and checking in another machine, and ensure the burn speed is low, at least half its suggested rate if possible, then do a cd self check on the burn machine. Then go to the install target machine. That will help check the basics in your situation. 

btw if the laptops are old - what RAM have they got? When you have got things working, be aware that the usual install and live cd takes a lot of ram, unlike the Alternate install cd which can be used for install with low ram.

good luck

---

### Post by ByteJuggler on 2008-07-29
1.) If you laptop is Blue screening on Windows, that can be due to either hardware problems, or due to your Windows having become corrupted for whatever reason.  If it's due to hardware problems then of course you'll have problems with any operating system, not just windows.  Can you please post the exact message you get on the BSOD (blue screen), sometimes that can give a clue as to what the problem is.

2.) Just to reiterate what others have said: If you download and burn the Ubuntu CD, you must take every precaution to ensure you've got a proper/perfect CD before you try to use it.  You'd be surprised how many problems are caused by iffy CD burners, poor quality CDR's, or corrupted download ISO files.  To help ensure a successful burn, observe the following:

a) When downloading the ISO, ideally use a download manager.  A very good Windows based one is [GetRight]("http://getright.com/"), although that's shareware.  A good Freeware one is FDM, [here]("http://www.freedownloadmanager.org/").

b) After downloading, check the downloaded file's MD5 checksum against the published one on the Ubuntu site.  See [here]("https://help.ubuntu.com/community/HowToMD5SUM") for information on how to get your downloaded file's MD5 checksum, and [here]("https://help.ubuntu.com/community/UbuntuHashes") for the current checksum (also known as "hash") values.  Your dowloaded image must have the same checksum/hash value.  If it does not, it has been corrupted and must be re-downloaded.

c) Burn the ISO image to a blank CDR.  Make sure to use name-brand CDR's, and burn as slow as possible, to help ensure a good burn.  A good free Windows based ISO burner is ImgBurn, [here]("http://www.imgburn.com/").  

d) After burning the image to the CDR, verify the burn by booting it and choosing the "Check CD" option.  This performs another MD5 checksum check on the CD itself.  If it does not pass, then you need to burn another CD (and/or use another CDR burner driver etc.)

e) Only if all the above worked successfully can you have full confidence and try booting Ubuntu from the CD.

---

### Post by koongoo on 2008-07-29
this post is in reply to a few people. 

I have not tried the slowest burn speed.I will try that. 

The laptop is lower end laptop that probably was a higher end one "5years ago" so, i believe i will give Xubuntu a shot. 

When the computer would blue screen it would only stay up for a few seconds. then the Laptop would restart again. repeating the process over and over.

The model of this note book is a 
(Jetbook "Jetta is the new company name" 2200A)

---

### Post by snowpine on 2008-07-29
> **koongoo said:**
> this post is in reply to a few people. 

I have not tried the slowest burn speed.I will try that. 

The laptop is lower end laptop that probably was a higher end one "5years ago" so, i believe i will give Xubuntu a shot. 

When the computer would blue screen it would only stay up for a few seconds. then the Laptop would restart again. repeating the process over and over.

The model of this note book is a 
(Jetbook "Jetta is the new company name" 2200A)

I googled that laptop and saw that 64mb of ram is the standard. That is not enough to run even Xubuntu, sorry. If you have at least 128mb, you might be able to get Xubuntu loaded using the alternate CD, see this thread: [http://ubuntuforums.org/showthread.php?t=873112](http://ubuntuforums.org/showthread.php?t=873112)

---

### Post by gjoellee on 2008-07-29
it may be something about your CD burner or the CD's...

---

### Post by JoneYee on 2008-07-29
I work with Windows Server Customer's all day and I recommend this addon for ISO (not DVD) burning inside of XPsp2 or Vista.  I've never had a problem with it burning ISOs.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

May be worth a look, you may just be getting a bad burn. 

When i attempted to use the wrong distro x86 on an amd64 I lost PS2 kybd/mouse function during install, but didn't run into the errors you indicate.

---

### Post by ByteJuggler on 2008-07-29
> **JoneYee said:**
> When i attempted to use the wrong distro x86 on an amd64 I lost PS2 kybd/mouse function during install, but didn't run into the errors you indicate.

Just to comment on this:  64-bit (AMD64 aka x64 or x86-64) is fully backwards compatible with 32-bit x86 processors, so you can use 32 bit versions on ubuntu on 64bit processors if you wish (with attendant limitations on RAM imposed by 32bit addressing.)  Your ps2 keyboard/mouse problems wasn't therefore related to the 32-bitness of the install.

---

### Post by Bucky Ball on 2008-07-30
> 64mb of ram is the standard

If this is the case with your setup, stop right there! and do a search for 'Damn Small Linux'. That (along with some other 'barebones' opsystems) is it. The post before was right, you won't even get Xubuntu up on a machine with these specs and that is likely the cause of a lot of your problems.

When trying to install, the process is probably crashing your ram therefore the blue screen and other unpredictable issues (possibly why it cycles through restart, blue screen, crash endlessly - crams the ram, crashes it, then like a good little machine, restarts and goes through the whole screw up again). Look at the upside - Memory is getting cheaper! A gig will give you a new world of computing! lol :) good luck ...

---

### Post by Helios1276 on 2008-07-30
I had some problems when I first installed also, using Infrarecorder and burning the disc REAL slow made em' go away.

---

