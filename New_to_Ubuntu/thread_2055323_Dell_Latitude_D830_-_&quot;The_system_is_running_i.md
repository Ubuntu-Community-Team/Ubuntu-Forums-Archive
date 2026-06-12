---
title: "Dell Latitude D830 - &quot;The system is running in low-graphics mode&quot;"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by metilly on 2012-09-09
===IF YOU WANT THE SHORT VERSION, CHECK MY LATEST POST.   THIS CONTAINS ALL DETAILS BECAUSE I DON'T KNOW WHAT YOU NEED===

Hi all,

I'm mostly new to Linux except a bit of messing around in Redhat 9 days  so please give me exact commands to type and why.  I'm pretty cluey  around Windows so using standard terms like properties is fine.  (I  wouldn't be surprised if what I need to know is here on the forum but I  don't know enough of the commands to know what is specific to someone's  situation and what's standard across Ubuntu.)  I've detailed quite  thoroughly because my ignorance means I don't know what you'd expect to  be happening and whether any of it is unique to my situation.

I don't recall which version of Ubuntu I installed.  I was having  wireless networking issues but one version worked "out of the box" and  I've updated ever since so I assume I'm on the latest version.

I think there was an update done the day before my laptop struck this  problem but not sure.  I am pretty sure that there have been no updates  done since before midnight GMT coming into Friday, 7th September.   However, I think I've been having graphics problems from shortly before  the latest updates.

Basically I've found a few times lately that if I close the lid and let  the laptop go to standby, when I open up again, all I get is backlight  and a mouse pointer.  On Friday during the day, I decided to restart the  laptop because this was happening.  Ever since then, every  start/restart is causing the low-graphics mode error message.  Before I  can see the mouse pointer, I have to wiggle it a bit and then it doesn't  matter where on the screen I take it, it will either be white with  black surround or black with white surround.

After clicking OK, my options are:
1. Run in low-graphics mode for just one session
2. Reconfigure graphics
3. Troubleshoot the error
4. Exit to console login

This is what happens in each case when I choose one of those options and then press OK:

Option 1 doesn't work; it tells me to standby while it reconfigures the  display, I press OK and then I get backlight only.  I can type and it  appears on the screen but doesn't seem to achieve anything.  Pressing  the power button causes text to appear on-screen and then the laptop  shuts down.  I don't have time to read the text apart from it's  something to do with checking for running unattended upgrades.

Option 2 gives me the choice of using the default configuration or my  backed-up configuration.  I don't know if I have a back-up but since no  matter which choice I make I only get taken back to choosing which  configuration, I guess that doesn't really matter!

Option 3 I can't use because I have no idea what to do with any of it.  I get options of:
reviewing the xserver log file,
reviewing the startup errors (gives me a blank box),
editing the configuration file, (takes me back to the four choices I'm currently listing)
archiving the configuration and logs (tells me where they've been saved and where I can submit bug reports).

Option 4 causes the laptop to shut down with what looks like the same text as in option 1.

Once I did manage to get as far as being able to login and issue  commands but I'm not sure if that was a fluke or there's a consistent  way if I knew the right procedure.

So, that's the story and I'm hoping someone can tell me where to go from  here.  I doubt it's relevant but just on the off-chance it helps  someone, I installed WINE and then Office 2010 on top of that.  I'm not  sure about other programs but I can't do various things in Access,  possibly a write-permission issue.  I can open files and change data but  I can't seem to create tables or rename them.  I can't remember what  the error message is but it's something along the lines of violating the  rules for naming tables.

Oh, I can also boot from a live 12.04 CD and access my files so I'll  work on seeing if I can get them backed up.  I'd only just put a whole  bunch of video conversions through so didn't get chance to back up.   From what I've read, I'm guessing an update may have caused this problem  and it needs a resolution in case it happens again on a wipe/reinstall  and I could find myself trying to retrieve unbacked up work again.  If  it weren't for suspecting I'd hit trouble again, I'd just back up and  wipe/reinstall or google for how to repair an installation.

Thanks in advance.

Oh, and should a mod or admin notice I seem to have multiple accounts at  this IP address, please tell me - I was sure I'd already signed up...

---

### Post by 2F4U on 2012-09-09
What is the graphics card? If you don't know, you can find the information through the lspci command.

---

### Post by metilly on 2012-09-09
> **2F4U said:**
> What is the graphics card? If you don't know, you can find the information through the lspci command.

Could you give me instructions on how to do that?  I can use a live boot CD or if you know how I get logged into the installation at a command prompt, I can do that.  Then I need instructions on exactly what to type, line by line.

Some further information; I've been attempting to retrieve my files (using the live CD) and discovered that a some files/folders seem to have gone missing.  Sometimes when I try to access a folder I get the message that I don't have the appropriate permissions.  Asking for properties includes the response "some contents unreadable."  No file is able to be moved, only copied.  Two of my folders have question marks opposite them for the number of items in the folder.  I know exactly what was in those two folders because I have Cathy installed on another computer which was monitoring part of my files on this problem computer.  (Cathy is a program that creates listings of drives or folders that you choose and you can browse the listing whether or not that drive or folder is currently accessible.)  I find myself wondering if we're looking at drive failure but wouldn't know how to chkdsk on Ubuntu.

Ideally, I'd like to work from the command prompt of the installation to avoid permission errors so if someone knows a failproof way of getting to the existing installation's command prompt/terminal, please tell me.

---

### Post by metilly on 2012-09-09
Chances are good that it has an Intel GM965 Express chipset.  I just remembered you can usually get information about a Dell by using the service tag, which is what I used.  The machine itself has NOT been queried to confirm this.

---

### Post by metilly on 2012-09-09
I omitted to mention that I googled for how to check the disk and came across information on viewing S.M.A.R.T. data via the Disk Utility with the live CD.  It says the disk is fine but I have not run any Self-tests because I came across warnings about data becoming more difficult to retrieve in some situations with some disk checking methods so I'll wait for advice on that.

---

### Post by metilly on 2012-09-10
Brief summary of situation:
Initially getting only backlight and mouse when coming back from standby.  Now getting error message and can't get in.

Error message as in title and can't find a way to get to terminal login  reliably using the existing installation rather than live CD - might be  I'm ignorant of the correct way.

Files appear to have gone missing.  (Or maybe just aren't showing up while using the live CD?)

S.M.A.R.T. (using live CD) says disk is healthy but no self-tests run yet.



Continuing:
The video card is definitely an Intel:
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

The disappearing files is a worry.  I'm totally certain that more went missing.  I'm about to google for how to try file recovery on Ubuntu - all help and suggestions welcome!

Also, advice on whether it's safe to run the Self-tests provided in the S.M.A.R.T. facility and or likely to be beneficial to finding my files or at least stopping any others from going missing - I'm running off a live CD currently, version 12.04.

Surely I couldn't have malware eating my files?

---

