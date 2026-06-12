---
title: "Will I have to repurchase Windows?"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Morningleaf on 2012-04-01
I am going to use Ubuntu to save some files from my broken laptop before doing a complete format in an attempt to fix it... will doing this install Ubuntu? If so, will I have to repurchase windows?

---

### Post by tehchibipanda on 2012-04-01
Well, if you need to do that, I would recommend installing ubuntu on a separate partition. This will enable you to dual boot, and you can browse to your files on your ubuntu partition. Then you can do whatever you need to do afterwards to fix your laptop. Don't totally delete it; dual partition. Or (I've never tried this one myself) try a live CD/USB and see if that works.

---

### Post by BertN45 on 2012-04-01
You do not have to re-purchase Windows. But make sure that you have a CD/DVD with Windows. Sometimes Windows is put on a separate partition on your HDD, make sure you do not destroy that partition. For Acer and some other brands you can save that partition to cd/dvd, do so before you install Ubuntu.

If you loose your windows install partition, it will be very hard to get a official Windows system up and running again.

---

### Post by PhantomTurtle on 2012-04-01
Also make sure you have the product key, or else you cannot install.

---

### Post by Morningleaf on 2012-04-01
So windows was already installed when I got my laptop. I burned Ubuntu onto a disk from my desktop and am going to use it to get a few files from said laptop to a flashdrive before formatting and hopefully fixing the laptop... so what will happen with windows? Sorry, I'm technologically challenged.

---

### Post by Jerry N on 2012-04-01
You will run Ubuntu from the CD, you do not need to install it.  Use the file manager to copy the files you want to save to a USB flash drive.  (By the way, you should already have saved backup copies of any important files) After you have copied your files, you can then go through the Windows restore routine, that is either use the restoration DVD set you should have made when you initially set up the computer or use the restore partition on your hard drive.  

Please don't be offended but I would suggest you find someone knowledgeable in these matters to give you "hands on" help, maybe a savvy teenager.  

Jerry

---

### Post by GregA on 2012-04-02
MorningLeaf., 

It's likely your plan may make (whatever the situation is( . . . , much worse)).

Here's a safer method to go:

1.   Go to Distrowatch.com and download the latest "Partition Magic" live image.   Partition Magic is now one of the best 2 or 3 Live Linux distro's.  It will load into and run directly from ram memory versus the CD - - much much faster and actually usable.    You can use a couple of apps in Partition Magic to recover your files, and eventually, to repair or fix your hdd.

2.   Go to Distrowatch and get the latest beta for Kubuntu 12.04.   It's pretty stable (from what I read).   IF you use Kubuntu's live CD, it's much slower than Partition Magic, but it will allow you to see how compatible your laptop actually is with Linux.

It would also help if you provided some info on you laptop specs, especially the video info (intel integrated, nVidia, ATI, etc.??).  Likewise, it could also be very helpful if you fully disclosed what the issue is with your laptop.

One additional question, . . . . why do you want/need Windows?  Games, job related apps, etc., etc.??? (because if you don't need Windows, you can reformat your entire drive and install Linux at the same time - - provided you have a clear understanding of compatibility.

---

### Post by anewguy on 2012-04-02
It sounds like maybe you don't understand partitioning and formatting.  As already mentioned, most laptops (and a lot of desktops now also) come with a separate partition on the disk that is for resetting your PC back to the way it was when delivered by the manufacturer.  Many of these require you to run a program in Windows when you first get the PC that makes recovery disks to use that partition.

So, before you worry about formating, you need to be very aware of what you have on your PC.  Did you remember ever creating a set of recovery disks?  Did the PC come with 1 or more recovery disks?

What is the make and model of your laptop?  We can try to look it up on the manufacturers website to see what it has for emergency recovery - on some PC's it's as simple as pressing a key while the system is attempting to boot so that it starts the recovery instead.

This recovery would normally restore your PC back to the state it was in when delivered to you.  This means the entire disk would be wiped and Windows reinstalled.

However, without such a recovery partition and/or disks, you WILL lose Windows if you just format.  I cannot more strongly recommend you NOT format until more research is done.

So, please provide the answers to the questions I have asked, and also describe what the problem is that makes you think you need to format to begin with, and we'll go from there.

Dave ;)

---

### Post by Morningleaf on 2012-04-02
Yeah, I have absolutely zero idea what I'm doing... I'm just going off what I've heard on here and seen on Google because I have no computer smart friends. I have a HP ProBook 4530s that now refuses to start. I turn it on, the HP logo screen pops up, I go to the windows logo screen, and it freezes. Then there's a quick flash of blue screen and it takes me to the repair or start normally mode, but if I choose start normally it just does the same thing over. Repair does not fix it; I have also tried the restore to an earlier point in time and tried to use safe mode, neither of which have helped. I heard somewhere that I might have somehow deleted the file that allows my laptop to boot up? I dunno; I have no idea whats going on. I've never ran backup, is the problem, mostly cause I'm an idiot and kept putting it off. So basically I want to get some files (From whatcI've heard so far it sounds like Ubuntu would work for that? Thats the main reason I'm on this forum for this question) then I keep hearing format and return to factory settings... is there a difference between the two? Or are they the same?

---

### Post by kurt18947 on 2012-04-02
I don't have any advice on resuscitate your current Windows install.  If you have a sticker somewhere - often on the bottom of laptops and you can  read the numbers - you possess a valid license *for that windows version* e.g. home premium or professional and might be able to find install media.  I've used this download site and yes it's legal AFAIK.

[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)

I downloaded the appropriate .iso file, created a DVD with Brasero in Ubuntu and installed using the DVD.  Without a valid license the windows install is good for only 30 days.  This can be useful for people like yourself whose machine has a valid license but no install media.  Unlike factory restore media,  the above download may not have machine specific drivers.  Your ethernet, wireless, sound etc. may not work without additional stuff.  If you can connect to a network, Windows Update might be able to find some or all the drivers.  You should be able to find others on the manufacturer's web site.  The key is getting a network connection.  If you can get a network connection using an Ubuntu Live CD/USB you can download the correct .exe files for your machine, save it to a flash drive and use the flash drive to install the drivers in Windows.  Good luck.

---

### Post by sudodus on 2012-04-02
As you have been told by several other people, I strongly advice you to run a linux operating system from the CD or USB drive.

It can be a dedicated repair system like Partition Magic, or an install Ubuntu system, that you can 'test' live without installing anything. In both cases you can run the file browser (similar to Microsoft Explorer), find the important files and copy them to an[other] USB drive (flash drive or HDD).
     -o-
By the way, maybe you can try to run
```
chkdsk /f
``` from the windows repair mode that you found before:
> Then there's a quick flash of blue screen and it takes me to the repair or start normally mode, but if I choose start normally it just does the same thing over. Repair does not fix it

---

### Post by anewguy on 2012-04-02
First off, there is a BIG difference between formatting and returning to factory defaults.  Formatting will make the disk look like new - that is, nothing on it.  Restoring to factory default will use one of the recovery methods I mentioned and this will first format your drive then reinstall everything from either the recovery partition or from recovery disks back to the way things were when the PC left the factory.

So, we need to address 2 problems here.  First is getting you to a point where you can copy any file you might need to from the hard disk.  Second is to see if we can get Windows back for you.

For the first choice, yes Ubuntu can help you with that.  However, since you've always had just Windows on the PC you don't actually want to INSTALL Ubuntu, but instead run from one of the Live modes (where you are running from either a USB flash drive or from a CD).  You don't want to install for one big reason right now:  You would need to repartition your drive.  A partition is like a logical piece of your disk drive.  What you may have right now is a partition containing recovery and a partition containing Windows.  To actually install Ubuntu, you would need another partition, and where would the space for that partition come from?  From shrinking your Windows partition. Right now this isn't a good idea because the drive has not been defragmented in Windows first (the normal procedure is to run defrag TWICE in Windows before shrinking the partition).  If a defrag isn't run the possibility of data loss goes way up.  Since your data isn't backed up and you can't boot Windows, that means you can't run defrag and you can't afford to take the chance on losing any data.

So, by using another PC and downloading the installation CD image, you can then either burn a CD to run from or burn it to a flash drive (using unetbootin - there are how-to's on the net as well as many posts in the forum - need help - just ask!). I would suggest a flash drive for the following reason:  your only backup mechanism is probably going to be copying the Windows files you want to save to CD's, and if you are running from a CD I don't think you'll be able to burn a CD - perhaps with swapping CDs around, but since you are not tech savy there is no need to complicate things.

Please see this link for information on creating a bootable flash drive - I think that flash drive needs to be a minimum of 1gb in size.  It will be option 2, usb and select "Show Me How".  Obviously this will need to be done on another PC with net access.  You may end up installing unetbootin on that PC in order to build the flash drive.

[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")


Also, check the BIOS setup for your PC to be sure it allows booting from USB.  Any new or relatively new PC should be able to do that, but you want to make sure.

After you've done that much, post back and we'll help you through copying the files you want.  

In the mean time, I need to check to see if a CD burning app is included on the "live" option image.

Since you are not tech savvy I know a lot of the posts in this thread just leave you going "huh???".  Hopefully we can walk you through this simply and 1 step at a time.  

Remember - DO NOT *INSTALL* UBUNTU OR ANYTHING ELSE!!!

BTW - can't remember if you said (I think the vote is no) but do you have a Windows CD?  If so, you could try the recovery console from it as well.

Dave ;)

BTW - I only recommend saving the files to CD for one reason:  if you use a CD/R you can't overwrite the files.  Yes, you could boot CD and save to USB flash drive, and if that's what you want to do that's fine.  Just be sure to have enough USB flash drives or at least 1 large enough to hold everything you want to copy, and then you'll need to be extremely careful not to reuse that drive for something else before everything is back to the way you want it.  That's all - just what ever you want to do it and you are comfortable with.

---

### Post by Mark Phelps on 2012-04-02
> **Morningleaf said:**
> ... my broken laptop ... If so, will I have to repurchase windows?

If your laptop came with Windows preinstalled, then NO, you will not have to repurchase it; however, that license is for that laptop ONLY. It's not just Windows version-specific, it is actually PC-specific.

If the Windows version was activated in the BIOS (OEM PC's usually are), then you can replace your hard drive, and once you install Windows on it, it should reactivate without problems.

If you have no way to restore the Windows version, and the laptop is still within warranty, you should contact the supplier and see how much they will charge you for a set of Full-Restore disks.  That's going to be a LOT less than going out and purchasing a retail copy of Windows.

---

### Post by Morningleaf on 2012-04-02
I already have Ubuntu burned to a disk; I did that last night... I was just going to use that to boot, then put my files on a USB. But you're saying that I need to put Ubuntu on the USB, right? Sorry, like I said, I have no clue what's going on :p Oh, and the laptop does have a sticker with the Windows 7 product key and everything.

---

### Post by Jake5 on 2012-04-02
No, you can use the cd. Dave was just explaining that you could run it from a usb stick, and how to do so. What he is saying is that you can put a ubuntu live variant onto a usb stick, boot from the usb stick, and use your cdrom to burn permanent copies of your important files onto a cd-r or two. A great idea...thanks Dave and I'm glad to see you back buddy.

---

### Post by anewguy on 2012-04-02
It's perfectly fine to boot from the CD and copy to USB flash drive(s) as well.  Either one is fine and will work.  I just thought if you wanted to make sure you have permanent copies.  Just remember boot the "Try Ubuntu" option, *not* the install option.  Using the file manager you should be able to copy the files from your Windows hard disk to flash drive(s).  If you have any problems or questions at all doing so, please post back and we'll help you out.

Also, after you get your files copied to flash drive(s), post back and we can see what we might be able to do to get your Windows restored.

Dave ;)

---

### Post by anewguy on 2012-04-02
I've looked at HP's pages for your laptop, plus some additional pages on the net.  If your PC was running from the factory install - in other words, you never installed Windows or any other OS yourself, you'll be able to recover Windows after you save your files.  Be sure to save *ALL* the files you think you might need as none of those will be available that I know of after the restore.

Once you have everything backed up that you want, restart the PC and just keep pressing the F11 key.  Eventually the system recovery should come up.  If there is a repair option try that first, otherwise use the reset to factory defaults.  Repair will hopefully leave your programs and data intact, while the reset to factory defaults will not.

This is based on my understanding that you just want to use ubuntu to back up your files at this time, but you want to recover and run Windows.  I'm not a linux bigot, so I'm glad to try to help you get to that point.

Dave ;)

---

### Post by Morningleaf on 2012-04-02
One last question before I try this... I'll have to redo Norton, right? I did purchase that; it wasn't already installed.

---

### Post by anewguy on 2012-04-02
If there is a repair option in the recovery, perhaps not.  But I would say probably so.  I don't have an HP computer, so I've never seen the recovery option to know what's there.  As I said, be sure to backup everything you want first.  I would boot/run from the LiveCD, copy the file to USB, then maybe wait a day before continuing.  Why?  To tell the truth, I ALWAYS forget something and end up wiping stuff out before I realize it.  If you're like me, that extra day might make something else come to mind.  If you want your email, etc., backed up, be sure you know where your user-specific stuff really is - it used to be buried down inside a hidden folder prior to Windows 7.  I have Windows 7 on my laptop, but have never gone looking for any of that yet, just simply because I use Ubuntu on my desktop probably 99.99% of the time.

Best of luck, and remember - if in doubt, stop and ask back here.  We'll try to find a solution for you!  ;)

Dave ;)

---

### Post by sudodus on 2012-04-03
After saving your important files, but before reinstalling Windows, maybe you can try to run
```
chkdsk /f
``` from the windows repair mode that you found before:
> Then there's a quick flash of blue screen and it takes me to the  repair or start normally mode, but if I choose start normally it just  does the same thing over. Repair does not fix itThis simple way I have repaired several Windows installations.

---

### Post by HermanAB on 2012-04-03
Howdy,

I have been using Linux since about 1996 and have been using Linux almost exclusively since about 2002.

The long term solution to Windows issues is to make a virtual machine using either VMware or Virtualbox.  This provides you with a machine independent copy of Windows that you can carry with you wherever life takes you.  I have a WinXP VM, that I used for tax returns and whatnot and whenever I get a new machine or re-install Linux, I just copy it over.

---

### Post by FulciLives on 2012-04-03
Just boot up the computer with the CD of Ubuntu that you made and it should boot into the Ubuntu desktop (just make sure you select "Try Ubuntu" and not "Install" as someone else already said).

Then use the file manager to find the files you want and copy them to a USB stick or a USB hard drive etc.

After that my suggestion would be what someone else already mentioned:

1.) Go to this website: [CLICK HERE](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)
2.) Download the version of Windows that your license key is for which most likely is Home Premium 64-Bit (but it won't work unless you download the right version)
3.) Burn that to a DVD (I think the Windows 7 ISO downloads are all DVD size) and boot from it. Do a "clean" install using your License Key. By a "clean" install I mean tell it to wipe the hard drive and reformat it and this will give you a fresh new install of Windows 7.
4.) If all that works make sure you DO NOT ever lose that DVD nor the Licence Key. In fact to be safe I would make two copies of the DVD and put them in a safe place (also write down you product key and put it with each disc).

Oh and after your clean install ... go to the website of your laptop's manufacturer as they probably have a place to download specific drivers. For instance your wireless internet may not work without the driver. Be prepared for that. In other words have an Ethernet cord so you can plug the laptop directly into your internet modem or router (if you use a router).

---

### Post by anewguy on 2012-04-03
The chkdsk is a great idea - try it!

Herman:  great idea - but in this case the OP doesn't have a disk to install to a virtual machine, only the recovery partition.

As for these suggestions of downloading a copy of Windows (1) the op shouldn't need it - they should have everything they need in the recovery partition (2) we don't advocate downloading "bootleg" copies of ANY OS.  Please refrain from posting these links again.  This type of download is (1) illegal (2) guaranteed to be full of viri, trojans, what have you at a very deep level.

---

### Post by Morningleaf on 2012-04-03
How do I do the chkdsk?

---

### Post by CharlesA on 2012-04-03
Depends if Windows is actually starting or not.

I would suggest checking out a Windows forum, such as:

[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by WasMeHere on 2012-04-03
> **Morningleaf said:**
> ... I have a HP ProBook 4530s that now refuses to start. I turn it on, the HP logo screen pops up, I go to the windows logo screen, and it freezes. Then there's a quick flash of blue screen and it takes me [COLOR="Red"]to the repair or start normally mode[/COLOR], but if I choose start normally it just does the same thing over. Repair does not fix it; I have also tried the restore to an earlier point in time and tried to use [COLOR="Red"]safe mode[/COLOR], neither of which have helped...

> **Morningleaf said:**
> How do I do the chkdsk?

I have checked what is available during boot of my Windows XP. You wrote that you have Windows 7, but these things might be similar, at least you could try.

Press the F8 key during boot (before you get the screen with the Microsoft logo). Then you should come to a text menu with several options. You may not succeed to get there at the first attempt, you must press F8 at the right moment (early enough).

- Normal or standard mode

- several Failsafe modes. You might try the text mode alias command line, MSDOS or DOSprompt mode among these ones.

- repair mode (I don't know exactly what this mode is doing, but if you can get it going and start a text mode window, you may succeed.

Anyway, in the text window, write the following text

```
chkdsk /f
```
and start running it with the Enter key.

Probably you are starting that window in the system partition, which is usually [COLOR="Red"]volume C:[/COLOR], but you can check that running
```
dir
``` and try changing with
```
C:
```
```
D:
```
etc and search for the volume containing the directory WINDOWS
```
dir \WINDOWS
```

If the 'F8 method' doesn't work, you can move the hard drive to a working Windows computer (for example connect it via a USB adapter) and identify which volume it is, maybe E:
In that case run
```
chkdsk /f E:
```

Finally, if you don't want to take the HDD out from the laptop, then reinstalling is the way to go, but ***first you must recover your files***.

---

### Post by FulciLives on 2012-04-03
> **anewguy said:**
> The chkdsk is a great idea - try it!

Herman:  great idea - but in this case the OP doesn't have a disk to install to a virtual machine, only the recovery partition.

As for these suggestions of downloading a copy of Windows (1) the op shouldn't need it - they should have everything they need in the recovery partition (2) we don't advocate downloading "bootleg" copies of ANY OS.  Please refrain from posting these links again.  This type of download is (1) illegal (2) guaranteed to be full of viri, trojans, what have you at a very deep level.
They are not bootleg releases. They are clean OEM releases provided to Microsoft partners. Many websites posted those links advocating people to download the OEM ISO for their License Code. Why? Most manufacturers do not provide Windows discs anymore. That's complete BS. If you bought a computer with Windows pre-installed and have a valid license then you should have a disc.

Again they are clean OEM ISO's that will NOT work without entering a valid license key.

---

### Post by anewguy on 2012-04-03
> **FulciLives said:**
> They are not bootleg releases. They are clean OEM releases provided to Microsoft partners. Many websites posted those links advocating people to download the OEM ISO for their License Code. Why? Most manufacturers do not provide Windows discs anymore. That's complete BS. If you bought a computer with Windows pre-installed and have a valid license then you should have a disc.

Again they are clean OEM ISO's that will NOT work without entering a valid license key.

     Read the thread - he has windows on his recovery partition as long as nothing has been touched.  The thread you link to does NOT link to a Microsoft site - therefore they can't be trusted, simple as that.  Even bootleg copies can require a key, even what are "valid" copies can be compromised.

     Now, please quit posting what is for now irrelavent.  Follow the thread, follow the the replies from the OP - they are trying to do one thing at a time.  Throwing things like this in the middle of a thread only confused things.

---

### Post by anewguy on 2012-04-03
ooppsss

---

### Post by anewguy on 2012-04-03
Olle Wiklund: Thanks for the information.  Currently, we are just trying to be sure the OP gets all of the files saved they need to.

For everyone:

After that they can run chkdsk, as others have already mentioned, if they can get to the recovery console.

According to the net, there should be a recovery partition on the disk and is accessed via F11 at restart of the machine.

This user is very new at this and a little leary - can you blame them?  Let's try to keep things to one step at a time.  The current step is being sure everything is backed up that they want.  This is the step using an Ubuntu LiveCD, and Ubuntu is new to the user as well.

You see, if we keep this simple, straight forward and step by step instead of trying to add everything at once, it will accomplish 2 things:

(1) help a very leary user
(2) hopefully leave a good feeling about Ubuntu - maybe they'll come back and try it at some point in the future even if they do want just their Windows installation back for now.

So please, until the OP posts back the backups are complete, read the thread, follow the thread and leave things dealing only with the current step.  Right now, unless the OP posts back with questions on the backup, they are doing the backups.  So that should be covered.  After the OP posts back that the backups are complete, it should be again one step at a time - the first will be to try chkdsk via the recovery console of their current installation.  If that fails, the next will be to use the recovery partition.

This is a novice user with a laptop - I extremely doubt they are going to want to remove the drive, place it in another system (most probably with 2 adapters - 1 for the physical drive, 1 to convert the interface to that used in a desktop if needed).

So, please, everyone, keep with the flow of the thread and post only very simple instructions for a novice user.  Until something is said in the thread, please everyone refrain from posting.  We'll walk this user through carefully.

Thanks for the input and patience prior to posting.  I am by no means some form of guru here - just trying to patiently and simply walk the OP through the steps.  If I get to a point where I don't know what should be tried, I will post asking for additional input.  Until then, let's just follow the intent and flow of the needs of the OP.

thanks
Dave ;)

---

### Post by Mark Phelps on 2012-04-03
> **anewguy said:**
> ... the first will be to try chkdsk via the recovery console of their current installation. ... 
Problem is, there is no Recovery Console in Win7.  That was left back with XP.

However, they CAN boot to a command line.  That's typically done by pressing F8 repeatedly, which gets them into SAFE mode, and from there, they can choose the Command Line option.

Once in the Command Line interface, they can then enter the chkdsk commands.

---

### Post by anewguy on 2012-04-03
Thanks Mark - I've never screwed with Windows 7 - it just came on my laptop and I'm waiting for the 2-year warranty to be up before switching it to ubuntu.

So, OP:

Follow Mark's advice on how to get to the command line, then try the chkdsk from there.

If no success, post back and we'll start the recovery.

Again, right now the user is just working on backing up the files - let's tackle 1 thing at a time here so as not to confuse them.

---

### Post by Morningleaf on 2012-04-04
Almost done with my files... I'm doing the chkdsk next?

---

### Post by anewguy on 2012-04-04
Yep - follow Mark's advice above on how to do that.  If that works - please post back and let us know.  If not, post back that it didn't and we'll go from there - probably the system restore.  For now, just follow what Mark posted and post back the result.

Dave ;)

---

### Post by Morningleaf on 2012-04-04
I don't think the chkdsk is going to work... I went to the F8, then Safe Mode with Command Prompt, but in the middle of loading the windows files it stopped, flashed blue screen again, then went back at the hp screen and the start normally or launch repair.

---

### Post by anewguy on 2012-04-04
Not sure what launch repair does - you may want to try it.  Post back with the result from that and we'll go from there.

I hope you don't mind, but we're trying to keep things as simple and step-by-step for you as we can, as it sounds like you probably not a technical person (and believe me, there's nothing wrong with that!!).

Dave ;)

---

### Post by Morningleaf on 2012-04-04
Heh, believe me, I don't mind... I am terrible with technology. I've tried the launch repair a couple of times... it lets you either shutdown or try a list of advanced options like restore to an earlier point of time, none of which have worked. They all end up just restarting the laptop, then the whole thing starts over.

---

### Post by CharlesA on 2012-04-04
Definitely sounds like that install of Windows is hosed.

---

### Post by cmcanulty on 2012-04-04
Here you can download windows 7 iso s to burn to CD then use your key
[http://www.windows7hacker.com/index.php/2009/11/download-retail-windows-7-iso-from-official-website/]("http://www.windows7hacker.com/index.php/2009/11/download-retail-windows-7-iso-from-official-website/")

---

### Post by anewguy on 2012-04-04
Don't download a copy of Windows.  Instead, restart your PC and as it is booting (not the Windows boot - that will be too late) just keep pressing the F11 key.  This should bring up the restore to factory defaults option. If not, post back with what it shows.

Dave ;)

---

### Post by anewguy on 2012-04-04
> **CharlesA said:**
> Definitely sounds like that install of Windows is hosed.

Yepper!  Pretty much sounds that way.  According to the net, there is a recovery partition and SUPPOSEDLY you don't need any disks, and should reset to factory defaults.  The OP should be trying that now.

If that doesn't work, well, I'll leave it up to them if they want to (1) download a copy of Windows - non-Microsoft site so no matter what anyone says they are ALWAYS suspect (2) Contact the vendor to see if they have some sort of restore disk(s) that if not free may at least be cheaper than a new copy of Windows or (3) purchase a copy of Windows (and eat the cost). 

Hope things are going good!

Dave ;)

---

### Post by anewguy on 2012-04-04
BTW - here's just one of the other threads on the net I found about this:

Paul_Tikkanen
Regents Professor Paul_Tikkanen Regents Professor
Regents Professor
Posts: 9,864
Registered: 07-13-2010
Message 2 of 11 (9,246 Views)
Report Inappropriate Content
0
Re: HP Probook 4530s Recovery Manager
[ Edited ]
Options

08-12-2011 08:17 AM - last edited on 08-12-2011 08:19 AM

Hi, Dilan:

 

To the best of my knowledge this software was not included for your notebook. Nor can you download it from your notebook's support page.

 

Your recovery options consist of using the F11 key to launch the recovery process, or purchasing a set of Quick Restore DVD's (which I strongly recommend you do) for $10, if you live in the USA or Canada. Elsewhere in the world the costs range from free (such as in the UK) to more than $10.

 

The Quick Restore DVD's should have everything your recovery partion has, with a few exceptions perhaps.

 

To order recovery disks in the USA/Canada, you need to have your serial number and model number handy and call:

 

Call HP at 1-800-952-7689, option 1 (ordering restore disks is part of the list in the option).

 

If you need the information to order for outside the US/Canada, you can contact HP by phone for the country you live in at the link below. If they have a separate number for business PC's/notebooks, call that number.

 

[http://www8.hp.com/us/en/hp-information/summary/ww-contact-us.html](http://www8.hp.com/us/en/hp-information/summary/ww-contact-us.html)

 

Additionally, you can make an complete system image and recovery startup CD by using the Windows 7 backup program.

 

Paul


So, if the restore fails, you MAY be able to purchase a set of recovery disks for $10 - that's a LOT cheaper than a new copy of Windows!

Dave ;)

---

### Post by CharlesA on 2012-04-04
> **anewguy said:**
> Yepper!  Pretty much sounds that way.  According to the net, there is a recovery partition and SUPPOSEDLY you don't need any disks, and should reset to factory defaults.  The OP should be trying that now.

If that doesn't work, well, I'll leave it up to them if they want to (1) download a copy of Windows - non-Microsoft site so no matter what anyone says they are ALWAYS suspect (2) Contact the vendor to see if they have some sort of restore disk(s) that if not free may at least be cheaper than a new copy of Windows or (3) purchase a copy of Windows (and eat the cost). 

Hope things are going good!

Dave ;)
Yeah, I did that before on one of my other laptops. If you mash that key, it *should* boot into the "recovery mode" thing.

---

### Post by Morningleaf on 2012-04-05
Oh my gosh, thank you SO much, everyone!!! My laptop is back up and running :D

---

### Post by anewguy on 2012-04-05
Glad to hear it!  Thanks to everyone who pitched in here!  I assume the chkdsk worked?

Dave ;)

---

### Post by sudodus on 2012-04-06
> **Morningleaf said:**
> Oh my gosh, thank you SO much, everyone!!! My laptop is back up and running :D
Please let us know ***how*** you solved your problem :-)

---

