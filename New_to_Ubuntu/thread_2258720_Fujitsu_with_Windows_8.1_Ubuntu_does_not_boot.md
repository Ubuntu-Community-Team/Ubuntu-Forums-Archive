---
title: "Fujitsu with Windows 8.1: Ubuntu does not boot"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by doit2 on 2014-12-29
Hello guys,
At 1 am i had yet another problem with windows 8.1 and ultimately decided to try linux.
I put the N in the Noob but am stubborn as a bull, so have been watching "introductions" and reading manuals on how to carefully make the switch without destroying my lifework.
So far i started backing one old computer up and have been trying to get Ubuntu for a usb-test-drive on a quite-new Fujitsu lifebook with the notorious win 8.1.
Now although the com reads the usb driver, and i managed to use the simple instructions on how to attach the ISO file on top of it, and although the driver on my computer now reads "F: install ubuntu" - when i loaded up the computer nothing new appeared. Just that old microshit. I tried to F2 and F12 everything and got to that naked version of things. over there i tried to be smart and switch the booting order from Windows to "Cruzer" (It didn't read ubuntu from some reason!) and since then things got a bit worse, as of course neither Windows nor Ububntu loads up.
So it's already 6:30 Am (Where i live), and im tired and Ubuntu-less.
A Little bit of help from my stranger-friends, perhaps?

---

### Post by Jacob_Goff on 2014-12-29
Go to your bios system and then go to your boot order. If you don't know how to do so, when your computer starts up, press escape amd it will show you a list of options for your computer keys to map out where your bios system is. My bios system is F10 by default. I went all Ubuntu today and removed my Windows 7 because I thoroughly dislike it. I see you set up your bootable usb drive, but you need to leave the iso unpacked in itself and only open it with UNetbootin. I recommend this program because I know for a fact there there is nothing dangerous about it. I also recommend, if you dislike Windows 8 to install Ubuntu to the flashdrive, go to your partitions, and delete the hard disk storage that holds Windows files only. With that being said, I have told you to use a thumb drive for the simple reason is that it is secure from being erased on your flash drive so long as you don't toggle to delete Ubuntu from it. Next step is to check to see that you have no operating system on your computer. Let me mention before you remove your operating system that I am not responsible if you don't check to see if Ubuntu works on your thumb drive first. If it does, congratulations! Now, I want you to do me a big favor, and this is your favorite part... Since at this point you have no operating system, go ahead and boot from the flash drive. Once you have turned on your Ubuntu Linux, you won't have internet until you set up your connection which you will need an adapter compatible with Linux in the first place. Do me another favor and check around the forums and see for yourself if there is problems with what you have already before you do this next part, because someone might've already fixed it. If not, here's a simple solution... I had to do this myself because I have to admit, I made this stupid move myself and installed Linux to my computer before I was ready for this. If you did what I did, that's okay, there's an easy fix for this. I want you at that point to do yourself a favor and clear the partitions and start from your usb again if this has happened to you like it did for me. Then, moving on once you've come back to this part, I want you to click "Install Ubuntu" and the version you downloaded and installed to your usb should be there to click on, not the most recent one... Please note that.You may also want to know that you can update from an earlier version, there is no limits to your updates as long as you have the right computer and the parts for it. If you don't, that's okay, just enjoy what you have and be grateful that you have a computer with wonderful software for ages to come even if it's outdated if you don't have the resources or money to get a new computer for the newer versions. I still have my other PCs on earlier versions because they are at their peek, and I have accepted it. Hopefully this was helpful to you, thank you for listening to everything I have to say, it brings me great joy to help a fellow newcomer with the operating system, since I've had mine for less than a couple days now. I am also going to college for this stuff, so I have the books and the teachers for just about any question you could ask and I will find every last person an answer even if I have to stay up days-on-end. I've been dealing with computers, software, and operating systems my whole life.

---

### Post by oldfred on 2014-12-30
Couple of other threads, not many Fujitsus.

If you have to set password be sure to never ever lose that.

 Some systems require password to turn off UEFI
Fujitsu lifebook ah512. Secure boot options blocked in bios - UEFI password required
[http://ubuntuforums.org/showthread.php?t=2171114](http://ubuntuforums.org/showthread.php?t=2171114)
 Fujitsu Lifebook A512 [SOLVED] Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 
[http://ubuntuforums.org/showthread.php?t=2254442](http://ubuntuforums.org/showthread.php?t=2254442)

Many more UEFI links in my signature below.

---

### Post by QIII on 2014-12-30
My advice?

Get some sleep.  :)

It's not worth that kind of misery.  Come back to the forums when you are rested up and not frustrated.

---

### Post by doit2 on 2014-12-30
Guys,
Thank you so much for answering so quickly but to my sorrow, so far, I have only more difficulties:

0. Perhaps it's best to clearly state my intention: Im a very suspicious and caution user. Just like I don't trust Windows, I don't trust Linux or Ubuntu just because "It free and seems cool". That's why even before i pick dual-boot or replacing one OS in another, I wish to backup everything and test Ubuntu directly from the outer device. I saw that's possible here: [http://www.techradar.com/news/software/operating-systems/beginner-s-guide-to-linux-where-to-start-1066778](http://www.techradar.com/news/software/operating-systems/beginner-s-guide-to-linux-where-to-start-1066778)
I wish to do that also to make sure Ubuntu reads my wireless connection, as this is the main problem since i "updated" the computer to Windows 8.1. But like i mentioned, im stuck. My Fujitsu Lifebook responds to the USB stick ONLY from inside windows and not from the start up "Black screens before OS start working" (I have a word missing here, i guess).

1. Now because im new to all this, I don't understand even the basic language you guys use to help me. I checked "BIOS" and found it's more related to hardware. I Didn't understand why it's recommended to disable it, and how to do so from windows 8.1?

2. Likewise, I couldn't understand how to use the threads our lovely moderator shared here. As i said, i read and heard many Introductions and frustrating enough they didn't say a lot about BIOS, UEFI, or their relation to Ubuntu. Also, i still don't know which definition you mean in [COLOR=#000000]partition. [/COLOR]If you mean i got to divided my C memory, please explian why. I also don't know how to do so. One you-tube instruction did show this option from Ubuntu installation manager through the "Something else" option. As firstly i wish to test Ubuntu from and outer device, IM STIL O-SO-FAR-AWAY from that stage.

3. In addition, the backup to the old computer (ASUS Notebook) has failed multiple times after 57% backup (about 75GB) With "An Input/output" Error. The Error code is Ox807012D and i have no idea what to do from here.

Guess i need a hand-by-hand from mummy or something, as i feel like a 3-year-old baby in kindergarten, in China.

---

### Post by Mark Phelps on 2014-12-30
> 3. In addition, the backup to the old computer (ASUS Notebook) has failed multiple times after 57% backup (about 75GB) With "An Input/output" Error. The Error code is Ox807012D and i have no idea what to do from here.

Let's tackle this first -- as a backup is needed before you consider replacing anything...

That error code indicates filesystem corruption on the target drive, most likely due to hardware sector problems.  The one thing that might fix this is running CHKDSK on that drive -- which MUST be done from Windows or from a boot disk that will run Windows apps.  Can't be done from Linux.

To do that from inside Windows 8.1, do the following:
1) On the Start screen, click the search icon on the upper right and enter "check disks"
2) That should result in two options, choose the one that says Create and format hard disk partitions
3) This will open the Disk Management tool
4) It will take a while, but eventually, it will list out all your drives and the partitions each one contains
5) Scroll down through the list until you see the partition on the drive to which you're trying to write the backup
6) Right-click on that and choose Properties
7) Select the Tools tab
8) Click the button in the Error checking section that says Check -- this will run CHKDSK on that partition
9) If an option then comes up to Scan the drive, and if there's more than one option, choose the one to fix the errors

When that's done, you should then be able to use the drive for backups.

And, I strongly recommend AGAINST using the Windows backup feature -- it has problems.  Instead; download and install the free version of Macrium Reflect and use that to make an image backup.

---

### Post by oldfred on 2014-12-30
After the backups, some explanation.

BIOS is the 35-40 year old method of starting the computer it is a chip on the motherboard that starts the boot process. Most computers show a start up screen before operating system boot that is BIOS loading. It determines what hardware you have and reports that to the operating system and turns control over to operating system. But being so old it has had trouble keeping up with new hardware and was hard to maintain with all the fixes.
 [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 
So they developed UEFI, but it also has a BIOS mode called CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You get to BIOS or UEFI by pressing a key when system first powers up. Usually shown on very first screen, or in computer manual. Often delete key, f2 but varies a lot by vendor. This shows most common keys by vendor.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

You have to go into UEFI/BIOS and possibly set a password to allow more settings. And the added settings shoudl include allowing boot from external devices. That is a security feature to prevent unauthorized users from booting your system with just any boot key like Ubuntu.

---

### Post by doit2 on 2014-12-30
> **Mark Phelps said:**
> Let's tackle this first -- as a backup is needed before you consider replacing anything...

When that's done, you should then be able to use the drive for backups.

And, I strongly recommend AGAINST using the Windows backup feature -- it has problems.  Instead; download and install the free version of Macrium Reflect and use that to make an image backup.

Firstly thank you for understanding my NOOBNESS. I do think it's better to do it step-by-step as i already done some mistakes with the Fujitsu. Right now we are talking about a backup for an older computer, which is a deadmeat "Asus notebook Eee PC Shell series". After ill try everything on this old geezer, i will continue to Ubuntu my Fujitsu

So again, more problem. I did step you advised but no backup. I added a .PNG caption of the CHKDSK results and the ERROR "Reflect" gave me.

What's the assumption doc?
Thank you!

(And thanks Oldfred too, but i think only after the backup is done on both computers, i can finally go to the actual stage of giving the OS a try)

Edit: more details: As you see, the CHKTSK found nothing. Before running the Backup i erased all passed attemptes to get some space, but the image backup (which i have no idea how to use) stopped after ten minutes or so. Unlike when i used the Win Backup (which stopped midway), now the Destination folder in the F driver is empty. That's about it.
Second Edit: I tried to add an attachment of the Reflect log, describing what went wrong, but it's "invalid" for attachment.
So many setback until a computers gets its freedom! Tell old Pharaoh let my Hardware go!

---

### Post by doit2 on 2014-12-31
Ok so while the future seems vaouge for my Asus notebook (at least until somebody here saves the day regarding the backup), let's move along to the Fujitsu Lifebook.

Let's assume i can backup the current situation of the computer with an image. Does this backup gives full backup for all files?

After backup is a success, i wish to finally advance towards Ubuntu. Previously I got stuck on booting from USB in Bios. After our lovely MOD here explained it all, i see what needs to be done. Few questions though:
1. Say i get to Fujitsu BIOS, where should i go from there to make it boot Ubuntu from a portable key?
2. If i need a password for it, where should i find it?
3. Prehaps if im here i should do everything right so lets be clear about copying Ubuntu on a key: should it be the sole folder on the device? Should it be saved on a specific folder on the outer device?
4. NOW FOR UBUNTU ITSELF: I wish to first put it into test, meaning i don't want to install it yet but to try and see wheather it reads Wi-Fi and all. How is this thing done?
5. Like it and wish to install it. Will choosing "dual-boot" means windows will operate alongside Ubuntu and slow down my computer, or will be saved as backup on the Hardisk Memory?
6. If i choose to replace windows altogether, will this erase it for good and if so, what are the benefits in choosing this option? 

Although i read many introductions and manuals, this questions where not addressed directly and make it hard for me to understand how to use the program and to be exited from it.
Thanks a lot for you help and please keep in mind my old Asus aswell

Peace and love

---

### Post by oldfred on 2014-12-31
Did you review the links from other Fujitsu users. They often provide details of your specific vendor even if not same model.
First screen should show which key to get into UEFI/BIOS, often del or f2 keys.
You will find many UEFI screens, most should have explanations of what each menu item is.

You either install Ubuntu to a flash drive or DVD. Flash drives are reusable and a bit faster. Running in live mode will not be as fast as an install as both flash drives & USB ports as not as fast as internal SATA drive. Installer will totally erase flash drive, extract ISO, and make it bootable.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
            [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
    
When you boot from UEFI menu you will have two boot choices, one will be a BIOS boot and the other UEFI. Usually in UEFI menu the UEFI one is clearly labelled UEFI and the other just has the label or name of flash drive.

       You will need to use the 64 bit version of 14.04 LTS or 12.04 LTS and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode. You will also need Boot-Repair for several work arounds for Vendor UEFI issues and grub bugs.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
Flash drive then has screen for install or try modes. So you do not want to click install but test your system with the live mode or try out the system.

Generally best not to erase Windows. And with dual boot your are in either one or the other, so they do not interfere with each other when running. But Windows likes to make it a bit more difficult as it has its fast boot, requires the secure boot at least initially, and likes to reset system to make Windows default boot.

But many users find one application or game that does not run in Ubuntu and want Windows back after totally erasing it. Good reason for full image backup, but some have accidentally selected the erase entire drive option when installing. And some advanced install options like LVM with full drive encryption does mean then entire hard drive will be erased including all of Windows and any Windows restore partitions. In Linux a drive is the entire phyiscal drive not a partition like Windows may call a drive.

---

### Post by Mike_Walsh on 2014-12-31
> **doit2 said:**
> Ok so while the future seems vaouge for my Asus notebook (at least until somebody here saves the day regarding the backup), let's move along to the Fujitsu Lifebook.

Let's assume i can backup the current situation of the computer with an image. Does this backup gives full backup for all files?

After backup is a success, i wish to finally advance towards Ubuntu. Previously I got stuck on booting from USB in Bios. After our lovely MOD here explained it all, i see what needs to be done. Few questions though:
1. Say i get to Fujitsu BIOS, where should i go from there to make it boot Ubuntu from a portable key?
2. If i need a password for it, where should i find it?
3. Prehaps if im here i should do everything right so lets be clear about copying Ubuntu on a key: should it be the sole folder on the device? Should it be saved on a specific folder on the outer device?
4. NOW FOR UBUNTU ITSELF: I wish to first put it into test, meaning i don't want to install it yet but to try and see wheather it reads Wi-Fi and all. How is this thing done?
5. Like it and wish to install it. Will choosing "dual-boot" means windows will operate alongside Ubuntu and slow down my computer, or will be saved as backup on the Hardisk Memory?
6. If i choose to replace windows altogether, will this erase it for good and if so, what are the benefits in choosing this option? 

Although i read many introductions and manuals, this questions where not addressed directly and make it hard for me to understand how to use the program and to be exited from it.
Thanks a lot for you help and please keep in mind my old Asus aswell

Peace and love

You won't need a password to use a Live USB (or Live CD/DVD); where would be the point?

You can't set a password before you've even used the Live System, let alone committed yourself to installing it; the whole idea of it is to test your hardware out BEFORE you decide if you even WANT to go any further.

The 'Live' option is accomplished by downloading the Ubuntu .iso image (if you haven't already done so), and either burning that image to a DVD (too big for CD!), or installing it to a USB stick, with an installer like UNetbootin. There ARE others on the market, but I would recommend it to a beginner, because it's really easy to use, plus it's available in both Linux & Microsoft versions.

Where it asks you for persistence, give it a couple of GB (say, 2048 MB); this enables you to try things out over the course of more than one session, as it will save any settings or alterations you make, just as a fully-installed system would.

Once you've done that, you'll need to go into your BIOs, or boot menu, and choose which one you want to boot from. If you've burned to disc, of installed to stick SUCCESSFULLY, then, all things being equal, it should boot up.

After you've tested your hardware out, to find out what (if any) problems you may or may not have, you have two choices. 

1) You continue to the install phase from within the 'Live' session, or (which I suspect you want for now),
2) You simply shutdown as you would with any operating system.

In Ubuntu, you click on the 'gear' symbol in the very top right-hand corner of the screen, then select 'Shutdown' at the bottom of that menu. You then click on the big white 'button' in the middle of the screen.....you can't miss it!

Hope that helps. I only started with Linux earlier this year myself, after 30-odd years of playing around with these gadgets.....and I, too, prefer clear, simple instructions, that are simple & easy to follow. I'm not fluent in 'geek-speak'...! :)

Let us know how you get on. We were ALL 'noobs' at some point.


Regards,

Mike.


BTW, never be afraid to post with questions here on the forums; we're all here to help each other out, after all.

---

### Post by doit2 on 2015-01-02
> **Mike_Walsh said:**
> 
BTW, never be afraid to post with questions here on the forums; we're all here to help each other out, after all.

Funny you wrote that, as i am very close to give up on Ubuntu. Seems like the more i read the less i understand. It appears so many things can go wrong, and no one address it in a simple manner. This makes me think that using Linux is not for people who are not programmers.

The thing that prevents me the most from progressing is that i can't seem to find a simple version of instructions. [COLOR=#ff0000]EXAPMLE:[/COLOR] I understood what OLEDFRED suggested until this line: _"_[COLOR=#000000]_You will also need Boot-Repair for several work arounds for Vendor UEFI issues and grub bugs."_ Because i figured i know need **AN ADDITIONAL FILE**, i just didn't do anything until i understand **WHAT IS "BOOT-REPAIR"**, Where do i get it and what's it's use?
[/COLOR]I completely lost our MOD with this sentence: "[COLOR=#000000]_Systems need Windows fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings_." [/COLOR][COLOR=#000000]IS THERE A DIFFERENCE BETWEEN **FAST AND QUICK BOOT?**[/COLOR][COLOR=#000000] DOES SYSTEMS **NEED WINDOWS** NOW? DOES IT GO TO **SLEEP DURING WINTER**?

Of course i got confused like that many times during the last few days, as i put hours on hours trying to be a good student of Ubuntu. But [/COLOR]I still don't know how exactly to put Ubuntu on a USB-stick, or how exactly should i use the stick to test Ubuntu without installing it yet. I also still don't understand weather my image backup for the Fujitsu went ok, or who should i backup my old Asus notebook.
Basically Im still at square 0.

So I guess you see now, why am i on the verge of giving up... Problem is, that if i give up now, i know i will never try it again and will be forced to hate-and-use windows all my life.

---

### Post by doit2 on 2015-01-02
Ok so for the sake of organisation i **divided my question into posts.** This post will deal ONLY with putting Ubuntu on a stick. The next one will deal with backup, and a third one with testing Ubuntu.

[B]Putting Ubuntu on a stick:

[/B]You wrote "if you [COLOR=#000000]installed to stick SUCCESSFULLY, then, all things being equal, it should boot up" _First Q:_ How can i know if the installation was a success?
 
I already installed it once, using [/COLOR]http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows
but it didn't work on the Fujitsu.
I also need to be GLAD THAT IT DIDNT WORK because until the most recent post from OldFred nobody mentioned that UBUNTU ERASES EVERYTHING ON THE STICK.

So if i gather all bits of information by know, seems like i need to clear up a stick before putting the ISO on it. But other then that i again know nothing, because some instructions say to put the ISO directly on a 1GB stick and that's enough, some say i need to create the stick to be bootable (2GB) and some advice 4,8,32 GB operations. Again, im confused.

Please help my as you would help a child.

---

### Post by doit2 on 2015-01-02
[B]Backing up the systems before trying Ubuntu:


[/B]1. My_ asus notepad*_, is an old and mis-used computer. This is the computer i wish to get Ubuntu first. But i had trouble backing it up, as on several attempts my outer memory drive (An I-OMEGA) stopped midway through (57%). Reflect backup also failed.*
Now, i already copied all the photos, docs and videos using the simple "copy-paste" method. Should i continue to try and give a full backup to this computer? Or should i just try Ubuntu it without a backup?

2. My Fujitsu Lifebook (A series) is my main Computer, tough it has many problems. Most of them i due to it's Windows 8.1 OS. That's why i wish to get Ubuntu on it aswell. Now i already got and Image-Back-up using "Reflect" as i was adviced here. Now i wish to know how can i make sure the back up was a success before playing around?

*The asus interface and reflect failiure with it is shown in an attachment

---

### Post by doit2 on 2015-01-02
[B]TESTING UBUNTU:


[/B]let's all assume i could back up both of my computer **safely ** and get Ubuntu on a stick [B]the right way.
[/B]Now still don't want to immediately jump into the water, but test Ubuntu using what i understood is "the live version". I will probably just try it out once, to check WIFI connection.
So just correct me if im wrong, but all i need to do is thus:
1. Get a clear USB stick and put Ubuntu on it.
2. Insert USB stick in the computer when it's shut down.
3. Start it up and address the BIOS menu (using F2, Del, F12 or what not)
4. From that menu, choose the option with the stick name on (for example: Sansa cruzer)
5. This will load up Ubuntu in it's live version. It will be slower, but should work as if it's installed. on this phase i cant test the Ubuntu looks, style and interface?
6. shut down and ejecting Stick will clear everything and windows will load automatically without erasing or saving any action?

Once again thank you so much for baring with me...

---

### Post by oldfred on 2015-01-02
You may have to add password to be able to turn on a boot from USB port or enable a USB port.
If Sansa is name of flash drive, the new UEFI will show it twice.
UEFI - Sansa
Sansa

The UEFI will boot in UEFI mode.
the Sansa entry then is a BIOS boot. 
For testing you can use either one
But since Windows is UEFI, you should install in UEFI mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Ubuntu has fixed most of the issues that your needed Boot Repair for. Still good to have in tool box in case repairs are needed. And very good are creating a report of system configuration so we know exactly where you are at.

Different users were calling quick boot and fast boot, but really the same thing.
I did find on my new mother board another quick/fast boot setting that was only related to UEFI, not Windows. You must turn off the Windows fast boot setting. With my UEFI if I did not change it from its fast boot setting, it made it difficult or impossible to get into UEFI as it immediately starts booting before you can even press a key. I set a 3 sec delay on that setting. It also has a setting that after a full power down or cold boot, that it would use normal boot, so you could get into it.

Info on Boot-Repair:
      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by doit2 on 2015-01-02
> **oldfred said:**
> You may have to add password to be able to turn on a boot from USB port or enable a USB port.
If Sansa is name of flash drive, the new UEFI will show it twice.
UEFI - Sansa
Sansa


Hi OldFred, it appears most of the things you mantioned maybe helpful with my Fujitsu as it's quite new (2013) computer. Right now i wish to test Ubuntnu on an older computer. An asus EEE notepad (it's info is on an attachment above). It's a 2009 computer, and im not sure it has a UEFI.
Also most of the link you shared relate recommend Ubuntun 64Bit and im quite certain a 2009 Asus needs 32Bit. Does this makes any difference? 
And then, if i load Ubuntu 32Bit on a portable USB stick, can i then reuse the stick with a 64Bit Ubuntu? (I hope i can slowly manifest why this is so confusing for a noob)
Thirdly, I didn't understand what is the meaning of "adding a password" or where should i do it?
And thank you for boot-repair tip, i will download it immediately after trying Ubuntu.

---

### Post by verymadpip on 2015-01-03
Hi there.
With regard to the Asus:
Have you run chkdsk on the hard drive you are trying to back up?  That could be the problem.  This is old, but worth reading:
[http://support.macrium.com/topic.asp?TOPIC_ID=4228](http://support.macrium.com/topic.asp?TOPIC_ID=4228)

Personally, I would use a 32bit OS on the Asus.  It seems not to be a UEFI machine - I've had a quick look at the manual, & Windows 7 starter doesn't come in 64 bit as far as I can tell.

To get Ubuntu on a USB stick I'd use UNetbootin.
Google it on a Windows machine, & follow the link to the Sourceforge website.  It will give you the right version for the machine you are using.
If I remember rightly, you dont have to install UNetbootin, you can just open the zip file & double click the executable (application) & it will run. 

Get your Ubuntu from here:
[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)  You want ubuntu-14.04.1-desktop-i386.iso
****

---

### Post by oldfred on 2015-01-03
My old laptop from 2006 runs 64 bit Ubuntu. But Asus has different models and I do not know them. It will not be UEFI, but only BIOS.
You can install a 32 bit Ubuntu on 64 bit system but not in UEFI mode which you will want on Fujitsu.

There have been many threads on Asus models, not familiar with all the various models. This thread has Fujitsu in title, so we should only discuss the Fujitsu here. If you want help on an Asus system start a new thread with that in the title.  You can search forum easier with Google and include in search site:ubuntuforums.org.

Go back and look at the threads I posted where other Fujitu users posted. I believe the password is in your UEFI/BIOS settings. You have to learn how to get into UEFI. My new built system has a motherboard with its own fast boot setting. And only a full power down gave a standard boot where I could press the del key and get into UEFI. Check your manual. You may even have to remove battery and hold power key to drain system to get to to do the full start up with UEFI so you have a couple of seconds to press correct key to get into UEFI.

---

### Post by JeQhdMD on 2015-01-04
Before going much further in your quest to "retrofit" PC's you already own with any type of Linux (like Ubuntu), I would suggest you fully explore the following link:

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

I realize these PC's would mean purchasing new hardware (prices range from about $450 to $2500 USD) depending on the hardware and customizations applied.   But if you clearly do not understand even the basics of computing (hardware and software) . . trying to do something relatively complex (now that UEFI is the norm versus traditional BIOS) will likely result in failure, and costs (that could pay for 50% or more of a lower end linux system).   

If you can't afford (or even if you just do not prefer the expense) . . . it may be best for you to retain windows . . . perhaps even getting windows 7 installed on the new machine.   IF you live close to an area that has a local linux users group or club, you could attend a meeting and see if someone will do the install for a club project or a small fee.    Even a local university/college computer dept. may have students willing to help (by posting message in appropriate media).   In other words, to pursue the road you're "now" taking, you may need hands-on help.     Just my 2 cents, . . . feel free to totally disregard.

---

### Post by Mark Phelps on 2015-01-04
> Now i wish to know how can i make sure the back up was a success before playing around?

The paid version of Macrium provides an option to auto-verify the integrity of the backup just after it has been created.  The free version does not do that.

However, you can go back into Win8.1 and using Macrium, Verify the integrity of the backup. You do this using Restore --> Browse for Image --> Open the image you want to check --> Select the Verify option on the right.

If the Verify completes without problems, the image is good.

---

