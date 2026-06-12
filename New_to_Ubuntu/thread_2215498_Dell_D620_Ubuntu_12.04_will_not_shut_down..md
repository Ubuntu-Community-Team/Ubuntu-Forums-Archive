---
title: "Dell D620 Ubuntu 12.04 will not shut down."
date: 2014-04-07
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-04-07
When I try to shut down my Dell D620 (12.04), it goes to the purple screen with the Ubuntu logo and the five dots and will not shut down.  Ever.   When I try to pull up a terminal window for a force quit, I get a black page with a few lines of very tiny text about processes that were successfully shut down, and then a line that says, "***Asking all remaining processes to shut down . . . . . . . FAIL***."

Everything was working perfectly until I tried to shut it down for the night.

At this point, I seem to have no option other than to hold the power button down until it shuts off.   I feel like I'm strangling the poor thing. :)

---

### Post by squakie on 2014-04-07
What happens if you open a terminal window and type:

sudo shutdown -h now

---

### Post by mörgæs on 2014-04-07
There are some reports about the problem in 12.04, but I haven't seen it mentioned in later releases.
Does shutdown work in a live boot of 13.10 or 14.04?

---

### Post by riverguy99 on 2014-04-07
Squakie, once it hangs, I can't bring up a terminal window. (See my original post.)  Last night when I went through this I got this curious response on the black screen:

[B]plymouthed: ply-terminal. c:630: ply_terminal_set_mode:Assertion `terminal != ((void*)0)   Failed
[/B]
Does that give anyone a clue?

Sure would like to fix this!

---

### Post by monkeybrain20122 on 2014-04-07
Did you enable quick starter for LibreOffice? If so, disable it.

---

### Post by riverguy99 on 2014-04-07
Quick starter for LibreOffice is not enabled.

The black screen that happens on a shut-down attempt says, "***Asking all remaining processes to shut down . . . . . . . FAIL***," so it seems that something is still running.   I guess all I need do is to figure out what that is?

---

### Post by squakie on 2014-04-07
What I meant was to try to shutdown using the terminal, not the way you are currently attempting.  This may help isolate things and there should presumably be more messages on the screen that may help.

---

### Post by riverguy99 on 2014-04-07
Tried that, too.  Same results. And yes, there is a whole page of tiny-type messages.  Is there a way I can cut/paste or otherwise copy that page?  Remember, my mouse is inop at this point!

---

### Post by squakie on 2014-04-08
Well, I thought there would be some type of record in a log file, but I search in /var/log and can't find anything referencing a shutdown (just did one so I would be able to spot the time in a log).  Not knowing, I did some searching on the net and it appears (and only makes sense) that Ubuntu can't write to a log file once the file system(s) are dismounted, and I *think* that may come fairly quick in a shutdown.

You'll love the suggestion in one such thread:

"If you can't see the messages because of the Plymouth blue screen press esc during the shutdown to see the messages.  Use your video camera to record those messages as they scroll by then post it back in a response".

Sounds rather silly to me, but it would work. ;)  If you try that just post it back here as an attachment or provide a link to something like an Ubuntu 1 public share or something similar.


BTW - where's Forestville or Forestvilee or whatever it is CA?  I lived down along the coast in the LA area in the 80's.  Never made it up past tubing on the Kern River past Bakersfield, so I'm curious where about it is in the state.

---

### Post by riverguy99 on 2014-04-09
Squakie, sorry its taken me a day to get back to this, but work seems to fly in the face of getting my computers sorted.  So for lack of a better way to deal with this, I took some pics of the screens of text I get when the computer hangs on shut-down and I attempt to open a terminal window (contr-alt-t). They are in a dropbox file that you can view here: [https://www.dropbox.com/home/no_shut-down_screendraw](https://www.dropbox.com/home/no_shut-down_screendraw).

The two short ones are what come up.  #2 is the right end of the display that I could not get into the photo and still have it readable.
The full page of text is what comes up for only about three seconds on boot-up.

Another symptom here is that now when I boot up,  instead of the computer just defaulting to Ubuntu after the usual 30-second wait, it hangs on the "select OS" screen until I hit Enter.

Forestville?  We're about an hour's drive north of SF, between Santa Rosa and the ocean, on the Russian River and deep in the redwoods.  Peace and quiet in abundance here, and still affordable by CA standards!

---

### Post by squakie on 2014-04-10
Well, I need to think on those for a little bit.  In the mean time, it sounds WONDERFUL where you are!

An here's my dumb question #"n" - how do I get to your pictures?  I tried just the link and I had to create an account first.  After that, it just goes to my account and tells me the folder doesn't exist - so I'm not seeing it.  An help on that would be appreciated!

---

### Post by riverguy99 on 2014-04-10
Not sure if this is an appropriate thing to do here, but I'd like to refresh this conversation and maybe get some more feedback.

The issue:  12.04 will not shut down.  Whether from a terminal command or an attempted normal shut-down, it hangs at the purple screen with the Ubuntu logo and five dots.  If I attempt to pull up a terminal window at this point, I get a message on a black screen.  Then after a power-switch shut-down, on restart, I get another screen of type that stays for only about 3 seconds. So for lack of a better way to deal with this, I took some pics of the  screens of text I get when the computer hangs on shut-down and I attempt  to open a terminal window (contr-alt-t). They are in a dropbox file  that you can view here: [https://www.dropbox.com/home/no_shut-down_screendraw](https://www.dropbox.com/home/no_shut-down_screendraw).

The two short ones are what come up when I attempt to open a terminal window.  #2 is the right end of the display  that I could not get into the photo and still have it readable.
The full page of text is what comes up for only about three seconds on boot-up.

Another symptom here is that now when I boot up,  instead of the  computer just defaulting to Ubuntu after the usual 30-second wait, it  hangs on the "select OS" screen until I hit Enter.

If there's a useful message in all that, I'd sure love to hear about it because I don't suppose it's a good thing to shut down the computer with the power switch!

Thank you!

---

### Post by riverguy99 on 2014-04-10
OK, I think I see what I did wrong.  You should not even have to have a Dropbox account to do this!

Please try this link:  [https://www.dropbox.com/sh/mc3t24edmf6h40m/OrrlmTd6eq?n=179834464](https://www.dropbox.com/sh/mc3t24edmf6h40m/OrrlmTd6eq?n=179834464)

There are 3 photos.  #1 and #2 are the same screen but in two pieces.  It will be clear when you see them. The other shot is of the full page of text that shows for about 3 seconds on boot up.

I hope you find something useful in there!

Thanks!

---

### Post by squakie on 2014-04-11
Ok, I think there is something else in play here.  I looked at the first 2 screens and noticed that it does say the system will now halt.  So, what I'm thinking is perhaps it IS halting, just not powering off.  If that's the case, we may need to look at things like the power handling in the BIOS.

What I would try:

- don't try shutting down the normal way, instead:

- open a terminal window
- type:

sudo shutdown -H -p  (I think that's it - capital H followed by the -p (for power off after halt)

if you get some type of syntax error from that be sure to post back what it says

if no syntax error, post back what does or doesn't happen.

---

### Post by riverguy99 on 2014-04-11
In response to sudo shutdown -H -p, I get this:

papa@papa-Latitude-D620:~$ 
papa@papa-Latitude-D620:~$ sudo shutdown -H -p
[sudo] password for papa: 
shutdown: invalid option: -p
Try `shutdown --help' for more information.
papa@papa-Latitude-D620:~$

---

### Post by squakie on 2014-04-11
It may be worth adding the acpi option as a boot option.  You could try "noacpi" - if that doesn't help try "acpi=force".  Acpi is how power is handled on the PC, in this case it may/may not allow a power-off at halt (shutdown).  I would first try noacpi - indicating not to use acpi at all.  If that doesn't correct it, try changing that to acpi=force to force acpi.   You can do this via the grub menu or you can change the grub configuration file as needed (not grub.cfg - it is overwritten on many updates).  Let us know how that goes.

---

### Post by riverguy99 on 2014-04-11
Uh, you lost me on "You can do this via the grub menu or you can change the grub configuration file as needed."  I'm still learning and this is new to me, but hey, I'm all about learning.  How do I do it?

---

### Post by riverguy99 on 2014-04-11
BTW, if it matters, this is a dual boot with XP and Ubuntu was installed as "side-by-side." I wish I would have done it the other way with its own partition.  I did that on another machine here and it works better all the way around.  This no-shut-down thing just happened one day after it had been working fine for the week since I installed it.  Is there a way I can re-install 12.04 as a "repair" without losing all the settings and stuff I've worked so hard to get in place?

---

### Post by squakie on 2014-04-11
Oh, when you say side-by-side, do you mean it's a wubi install and not a true dual boot?

---

### Post by riverguy99 on 2014-04-11
Not a wubi install. I downloaded the 12.04 ISO and installed with a USB.  At the screen that comes up early in the install there are three options:  Install as a trial, install side-by-side, or "other."  Other allows you to create a partition for Ubuntu.  I selected the side-by-side for some reason.  On the other installs I created the partition and I wish i had done that on this one.

If there appears to be no fix for this shut-down issue, I may just start from scratch and do a new install.  I'd REALLY rather not do that!  Did you find anything of note in those screen shots?

---

### Post by squakie on 2014-04-11
What I noticed in the screen shots is that the system does halt - it just doesn't power off.  That's why I mentioned the acpi option at boot.

I forgot about that side-by-side option in the partitioning part of the installer.  So at least I know that you really do dual-boot and I assume get a grub menu?

Let's try this:

- boot Ubuntu
- open a terminal window
- type:

gksudo gedit /etc/default/grub <press enter>

This will call up an editor with the defaults for the grub config in it.  Look for a line that looks something like:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change that line to look something like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

- click on the "Save" on the editor bar.
- exit the editor
- type:

sudo update-grub <press enter>

- now select shutdown and use the reboot option, not the complete shutdown option 
- after reboot, now try the shutdown option and see if it works as you want
- if not, repeat all of the above but change "acpi=off" to "acpi=force" and see it that helps

The reason for the shutdown/reboot in the middle of this is because even though the grub config was updated, it still doesn't take effect until after a reboot.  Trying to shutdown and expect power off at that point still would result in the same problem.

Let us know if any of this makes a difference or not.

---

### Post by riverguy99 on 2014-04-11
Well . . . it was already set to "quiet splash acpi=force."  I changed it to "off" and tried to reboot.  Same deal, no shut-down.  Then I powered down manually, restarted, and now, WHOOPEE!  my second display no longer is recognized and the display on the laptop is all out of whack.

This is getting a bit frustrating and I think I'm just ready to re-install 12.04 from scratch. Hours of work, but at least I would feel like I was making some progress.  :)

BTW, on my attempt to reboot, I got that same screen with the line:

"-*killing all remaining processes...........................fail."

Did you get any useful info from the screenshots?

---

### Post by squakie on 2014-04-12
Nope - didn't glean any more from the screen shots.  Right now I'm at a dead end as far as my limited knowledge goes.  I did find a post on the net about this and it put in some different options in the boot line, but since I have no clue what they do or the consequences I can't blindly recommend them even if they might work.

At boot, with the weird screen, can you ctrl/alt/F1 and get a readable terminal window.  If so, try:

sudo cp /etc/default/grub /etc/default/bad-grub

sudo cp /etc/default/grub~ /etc/default/grub

sudo update-grub

then reboot:  sudo shutdown -r now  do you get a normal screen back?  Won't do anything with solving your problem, but would at least get you back to a GUI'd environment so you could back things up, etc., before installing over again.

I also found another post that says to put the acpi=force in a different line:

GRUB_CMDLINE_LINUX="acpi=force"

and reset the other back to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then sudo update-grub and restart, then try shutown again


BTW - if you can, try 12.10 and see if it helps any or not.

Sorry I can't be of help.  Hopefully someone else will see this thread and come to your rescue.

---

### Post by mörgæs on 2014-04-12
> **squakie said:**
> BTW - if you can, try 12.10 and see if it helps any or not.

No, the two options are 13.10 and 14.04. 
12.10 is out of support in a few weeks.

---

### Post by riverguy99 on 2014-04-12
> **squakie said:**
> Nope - didn't glean any more from the screen shots.  Right now I'm at a dead end as far as my limited knowledge goes.  I did find a post on the net about this and it put in some different options in the boot line, but since I have no clue what they do or the consequences I can't blindly recommend them even if they might work.

At boot, with the weird screen, can you ctrl/alt/F1 and get a readable terminal window.  If so, try:

sudo cp /etc/default/grub /etc/default/bad-grub

sudo cp /etc/default/grub~ /etc/default/grub

sudo update-grub

then reboot:  sudo shutdown -r now  do you get a normal screen back?  Won't do anything with solving your problem, but would at least get you back to a GUI'd environment so you could back things up, etc., before installing over again.

I also found another post that says to put the acpi=force in a different line:

GRUB_CMDLINE_LINUX="acpi=force"

and reset the other back to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

then sudo update-grub and restart, then try shutown again


BTW - if you can, try 12.10 and see if it helps any or not.

Sorry I can't be of help.  Hopefully someone else will see this thread and come to your rescue.


Thank you for all your efforts in this.  I guess my next move will be to format my HD and start over with a fresh install of XP and then a frest install of Ubuntu, this time in its own partition.  I hardly ever use XP, but I need it in there for those rare times when I need to pull up something that will only run in Windoze.   I'm happy with 12.04 on my other machines and I like the fact that it is LTS, so I think I'll stick with it. 

Cheers from Forestville!

---

### Post by 12max on 2014-04-12
> **riverguy99 said:**
> Thank you for all your efforts in this.  I guess my next move will be to format my HD and start over with a fresh install of XP and then a frest install of Ubuntu, this time in its own partition.  I hardly ever use XP, but I need it in there for those rare times when I need to pull up something that will only run in Windoze.   I'm happy with 12.04 on my other machines and I like the fact that it is LTS, so I think I'll stick with it. 

Cheers from Forestville!

XP is no longer being supported by microsoft, as from this week

---

### Post by riverguy99 on 2014-04-12
Yeah, XP's demise is why I converted our five computers over to Ubuntu.  I do still need to have it available on at least one machine if I ever need to access old work that I can only service with XP apps, so I figure as long as I never go online with it, it will remain a functional in-house tool.

---

### Post by squakie on 2014-04-13
If you did the "along side of Windows" option in the install, I *think* it probably shrunk the existing partition (where XP is?) and then created a new partition in the space that was saved and installed Ubuntu there.  What I'm getting at is that you shouldn't need to erase the entire drive - just clear the Ubuntu partition (actually, probably 2 - one for the file system and one for swap) and reinstall Ubuntu.  That's *if* the "along side of" option did what I *think* it did.  Try booting a live media (like the liveDVD) and running gparted to see what your current partitions look like).

---

### Post by riverguy99 on 2014-04-15
I think I'm just going to give up.  I started a thread on this several frustrating days ago because after re-installing 12.04 with XP on a Dell D620, everything worked fine but it would not shut down.  I installed via USB prepared in Ubuntu Startup Disk Creator, I tried several different 12.04 downloads from different Ubuntu sites, I tried several different USB sticks, including the very same one I used to install 12.04 the first time on the same computer.  I tried everything I could think of, so there was only one thing left:  Yesterday I reformatted the ehtire HD, reinstalled XP from the original install CD and then installed 12.04.  Everything worked sweetly, Ubuntu found and configured all the drivers, the network, and both my displays were up and running at their preferred resolution.  Then I downloaded all the available updates and tried to restart.  Guess what?  Right.  It will not shut down.  

This computer worked, with 12.04/XP side-by side, and it worked perfectly until a few days ago when it would no longer shut down.  Three long days of trying dozens of suggested fixes, now starting completely from scratch, and the same results.

I'm now feeling that maybe I shouldn't have switched all five of our office and home computers over to Ubuntu after all . . . The rest of them are fine . . . but this one?

I could really use some encouragement here!

---

### Post by baphomet2 on 2014-04-15
Does anything happen?  Does it drop out of the window manager or just sit there?  Anything pop up at all?  Have you tried running "sudo init 0" from the command line?  That might give you some output to maybe clue us into what is causing the hang up.

---

### Post by riverguy99 on 2014-04-15
It just sits there with the purple closing screen (Ubuntu logo and the five dots) forever. At this point, a Terminal window will not come up.  OK, so here's the latest:  I just reformatted the entire HD again, re-installed XP from the original CD.  Once it was installed and working fine, this time I downloaded the 32 bit version of 12.04, just so I'd have yet another distinctly different version, I generated an install USB with Ubuntu Startup Disk Creator, and installed 12.04.  It installed just as it is supposed to, and of course as soon as it was up an running, I tried to shut it down.  Same results.  It just hangs there.  

Now this has happened with 12.04 64bit, 12.04 32bit, and 13.10. I've used four different USB sticks and OS downloads from several different Ubuntu sites. Same results every time.  I'm beginning to feel it has nothing to do with Ubuntu and everything to do with something about this computer.  Funny thing is the reason I am trying this install (for the last three days) is that I had already successfully installed 12.04 64 bit and it had been running great for a week (dual boot with XP), and then one day it wouldn't shut down.

BTW, I have successfully installed 12.04 on four other computers in our office and home, two of them identical Dell D620's to this one that is driving me nuts.

---

### Post by mörgæs on 2014-04-15
Threads merged. Please don't open multiple threads on the same topic.
How does it work in 14.04? Also trying X/Lubuntu for comparison is a good idea.

---

### Post by baphomet2 on 2014-04-15
So that caught me off guard.  The thread merged and all of a sudden there was all this other information and I thought "Was I stupid and not read the entire thread?"  Thanks morgaes for setting that straight.  Now back to the issue.  From the screen shots it looks to me like Squakie is right and that there is something stopping the actual toggle of power when the system is halted.  Have you looked in the logs (should be either /var/log/messages, /var/log/syslog or /var/log/dmesg) to see if you are getting any hardware errors?  I hate to repeat command line requests so please forgive me if you already tried this.  Next time you want to shutdown instead of shutting down through the GUI open up a terminal and type "sudo init 0".  This guarantees that it will run through all the shutdown scripts and hopefully give us more information.

---

### Post by riverguy99 on 2014-04-15
I tried "sudo init 0" and several other "quit" and "force quit" commands that were suggested.  Nada.  Same results.  I posted a photgraph of the entire page of dialog that come on the screen for only about 2 seconds on bootup after a power down to shut off the computer.  Evidently there was nothing in there of any help.  Used to be if I tried to open a Terminal while the stalled closing screen was up, I got some script with a line about "closing all remaining processes..................FAILED."  That hasn't happened in the last few re-installs.  Now I can't open a Terminal window with the purple screen up.

---

### Post by kubug on 2014-05-02
Hi there,

Got the same Dell D620 here which had the same issue. Once I fixed the wireless card drivers the reboot/shutdown started working.
The laptop has a BCM4311 (Dell 1390) wireless card. Here is how I got it working:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

Fix is from [http://ubuntuforums.org/showthread.php?t=1997880&p=12001985#post12001985]("http://ubuntuforums.org/showthread.php?t=1997880&p=12001985#post12001985")

---

### Post by riverguy99 on 2014-05-07
> **kubug said:**
> Hi there,

Got the same Dell D620 here which had the same issue. Once I fixed the wireless card drivers the reboot/shutdown started working.
The laptop has a BCM4311 (Dell 1390) wireless card. Here is how I got it working:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

Fix is from [http://ubuntuforums.org/showthread.php?t=1997880&p=12001985#post12001985](http://ubuntuforums.org/showthread.php?t=1997880&p=12001985#post12001985)

WOW!  After a month of trying a bezillion "fixes" including reformatting my HD and reinstalling 12.04, this simple trick did the job.  Since there were quite a few others on the Forum with this same issue, I hope they all find your posting. I still have no idea WHY this should have worked, but it did.

THANK YOU SO MUCH!!!

---

### Post by kubug on 2014-05-07
You are welcome. I was fixing this laptop up for someone else, and those were the two major issues with it. But once the wireless drivers were installed, the machine didn't hang on shutdown anymore either. 
I figured I better post what I had found here so that others don't have to look for as long as I did.

BTW, I also put a cheap little 60GB SSD ($40!!) in that laptop and it made it work awesome. Got some more life out of it for just a few bucks.

Cheers!

---

