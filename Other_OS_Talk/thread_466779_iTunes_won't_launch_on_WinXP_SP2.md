---
title: "iTunes won't launch on WinXP SP2"
date: 2007-06-07
forum: Other OS Talk
---

### Post by voided3 on 2007-06-07
Hello, I just did a fresh install of the latest iTunes (7.2) and when I go to launch it I get the classic "iTunes has encountered a problem and needs to close" dilogue. I have all startup items disabled as per msconfig except for my AVG Free A/V, Zone Alarm firewall, and my ATI graphics driver, and I did restart my system after installation. Quicktime works, but for some reason its icons on the start menu aren't there, just the generic windows shortcut icon. Any ideas? Thanks!

---

### Post by brim4brim on 2007-06-08
qttask is the process that has to run in order for Quicktime to be in the tray.  You can enabled it in Quicktime settings (which is separte to Quicktime options in the player).

Try repairing iTunes from Add/Remove Control Panel if it is an option.  Otherwise just reinstall it.  Its not worth the hassle.  iTunes installs crap all over the place so its hard to work out what the problem is if it gives no errors what so ever.

I don't know if iTunes produces logs but might want to check its directory for logs.

---

### Post by voided3 on 2007-06-08
[IMG]http://i6.photobucket.com/albums/y247/voided3/itunesqterror.png[/IMG]

That about summarizes my situation as a whole (haha). I have reinstalled it about three times as well and have tried the repair option too. This really bugs me. My other computer is doing the same thing with SiS Sandra for some reason too, but itunes works on that and SiS Sandra works on this just fine and they are practically identical computers setup with the same windows disk! (both Socket A Athlons running at 1.4ghz w/ a KT133A chip). Just a further reminder of why I keep linux on all of my computers.... Any further suggestions?

---

### Post by voided3 on 2007-06-13
I think this computer hates Apple software; the new Safari 3 beta does the same thing. GAH! I was hoping to wait to reformat until Gutsy Gibbon comes out, but I guess I may be doing that sooner than I thought... unless there are any further ideas of course.

---

### Post by peterbrewer on 2007-06-13
Obligatory:
Get a mac.

Sorry, couldn't resist.  Your best bet is to just do a fresh reinstall of itunes.  You could try rolling your pc back in case an update caused the problem.

---

### Post by voided3 on 2007-06-13
Haha, I have a Macbook Pro fortunately as well in addition to my pile of Linux boxes. Good point though on rolling it back, it very well could have been an update, but shouldn't those fix problems instead of making more... oh wait, it's windows. I'll try that and see if it works out, and if so, I think I might just ignore updates from now on; I really just use windows for a few games or for formatting drives in NTFS if I ever need to; I actually have VMware server on that same comp on Xubuntu and I have both a Win98 and WinXP virtual machines (Win98 for super old games and WinXP for iTunes (actually works), even though my iPod is in HFS+... so basically just for the heck of it). I even have plenty of RAM to run both OSes simultaneously (especially since I use Xubuntu); 1.25GB :-) Thanks for the help and any other insights are welcome!

---

### Post by johnny4north on 2007-06-13
have you tryed songbird?  [http://www.songbirdnest.com/](http://www.songbirdnest.com/)  i believe that it installs on linux and windows.

---

### Post by voided3 on 2007-06-13
Wow, Songbird looks quite nice. I can't wait for the full release (but that doesn't stop me from using the beta :-D ) Looks like I have a good alternative.

---

### Post by voided3 on 2007-06-13
Alright, I got iTunes to work. I had installed Apple Software update while installing itunes+quicktime so i uninstalled itunes with add/remove programs, then ran software update and installed it with that. Weird stuff, but the moral of the story is I WON! Oh, and just in time for me to not use it since Songbird is just as cool (haha). Thanks!

---

### Post by johnny4north on 2007-06-14
note- check out the cool extentions for songbird.:)

---

### Post by voided3 on 2007-06-14
Yeah I saw the extensions; good stuff. Is there a graphic equalizer availablefor either Songbird or the ALSA mixer? I like to fine tune my media players for what speakers i'm using, whether it's my stereo or unpowered walkman speakers. Thanks!

---

### Post by johnny4north on 2007-06-14
i m not sure about songbird, but alsa mixer should do the trick.  i m on my puppy linux distro now. sorry.:(

---

### Post by thully on 2007-06-15
I had the same problem on an older PC - it's your processor.  Evidently the older Athlons don't support SSE extensions, and the new iTunes (7.2) uses them.  As a result, trying to run it on one of these systems causes a crash on load.  At this point you probably should just go back to iTunes 7.1 (google for a link to download it from) and hope Apple straightens this out in the next release.

---

### Post by voided3 on 2007-06-15
Ah yes, it is an Athlon t-bird and doesn't support SSE, but as I previously mentioned I got it to work for some reason. I did have that problem when trying out the Quake 4 demo though; it requires SSE extensions. I tried putting a mobile Athlon XP 1800+ I have on the board (IWILL KK-266R) but it refused to post after resetting CMOS and trying both FSB jumper settings, so I just left in the other CPU. I hope to eventually get a newer mobo in this comp, but honestly with the way it's setup now with a radeon x1300 pro, 1.25GB of ram, 585 watt PSU, and a 160GB drive, it performs quite well. I am aware of the fact that it is six year old technology, though. I just wish the original socket A Athlons supported more extensions; I am using Xubuntu right now on a 800mhz Pentium 3 computer I put together and that has more extensions (including SSE)! I could probably get a different mobo with something in the range of a 2500+ to 3200+ Athlon XP for pretty cheap on ebay I bet, but this computer has cost me a grand total of $100 through good deals and freebies, so I think i'll enjoy it for what it is as long as it continues to run. It basically has a new (year or less old) everything except the mobo and CPU so longevity shouldn't be a problem. And I have a Macbook Pro :-D (though being a 2.16ghz Core Duo model, I suppose that has been one upped by two generations of C2D models.... I just can't win can I?) Thanks thully and i'll keep on the lookout for itunes updates!

---

### Post by thully on 2007-06-15
I have a MacBook - that's my primary system and has been for a while (the old Athlon I mentioned was just retired for good). 

Are you using Ubuntu at all on the MacBook Pro? If you don't have Ubuntu on the MBP at all, try w/ VMware Fusion beta 4 - it runs quite well except for no 3d (you do want at least 1GB ram, and 2 is great).  You can also do a dual-boot w/Boot Camp which is faster and has 3D but more glitches. Right now I'm running Ubuntu Gutsy on my MacBook as the main OS, but I figure I'll probably just go to OS X + Gutsy, Feisty, maybe Solaris/FreeBSD/another distro, and XP on VMware Fusion (easier to do everything that way).

---

### Post by voided3 on 2007-06-16
I just so happen to use VMware Fusion beta 4 with WinXP. DSL, and Xubuntu. I have had good luck with it, but I noticed that the latest beta caches up ram differently and seems to use more overall. I have my WinXP VM set to use 640mb even though I have 2GB of ram so it doesn't have to page file; kind of a bummer, especially since this is without any other apps open after a fresh boot with the only startup item being SMCfancontroller. Oh well, still a great tool to have.

---

