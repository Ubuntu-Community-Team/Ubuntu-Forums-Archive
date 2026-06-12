---
title: "Corrupted system"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Shooter40 on 2008-10-31
I have just started to use Ubuntu Linux.  I have no experience with Linux operating system or command system, but have a reasonable knowledge of computers and Windows operating system through XP.

The computer dedicated to Ubuntu is a Dell Dimension L550r, Pentium III, 548.2 MHz, Chipset Intel i801e, Memory 512 KB, 40 GB Hard Drive.

The computer is part of a Windows XP home network.  There is a desktop running Windows XP Home, at times a laptop running XP Home, and the Dell running Ubuntu 8.04.1.  There is a HP DeskJet 812C attached to the desktop via a parallel connection that I want to be able to print to from the Ubuntu computer.

I have installed Ubuntu twice before and because of this same problem had to reinstall it.  I have tried Debian and could not get it to work with the printer.  Ubuntu set up both the network for sharing files in both directions and the printer very simply and with no problems.  So for the third time I was happy to use Ubuntu and liked the program and ease of setup.

Below is the problem that occurred all of a sudden, each time I installed Ubuntu.  Ubuntu operated very well for a week or two then all of a sudden the following was noticed:

When starting the computer all seemed normal through the password entry.

When the desktop screen came up the panels at the top and bottom of the screen came up normally, with the exception that my user name and the network and volume icons, and date were not shown yet.

Then the the panel stripes across the top and bottom went blank.  It took 30 seconds or more before they came back normal with all icons and information.

From that point I could no longer bring up the root terminal, install updates because the root password window would not come up, and I could no longer see the network computers.  When Places -> Network was clicked on top panel, the Windows Network icon came up in a window.  When that was clicked the Davron (My domain name) icon came up.  When that was clicked after a long time the “search” just quit and a 0 appeared in the lower left hand corner.

The computer will no longer print to the Windows printer attached to the desktop.  It looks as though it will and then everything just stops and nothing happens.
The only thing I can think of is that perhaps I was going to access a file on the desktop from the Ubuntu machine and stopped it short by closing the window.

Could this have corrupted a file?  Is there any log or anything that will tell what is or is not going on so the situation can be corrected?  If so … how do I get it and send it to someone who may know how to correct the problem.  Is there any program that will scan the computer, find and correct corrupt files, similar to Scan Disc on Windows?

I am about to give up on Linux, but really hate to because I see good potential.  Please help!

---

### Post by lH)4~mK0e on 2008-10-31
I believe the Ubuntu Live CD still has a Memory Test option on the CD menu.  I would try that first.  It sounds to me like a memory issue.  Give that a try and if anything shows up in RED then it's either a bad stick of memory, wrong memory types or speed mismatched (i.e. PC100 running with PC66, or PC133 running with PC100) or the memory is not fully compatible with your motherboard.  Even if you don't get similar issues with another O/S it still could be a factor.

---

### Post by Daveth on 2008-10-31
certainly should not be a printer problem, as it is listed as working perfectly under linux

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_812C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_812C)

Very odd that the failures seems to come on later - if your workload is fairly constant over the period i would have thought a memory failure would have shown up at the outset. Have you ever run it on its own, just connected to the internet, with no XP networking? Might be worth trying to see where the failure point actually is- the picture seems too complex at the moment.

---

### Post by Shooter40 on 2008-10-31
Thank you for the suggestions.  I ran the memory test with two passes 0 errors.  I have two new 256MB memory sticks installed of same brand - PC133's.  Computer worked fine as mentioned both for file exchanges and printer.

Shut down XP computer and started Ubuntu computer alone.  It runs directly to the router and to the Internet.  Did same thing ... started normally then top and bottom panel strips went blank and when they finally came up normal looking, I could not update the three updates that are waiting because the password window would not come up and I could not bring up the Root Terminal.

Tried with the router shut down.  Panels didn't go blank, but still took a long time for my name, network icon and date to come up.

Any further suggestions?  Is there any program that will go through the files and correct anything that is corrupted or any logs that will tell someone where problem is?

---

### Post by lH)4~mK0e on 2008-11-01
I guess, were there any issues with the computer previously?  Say, with another operating system?  Unfortunately, some systems that I have run into (desktops with PC133 that are not proprietary like Dell or hp) don't like to run Ubuntu 8.04 very well.  There is a lot of image corruption like what you are mentioning, and issues with settings not saving properly.  One other thing I would suggest, try to identify the manufacturer of the hard drive, and then google for "ultimate boot cd" and download that on a known good working system with a CD burner.  That disc will have several manufacturer specific utilities that will help in diagnosing possible hard drive failures.  If it passes a Basic or Quick test (which is good enough for most manufacturer's tech support agents) then I might suggest using dapper or feisty versions of Ubuntu.  It is possible that some newer kernel mode driver or module just doesn't use your hardware properly in Hardy.

---

### Post by Daveth on 2008-11-01
um, what about keeping it off the XP network, and seeing what processes and how much cpu effort is taking place underneath- it sounds like it is busy with other tasks.
You can run
```
top
```
to show this and see what it says (there are probably tidier grep commands but I cannot recall them).
Is Compiz running- turn it off and see what that does and if it makes any difference.

---

