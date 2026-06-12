---
title: "[SOLVED] Nervous Newbie"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by FireDancers on 2008-08-25
I've been reading through the forums & links from it trying to get a grasp and gain confidence to try ubuntu.

I downloaded & burned a CD and have tried to do the run Live CD thing.  That seems like the "safe demo" way to try ubuntu.  I would hate to screw up my computer by being curious.  I've read to back up all my Windows stuff first, but don't really know how to.  I figured I'd go ahead & try to run the Live CD, but haven't been able to get it to boot up.  I've gone into the BIOS and set it to boot from the CD, but it keeps booting Windows (although a black screen has popped up a couple of times which says it's booting the CD, but then Windows boots anyway).  

I've been spending a lot of time with this, and need to either get it working or just forget about it :confused:.  I really like the idea of being able to use open source software, and also not having to be concerned about viruses, and fighting the MS monopoly, etc.  I'm not very computer literate....I'd feel so dumb if I ruin my computer.


My computer seems like a great one for the "dual boot" since it has 2 hard drives.  The second one is totally empty.  I just don't want to think about that until after I've tried the Live CD version first.

There is a lot to read on the forum, but it's overwhelming.  


I guess you folks want to see a sentence end with a "?", right?


Okay, I need to be reassured that running the Live CD is the safest way to proceed.  Then I need help figuring out how to get it to boot up.  Btw, I did the verify test and the CD passed.

Did I give enough info to get some help?  

Hopefully this time tomorrow I'll be :) instead of :(.  LOL

thanks,
Glenn

---

### Post by aheckler on 2008-08-25
The LiveCD is perfectly safe. It will not touch your Windows installation in any way.

As for why you can't boot to the CD, I'm not sure. Someone a bit more knowledgable will be along shortly. :)

---

### Post by Too Late on 2008-08-25
Probably you have made some mistake when burning that CD. In Windows, go to My Computer and open that CD. Tell us what you see there, inside the disc.

---

### Post by aheckler on 2008-08-25
> **Too Late said:**
> Probably you have made some mistake when burning that CD. In Windows, go to My Computer and open that CD. Tell us what you see there, inside the disc.

He did say that he verified the disc.

---

### Post by Seanuntu on 2008-08-25
What happens when you try to boot from the live CD?

Does it just go directly to windows?  If so, you might need to change your boot order (in the BIOS), and set it to boot from CD.

If it just hangs, does it provide an error message?

What kind of computer do you have?  How old?

---

### Post by WRDN on 2008-08-25
How did you burn the iso to the disk?
I know of some people that have tried to burn it as a data disk, but this does **not** work. If you boot into Windows, and put the disk in, what appears?
A screen should appear allowing you to install Ubuntu using Wubi, find more information, or boot from the CD. Select the option to boot from the CD. Reboot and hopefully, it will boot from the disk.

---

### Post by Daveski on 2008-08-25
Do you have access to another computer you can try to boot the LiveCD? This will eliminiate the CD as being the problem - although 9 times out of 10 it is a problem with the CD.

Also, are you able to boot to any other (bootable) CD in your computer? The Windows CD for example? This will eliminate your boot process, computer BIOS settings as the problem.

---

### Post by Too Late on 2008-08-25
> **aheckler said:**
> He did say that he verified the disc.
Verifying the disc doesn't guarantee that you've burned that iso file correctly and made that disc bootable.

---

### Post by drsaamah on 2008-08-25
I second what WRDN suggests.  If Wubi is not auto-starting in Windows, then you probably burned the iso file onto the disc as opposed to burning a disc with the unarchived iso.  I had a friend that did this a few months ago and it took me forever to figure out what he had done wrong.

---

### Post by starcannon on 2008-08-25
The best way to verify data is with MD5SUM(apologies if you did this already), use this to verify the iso you downloaded(useful for this and any data you download in the future).

You can download a freeware utility for windows here:
[Download WinMD5Sum - Freeware Windows MD5 checksumming utility.]("http://www.nullriver.com/products/winmd5sum")

I also read that you can checksum from the windows command line here:
[http://www.brunolinux.com/01-First_Things_To_Know/Checksum_in_Windows.html](http://www.brunolinux.com/01-First_Things_To_Know/Checksum_in_Windows.html)
though I believe you still have to download the software for it.

For the Ubuntu Linux iso md5sum should return:
```
8895167a794c5d8dedcc312fc62f1f1f
```
That and other useful md5sum information can be read here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burning your Ubuntu Linux CD from within Windows is covered in a very nice How To here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
It also goes over the MD5Sum in that article(I wish I'd have found it first)

Okay that part said, I think the best bet for a new person who is worried about things is to do whats called a "WUBI" install. This lets you install Ubuntu from the Windows desktop; and has the added benefit of allowing you to uninstall it using the Windows Add/Remove Software Utility in the Windows Control Panel. The Ubuntu Disk you downloaded should have Wubi available right on it, if you prefer the latest Wubi installer and information, please read here:
[http://wubi-installer.org/](http://wubi-installer.org/)

Finally, don't hesitate to search these forums, search google(just throw the word ubuntu at the end of your query), and feel free to ask here. Were a very friendly bunch here at the Ubuntu Forums, and we've all been where your at now.

Good Luck, Welcome, and Hope to See You around the Ubuntu Forums!
~starcannon

---

### Post by maddave2008 on 2008-08-25
i also am a nervous newbie,just a thought but what speed did you burn the iso,i've found the slower you burn iso's the more reliable they are,use imgburn to burn your iso's and burn at 4x or even at 2x,hope this helps.

---

### Post by FireDancers on 2008-08-25
I tried going into the BIOS and clicked for the CD to boot first, then exited by pressing F10 to save.

There's no error messages.

My computer isn't very old.  It's an Acer Aspire w 320 gig HD & 2 gig of memory.  It has 2 DVD burners and a lot of USB slots and other card readers.  And I just got a highspeed connection last week. :)  



There is a problem sometimes with my DVD/CD drives not starting, or being read immediately when I click on "my computer".  I checked the device drivers and see 2 different "names" but I don't know which DVD/CD drive is which name.  I added the second one myself after buying the new computer because it was on my dead computer and I didn't want to trash it.  Maybe that's part of the problem?

---

### Post by Too Late on 2008-08-25
What happens when you go to "My Computer" and double-click that CD?

---

### Post by FireDancers on 2008-08-25
It says ubuntu-8.04.1-desktop-i386

but it also has the icon of one of the CD burner software programs which I tried to use to burn it (an unsuccesful one).  When I click "properties" the window in the General tab says only "ubuntu-8.04.1-desktop-i386" as it should.  The size reads 694MB (728,221,696 bytes)

What program should I open it with?


Also, I have had some trouble with my DVD/CD drives not always working when I insert a disc.  I went into the "device drivers" and there are 2 different names, probably because the sencond drive is an aftermarket from my old computer that I installed.  It says the drivers are good, but something causes them to often hangup instead of running. 

Not sure what to do to get them working correctly?

---

### Post by Too Late on 2008-08-25
Ok, that's very nice. There seems to be no other problem that your burning skills. Or, maybe your burning software is not so good. What software are you using? I mean, how did you actually burned that disc? Here's a guide how it should be burned: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto). At a glance, you must not burn that .iso file as data.

EDIT:
This happens so often. In my opinion, every burning software should have a feature which warns the user when he's going to burn a single image file into disc as data. The program should say something like this:
> Are you sure you want to burn the selected image file into disc as data? This operation will not make the disc bootable.

[ ] Don't ask me next time.

YES / NO

---

### Post by zamadatix on 2008-08-25
i tkae t you have tried both drives then. i had a similar problem on my laptop but it just turned out the cd player was half broken... it would still read the disc an sometimes work but not always... what program did you use to bun at what speed? (i use iso recorder light and very simple ot use)

---

### Post by FireDancers on 2008-08-25
I will try to reburn the CD with the reccomended software.  Maybe mine is wrong/bad , but it is labeled as "ISO file".

I'll post back after I work with it some more.

thanks,
Glenn

---

### Post by zamadatix on 2008-08-25
hmm just make sure you burn it slow 9sometimes i jsut burn them t 1x because its so darn annoying to reburn wiht my crappy burner)

---

### Post by FireDancers on 2008-08-25
Ok,

I just burned a new CD in the 2nd drive & tried to use the same drive to run it.  I used Infrarecorder this time to burn without any problems.

I went into the BIOS to make sure "boot from CD" was switched on.  For some reason it keeps reverting back each time I restart to "boot from Hard Drive".  That seems to be "a" problem, if not the problem?  F10 doesn't seem to make it hold.

Also as mentioned, I am getting a quick notice reading:

Verifying DPI pool
Boot from CD
Boot from CD_

Then the Window startup tune & icon come back....

What's wrong?

thanks,
Glenn

---

### Post by hyperhopper on 2008-08-25
A, I would recomend downloading wubi and trying it,which has been done on 2 of my computers and works like a charm. You can even change it from add/remove programs like a regular application. Or go to [http://infrarecorder.sourceforge.net/?page_id=5]("http://http://infrarecorder.sourceforge.net/?page_id=5") and select the iso and then burn it to a disc. I dont see why people say to go slow. I have made about 5 disks at 40X speed with no problems whatsoever.

---

### Post by hyperhopper on 2008-08-25
Gah you outposted me!
I was going to say infra recorder oh noes lololol

---

### Post by ingeva on 2008-08-25
A little late perhaps,

but have you tried pressing a key on the keyboard when the computer sais it will be booting from the CD?

On my Windows computer, it boots from the HD unless I do, even if the CDROM is the first boot selection in the BIOS.

---

### Post by cocodaclown on 2008-08-25
I'm a nervous newbie to m8, welcome to the club.

I decided to 1) ask for a Ubuntu disc to be sent to me 2) use WUBI.

WUBI worked like an absolute charm in loading Ubuntu. When using WUBI, place it in the same folder as your ISO, direct WUBI to it and just wait for the install to finish. Reboot, opt for Ubuntu when the screen comes up and prepare to start a learning curve like no other ive experienced. 
Everything seems fine except I cant get flash to work. Thats going to be my new thread in this forums right now........

---

### Post by estyles on 2008-08-25
(edit: I see you said that you used InfraRecord to burn it this time, so maybe you were able to burn it correctly?  If so, please verify that the disk contents are some folders and files, and NOT an .iso file...  If so, then kindly disregard the rest... :) )

Too many replies and I think you and a lot of people are missing that you (almost certainly, as far as I can tell) burned the .iso file to the drive as data.  The contents of your drive are just the .iso file, correct?  That's your problem, and that, as far as I can tell, is your only problem, so far.

You need to burn the .iso file as an image, not as data.  If you've done it correctly, you will see a few folders and files on the drive, *not* the .iso file.  Sorry to say that you may have made a few coasters, but that should solve your problem.  The actual mechanism for burning it as an image will depend on what software you are using to burn the disk.  I recall that when I first tried Ubuntu, I followed step-by-step the tutorial from [www.psychocats.net](www.psychocats.net).

In particular, follow the section on "Burning the ISO" from this page: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso).  Make sure you "Burn image", NOT drag-and-drop the .iso or something like "burn data".

---

### Post by Shippou on 2008-08-25
Here are my views (summarized):
1. Burn the .iso file, When you burn it, click on it. Please tell us your burning software for more precise instructions.

2. Boot from the CD.

3. Then you are set!

Mostly the problem arises from the CD burning. Most people burn the iso file itself, not its contents, so it ends up not being bootable.

Also, I suggest you use a CD-RW, so that when you mess up with the burning process, you can erase the CD (DVD-RW is so large).

Sorry for the post. I just read your thread.

Good luck in your Linux experience! :)

---

### Post by candtalan on 2008-08-25
> **FireDancers said:**
>  Then I need help figuring out how to get it to boot up.  Btw, I did the verify test and the CD passed.

How exactly did you do the verify test? The test I recall requires you to have the CD boot up in the CD drive anyway. So if it is booting in the CD drive to do a verify CD test, then I wonder why it is not doing the same thing in the same drive to simply boot the live CD?

Are you doing the verify in a different cd drive or even in a different machine I wonder?

Assuming you have burned the image file (slowly not fast) onto the blank CD, then if you have put the CD into the target machine and booted, and then chosen the verify CD option which will hopefully pass, then restart and boot the live cd - all in the target machine.

If you have used a different machine to boot and verify the burned CD as ok, then you would begin to suspect the cd drive in the target machine.
hth

---

### Post by estyles on 2008-08-25
> **candtalan said:**
> How exactly did you do the verify test? The test I recall requires you to have the CD boot up in the CD drive anyway. So if it is booting in the CD drive to do a verify CD test, then I wonder why it is not doing the same thing in the same drive to simply boot the live CD?

Are you doing the verify in a different cd drive or even in a different machine I wonder?


I'm assuming he means that he did an md5 sum.  OP - read my last post above and post back!

---

### Post by mr_andersen on 2008-08-26
I just installed Ubuntu for the first time.  I used a USB drive to do the install.  (I bought a Shuttle, no cdrom drive)  I followed the instructions a unetbootin.sourceforge.net.  

Very happy with the results, the install was flawless, only took about 25 minutes.  

I couldn't manage to get the OpenVPN gui working, but I can login to my VPN from the CLI.  

Perforce was a bit of a hassle, but finally managed to get that working also.  

Very happy so far.  My machine came with Foresight installed, after a couple logouts, my Network Manager got hosed and I couldn't recover, so decided to try Ubunutu.

---

### Post by FireDancers on 2008-08-26
> **candtalan said:**
> How exactly did you do the verify test? The test I recall requires you to have the CD boot up in the CD drive anyway. So if it is booting in the CD drive to do a verify CD test, then I wonder why it is not doing the same thing in the same drive to simply boot the live CD?

Are you doing the verify in a different cd drive or even in a different machine I wonder?

Assuming you have burned the image file (slowly not fast) onto the blank CD, then if you have put the CD into the target machine and booted, and then chosen the verify CD option which will hopefully pass, then restart and boot the live cd - all in the target machine.

If you have used a different machine to boot and verify the burned CD as ok, then you would begin to suspect the cd drive in the target machine.
hth






I just re-verified the CD using md5v12011 and it passed with o% errors.

While it was verifying I could not hear the CD drive running, but the process took about 6+ minutes.  After it passed I heard the CD drive spin some...I don't know what this means.

I will try to do a Live CD boot again now and see what happens.  The CD is still in the same computer & drive that I just used to verify with.  I'll report back in a few minutes.

thanks,

---

### Post by FireDancers on 2008-08-26
> **estyles said:**
> (edit: I see you said that you used InfraRecord to burn it this time, so maybe you were able to burn it correctly?  If so, please verify that the disk contents are some folders and files, and NOT an .iso file...  If so, then kindly disregard the rest... :) )

Too many replies and I think you and a lot of people are missing that you (almost certainly, as far as I can tell) burned the .iso file to the drive as data.  The contents of your drive are just the .iso file, correct?  That's your problem, and that, as far as I can tell, is your only problem, so far.

You need to burn the .iso file as an image, not as data.  If you've done it correctly, you will see a few folders and files on the drive, *not* the .iso file.  Sorry to say that you may have made a few coasters, but that should solve your problem.  The actual mechanism for burning it as an image will depend on what software you are using to burn the disk.  I recall that when I first tried Ubuntu, I followed step-by-step the tutorial from [www.psychocats.net](www.psychocats.net).

In particular, follow the section on "Burning the ISO" from this page: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso).  Make sure you "Burn image", NOT drag-and-drop the .iso or something like "burn data".





This last attempt didn't work either.

I think the quote above is probably the issue, so I'll try to determine if this is it and go from there.

---

### Post by FireDancers on 2008-08-26
YES!!  New burn got it running.

Everything's fine now.

thanks,
Glenn

how do I add "Solved" to the thread title?

---

