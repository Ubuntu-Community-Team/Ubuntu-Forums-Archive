---
title: "store dvds on hard drive and play back"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by squakie on 2013-05-23
novice at video - i'de lik4 to load all my dvds to disk so i can select and play them without swapping disks anymore.  i've heard the term "ripping" but not vsure what to do.  i'd like the menus, movie, extras, etc., just like using the disk itself.  I've just "downsized" by selling al of my computers.  i have found i can do a lot simple things just using my tablet.  so today i went to microcenter and bought a little zbox, a hdd and some memory.  i have 750gb esata drive i'd like to store and play my movies from - output via hdmi to my hd tv.  I'd also like to use it as a small desktop as well.
also, if i buy a bluetooth adapter (usb) is there someway to use my tabley as a remote controlof sorts?

any simple to follow how-o's, web links, etc., would be greatly appreciated!

---

### Post by andrew.46 on 2013-05-24
Best quality comes from simply storing a copy of the DVD on your HDD, takes a lot of space but quality is same as DVD itself. If you like the commandline vobcopy will do this for you (and decrypt at the same time) with:

```
vobcopy -m
```

There will be gui methods of doing this as well but I am on uncertain ground there...

---

### Post by squakie on 2013-05-24
I'll give that a try - as soon as I pick up the USB external DVD/row drive I forgot completely about :-)  do you know if xmbc could be of help to me as well?

---

### Post by squakie on 2013-05-26
while I'm waiting for portable DVD drive to come from eBay (talk about stupid to forget the that :-)  ), is there some sort of software that is kind of "all encompassing" software that loads DVDs to disk, creates a library of them, allows look up in the library and plays what you select?

I looked like in the readme sticky, but I didn't see how you supposed to copy them to disk and then play them.  as a sample of my questions about that, do I copy the DVDs as is iso images, and if so, do you have to mount the iso?  how do you select and play it?

sorry for the ignorance, but I don't know anything about these things.

---

### Post by squakie on 2013-05-27
I have a few questions about loading dvds to my hard disk for later playback in something like xmbc.  

do i just create iso images?  I've looked at the the wiki for xmbc but it's not real clear about what to do with iso images   so they are indexed, etc.

i'm familiar with playback of css disks, but anything beyond that i'm a complete novice withe all things video.

thanks

---

### Post by mapes12 on 2013-05-27
I use K9copy for backing up my DVD's to .iso files and Handbrake for compressing them into mp4 files for viewing on the move.

---

### Post by squakie on 2013-05-28
Bump.

---

### Post by leunam12 on 2013-05-28
Rip to .iso using K9copy; VLC will play .iso files and there are a few VLC remote controls for android.

---

### Post by oldos2er on 2013-05-28
I use k3b to rip DVDs to *.iso.

---

### Post by squakie on 2013-05-28
> **oldos2er said:**
> I use k3b to rip DVDs to *.iso.
Do you know if xmbc can index those and do the playback?  I don't want to have to do any mount, etc., just " push the button" in xmbc and have it play.  So far everything I've read from xmbc doesn't go into the specifics.

Thanks Ann.

---

### Post by oldos2er on 2013-05-29
I've never used xbmc and know nothing about it, sorry.

---

### Post by Grenage on 2013-05-29
XBMC plays ISO files (and just about everything else) wonderfully.  I used it on my media centre, where all the ISO files are stored; I can throw the DVDs in the loft, although I really wish I could just throw them away.

Once the files are in the library, you just select the movie you want, and press to play.  No mounting, no messing, no fuss.

---

### Post by squakie on 2013-05-29
Great!!  Thanks !!  And thanks to everyone who replied as well!

---

### Post by squakie on 2013-06-01
indeed, i created an iso using k3b just to it and xmbc - worked great!

---

### Post by squakie on 2013-06-05
Hey, this sure worked out great!  I have now have the desktop also running as a samba server.  I have xbmc on the deskltop so I can play movies/music/etc., AND I can connect from my tablet with the tablet version of xbmc and do the same, AND have a test bed Raspberry Pi set up with Rasperian, xmbc installed and working with local hard drive and via the server!  This is all working out just like I wanted it to!  I'm just waiting on the unique key for my CPU id so I can enable mpeg2 on the Raspberry Pi so I can play dvd's and dvd iso's.  It was all of $3.14 U.S. at the time I ordered it (I think it's based on the current exchange rate) and I should have it in a day or 2.

Thanks everyone for your great help and patience!!

EDIT:  forgot about the remotes - I just use the wireless mouse for the desktop, and for my test bed Raspberry Pi I found some info with a very minor addition of a part (read: a single part - I/R receiver from Radio Shack) connect to one or the programmable io pins, a voltage pin from the board and a ground pin from the board, then lirc which I have already installed.  Will be doing that minor work tomorrow and then I can use a regular TV remote for the Raspberry Pi and leave it headless.  If you're not familiar with the Raspberry Pi, I would suggest checking it out.  Fro $39 plus cables and some work software wise [relatively easy = Rasperian the OS is based on Debian so some things look very familiar), you can biuld a media center.  Since the box is running linux, there's also web browsing, etc..  It is based on a slower CPU and you will need USB external disk(s), but it's quite amazing for $39.  OS, etc., sits on an SDHC card you plug into the board.  Easy to create right from Ubuntu.

---

### Post by Cheesemill on 2013-06-05
If your TV supports CEC then you don't even need an additional remote, the TV remote will send signals to the Raspberry Pi via the HDMI cable.

I have mine set up this way, the Pi also gets powered by the USB port on the TV. This method makes the cabling very neat and tidy as there are just 2 cables between the Pi and the TV and a WLAN dongle in the Pi, no external cabling required. You can also get cases for the Pi with mounting holes that match the VESA mounting holes on the back of the TV keeping everything out of sight.

---

### Post by squakie on 2013-06-05
I was just trying that on the TV here in the basement.  It's a cheap Haier set and so far I can find anything beyond extremely simple set up options on it.  Might try it on another TV that quite a bit better (the apples/oranges thing) and see if it works there.

Thanks again!  BTW - I see that xbmc for Android must still be in the beginning stages.  I can play some iso's fine, other either don't start or cause xbmc to abort.  They all play fine on the main system accessing them via the share, so it's obviously a xbmc for Android problem.  I've only loaded 8 movies to the share so far - just my Harry Potter movies so I could test.  It's interesting that the ones that cause problems in Android are the 2 smallest ones - below 7.4gb.  Might see if xmbc has anything on that or if they want to know.

---

