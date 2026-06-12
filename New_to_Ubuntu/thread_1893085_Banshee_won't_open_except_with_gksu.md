---
title: "Banshee won't open except with gksu"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by JohnDillinger43 on 2011-12-09
I've been trying to get my iPod to jive with Ubuntu, and have been having some issues.  First I tried GTKPod, which froze.  Next I tried Banshee, which I've had better luck with.  I imported files from my music drive yesterday, and today when I went to open Banshee, it wouldn't open.  When I click on the icon, it flashes like it's opening, but nothing ever happens.  At first I thought it might just be slow, but it's been an hour now and nothing has happened.  It will open if I run gksu banshee from the terminal, but then when it opens my music library is missing.  Wondering if anybody else has had this problem or knows how to solve it.  I'm in the process of switching over from Windows, so my music drive is NTFS, don't know if that's an issue.  My Ubuntu installation is on its own ext4 drive.

Also, as a side note, when I did get Banshee to work yesterday it ran very, very slowly.  I don't think it's my system, I'm running an Intel E8400 2x3Ghz with 4GB of memory.  The OS HDD is mostly empty.

---

### Post by gennatolls on 2011-12-09
Banshee is full of bugs, I encounter that problem you are having all the time. Open up system monitor, navigate to processes and end banshee. It should restart fine after that. I have music playing throughout the day and it locks up 2-3 per day. The reason you dont see your playlist when you gksudo banshee is because your music is in your home folder. Root is treated as a completely different user, and when you used gksudo your in affect signing in as root and running banshee. NTFS partition shouldnt be a problem. When I used to dual boot, I would just mount my Windoze partition to play music. You may try the music player rhythmbox, I found it to be a very good player and superior to banshee. It has been the default music player for ubuntu for a while and is returning in 12.04.  I dont have an ipod so cant help you there. Good luck

---

### Post by JohnDillinger43 on 2011-12-10
Thanks, that makes a lot of sense.  However, for some reason I can't get system monitor to open either.  It looks like banshee isn't running when I do "kill banshee" in the terminal, though I'm not sure.

---

### Post by JohnDillinger43 on 2011-12-15
This issue seems to have disappeared after restarting my system; Banshee opens and I can scroll through my music library.  However, I still can't transfer anything to my iPod.  Banshee doesn't seem to recognize the music files on the device, though it recognizes that there is space being taken up.  This is a new development, because before Banshee crashed (triggering my original post), it did recognize the music on the iPod.  Anybody else had this problem?  Or any suggestions about a better alternative to Banshee for iPod management?  I didn't have any luck with gtkpod, but I've read about a few other programs that people seem to like.

---

