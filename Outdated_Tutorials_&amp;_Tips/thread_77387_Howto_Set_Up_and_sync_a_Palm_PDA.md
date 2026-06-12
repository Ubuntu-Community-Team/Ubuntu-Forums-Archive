---
title: "Howto Set Up and sync a Palm PDA"
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by matthew on 2005-10-16
[COLOR=DarkRed]EDIT: This howto is rather old and is no longer being actively supported.[/COLOR] The information here may still work...it did for me on every release except 6.04. You are still welcome to post questions in the thread and I and others will probably read them, but I can't promise there will be any good answers forthcoming. I recommend looking at the wiki for the latest: [https://wiki.ubuntu.com/CategoryPDA](https://wiki.ubuntu.com/CategoryPDA) . [COLOR=DarkRed]/EDIT[/COLOR]

I am submitting this for testing by the Palm PDA-using community. I have only tested this with my computer and palm, so this should not be considered definitive yet until others post with their equipment and results.

**For the record, here's my setup:**
Laptop running Ubuntu 5.10 "Breezy Badger"
Palm m130 using PalmOSv4.1
Syncronization is being accomplished using a USB cradle or cable
I am synchronizing my calendar, datebook, contacts with Evolution

1 - Plug the usb cable into the usb port on your computer.

2 - Put your Palm in the cradle or plug in the cable.

3 - Go to System->Preferences->Palm OS Devices

4 - In the Pilot Settings pop-up select the Devices tab and click Add.

5 - In the Device Settings pop-up enter info as follows:

Name: Cradle
Port: /dev/ttyUSB0   <--*see bottom
Speed: 57600
Timeout: 2
Type: USB

Click OK and then click Add again and enter:

Name: Cradle1
 Port: /dev/ttyUSB1   <--*see bottom
 Speed: 57600
 Timeout: 2
 Type: USB

6 - Now, back in the Pilot Settings window select Pilots and click Add

7 - Once the new pop-up appears, press Synchronize on your PalmPDA

While it is searching, select "Get from pilot" in the pop-up window just mentioned. Your computer should synchronize and get a Name, ID and username from your PDA. Now your device officially exists in the gpilot database on your computer.

8 - Close the most recent pop-up. You should still have the main Pilot Settings window open. Click the Conduits tab to decide what you want to synchronize and so on...this is essentially the same as what you may have used on other OS's.

**Finally:** Every time you want to sync, make sure gpilot is running and then hit the sync button on your PDA.

**Note:** I have not tried yet to install software, etc on my Palm from Ubuntu. 

**My current Conduits settings look like this:**
Backup-enabled (E) [makes a folder in my /home]
EAddress-synchronize (S)
ECalendar-S
Expense-disabled (D)
File-E
MAL-D
MemoFile-S [makes a folder in my /home]
Sendmail-D
Test-D
Time-E

*this is important! /dev/pilot never worked for me even though it is the default. I ran ```
ls /dev/ttyUSB*
``` while the PDA was plugged in and sync was initiated from the PDA to discover which address to use here.

[COLOR=Red][I]Please post your thoughts, experiences, questions and comments. This has only been tested so far by me with the equipment listed above. I would love to see a list develop of what works/what doesn't for those who want to use these devices.

[/I][COLOR=Black]EDIT: If you are reading this you might want to take a look at these two wiki pages before you do anything.
[https://wiki.ubuntu.com/PDADeviceList](https://wiki.ubuntu.com/PDADeviceList)
[https://wiki.ubuntu.com/EasyPalmDeviceSetup](https://wiki.ubuntu.com/EasyPalmDeviceSetup) **I haven't tried this since my palm is working, but it might save you some time.

EDIT#2: Someone in [this thread]("http://ubuntuforums.org/showpost.php?p=528113&postcount=5") found this link helpful. Looks good. [http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html)
[/COLOR][/COLOR]

---

### Post by vvlist on 2005-10-21
Hi, I used your howto with my visor prism (Palm OS v.3.5.2H), and issuing /dev/ttyUSB0 had the output: /dev/ttyUSB0 I followed the rest directions to the T. Nothing happened. So, just so everyone knows, this method does not work with visor prisms.

---

### Post by matthew on 2005-10-21
[quote=vvlist]Hi, I used your howto with my visor prism (Palm OS v.3.5.2H), and issuing /dev/ttyUSB0 had the output: /dev/ttyUSB0 I followed the rest directions to the T. Nothing happened. So, just so everyone knows, this method does not work with visor prisms.[/quote]
Thanks for the input. BTW, what was the output of
```
ls /dev/ttyUSB*
```
run while the pda was in the cradle/attached to the cable and to the computer and trying to sync?

---

### Post by naomi on 2005-10-23
Many thanks for this helpful tutorial! :)

I have a Tungsten T5 and the /dev/pilot didn't work for me either. However /dev/ttyUSB1 worked.

Btw any idea on how to synchronise with Avantgo? I read the following thread
[http://www.ubuntuforums.org/showthread.php?t=53752]("http://www.ubuntuforums.org/showthread.php?t=53752")
but I was wondering if there is a better/easier solution having the new Ubuntu release installed.

---

### Post by matthew on 2005-10-23
Hi, naomi,

I'm glad that this worked for your T5. Thank you so much for posting your results. I'm afraid I don't have any experience with Avantgo so I am not able to help with that. Sorry.

---

### Post by CrunchyDoodle on 2005-10-23
Can you still run the Files application on your T5 after syncing it with ubuntu? My LifeDrive can't. I get a hard crash if I run Files, as does a number of LifeDrive owners who have used other-than-the-supplied Palm Desktop to Hotsync. I do realize a T5 is not a LifeDrive, but they are quite similar. 

Bye.     :cool:

[QUOTE=naomi]Many thanks for this helpful tutorial! :)

I have a Tungsten T5 and the /dev/pilot didn't work for me either. However /dev/ttyUSB1 worked.

Btw any idea on how to synchronise with Avantgo? I read the following thread
[http://www.ubuntuforums.org/showthread.php?t=53752]("http://www.ubuntuforums.org/showthread.php?t=53752")
but I was wondering if there is a better/easier solution having the new Ubuntu release installed.[/QUOTE]

---

### Post by naomi on 2005-10-24
[QUOTE=CrunchyDoodle]Can you still run the Files application on your T5 after syncing it with ubuntu? My LifeDrive can't. I get a hard crash if I run Files, as does a number of LifeDrive owners who have used other-than-the-supplied Palm Desktop to Hotsync. I do realize a T5 is not a LifeDrive, but they are quite similar. 

Bye.     :cool:[/QUOTE]

Yes, I can! Haven't had any problems after synchronizing with Ubuntu :)

---

### Post by simplyw00x on 2005-11-12
I am using a T|T5, and the following problems occur:
[LIST]
[*]PalmOS Devices is in 'Preferences', not 'Administration'
[*]The options described in the HOWTO are not available in the dialog I see when opening 'PalmOS Devices'
[*]The output of 'ls /dev/ttyUSB*' is "ls: /dev/ttyUSB*: No such file or directory"
[*]The autodetect does not work.
[/LIST]

---

### Post by matthew on 2005-11-12
[quote=simplyw00x]I am using a T|T5, and the following problems occur:[LIST]
[*]PalmOS Devices is in 'Preferences', not 'Administration'[/LIST][/quote]

You are right! I'm sorry about that. I have fixed this in the how-to. Thank you for pointing it out.[quote=simplyw00x][LIST]
[*]The options described in the HOWTO are not available in the dialog I see when opening 'PalmOS Devices'[/LIST][/quote]
At the upper left, just under the main title bar are three tabs. The Devices tab is the one in the middle between Pilots on the left and Conduits on the right.[quote=simplyw00x][LIST]
[*]The output of 'ls /dev/ttyUSB*' is "ls: /dev/ttyUSB*: No such file or directory"[/LIST][/quote]
Was the cradle plugged in to the computer with the Palm attached ***and*** trying to sync at the time you ran this command?[quote=simplyw00x][LIST]
[*]The autodetect does not work.[/LIST][/quote]
It won't work until everything else is completed correctly.I have to go out of town for a few days. I hope to be able to check in Monday or so.

---

### Post by matthew on 2005-11-13
I added the following two links to the how-to. You might find them helpful.

[https://wiki.ubuntu.com/EasyPalmDeviceSetup](https://wiki.ubuntu.com/EasyPalmDeviceSetup) **I haven't tried this...my palm is working and I used my method, but this seems pretty easy.

[https://wiki.ubuntu.com/PDADeviceList](https://wiki.ubuntu.com/PDADeviceList)

---

### Post by aldmal on 2005-11-28
I have a Tungsten T and had all the same problems.

[QUOTE=simplyw00x]I am using a T|T5, and the following problems occur:
[LIST]
[*]PalmOS Devices is in 'Preferences', not 'Administration'
[*]The options described in the HOWTO are not available in the dialog I see when opening 'PalmOS Devices'
[*]The output of 'ls /dev/ttyUSB*' is "ls: /dev/ttyUSB*: No such file or directory"
[*]The autodetect does not work.
[/LIST][/QUOTE]
 
I'm running the current Ubuntu on a AMD 1600. I followed all your instructions and the two other links you posted and nothing worked. I've tried to use jpilot also - same results. It seems that Ubuntu is not working on any of my USB ports. I have 6. My printer is on a USB and does not work either.

Any more suggections would be greatly appreciated.

---

### Post by matthew on 2005-11-28
[quote=aldmal]I have a Tungsten T and had all the same problems.

[quote=simplyw00x]I am using a T|T5, and the following problems occur:[LIST]
[*]PalmOS Devices is in 'Preferences', not 'Administration'
[*]The options described in the HOWTO are not available in the dialog I see when opening 'PalmOS Devices'
[*]The output of 'ls /dev/ttyUSB*' is "ls: /dev/ttyUSB*: No such file or directory"
[*]The autodetect does not work.[/LIST][/quote]  
I'm running the current Ubuntu on a AMD 1600. I followed all your instructions and the two other links you posted and nothing worked. I've tried to use jpilot also - same results. It seems that Ubuntu is not working on any of my USB ports. I have 6. My printer is on a USB and does not work either.

Any more suggections would be greatly appreciated.[/quote] Hmm... Well, since there are two of you having problems with a PalmT/T5 I am beginning to wonder if there may simply be a problem with that series. Without access to any equipment other than my own I can't play with it to try to figure out the problem. I did take a very quick look on Google and thought these might be helpful to you in your quest.

[http://mail.gnome.org/archives/gnome-pilot-list/2005-August/msg00020.html]("http://mail.gnome.org/archives/gnome-pilot-list/2005-August/msg00020.html")
[http://www.pilot-link.org/]("http://www.pilot-link.org/")
[http://www.pilot-link.org/node/160]("http://www.pilot-link.org/node/160")

If/when you get your T/T5 working please post back here for others who may be trying to do the same thing. It seems that many people are having trouble syncing that series.

EDIT: someone [in another thread]("http://ubuntuforums.org/showpost.php?p=528113&postcount=5") found this link incredibly helpful in getting their PalmIIIC to work...thought I would add it here as well: [http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html)

---

### Post by dotmil on 2005-11-28
No luck here with Tungsten E and self-built kernel 2.6.14-ck. The output to /var/log/messages shows the device as recognized on ttyUSB0 & ttyUSB1 (as normal), but the device nodes are never created. Instead, when I click to hotsync it appears that the udev creates it at /dev/usbdev5.1++ each time I click it (had up to usbdev5.10 before I gave up). Any ideas on how to work around this problem? I tried adding usbdev5.* in place of ttyUSB* in the udev rule from above, but no joy there either.

---

### Post by aldmal on 2005-11-29
Well, my eyeballs hurt from all the reading and my hair is in a pile around my chair but my Palm still does not sync. :=(

Here's specifically what I've done so far.

Per [http://www.pilot-link.org/node/111](http://www.pilot-link.org/node/111) my Palm's spec are:
      Palm OS:              5.0
      Kernal:                 2.4.21-pre 1
      Port:                    USB
      Vendor/product:    0830/0060
      Port(Linux/BSD)     USB0

Following the instructions in [http://pilot-link.org/README.usb](http://pilot-link.org/README.usb) I created a file in /etc/udev/rules.d called pilot.rules, with the following information in it:

         BUS="usb" SYSFS{product}="Palm Handheld*" KERNEL="ttyUSB*"                          SYMLINK="pilot" MODE="666" KERNEL="ttyUSB*" SYMLINK="pilot"

I also entered the following instruction:

modprobe visor product=0060 vendor=0830

I opened J-Pilot and tryed to snyc. No luck. My Palm timed out.

My /var/log/messages shows the following:

usb 1-1: new full speed USB device using uhci_hcd and address 5
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
visor: already loaded
usb 1-1: USB disconnect, address 5
visor 1-1:1.0: device disconnected
visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1

I tryed J-pilot a few more times with the same message. The only thing I see changing in my log is the address. It keeps incrementing 1. So when it got to 8 I stopped.

Next, I opened Gnome Pilot Settings and ran it with the following setting:

       Cradle
       /dev/pilot
       speed 57600
       Timeout 1
       USB

The Palm timed out. Same log message but address 9.

I tried again with all the setting the same except for /dev/pilot changed to /dev/ttyS0. Got the same message except for address now 10

Granted, I'm new to Linux, but it can't be that hard to get the Palm running. Or can it?

---

### Post by matthew on 2005-11-29
dotmil and aldmal:
I'm not sure what to do from this point to help you out. Sorry. I truly wish I could be more helpful, but I'm just a guy who got his stuff working (maybe I was lucky and have the same hardware as a developer?).

You may want to go to [https://bugzilla.ubuntu.com](https://bugzilla.ubuntu.com) and file a bug report so the developers know you can't get your equipment to sync. That would at least let them know since they don't generally hang out in these forums.

---

### Post by aldmal on 2005-11-29
And the saga continues.

On another website I found out that KPilot works. So I installed KPilot and ran the set-up wizard. It found my Palm. So at least now I know that the hardware is working. 

Two points.

The KPilot set up wizard recommending against running auto detect in 2.6  because it might not work until a reboot. They are right.

The second thing is that KPilot cannot sync with the current rel of Evolution. Ubuntu does not come with KCalender. So all I can do at this point is backup my Palm data to the PC.

On the pilot-link site I found some comments that rel 0.12 does not work 0.11 does work with the Palms. I downloaded the correct version but have no idea how to install it correctly. 

Oh boy! new operating systems are so much fun!

---

### Post by matthew on 2005-11-29
[quote=aldmal]And the saga continues.[/quote]Phew. Well, at least there is progress. Good job.
[quote=aldmal] Oh boy! new operating systems are so much fun![/quote]Isn't it? No matter who the players have been the problems exist, sometimes even if it is the same company and just a newer version of the OS. You seem to have a pretty good attitude about it and that gives me hope that you will discover a real solution.

---

### Post by aldmal on 2005-11-29
I fell like I'm on a hopeless quest!

To further the research. I installed KDE desktop and ran it. KPilot and Kontacts work together. Only the first sync of a sesion works. It seems that the problem is in Ubunbtu. Every time the Palm port is opened the address increments one. So KPilot will work the first time and then go dead.

We need to find a way to stop Ubunbtu from incrementing the address. I'll have to look around for this solution.

Along the way, I also loaded and ran XFc, the only Palm sync apps I could find were from Gnome and KDE. So I did not bother testing it. By the way, didn't like the GUI either.

Thanks for the kind words and support.

---

### Post by aldmal on 2005-12-01
Victory is sooo sweet.

I knew if I pushed enough keys something would work.

What worked for me.

I searched and applied all advice I could find. Nothing worked. Today I did a  (pardon my DOS) format C: 

Installed Breezy all over again. Update it. Tried to sync - nothing. Tried jpilot - nothing. Tried Multisync - nothing.

Downloaded and installed KDE desktop. In other words I changed from Ubuntu to Kbuntu. Have synced half a dozen times now :-) I keep doing it just to enjoy the little sound my Palm makes when it completes a sync. Music to my ears.

I suspect there is something broken in the Gnome conduits. When I press sync the system sees the Palm and the Palm sees the system but no data trasfers. The sync just times out. In KDE the sync works just like it did in that OS that shall remain unspoken. ;-) 

Hope this helps.

---

### Post by matthew on 2005-12-02
aldmal: congratulations! I'm glad it's finally working. Sorry it was such a bear to figure out. Hopefully your post will help someone else who is struggling.

---

### Post by styla on 2005-12-06
hi, folks!

what helped aldmal is not really an option for me. i just don't have quite the time to reinstall my linux. plus, evolution *is* a nice program.

I have a Palm m500 I recently bought off ebay. All the syncing stuff is cool, but takes a *lot* of time to configure *sigh*. I've looked into kpilot, too, but since it doesn't sync with any GNOME apps, I kicked it out again. I have my reservations in regards to KDE, I have to admit.

Anyway, the syncing has worked great for a few days now, but at some point I figured I would like to use the sendmail conduit as well. I did a few changes in the gnome-pilot settings but nothing helped, the palm won't sync any more. It just times out - and I hate it when that happens... :( 

Whatever, it's late. I'll try again tomorrow and let you guys know what happens.

---

### Post by Grue on 2005-12-07
How about a guide to get IRDA syncing to work?

I posted a question on the subject [here](http://ubuntuforums.org/showthread.php?t=97845).

---

### Post by Sokraates on 2005-12-07
After a lot of searching (read this thread, too) I finally got syncing working again. Posted it to another thread a few days ago, so I'll just quote myself.

Hope it helps someone.

[HTML]I had the same problem with my Tungsten E. gnome-pliot, jpilot and kpilot refused to sync after upgrading to Breezy. And they all complained that ttyUSB1 didn't exist. Before the upgrade, it worked like a charm.

The solution:

```
$ sudo gedit /etc/udev/rules.d/10-custom.rules
```

Delete the following line:

```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```


Right. Just the one we all entered to make syncing work with Hoary.
I figured it out after trying to sync with a breezy live-cd and it worked.

If there are no other entries, you can probably delete the whole file.

Edit: Forgot to say, that it now works with jpilot and kpilot, using /dev/pilot or /dev/ttyUSB1.[/HTML]

By now I've deleted /etc/udev/rules.d/10-custom.rules, since another entry prevented my digicam from being recognized in PTP-mode.

---

### Post by gypsy98101 on 2005-12-14
I will add my two cents just in case someone still can't get theirs to work and to request some comments on my solution.
First, I tried pretty much everything I could find in these forums, including some udev scripts.  Please note that I am very much a noob and I was doing things that I hardly understood so I'm not totally sure what state my computer was in except that my 'palm pilot' (actually a Treo 600) would only be recognized if I logged in as root.  If I logged in as root, things worked nice, everything would hotsync, it was heaven.  But since I do in fact understand the dangers of working in the root login, I don't want to use root for anything except sys admin stuff.  
So my problem was precisely this:  everything worked fine as root, but I couldn't 'see' the device when logged in as a normal user.  I found a few threads that alluded to this problem, but none of them really helped.  Part of the problem is that the device node is not created until an actual hotsync is performed, and then it's kind of fleeting.  I tried configuring KPilot lots of ways to sort of 'guess' which node was going to be created, but nothing worked reliably.  I was frustrated.
Here was my solution:  I logged in as root (here is yet another valid use for the root account) so I could watch what happened.  I opened konqueror to the '/dev/' directory and then plugged in myTreo.  When I hit the hotsync button, I noticed that a new node, which was actually a link, was created named '/dev/pilot/'.  So guessing that priveleges on that thing were really at issue, I quickly checked what the owner/group and privileges were of that node.  I noticed that the owner was root but the group was something funny, like 'dialout' or something.  Not having any other plan, I opened KUser while still in root and added the group 'dialout' to my other limited-rights account.  Guess what.  When I logged in as the limited-rights user (+dialout) everything worked like a champ.  Now I can hotsync as an ordinary user and life is SWEET again.  
I'll also throw in that, armed with this new e-weapon, I was also able to get my iPod noticed as an ordinary user although I had to add a different group (plugdev or something like that).  Now I really feel like I'm on to something here.
So here's my question to anyone, how dangerous is adding these groups to a limited-rights account?  I understand completely that the more groups I add, the less limited the account is, but are the two groups I just mentioned (dialout and plugdev) something to worry about?  And if so, how would I locate and change whatever the thing is that is dynamically creating these nodes in dangerous (if so) groups?

---

### Post by silverfire on 2005-12-16
Here's a question for you. I can sync and install files to my Zire 71 just fine. The only problem is I can't install anything directly to the SD card. I have to install to the device, then move the installed app to the card after. I installed a freeware MP3/OGG player app and would like to use it; however, I cannot get the media files on the card in a way that lets them be recognized.

I tried formatting the card, thinking that might help. Ha. Now I can't do anything but read the card with the SD card reader I have on my computer. So I can't put the music files on the card that way, either.

Anyone have any ideas on how I can get this to work? I'd love to be able to install things directly to the card, like you can in the Palm Desktop software in Windows. And I'd also love to be able to take advantage of the music-playing ability my Palm has. Any help you can offer will be greatly appreciated.

Thanks.

---

### Post by matthew on 2005-12-16
[quote=silverfire]Here's a question for you. I can sync and install files to my Zire 71 just fine. The only problem is I can't install anything directly to the SD card. I have to install to the device, then move the installed app to the card after. I installed a freeware MP3/OGG player app and would like to use it; however, I cannot get the media files on the card in a way that lets them be recognized.

I tried formatting the card, thinking that might help. Ha. Now I can't do anything but read the card with the SD card reader I have on my computer. So I can't put the music files on the card that way, either.

Anyone have any ideas on how I can get this to work? I'd love to be able to install things directly to the card, like you can in the Palm Desktop software in Windows. And I'd also love to be able to take advantage of the music-playing ability my Palm has. Any help you can offer will be greatly appreciated.

Thanks.[/quote]I've never tried to do this. If no one replies here you might want to post a new thread in case there is someone who might know but who is not reading this particular thread.

---

### Post by silverfire on 2005-12-17
I got the read-only access problem fixed. I ended up having to do a mkfs.vfat on the device, after I finally got it unmounted (I'd switched back to Linspire, in the hopes that maybe it was just something in Ubuntu that was causing it, and I ended up unable to unmount it until I killed a process trying to access it or write to it or something along those lines). 

I got the player program re-synced to the Palm, put a test .ogg file on the card, then tried it out. It worked. Yay. :D

Now my only concern is still the install directly to card issue. Not as big an issue now, but still an issue.

---

### Post by dotmil on 2005-12-18
[QUOTE=Sokraates]After a lot of searching (read this thread, too) I finally got syncing working again. Posted it to another thread a few days ago, so I'll just quote myself.

Hope it helps someone.


By now I've deleted /etc/udev/rules.d/10-custom.rules, since another entry prevented my digicam from being recognized in PTP-mode.[/QUOTE]

Awesome! This finally got me up and running! Thanks!

---

### Post by pito on 2005-12-19
Hello...Hope I am not boring you...

I do have problems with synchrinizing my Palm with the 5.10 ubuntu. It worked OK on Fedora Core3 for over a year. Now Ihave switched to Ubuntu. Very nice Distro but the palm-pilot stopped to work.

I see that /dev/ttyUSB0 and /dev/ttyUSB1 are created when the the Palm Pilot is connected.
I use UDEV utilities and I see that it create correct /dev/pilot automatically every time the pilot is connected.

In the /var/log/messages I see all the stuff correctly initialized.
The problem is that when I Sync the Palm nothing happends.
dplsh -p /dev/ttyUSB0 is not working
dplsh -p /dev/ttyUSB1 is not working
dplsh -p /dev/pilot neither works

/sbin/lsmod shows usbserial as stated on some TODOs lists.


I did try the GNOME UI for pilot but with the same negative result.

Any clue ? MAybe some one of you has the same problems ?
Is there any possibility to debug/log things on line and see what is happening ?

Best Regards
PiTo

---

### Post by styla on 2005-12-20
well... syncing works for me.

i had put /dev/USB0 and /dev/USB1 as Cradle and Cradle1 in my Gnome-pilot settings thingy but it wouldn't sync. Or rather, it did once and I thought awesome. But the next time I tried, it didn't.

Just yesterday I added yet another cradle: /dev/pilot as Cradle2 and lo, it did sync again.

Just to make sure I don't tell you crap I just tried five syncs on my palm m500 (like the ad says: "Isn't it great when things just... work?"). They worked smoothly - after I unplugged my MP3 player and plugged the HotSync station in again... ;)

---

### Post by pito on 2005-12-20
Good for you Stylla

I will try to find a Windows machine in the near(I do only have Linuxes at home) and try to Synch there. If not I will probably reset my palm, since I do see all the initalizations OK, beside ths sync itself.
I have read somewhere that in some cases the Palm Sync hangs due to static discharge, and I did not synch mine for some moths...

see u.
PiTo

---

### Post by crispingatiesa on 2005-12-22
Thanks a lot for the how to , I got a lifedrive for christmas, used your how to  and everything went painless

---

### Post by matthew on 2005-12-22
pito: Sorry we haven't figured out how to get it working for you...

styla: I'm very pleased syncing worked so easily for you! That's encouraging.

crispingatiesa: Cool! It's so gratifying when something so potentially difficult works so easily for someone.****

---

### Post by pharm.foo on 2005-12-23
Thank you Matthew,

you're mini-HowTo inspired me to a:

sudo apt-get install pilot-link
sudo apt-get install jpilot

And with the proper /dev/ttyUSBx setting in jpilot, the Ubuntu
5.10-Lifedrive HotSync works just fine out of the box :-)

(I use jpilot because evolution's tasks categories don't seem to sync?!)

---

### Post by matthew on 2005-12-23
[quote=pharm.foo]Thanks you Matthew,

you're mini-HowTo inspired me to a:

sudo apt-get install pilot-link
sudo apt-get install jpilot

And with the proper /dev/ttyUSBx setting in jpilot, the Ubuntu
5.10-Lifedrive HotSync works just fine out of the box :-)[/quote]Cool...glad to hear I could help a little!

---

### Post by pito on 2006-01-01
The sync saga is going on...

As mentioned earlier I do have problems to Sync the Palm pilot IIIxe
with the serial-usb converter of type KL5KUSB105D. I did all the trix
nothing happends.

What I did today was that I borrowed a Palm Tungsten T2, with the USB.
Connected it to the Ubuntu 5.10, pressd sunc and run the dplsh
-p /dev/ttyUSB0

Every thing worked at once No problem at all.
The I started the jpilot and once again. All works perfect.

It seems to me that the serial-to-usb dongle does not work any longer
with pilot-link or not with the new core. It really did a year ago when I installed the Fedora Core 3. 

Maybe there has been some smart changes in the new releases ?

Part of the :$lsmod (when running on palm IIIxe with serial to USB
dongle looks like that.

kl5kusb105             11524  0
visor                  16652  0
usbserial              26984  2 kl5kusb105,visor

what is scary here is that I do two usb serial connection one kl5usb105
and second visor. Maybe the system get confused ?

What I see in the /var/log/messagess is again a little special

when running on Palm T2 I see:

localhost usb.agent[8891]:      visor: loaded successfully

when running pn Palm IIIxe I see:

localhost usb.agent[9784]:      kl5kusb105: loaded successfully

Again we see that now the serial converter is loaded not visor...

Maybe it will give someone a clue ?

Did any body try the serial-usb converter with later pilot-link or later
kernerl ?


Best regards and HP NY
PiTo

---

### Post by TransitMan on 2006-01-05
Just thought I'd pop in and thank those that posted their various setups for getting their Palms to work

After a lot of trial and error, I finally got my Palm m500 to sync. 
Such a sweet sound it is too.
Just one more step in getting away from M$ and the pricey OS.

---

### Post by matthew on 2006-01-05
TransitMan: Glad to hear it and welcome!

---

### Post by chakra_dude on 2006-01-20
got my Palm M105 to work.
will try my M515 later this weekend

---

### Post by matthew on 2006-01-20
[quote=chakra_dude]got my Palm M105 to work.
will try my M515 later this weekend[/quote]Great! Please let us know how it goes with the m515.

---

### Post by ajmoncrief on 2006-01-30
I had a m500 synching sucessfully under breezy and hoary using the howto on this site: [http://www.ubuntuforums.org/showthread.php?t=3591](http://www.ubuntuforums.org/showthread.php?t=3591).  I however, am having one helluva time getting gnome-pilot to detect my new T|X or TX whatever you wanna call it.  I can get most of it to work on kpilot, and it seems to be doing something (although I cant tell what) on jpilot.  But I would really prefer gnome-pilot as evolution for me is much much more stable and usable than kontact.  Any ideas?

---

### Post by matthew on 2006-01-30
Hmm. I don't have any experience with that specific model. Anyone else out there used one??

---

### Post by Brigrat on 2006-01-31
I am still new at this, and was getting very frustrated that getting my palm to work was that hard.  I have both a palm m130 and a Kyocera 7195 Smartphone based on a palm OS 4.1.  I could only get the serial connection to work before, as the USB was still a booger.  I finally spent about 3 hours looking at every google/wiki/forum thread - tried everyone...
Then down loaded finally KPILOT.  It came up loaded, configured, and worked.  It located recognized the smartphone just as fast as it did the M130.  Gave me the option of using either evolution or kontact as the pc side.  As the saying goes it just worked.  I am going to try my ancient palm visor tonight and post those results tomorrow.  So for those who are tired of beating their head against the wall.  give KPILOT a try.

Dan\\:D/

---

### Post by matthew on 2006-01-31
[quote=Brigrat]I am still new at this, and was getting very frustrated that getting my palm to work was that hard. I have both a palm m130 and a Kyocera 7195 Smartphone based on a palm OS 4.1. I could only get the serial connection to work before, as the USB was still a booger. I finally spent about 3 hours looking at every google/wiki/forum thread - tried everyone...
Then down loaded finally KPILOT. It came up loaded, configured, and worked. It located recognized the smartphone just as fast as it did the M130. Gave me the option of using either evolution or kontact as the pc side. As the saying goes it just worked. I am going to try my ancient palm visor tonight and post those results tomorrow. So for those who are tired of beating their head against the wall. give KPILOT a try.

Dan\\:D/[/quote]That's great! I hope someone else finds this useful. Thank you for letting us know what worked for you!

---

### Post by Moonbuzz on 2006-02-04
I've used the instructions in the wiki and it worked from the get go, got the palm synchronized with Evolution and gpilot, but I still have one problem that prevents me from fully enjoying it, as I can't install files. I've tried placing them in the MyPilot folder, but every sync just move them to a "delete" folder under that folder. Any ideas what I'm doing wrong?

---

### Post by matthew on 2006-02-04
[quote=Moonbuzz]I've used the instructions in the wiki and it worked from the get go, got the palm synchronized with Evolution and gpilot, but I still have one problem that prevents me from fully enjoying it, as I can't install files. I've tried placing them in the MyPilot folder, but every sync just move them to a "delete" folder under that folder. Any ideas what I'm doing wrong?[/quote]That's a great question. I have never tried to install files. I filled my pda's capabilities under Windows and it's never crashed. I'm on the road at the moment and won't be home for about 10 days. I'll try it out when I get time. In the meanwhile, hopefully someone else will chime in here.

---

### Post by pangloss on 2006-02-22
I didn't find it terribly obvious that I need to run gpilot-install-file before sync.

e.g. ```
$ gpilot-install-file -l foo.prc
```

[QUOTE=matthew]That's a great question. I have never tried to install files. I filled my pda's capabilities under Windows and it's never crashed. I'm on the road at the moment and won't be home for about 10 days. I'll try it out when I get time. In the meanwhile, hopefully someone else will chime in here.[/QUOTE]

---

### Post by steve650 on 2006-03-23
It works!  I have a Palm T2 in a USB cradle and it recognized the USB0 immediately.  Thanks for saving time and aggravation.  One small glitch... it won't sync the categories.  Can anyone help with this?  

Steve

---

### Post by mcwtlg on 2006-03-24
I have a Tungsten E and I use Gnome.  I still have not gotten the darned thing to sync 100%.  It hangs on jpeg something and all the searching I have done says that synching under Gnome with a Tungsten E is not possible.

Any other T|E users running Gnome?

I never really liked KDE, but I really am enjoying running XFCE on my two underpowered boxes (1 at work and 1 at home) and I am thinking about running it full time on my newer (3 ghz) machine.  What about synching my T|E under XFCE?  Anyone?

---

### Post by EscapeForSurfing on 2006-04-04
First: thanks for this how-to, the only one i found working for my T|E!! 

Just a question: I used tu use windows and "documents to go" for sync .xls .doc and so on. Do exist something similar for Ubuntu (even working with OpenOffice file)?

I apologize for my bad english.

---

### Post by matthew on 2006-04-05
[quote=EscapeForSurfing]First: thanks for this how-to, the only one i found working for my T|E!! [/quote]You are very welcome. I'm glad it worked for you!

[quote=EscapeForSurfing] Just a question: I used tu use windows and "documents to go" for sync .xls .doc and so on. Do exist something similar for Ubuntu (even working with OpenOffice file)?[/quote]That's a great question...I wish I knew the answer to it. Anyone else want to chime in here??

[quote=EscapeForSurfing] I apologize for my bad english.[/quote]It's far better than my French! No apology necessary.

---

### Post by EscapeForSurfing on 2006-04-05
[QUOTE=matthew]
That's a great question...I wish I knew the answer to it. Anyone else want to chime in here??
[/QUOTE]

No problem... but this is the last think i need to  learn, before abandone Windows (actually i have already a dual-boot).....
But I'm very happy, i started to use Ubuntu two weeks ago, i though it would be more difficult!! \\:D/

---

### Post by marsopia on 2006-06-08
1 - Plug the usb cable into the usb port on your computer.

2 - Put your Palm in the cradle or plug in the cable.

3 - Go to System->Preferences->Palm OS Devices

4 - In the Pilot Settings pop-up select the Devices tab and click Add.

5 - In the Device Settings pop-up enter info as follows:

Name: Cradle
Port: /dev/ttyUSB0 <--*see bottom
Speed: 57600
Timeout: 2
Type: USB

Hi Mathew and everyone!
I am a Ubuntu user since 4.10, and my Visor Dlx always worked fine, till I upgraded to Dapper Beta, I lost the cappabillity to sync. I made a clean install of final Dapper, willing it would solve the prob.
Ther is no PalmDevices on my System->Administration menu.
I get this when I do 1 mariano@mariano-desktop:~$ ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2006-06-08 18:00 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2006-06-08 18:00 /dev/ttyUSB1

I Tried both ttyUSB0 & 1 on Jpilot, but nothing happens.
Any idea how to fix this?
Thanks in advance

Mariano

---

### Post by matthew on 2006-06-08
Hi, Mariano. Bad news...almost all of us are finding it nearly impossible to sync with Dapper. I don't know what changed, but I know bugs have been filed. Hopefully an update soon will fix the problem. I myself have been unable to sync in Dapper.

---

### Post by wastrel on 2006-06-08
The bug in dapper relates to how gpilotd talks to USB:

[https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653](https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653)

If you can network sync or IR sync it should work.  Meantime, sync with jpilot instead of gpilotd.

---

### Post by marsopia on 2006-06-08
[QUOTE=wastrel]The bug in dapper relates to how gpilotd talks to USB:

If you can network sync or IR sync it should work.  Meantime, sync with jpilot instead of gpilotd.[/QUOTE]
TY Mathew & Wastrel!
It seems I have to wait... and go on syncyng w/guindows.... I have no irda on my pc.. lets wait..

ty again 4 your advice...


mariano

---

### Post by pito on 2006-06-18
Hello Friends...

I do use a Tungsten E2. 
For a long time I have been using Ubuntu 5.10 with hand made compiled new pilot-link 0.12.4 and updated jpilot.
It worked perfect for several months.

Yesterday I moved form 5.10 to 6.06 and the Pilot-Link and jpilot stopped to work.

I was able to get "dlpsh" to run three times but that is all.

Is there any body who was able to sychronize to Palms after upgrade to Ubuntu 6.06 ?


/piotr

---

### Post by Paul Chang on 2006-06-21
I got my old HandSpring Visor work in Dapper. This is what I did:

(1) Install Jpilot and pilot-link. They are in the repository.
(2) Creat a USB node in /dev/, and change the permission:
        > sudo mknod /dev/ttyUSB1 c 188 1
        > sudo chmod 666 /dev/ttyUSB1
(3) Creat a link "pilot":
        > sudo ln -s /dev/ttyUSB1 /dev/pilot
(4) Load module "visor"
        > modprobe visor
(5) Start Jpilot, and click the syncronize button, I am prompted to press the HotSyc button of the HandSpring
(6) Press the HotSync button.

---

### Post by pito on 2006-06-28
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds. 
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by matthew on 2006-06-28
Pito: that's encouraging news. I don't use my Palm much anymore anyway, but when the kernel is updated I'll certainly be testing it.

---

### Post by jjcv on 2006-06-28
[QUOTE=matthew]Pito: that's encouraging news. I don't use my Palm much anymore anyway, but when the kernel is updated I'll certainly be testing it.[/QUOTE]

What is the process for kernel upgrades within Drapper?   Can we expect one to fix problems like this....?

Thanks

---

### Post by matthew on 2006-06-29
[quote=jjcv]What is the process for kernel upgrades within Drapper?   Can we expect one to fix problems like this....?

Thanks[/quote]Usually an Ubuntu distro only receives security updates for kernels, not new kernel editions, so it is possible that the 2.6.17 kernel won't make it in Dapper, but if there are problems like this and the devs can't find another way to fix it I think they might make an exception.

When kernel updates are available the Update Manager may tell you, just like with security updates. In any case, you can always look in Synaptic under linux-image...

---

### Post by fandelau on 2006-08-06
Mathew:
I recently installed Dapper, and got it to the point where it does everthing I need... except for the palm sync...
I don't see this option under system -> preferences...

> **matthew said:**
> 

3 - Go to System->Preferences->Palm OS Devices



I tried reinstallin the gnome destop and all the palm packages... yet I still can't see the option you mention... I'm this short from reinstalling everything! What am I doing wrong? Please help!
Thanks in advance!

Ramon.

---

### Post by matthew on 2006-08-07
Ramon, it is possible that you haven't done anything wrong. This guide was written for Ubuntu version 5.10 (Breezy) and so far everyone has had lots of problems with Palm devices and syncing using 6.06 (Dapper). You can try to install the package "gpilotd" and see if that helps you, but even with everything installed I can't get my Palm m130 to sync with my computer at the moment. Some who have posted in this thread and others have said the problem is with a major change that was made in the Linux kernel 2.6.15 that Dapper is using, but that this issue is fixed in 2.6.17 that the next version of Ubuntu will be using. For now, the options are either wait for the next edition of Ubuntu (Edgy, due in October) or learn how to download and compile your own kernel (there are lots of threads about this and also [this page]("http://doc.gwos.org/index.php/Kernel_Compilation")).

---

### Post by megamania on 2006-08-07
> **fandelau said:**
> Mathew:
I recently installed Dapper, and got it to the point where it does everthing I need... except for the palm sync...
I don't see this option under system -> preferences...

I'm not at home now (i.e. no Ubuntu at hand), so I can't check it for you, but there's a "menu editor" (or something like that) that hides/shows some of the menu entries.

Sorry I can't be more specific, but try that before reinstalling.

---

### Post by pito on 2006-08-08
What I did to get it working was to use kernel from u510.
I went to /boot/grub/

modifiedd the menu.lst i a way that it starts to use kernel 2.6.12-10-386

######
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
######

an old kernel for latest u510, reboot the system and then write:
sudo modprobe visor

And then I can use both pilot-xfer and jpilot. The jpilot is precompiled by me in order to be compatible with bigger page size for the newest palms.
but you can use standard version too.

What I did at the end is that I made two menu.lst 

u510_menu.lst and u606_menu.lst to switch between the newest kernel and old kernel.

It works as long and we do not get the kernel fixes

good luck.

Piotr

---

### Post by helfrez on 2006-08-08
What still amazes me is how flawlessly kpilot can sync with Kontact and everythign else under the sun including remote syncml access to my egroupware server. But to this day, GNOME still relies on a broken gpilot that rarely works. I would actually prefer to be using GNOME but gpilot+evo is and always has been a poor hackjob. You would think it wouldnt be so hard, or someone would have come up with a cleaner solution by now. Syncing with my treo 650 is a must, and Kontact+Kpilot works flawlessy and completely. Gpilot+Evo is still a incomplete sync when it works properly because you cant sync all categories and things of that nature.

---

### Post by janbockaert on 2006-08-12
coldsync did the trick for me.you can install it with synaptic or apt-get.

what i did: install coldsync, removed kpilot (just to be sure, kontact and kubuntu desktop also removed - no problem, i'm using evolution)
run evolution in edit choose syncoptions, pressed one or maybe two times the hotsync button on my treo 600, and everything worked as it was supposed to work.

this is another forum post: [http://www.ubuntuforums.org/showthread.php?t=214264](http://www.ubuntuforums.org/showthread.php?t=214264)

good luck

---

### Post by CameronCalver on 2006-08-15
I have set my palm up with the guide but how do i add music / video /photos/files onto my palm not using a memory card


p.s this is urgent

---

### Post by Steve1961 on 2006-09-22
Just bought a Palm T|X and tried syncing with evolution, but the applet just locked up and the hotsync failed.  Reading through this forum there seems to be a number of possible fixes, but this is what worked for me.  First I added the following line to /etc/fstab:

/proc/bus/usb/  /proc/bus/usb/  usbfs    none        0       0

Then I created a file called pilot.rules in /etc/udev/rules.d/ and inserted the following line:

BUS="usb" SYSFS{product}="Palm Handheld*" KERNEL="ttyUSB*" SYMLINK="pilot" MODE="666" KERNEL="ttyUSB*" SYMLINK="pilot"

Finally I edited /usr/share/gnome-pilot/devices.xml and changed this entry:

 <!-- Palm Zire 31 -->
<device vendor_id="0830" product_id="0061" /> 

to this:

<!-- Palm Handheld -->
<device vendor_id="0830" product_id="0061" />

After rebooting hotsync worked perfectly.  Occassionally it fails after the first hotsync but it always seems to work after rebooting.

---

### Post by mommebu on 2006-10-02
After finally managing to let gpilot and the TX have an initial talk exchanging Username and ID, when I retry synchronising I get the following message in gpilotd:
gpilotd-Message: setting PILOTRATE=57600
gpilotd-Message: Cradle Cradle has 0 events
gpilotd-Message: corba: orbed_notify_user, notifications->connect.size = 1, id = colibrì
gpilotd-Message: Client appears to be disconnected...

(gnome-pilot:6884): gpilotd-WARNING **: orbit_daemon_glue.c:1494 Exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0

gpilotd-Message: removing monitor on colibrì for IOR:010000
*** glibc detected *** free(): invalid pointer: 0x080724d8 ***

while the palm hangs in the 2nd step of the sync process (user identification).

Any suggestions?

cheers

---

### Post by firebirdworks on 2006-10-02
humm.. good guide!
Does anyone know anything about pocket pc?  I would live to install Ubuntu on mine, or at least let it hold some of my documents.

---

### Post by High|ander on 2006-10-09
Hello guys!

After alot of work, i finally got my palm tx to sync with gpilot.

I use the network sync with wireless (tried with USB, but i didn't get it to work).

Using Edgy

---

### Post by trbloomer on 2006-10-24
Thought I'd say thank you works like a charm.

In my case I'm using a Clie TG50 on tty/usb1
Gpilot version 2.0.14
Edgy Eft RC
So thanks and yes you can use a TG50 :)

---

### Post by matthew on 2006-10-31
I am pleased to report after an upgrade to Edgy I can sync consistently once again. The only bumps I am experiencing are that 1) Evolution has to be closed when I sync and 2) when I sync two copies of gnome-pilot open. I can live with both. 

On the positive side, now everything syncs, not just my calendar and basic data. I had a hard crash while using Breezy ages ago and lost all the programs I had installed to the Palm back when I used Windows. Apparently they were saved on my computer, but with Breezy and Dapper I was unable to restore them, only my calendar, address book and notepad were restored. However, I didn't delete or change anything Palm related on my /home partition and now that I have Edgy installed I can sync consistently and at the first sync a full restore was done and _everything_ I used to have on that Palm has been restored...programs, everything. I am truly pleased.

---

### Post by ubuntuben on 2006-11-04
I'm also happy to report that I can once again sync my Handspring PDA after upgrading to Edgy on both my PC and Mac! Both machines sync consistently whereas before I couldn't sync at all. Was able to under Breezy, but things were broke under Dapper. Gnome-Pilot works once again. Hats off to the Edgy team! Any chance of the fixes getting incorporated into Dapper since it is LTS?

---

### Post by dangermouse28 on 2006-11-06
Dapper can be fixed by upgrading the kernel to 2.6.17 as this is where the problem lies.

---

### Post by ubunovi on 2006-11-07
Hello specialists!
Thanks to all of you, after many hours and disapointing testings I succeed at last.
How it finaly worked for my config:
"Edgy" + evolution 2.8.1 + USB-Cradle + Palm zire 71
(1) uninstalled all that "k"-stuff (kpilot, kontact, korganizer)
(2) installed "coldsync" und evolution (with "gpilot"-stuff)
(3) killall to "k"-stuff-daemons
(4) killall to "gpilot"-stuff und all evolution processes
(5) search palm with (g) palmos-device and config all contibutes just fine for me

Until now, everything works very well.
Hope this helps someone else too!

---

### Post by Keith_Beef on 2006-11-19
Thanks for a great thread.

A friend recently gave me, very generously, a Palm Tungsten T5 that was "surplus to requirements" (i.e., he has three more recent Palms).

He reset it back to the "as from factory" state before giving it to me.

I am using Ubuntu 6.06 LTS, with all updates installed.
2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686 GNU/Linux

I built the computer myself, around an Asus A7N8X-E deluxe mainboard.

I plugged in the palm, and looked with USBView.

Left hand panel shows:
```

|-EHCI Host Controller
|-OHCI Host Controller
|-OHCI Host Controller
  |-palmOne Handheld
  |-Back-UPS ES350 FW: ..snip..
```

When I click on the entry in the tree for the Palm, the right hand panel shows:

```
palmOne Handheld
Manufacturer: palmOne, Inc.
Serial Number: 504E35424D32513556324B46
Speed: 12Mb/s (full)
USB Version:  1.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 16
Number of Configurations: 1
Vendor Id: 0830
Product Id: 0061
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 1
	Attributes: c0
	MaxPower Needed:   2mA

	Interface Number: 0
		Name: visor
		Alternate Number: 0
		Class: ff(vend.) 
		Sub Class: 0
		Protocol: 0
		Number of Endpoints: 4

			Endpoint Address: 81
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms

			Endpoint Address: 02
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms

			Endpoint Address: 86
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms

			Endpoint Address: 07
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 64
			Interval: 0ms
```

Promising, so far.

I set the Palm to "Drive Mode" to try using it as a simple external hard disc.

This popped up very briefly a drive icon on the desktop, marked "INTERNAL", but his disappeared quickly. Dmesg reported:
```
[17180300.428000] end_request: I/O error, dev sdb, sector 801
[17180300.428000] Buffer I/O error on device sdb1, logical block 558
[17180300.428000] lost page write due to I/O error on sdb1
```

Then, a second drive icon appeared, representing the SD card that was in the slot. This card came from my Canon digital camera.

At the same time as the drive icon appearing, the tool for importing photos appeared. This behaved exactly as it would if I had connected my camera.

I unmounted the volume, and put the Palm back into normal mode.

I didn't have an entry in the System -> Preferences menu for Palm devices, so I started up the GnomePilot applet, and went through the set-up wizard, describing the connection as:
> Cradle
/dev/ttyUSB0
57600
USB

No joy; the Palm announced that it could not sync with the computer, and gPilot stayed stuck.

Now maybe there's something in the output from USBView that would have told me that it wouldn't work, but I didn't see it.

I went back, and changed the connection to:
> Cradle
/dev/ttyUSB1
57600
USB

Oh, Joy.

Now, GPilot finds the Palm, who chirps, and shows the message "Hotsync operation complete".

It would be nice to find a way of synchronising my Evolution diary with the Palm, and a way of putting some images, documents and music files on there, too.

I enabled diary synchronisation in Evolution and tried to start the process, but it failed. Now, the icon for the GPilot applet has disappeared from the panel.

When I add it, is no longer works...

Looks like I broke something.

I had to kill off a load of gpilot control processes.

Well, when I keep an eye on /var/log/messages, I see that although the Palm showed up on /dev/ttyUSB1 at first, it is now showing up on 
/dev/ttyUSB2 and /dev/ttyUSB3. Setting the device to /dev/ttyUSB2 doesn't work, but /dev/ttyUSB3 seems to work at first.

I get a cheerful chirp, and a message that synchronisation is starting, then Palm shows that it is identifying the user, but finally fails with the message "The connection between the device and your desktop was lost".

If this is an authentication failure, maybe I need to change some Pilot settings to match my UID on the computer?

So, I tried telling GPilot to get the user name and ID from the Palm device. In /var/log/messages, I see:
```
Nov 19 13:47:10 localhost kernel: [17196696.116000] usb 1-1: new full speed USB device using ohci_hcd and address 57
Nov 19 13:47:10 localhost kernel: [17196696.344000] visor 1-1:1.0: Handspring Visor / Palm OS converter detected
Nov 19 13:47:10 localhost kernel: [17196696.344000] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
Nov 19 13:47:10 localhost kernel: [17196696.344000] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
```
so I try going through /dev/ttyUSB1.

Once again, the gnome-pilot progress window freezes, the Palm eventually displays its message "The connection between the device and your desktop was lost".

I read in [another post]("http://ubuntuforums.org/showpost.php?p=1721905&postcount=77") in this thread, > that [it can be] fixed by upgrading the kernel to 2.6.17 as this is where the problem lies.

Well, just to try a different way of doing things, I started up kpilot to get the user and ID from the Palm.

This connected, detected that the device was on /dev/ttyUSB1 and got a username and ID. The palm also announced that a HotSync operation had completed.

So the problem is neither hardware, nor kernel related. It seems to be either the GPilot programs, or a library problem.

At least I know that synchronization should be possible. KPilot says it can synchronize the calendar with Evolution, but so far, it doesn't work...

Grr!!! I just tried a couple more times, and now KPilot just bombs out while detecting the device!

Beef.

---

### Post by compwiz18 on 2006-11-29
Worked great, thanks.  BTW, I have a Sony Clie on Edgy.  /dev/pilot worked about half the time, the other half the Palm froze and I had to soft reset it (very annoying)

---

### Post by sockrebel on 2007-01-31
My treo650 does a soft reset during the "Get from Pilot" step as soon as I press the sync button on the cradle/palm.  I've tried to sync following several different how-tos, but it does a soft reset everytime.  It syncs fine on Windows.  Anybody seen this problem, or have any idea why it happens?

---

### Post by eamann on 2007-02-13
Hi!

Like so many others, I have spent hours and hours trying to get my Palm Zire 71 to sync (in my case using J-Pilot). In vain. Frustration.

Then yesterday I read on this site that opening J-Pilot as root could solve the problem. I tried it and it worked! I could not believe my eyes! I thought it was a fluke and tried a second time and a second time it worked!

I hope that this will help some of you solve your problems!

Many thanks to the author of this how-to and to all the others who have contributed!

Best wishes,

Eamann O Ruairc

---

### Post by MoebusNet on 2007-05-01
Maybe this will help someone:

I got my Treo 650 to synchronize with J-Pilot by entering **usb:** in the serial port window.

Because it took me so long to figure it out, even following a forum suggestion I'll repeat it here in detail.

Obtain J-Pilot from Synaptic package manager if it isn't installed.

Open J-Pilot, then from the menu File => Preferences => Settings => Serial Port (/dev/tty/S0, /dev/pilot)

To the right of "Serial Port (/dev/tty/S0, /dev/pilot)" there is a blank window. Enter "usb:" without the quotes in that window.

It may sound dumb, but it took me several tries over a couple of hours to notice the colon sign (**:**) after usb. Even then it was only trying and failing with all of the permutations from "/dev" and rereading the post for a fifth time.

After that you can click on J-Pilot's synchronize button, then the Hotsynch button on the Treo.

I'm sorry, but I lost track of the writer whose post I was following to give credit. Thank you, none the less!

---

### Post by eamann on 2007-05-12
Hi!

Thank you very much for posting that information! It has enabled me to sync my new Palm TX on Ubuntu (Feisty) using J-Pilot, which I could not do before.

Eamann

---

### Post by MondoTofu on 2007-05-17
Sometimes I get the feeling that I'm using stone tools (palm IIIxe via serial port), but I was able to get gpilot to work with it after finding that  /dev/ttyS0  was the correct port to use.

The wizard helped identify the User Name already stored on the pilot, but it seemed stuck and communication was lost.

Editing the /etc/fstab to insert  /proc/bus/usb was a mistake... after clicking on the desktop applet, I got a "flash mob" of windows popping up to show me "Pilot Settings".

After removing that and rebooting, I was able to sync with the computer.

By the way, I've updated Dapper to Linux kernel 2.6.15-27-386

---

### Post by ByteDoc on 2007-05-18
Quick share of my experiences:
Running Feisty Fawn, connecting with a Palm Tungsten E2 (my wife's latest gadget).

After a couple of nerve straining hours (following instructions on several of the links in this thread) I gave up for the night. I did "modprobe visor", added "visor" to /etc/modules (without restarting though, I thought I loaded it correct manuall), but no success on the first day. I also installed pilot-link sometime during the evening.

I don't know why it didn't work, guess there was a minor error that occured after countless unsuccessful and cancelled tries, because even on starting HotSync the device did not show up in /var/log/messages reliably.

Today I gave it another try, knowing that visor was loaded on system start, and I tried to keep all my tries "clean".
usb: did not work, neither did /dev/ttyUSB0
But with /dev/ttyUSB1 I managed to get the palm recognized, and backups/syncs work now!

Next challenge now is to get the sync process to read more than 1 calendar from evolution and include it in the sync, but for now I'm happy I got a connection and can sync at least basic stuff.

Max

---

### Post by niceguy123 on 2007-09-17
Moe,

Thank you so much. I have been at this for hours (embarrassed to say days). Read so many forums and installed a few applications and tried all kinds of configurations usb1, usb2 etc. and thanks to you I just ran USB: and the connection was made. 

> **MoebusNet said:**
> Maybe this will help someone:

I got my Treo 650 to synchronize with J-Pilot by entering **usb:** in the serial port window.

Because it took me so long to figure it out, even following a forum suggestion I'll repeat it here in detail.

Obtain J-Pilot from Synaptic package manager if it isn't installed.

Open J-Pilot, then from the menu File => Preferences => Settings => Serial Port (/dev/tty/S0, /dev/pilot)

To the right of "Serial Port (/dev/tty/S0, /dev/pilot)" there is a blank window. Enter "usb:" without the quotes in that window.

It may sound dumb, but it took me several tries over a couple of hours to notice the colon sign (**:**) after usb. Even then it was only trying and failing with all of the permutations from "/dev" and rereading the post for a fifth time.

After that you can click on J-Pilot's synchronize button, then the Hotsynch button on the Treo.

I'm sorry, but I lost track of the writer whose post I was following to give credit. Thank you, none the less!

---

### Post by superdif on 2007-09-22
In my case I got my Palm M125 to sync with Gpilot and Evolution (I have still to test the installation of new programs since I don't have the need yet).

The only (marginal) issue I'm looking to silve is to get some sort of sync progress bar. So far I have to look to my Palm screen to see if it is finished.

Any idea?

Thank in advance.

---

### Post by vtommasi on 2007-10-29
I'm trying to synchronize a Treo 650 with JPilot. Everything went all right, exceptthat JPilot truncates the memos. I've tryed memo32, but it not seems to be the answer. Have any ideas about this? It's there any way to keep memos ok in JPilot?

---

### Post by cokebear on 2007-11-19
Recently, I rewsurected my old Athlon 700 machine with Ubuntu 7.10. Woohoo! Works charmingly well, much better than the "other" OS. However, I've got a Visor Prism and can't get it working. I tried going the following:
1. press Hotsync button on the USB cradle with Visor Prism on it
2. launch PalmOS Devices under System/Preferences, leads me to gnome-pilot wizard
3.Configured the Cradle such that:
  - Type: USB
  - Timeout: 2
  - device: /dev/pilot
  - speed: 57600

Nothing worked. Alternatively, I tried using /dev/ttyUSB1 and /dev/ttyUSB0 as mentioned in previous posts but to no avail. What can be done??

---

### Post by ectospasm on 2008-07-20
Thanks, MoebusNet!  This did the trick for me.

> **MoebusNet said:**
> Maybe this will help someone:

I got my Treo 650 to synchronize with J-Pilot by entering **usb:** in the serial port window.

Because it took me so long to figure it out, even following a forum suggestion I'll repeat it here in detail.

Obtain J-Pilot from Synaptic package manager if it isn't installed.

Open J-Pilot, then from the menu File => Preferences => Settings => Serial Port (/dev/tty/S0, /dev/pilot)

To the right of "Serial Port (/dev/tty/S0, /dev/pilot)" there is a blank window. Enter "usb:" without the quotes in that window.

It may sound dumb, but it took me several tries over a couple of hours to notice the colon sign (**:**) after usb. Even then it was only trying and failing with all of the permutations from "/dev" and rereading the post for a fifth time.

After that you can click on J-Pilot's synchronize button, then the Hotsynch button on the Treo.

I'm sorry, but I lost track of the writer whose post I was following to give credit. Thank you, none the less!

---

### Post by halitech on 2008-08-23
I just picked up an old Palm M105 and the instructions worked for me. I had to select serial port on the set up as the cradle was a serial connection instead of usb. The laptop does have IR but doesn't seem to connect on that (might be an issue with the laptop). I'm using 8.04 on a Compaq Armada laptop with 256 meg of ram and it synced with Evolution no problem.

I'm also using Xubuntu so went to Applications - Settings - PalmOS Devices and everything worked the first try :)

---

### Post by geoffkaniuk on 2008-09-04
Hi,

Following my recent upgrade to 8.04, I am completely stuck trying to get my Palm Pilot IIIe working.

The HotSync icon on the panel had frozen after the upgrade, so I re-installed gnome-pilot from the update manager.

When I click System>Preferences>PalmOS Devices, the applet seems to start then just times out after a minute.

I have tried running gpilotd-control-applet from the terminal.  It lists the following messages but does nothing further.

> geoff@geoff-desktop:~$ gpilotd-control-applet
** Message: Pilot name -> MyPDA
** Message: Pilot id   -> 1000
** Message: Pilot username -> Geoff Kaniuk
** Message: Pilot creation/rom = 912701023/51458048
** Message: Cradle Type -> Serial
** Message: cradle device name -> Cradle
** Message: cradle device name -> /dev/ttyS0
** Message: Pilot Speed  -> 57600
** Message: Timeout -> 2
gpilotd-Message: Activating object OAFIID:GNOME_Pilot_Daemon
** Message: pilot = MyPDA

geoff@geoff-desktop:~$ 


I would much appreciate any help in getting this working with Hardy Heron!

---

### Post by geoffkaniuk on 2008-09-05
After booting up this morning the problem seems to have cured itself.

The hotsync icon is back on the panel.

Hotsync works!

---

### Post by ArgentSilver on 2008-09-14
Since I found this info very hard to find, I'll post how I got my Palm TX with USB cable to sync under Kubuntu Hardy.

No changes to system files were necessary, though I thrashed around for a while doing that! Basically you have to tell your sync software to find your Palm device at "usb:" (without the quotes).

So for command line mavens, pilot-link works well, but you have to add this option --port=usb: to your pilot-xfer command. For example, "pilot-xfer --port=usb: -i filename.pdb" for an install command. Make sure you push the hotsync button on the Palm before issuing the command!

Under Kpilot, you have to go under its Settings -> Configure Kpilot then General Device settings and tell it the Pilot device is at usb:

Good luck, folks!

---

### Post by eudemus on 2008-09-15
I have succeeded in syncing my Palm TX on 2 machines (one running Kubuntu Hardy + Evolution and Gnome-pilot; the other running Fedora 9 (gnome, evolution, etc.)).

The combination seems to be:
Evolution
Gnome-Pilot
evolution plugins for gnome-pilot
visor (module)
usb:

I don't really know why that combination works. It doesn't work if I try to use /dev/pilot or /dev/tty*.... etc..

The most perpelxing thing is why, even though I am using usb: (which, I thought, was invoking libusb instead of visor) it doesn't work unless I have the visor module loaded. Accordingly, when I sync, I get the following message:
"Failed to connect using device cradle on port usb: check your configuration as you requested new-style libusb usb: syncing but have the old-style visor kernel module loaded."

But, even though it gives this message, the sync is perfectly successful. I've used the command line gpilot-install-file to add software to the device.

Perhaps my settings could be neatened up somehow. But I'm currently getting the syncing I need (which is more than I EVER EVER did with a Windows Mobile device and Synce, sadly).

If anyone wants to enlighten me as to why I'm getting the error message, I'd be happy to hear it. But it's hardly causing me sleepless nights that I have to click through an error message a couple of times a day (after the thing has successfully sync'ed).

Best of luck, y'all! Eudemus

---

### Post by keiffee30 on 2008-10-22
I have had a go at this on 7.10 with a Palm m515 using USB, and worked 1st time with palmOS Devices. So i tried it with 8.04 and it still works. 

**"Ubuntu is getting harder and harder to find faults with it"**

I have got 1 thing well 2 things i can not get to work yet "now here is a challenge for you ubuntu". 

1.) I can not install any new 'apps' on to the palm m515 as i can not find out how to do it? I have got the prc files etc etc just can not install them. 

Also ..........

2.) I would like to get my emails onto the palm (Evolution 2.12.1), but can not find where to set this up. It looks like its pointing to 'sendmail' would that be the only way to send emails from my Palm?.

As im looking for perfection (well everything working as it could) here any points would be lovely

---

### Post by tdmoore on 2008-11-05
I have spent the past many hours (now days) reading over the 10 + pages going back several years...and trying everything.
Looking for help.  Not an IT guy, fairly new to Ubuntu

Summary:
Running Intrepid Ibex 8.10.
My wife's Palm is a Zire 31.
Setup JPilot and followed the assistant, hooked into USB hub and hit the hot sync button and voila, it sync'd perfectly.  Honestly never looked at any of the settings.

Then we tried Evolution.  Nothing...tried everything on many of these posts. So, thought lets go back to JPilot and try again there.  Now nothing there.

We run dual boot with Windows.  Decided to try and go there...click and go.  No issues., it worked perfectly.

I am asking for assistance here as I have now tried so many things I am lost.  I see posts thanking others but trying to follow the instructions they used through the threads has lost me I am afraid.

Ultimate goal is to have the Zire sync with Evolution (my wife's preference over JPilot) and to move her from Windows to Ubuntu.  It's the last step in the migration, however it's the big one.

Thank you community...you have come through for me in the past, I hope on this as well.

---

### Post by 7morpheus7 on 2009-02-16
Thank you for the info, I used the easy palm device setup option and it worked for my palm t|x. I was not able to get it to work in win xp 64 bit, no drivers available. But it works just fine now. 2 thumbs up!

Sorry, I need to specify that the options that Matthew provided in the first post of this thread are what helped me out.
Big Thanks to you, Matthew!!

---

### Post by matthew on 2009-02-16
You are very welcome.

---

### Post by Ichido on 2009-02-25
> **MoebusNet said:**
> Maybe this will help someone:

I got my Treo 650 to synchronize with J-Pilot by entering **usb:** in the serial port window.

Because it took me so long to figure it out, even following a forum suggestion I'll repeat it here in detail.

Obtain J-Pilot from Synaptic package manager if it isn't installed.

Open J-Pilot, then from the menu File => Preferences => Settings => Serial Port (/dev/tty/S0, /dev/pilot)

To the right of "Serial Port (/dev/tty/S0, /dev/pilot)" there is a blank window. Enter "usb:" without the quotes in that window.

It may sound dumb, but it took me several tries over a couple of hours to notice the colon sign (**:**) after usb. Even then it was only trying and failing with all of the permutations from "/dev" and rereading the post for a fifth time.

After that you can click on J-Pilot's synchronize button, then the Hotsynch button on the Treo.

I'm sorry, but I lost track of the writer whose post I was following to give credit. Thank you, none the less!



Thank You Moebusnet):P

Your post has saved me many hours of Futile efforts!
Got my Palm Zire 72 Sync't with my Laptop and my Zire 31 Sync't with my Desktop:p

I have Copied your post into a *.odt file for future reference.

---

### Post by SteinbergerNate on 2009-03-30
Hello, all

I'm desparate. No matter what I try, I cannot get my Treo 650 to sync with anything under 8.10. I've tried just about everything I've seen. 

One thing to note, when I press the hotsync button, it doesn't create /dev/ttyUSB0 or /dev/ttyUSB1 like I'm used to it doing in the past.

I REALLY want this to work with Evolution but at the moment I can't even get it working with Jpilot.

---

### Post by megamania on 2009-03-30
> **SteinbergerNate said:**
> Hello, all
I'm desparate. No matter what I try, I cannot get my Treo 650 to sync with anything under 8.10. I've tried just about everything I've seen. 

One thing to note, when I press the hotsync button, it doesn't create /dev/ttyUSB0 or /dev/ttyUSB1 like I'm used to it doing in the past.

I REALLY want this to work with Evolution but at the moment I can't even get it working with Jpilot.
While with wireless it was easy, it took me a while to get my TX to work with Evolution via USB. This is what worked for me:

from terminal:
sudo modprobe visor

In gnomepilot settings (from within Evolution), in the devices tab create:
Name: any name here
Type: USB 
Timeout: 2 (default, left it that way)
Device: /dev/ttyUSB1 
Speed: 115200 - didn’t seem to want to work with the lower default setting 

Click the HotSync icon or button on the Palm
Be sure there's just one "gpilotd" process running (check with top or ps -A, and kill any gpilotd process)

---

### Post by SteinbergerNate on 2009-03-30
Still not getting /dev/ttyUSB1 or 0. Any other ideas?

---

### Post by SteinbergerNate on 2009-03-30
Ok, this is really strange. I shut my computer down before I went to work. I just came back home and fired it up. Without doing anything else, I hit the button and did ls /dev/ttyUSB* and got both devices showing up. 

So, I fired up Evolution to get it set up and now the devices won't show up any more. Even after another restart I can't get /dev/ttyUSB*

---

### Post by SteinbergerNate on 2009-03-30
Ok, one more weird bit of info. I found that if the palm is on when I put it on the cradle, everything comes up as it should. I got all the initial stuff taken care of and in fact I can get it to appear to synchronize.

However, it's not really synchronizing with Evolution even though the conduits are set up properly. Really frustrating.

---

### Post by SteinbergerNate on 2009-03-31
Solved. I set it up to do a one time action of copying to the pda and it did. Now everything syncs fine. Thanks for your patience!

---

### Post by roystreet on 2009-03-31
> **megamania said:**
> While with wireless it was easy, it took me a while to get my TX to work with Evolution via USB. This is what worked for me:

from terminal:
sudo modprobe visor

In gnomepilot settings (from within Evolution), in the devices tab create:
Name: any name here
Type: USB 
Timeout: 2 (default, left it that way)
Device: /dev/ttyUSB1 
Speed: 115200 - didn&#8217;t seem to want to work with the lower default setting 

Click the HotSync icon or button on the Palm
Be sure there's just one "gpilotd" process running (check with top or ps -A, and kill any gpilotd process)

Hey megamania (or anyone else for that matter),
    I just realized the beauty of wirelessly synchronizing my palm wireless with windows. I would love to do that with ubuntu, but I've never been able to do that. Synching with my palm is one of the major reasons I still use windows. How did you make it sync wirelessly? I use a palm TX right now & a HP laptop. 

I still can't get my palm to sync via the cradle either, it acts like it will, but then fails...It's weird it sync'd once to J-Pilot & then after that it fails. But I'd rather wireless sync now anyway.

Any ideas...Anyone?

Thanks!
~roystreet

---

### Post by megamania on 2009-03-31
> **roystreet said:**
> Hey megamania (or anyone else for that matter)
that should be very simple (or much simpler than via usb).

With Jpilot, Preferences->Settings:
Serial port = other  -  name= net:
Serial rate= 115200

If the palm is already configured for net syncing, just press the sync button on jpilot and then on the palm.

The same process applies to all the other palm-syncing programs.

That should be it!

edit: with Jpilot, since you're using a TX remember to select "Use Memos Database" and "Use contact database" in preferences (address and memos tabs)

---

### Post by _rH on 2009-07-23
> **megamania said:**
> While with wireless it was easy, it took me a while to get my TX to work with Evolution via USB. This is what worked for me:

from terminal:
sudo modprobe visor

In gnomepilot settings (from within Evolution), in the devices tab create:
Name: any name here
Type: USB 
Timeout: 2 (default, left it that way)
Device: /dev/ttyUSB1 
Speed: 115200 - didn’t seem to want to work with the lower default setting 

Click the HotSync icon or button on the Palm
Be sure there's just one "gpilotd" process running (check with top or ps -A, and kill any gpilotd process)

Thanks, worked a treat. 
Followed above, however, did not activate 'HotSync', and instead flicked 'Forward' until setup of PDA was complete. 
Next, I went:
System --> Prefs --> PalmOS Devices --> select PDA and 'Edit' --> For PDA Identification  'Get from PDA' --> Setup 'Conduits' --> Evolution and HotSync. Gameon!

---

### Post by tanngo on 2009-08-30
> **naomi said:**
> Many thanks for this helpful tutorial! :)

I have a Tungsten T5 and the /dev/pilot didn't work for me either. However /dev/ttyUSB1 worked.

Btw any idea on how to synchronise with Avantgo? I read the following thread
[http://www.ubuntuforums.org/showthread.php?t=53752]("http://www.ubuntuforums.org/showthread.php?t=53752")
but I was wondering if there is a better/easier solution having the new Ubuntu release installed.

hello:(
i have the palm tungsten has no station to set on just recharges directly.  love this thing and feel lost with oiut it. any suggestions/

---

### Post by eeeek on 2009-09-09
Hey, many thanks to those recently in this post. I got my Palm Tungsten E to synch with Evolution (contacts, etc). That will be an excellent resource. (I admit, I'm behind the times when it comes to handhelds)

However, I still can't get documents transfered from my Palm (Documents to Go) to Ubuntu (8.04). I have a list queued up to transfer from Ubuntu to my Palm and can't get that initiated, either. 

Ideas?

---

### Post by megamania on 2009-09-10
> **eeeek said:**
> However, I still can't get documents transfered from my Palm (Documents to Go) to Ubuntu (8.04). I have a list queued up to transfer from Ubuntu to my Palm and can't get that initiated, either. 

Ideas?
Use an SD card reader, and write/read the files directly to/from the card. It's so easy that it doesn't pay to bother looking for other solutions, in my opinion.

---

### Post by nferrario on 2009-09-17
I tried a lot of these solutions and can't get my palm to sync.  I'm using a Fossil Abacus running PalmOS 4, and I've already tried this:

```
Instructions for Abacus/Fossil Palm Watch
Get the necessary information especially the vendor and product ID from Linux.
Perform a Hotsync on the Palm Watch and issue a lsusb command during the Hotsync.
# lsusb -v
Bus 002 Device 002: ID 0e67:0002
Device Descriptor:
  bLength                18
  bDescriptorType        1
  bcdUSB              1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass        0
  bDeviceProtocol        0
  bMaxPacketSize0        8
  idVendor          0x0e67
  idProduct          0x0002
  bcdDevice            0.01
  iManufacturer          1 Fossil, Inc.
  iProduct                2 Wrist PDA
  iSerial                0
Create /etc/udev/rules.d/10-visor.rules the following information:
    BUS="usb", SYSFS{product}="Wrist PDA*", KERNEL="ttyUSB*", SYMLINK="pilot"
To make the Hotsync work for the Palm Watch, issue the following command.
# /sbin/modprobe visor vendor=0xe67 product=0x2
Add the following to /etc/rc.d/rc.local so it will initialize visor module with
the correct vendor and product ID for the Palm Watch after rebooting:
    /sbin/modprobe visor vendor=0xe67 product=0x2
```

adapted from:
[http://www.clasohm.com/blog/one-entry?entry_id=12096](http://www.clasohm.com/blog/one-entry?entry_id=12096)

but basically I can't find how the device is listed in /dev/, let alone get Jpilot OR gnome-pilot to work.  I also get the error "Failed sending request to gpilotd" when I use gnome-pilot setup.

Can anyone help me with this?  They just dropped support for palm in Snow Leopard and this is the only way I can use this device.

---

### Post by nferrario on 2009-09-18
OK got the ttyUSB0 and 1 working, but still getting the "Failed sending request to gpilotd" error...  Help?

---

### Post by jelabarre on 2009-10-30
I have the impression something *major* got reworked/re-engineered in the USB support code, so now the USB devices aren't showing up in the manner in which they used to.  So therefore "/dev/ttyUSB0" will never be a valid location in 9/10/Karmic, and any versions thereafter.  Am I right?
 
Thus far I have not been able to find an answer to this.

---

### Post by LargePiece on 2009-11-23
If anyone's having trouble with visor restarting/crashing your palm device, there's a bug report here:
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/421673](https://bugs.launchpad.net/ubuntu/+s...er/+bug/421673)

I ended up removing the modemmanager package and after a year of plugging away at this annoying problem, I can finally sync my lifedrive! Ace.
LargePiece is online now Report Post   	Edit/Delete Message

---

### Post by jar8422 on 2009-12-03
> **megamania said:**
> Use an SD card reader, and write/read the files directly to/from the card. It's so easy that it doesn't pay to bother looking for other solutions, in my opinion.

I've found that, after finding that I can sync my Palm TX with Ubuntu using J-Pilot, that a program called '[Card Reader]("http://www.mobile-stream.com/cardreader.html")' works perfectly with Ubuntu. It does what it says, turns the PDA into a SD card reader. Though isn't free, costs $11.95:-|, it can be found [here]("http://www.mobile-stream.com/cardreader.html").

Thought I'd let you all know of this App, Thanks [[COLOR=#980101]**matthew**[/COLOR]]("http://ubuntuforums.org/member.php?u=17635") for the info.
jar8422

---

### Post by NUboon2Age on 2010-06-22
After much experimenting I got it working:

Lucid, Palm 700p, USB cable/cradle

1) **Purged** (aka Synaptic "completely remove") **modemmanager** package (because otherwise I was getting continous Palm resets (see Bug #421673).
2) **Removed visor from /etc/module file** (not there by default, I'd added when experimenting earlier) 
Note the visor module conflicts with libusb  which appears to have been available from Jaunty onward.

My settings in **gnome-pilot**:

- Devices tab:
  - Name: Cable, you may choose what you like.
  - **Type: USB**
  - Timeout: 2 
  - **Device: usb: **
  - Speed: 115200 (not default -- don't know if this is vital, but it worked for me)

---

