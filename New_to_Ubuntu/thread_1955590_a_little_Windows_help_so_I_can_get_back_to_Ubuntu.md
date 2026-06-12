---
title: "a little Windows help so I can get back to Ubuntu?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by anewguy on 2012-04-09
My Windows 7 installation, using the default Windows Defender and Windows Firewall, "aquired" something that actually causes it to send bogus emails when I am in my Yahoo account.  I don't even use a PC-based email.  I reinstalled Windows, changed my passwords on line, and what happens?  Yep - starts sending the dang bogus email when I'm online.  Thanks Sam for the email that seems to have started all of this!

So, when I reinstalled Windows 7, I first booted a LiveCD to clear the partitions (my Ubuntu install is on a separate SSD, only grub was on the Windows hard disk).  I noticed when I booted using the Windows CD that it came up with some stuff about ISO Linux - probably 4 or 5 lines worth, then I got the press any key to boot from CD message.

So I'm wondering - where is the Linux text coming from - it almost looks like some sort of boot loader? 

What I would LIKE to do:

- reset the hard disk completely.  Remove all partitions, and if possible reset the boot sector, as I have a suspicion the bad thing is residing there.

After that I can reinstall Windows 7 and then run update-grub from the LiveCD so I can boot my Ubuntu installation back up.

Please - don't be one of those posters who tells me to get rid of Windows.  I do know a _little_ about what I'm doing here.  I actually need Windows for some projects.  I do mainly use Ubuntu otherwise.

If someone can educate me a little in these processes it would be greatly appreciated!

Thanks in advance!
Dave ;)

---

### Post by anewguy on 2012-04-10
Well, I'm *hoping* I solved this.

---

### Post by shuttleworthwannabe on 2012-04-10
Hi Dave, what I have tried before to overwrite the boot sector with MBR is use EasyBCD (one of the advanced menus). What this will do is restore the MBR (boot sector). What I would then so is reformat the HDD while installing Windows. Failing all this, could this be in the BIOS?? Would flashing that work?? I am just speculating.

Hope you come right. Awful stuff that.

---

### Post by anewguy on 2012-04-10
I'm *hoping* it was a boot sector rootkit - Windows.  I booted a LiveCD and ran disk utility.  I removed all the partitions off both my hard disk and my SSD (now I have to reinstall ubuntu), then I set the "bootable" off (I think the option is actually something like "boot" and you get to chose options - I chose none).  I figured in this way the space that would go the the boot sector would get wiped with a disk utility format with no partitions and none as the type.  This ran extremely quick, but I think it may have wiped the boot sector.  Did this on both devices.  So, I had kinda of a naked drive setting there not marked as bootable.  Windows installed, made it bootable, so I'm guessing the boot sector has been cleared.

So far nothing has showed up.  I keep 2 dummy email addresses in my Yahoo contacts - that way if something starts sending things out without me knowing it I get an indication because I receive back undeliverable emails with the email text in them.  That's how I caught this one.  I had even run Avast and Malwarebytes in Windows and they claimed nothing wrong.

So, for now all I have on this desktop is Windows 7 until I reinstall Ubuntu for dual boot (I had Ubuntu all on the SSD).  At least my other desktop has Ubuntu so I can still do what I want there.

So, I'm crossing my fingers that it is fixed - but I won't know until some time passes by.  

For those interested, I got an email, supposedly from someone I know, which just contained "This is intense you have got to look at it" and some web address containing inews15.  Clicking on the link in Windows (this is my guess at this time) ran a 13 minute film "clip" - I suspect it also installed the root kit while that was going.

Dave ;)

EDIT: I should probably add that I tried the LiveCD/install Avast/have Avast check the Windows disk route, but after installing and updating the definitions, I couldn't get Avast to run (it in fact appeared not to be installed!).  So I tried what I did instead.  And.....I'm really hoping it didn't load itself in the BIOS as that will be a lot of fun to get rid of.  To top it off, at least 1 of the people in my contacts list that this thing used now has the same problem.  BTW - I have no PC-based email - I strictly use web based email - and yet this thing got in, got my Yahoo contacts list and sent itself out to everyone in that list.

---

### Post by westie457 on 2012-04-10
@ anewguy

One procedure I use to clean Windows malware is boot Windows into Safe Mode with Networking and install 'SuperAntiSpyware', to the best of my knowledge this is about the only program that can be installed without the main system drivers and services running. Once installed let it update and then do a full scan.

Delete all items found and reboot into normal Windows, Then run another scan using 'AntiMalwareBytes' again deleting any items found.

So far the above has saved three Windows systems that would normally have to be wiped.


Now onto what I might would do if the above failed after changing the passwords.

Using either a LiveCD/USB in Live mode or booting straight into Ubuntu, (LiveCD is for only one HDD and normal Ubuntu is for separate drives). After checking which drive to work on - SDa, go to the 'Deveice' menu and click on Create..  This will rewrite the Mbr effectively making the drive appear to be empty.

Now I would get the Windows disc ready and reboot giving the install media a fresh hard drive to format and partition as necessary.


I appreciate that this might be too late for you however somebody might find this useful.


Edit; Had one of those rogue email things a while ago. In my case Changing the account password and logging out of the account stopped rogue emails being sent. Like you all my email is web-based not pc-based.

---

### Post by Mark Phelps on 2012-04-10
IF you're not sure about the rootkit problem, then go to the Kaspersky site and download their TDSSKiller app.  It finds and wipes rootkits. They update it every week or so and it's available for free.

They also provide a downloadable "Rescue CD" image that is their AV product that can be burned to CD -- and you can use that to run an AV scan.

Also, don't rely on Bitdefender in MS Windows; instead, get the new Microsoft Security Essentials. For a free product, it's not bad.

---

### Post by anewguy on 2012-04-10
> **Mark Phelps said:**
> IF you're not sure about the rootkit problem, then go to the Kaspersky site and download their TDSSKiller app.  It finds and wipes rootkits. They update it every week or so and it's available for free.

They also provide a downloadable "Rescue CD" image that is their AV product that can be burned to CD -- and you can use that to run an AV scan.

Also, don't rely on Bitdefender in MS Windows; instead, get the new Microsoft Security Essentials. For a free product, it's not bad.

Hey Mark - thanks!  Can you tell me if I'd be better off with MSE versus Avast AV, Malwarebytes and ZoneAlarm?  I ask because I had a couple of friends tell me to use that also.  I'd sure be interest in something like that if it might provide more protection (as dumb as I may sound, since Windows is MS and MSE is obviously MS, perhaps they know more about checking these things and how they'd hook to Windows??).

Again - thanks!

Dave ;)

---

### Post by jadtech on 2012-04-10
first thing I would have done is to delete the yahoo account altogether saving nothing from it before you wiped the computer then after  everything was  re installed. set up a whole new mail account ..

make sure there is no network connections before you partition and re install everything the first and only thing to use the connection will be to get all the updates for windows and virus scan..

the chance of getting on the internet with windows without all the updates or virus scan without getting infected is most likely less then a half hour..

---

### Post by anewguy on 2012-04-10
Deleting the Yahoo account was not needed - it's the website the mail directs you to that does the infection from the best I can tell.

As for the rest, well I do know a *_little_* about what I'm doing.

---

### Post by anewguy on 2012-04-10
So far, so good.  Going to mark this solved for now.

Thanks everyone for your input!!

Dave ;)

---

### Post by Mark Phelps on 2012-04-10
I don't use MSE, but from what I've read, in terms of FREE AV products, it's a good as MalwareBytes Anti-Malware and SuperAntiSpyWare.

My own preference is Norton AV.  Quit using it back in 2005 when it became bloatware and took over your PC. Started again in 2009, and have been impressed with it ever since.

Switched over then when I was using ESET NOD32 -- and got a infection.  Downloaded and ran a trail of NAV, and it cleaned up the PC.  Been a fan of it since.

However, I think Avast is supposed to be quite good as is Kaspersky.

---

### Post by anewguy on 2012-04-11
Thanks Mark!

I'm *hoping* I have things fixed now, but I did receive to undeliverable email messages tonight with the bad email in them.  Both were because the stupid thing tried to send to ubuntu forums.  The bad news is that they were time stamped for just after midnight Tuesday morning.  I don't even remember now (the late 60's and 70's were kind to me ;) ), but I think I had updated things by then.  Hopefully they are just late echo backs, since I haven't had any more from the 2 bum email addresses I keep in the address book for just such things.

Again, thanks!  I just may download that and install it tonight yet.

Have a good one!

Dave ;)

---

### Post by shuttleworthwannabe on 2012-04-13
Dave--about AV preferences--MSE is light on the system and so is Avira; I found Avast and AVG quite hungry on resources and also have some false negatives cf to avira.

---

### Post by anewguy on 2012-04-13
Yeah - I had some problems with Avira a couple of years back so haven't gone back to try it out again since then.  I have always been happy with Avast, but I did install MSE as it appears to have some real-time protections that I'm not sure if Avast has or not.  I do know that when I got on the net Avast was constantly scanning so I assume it was doing the same real-time scans.  I just hope a Microsoft security package doesn't have security holes in it like Microsofts' OS does!

I think that what happened was that in the process of trying to get my wireless to work on the new PC I used the Windows firewall until I could get online and get ZoneAlarm, and then forgot to get anti-virus because of how long and frustrating it was to get my wireless working.  Mind you, wireless in Windows - the same adapter works out of the box in Linux!  So for once something worked backwards, and it was a lot bigger pain getting it to work in Windows then I've ever had, including Broadcom several years back, in ubuntu!  So, without the ani-virus, I open an email on my Yahoo account online then click a link.  That link said something like "you've got to see this, it's amazing" or some such thing.  When you get to the link you can click to watch a 13 minute video that turns out to be nothing.  I think either just opening the web site, or more in particular probably opening the movie, resulted in a rootkit getting installed.  It was a pain the behind getting rid of it!

So far I think I have it fixed now - no more returned as undeliverable emails with that link in it.

Hope things are going great!

Dave ;)

---

