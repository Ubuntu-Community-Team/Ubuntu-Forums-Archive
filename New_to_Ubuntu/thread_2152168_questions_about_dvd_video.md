---
title: "questions about dvd video"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by squakie on 2013-06-07
Well, I've got the Samba shares working with my PC,Google Nexus tablet and a Raspberry Pi so they can all watch the same videos via XBMC.  That's great!  Now I have some really elementary questions about handling dvd videos.  Try to be patient - I know absolutely nothing about this - so I don't know what it's called to even look for help.

Currently I have been using dvd iso images on the share, however they do take up quite a bit of space (I have a 2 TB drive for them, but hey - so far my movies are averaging over 7gb each).  I have seen mentioned in the forums for Raspberry Pi and XBMC that people are taking dvds and somehow just extracting the movie and it's sound without all the other stuff on it, and then making the files something like mkv or something - supposedly these take less space but still play in XMBC.  This would also help because both the XMBC that runs on my Android table and the XMBC that I have running with Raspberian (e.g., ARM) have problems working with the DVD "preliminaries" and even the menu.  Can work with it, but would prefer it be cleaner.

So, can someone tell me more about what this is, perhaps point me to some simple how-to's for it, and if possible a way to do it in Windows also. I run ubuntu 13.03, but one of the Raspeberry's is going to have it's own usb hard disk and going to be for my sister and brother inlaw - and they do Windows.  So after finding out what the heck this all is and how to do something with it, I then need to find a way to duplicate the process for them.  That is unless someone knows how to do this on the Raspberry Pi running Rasperian (based on Debian) - then I could just set them _up on the Rasbberry Pi_ that I installed XMBC to (not stand alone XBMC).

Any insight into possibilities, nomenclature, etc. would be greatly appreciated by a non-novice ubuntu user who just doesn't know ANYTHING about video!

---

### Post by cariboo on 2013-06-07
I use [Handbrake]("http://handbrake.fr/") for ripping DVDs. I personally use the handbrake/snapshot ppa, to get the latest vsersion. you can add the ppa by opening a terminal and either typing, or copy/paste the following command:

```
sudo apt-add-repository ppa:stebbins/handbrake-snapshots
```

then run the following command:

```
sudo apt-get update
```

You should now be able to download and install handbrake using your favourite method.

With the settings I use, the resulting files average about 2.5GiB.

---

### Post by squakie on 2013-06-07
i'll be giving it a try now, since I already have handbrake.  I've never been able to do the rip thing, but i did notice it shows thge chapters to be converted so i guess it must be doing it.  Obviously the decoding and creating a different file type will run a lot longer than just creating an iso.  it probably doesn't help that my little zbox is only running a dual core atom processor instead of a grown-up processor ;)

---

### Post by squakie on 2013-06-07
I changed file type to mkv - result looks good and shrunk from 7+ gb to about 1.2 gb, and it works in XBMC fine.  Going to try that in XBMC on the Raspberry Pi - I suspect it will take care of the problems there since there will no longer be any menus, etc..

I also took just the defaults and let it create an mpeg4 file also.  That completed in an hour versus 5 hours to do the mkv.  I really don't see any noticable differences in the video and audio quality.  The resulting mpeg4 file is only 747 mb.  

So, since the mpeg4 - which is the default - converts so much faster and the file size is so small, I think I'm just going to go with the defaults from Handbrake.

Thanks for the additional help!  I never figured any of this out before, but the ripping was quite easy - put the dvd in, start Handbrake, point to the dvd so it gets the info for the disk,. and just start and walk away.  Couldn't be any easier, and I suspect that since there is Handbrake for Windows and libdvdcss for Windows, it should work fine as the conversion tool for them on their Windows machines as well.

I'm pretty excited - these little Raspberry Pi's can do a lot!

Thanks for ytour help on this entire adventure for me - you've been a great help!

---

