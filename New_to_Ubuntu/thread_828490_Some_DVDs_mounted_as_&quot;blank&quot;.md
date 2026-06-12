---
title: "Some DVDs mounted as &quot;blank&quot;"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by angelsneverdie on 2008-06-13
Ok.  So I was running gutsy.  I burned all the files to dvd that I wanted to keep and wiped everything and did a clean install of Hardy.  Now, the dvd's that I burned, i pop em in and it shows them as blank dvds.  I took them to work and put them in a win xp machine and they were read fine.  So i copied the data to my work computer, and then reburned the dvd's and even those load as blank.  

I should note however that this is not true of all of the dvd's that I burned as backup.  A few of them actually worked.  The ones i burned from windows I did use the udf filesystem (nero said anything over 2 gigs had to use it) - but the ones I burned in gutsy should be fine.


why can't my computer read dvd's properly?  this seems like a relatively important feature to have problems with on a release.

thanks for the help!

---

### Post by expatCM on 2008-06-13
I wonder if it is something simple like needing to run a CD cleaner to brush the dust off the drive lenses?

---

### Post by angelsneverdie on 2008-06-14
> **expatCM said:**
> I wonder if it is something simple like needing to run a CD cleaner to brush the dust off the drive lenses?

i just tried using a can of compressed air to clean things out.  No go.

---

### Post by stinger30au on 2008-06-14
i have a cds like this too. they read fin in xp, but no go in ubuntu.

i tried swapping the drives and still no go.

i have a feeling it may have something to do with how the session has been rerecorded on the disc

---

### Post by angelsneverdie on 2008-06-14
> **stinger30au said:**
> i have a cds like this too. they read fin in xp, but no go in ubuntu.

i tried swapping the drives and still no go.

i have a feeling it may have something to do with how the session has been rerecorded on the disc

all the discs i burned should be the same - i did them one right after another, all from the same program, all without even closing the dvd writing program inbetween (i used gnomebreaker).

Any other ideas?  It is frustrating that my computer won't read dvd's when every other computer will.

---

### Post by angelsneverdie on 2008-06-17
bump

---

### Post by Golem XIV on 2008-06-17
Same problem here on a couple of DVDs that report fine under Windows, but under Ubuntu show up as empty.  Note - not blank, definitely recorded, but there's nothing to be seen in Nautilus, not even hidden files.

---

### Post by angelsneverdie on 2008-06-21
bump

---

### Post by stella2657 on 2008-06-21
> **angelsneverdie said:**
> all the discs i burned should be the same - i did them one right after another, all from the same program, all without even closing the dvd writing program inbetween (i used gnomebreaker).

Any other ideas?  It is frustrating that my computer won't read dvd's when every other computer will.
same problem here - drive shows blank disc or error no disc, ripped out drive and replaced, still the same problem.

---

### Post by martinquested on 2008-07-18
I have a similar problem except that my DVD shows up as not quite blank - one folder is visible, let's call it "Scottish"

Oddly, that folder is *not* visible when I stick the DVD in my DVD player (the one connected to my TV).  In the DVD player, I see over 40 folders, everything that's on the DVD-ROM, *except* for the folder "Scottish" which I can see on kubuntu.

This is really weird.  I cannot remember whether I burned this DVD in two sessions or one, but whether or not, it should be possible to read this thing.  Something is clearly very wrong with the way the DVD is being mounted...

Does anyone have any idea what we should be looking for?

---

### Post by SunnyRabbiera on 2008-07-18
for burned dvd's make sure they are finalized

---

### Post by martinquested on 2008-07-18
I think they're finalised.  Otherwise it would not work in the DVD player in the lounge.  Also, if they were not finalised, I'd be able to import the open session into K3b and similar burning programs.

---

### Post by SunnyRabbiera on 2008-07-18
how many dvd players you have in your house may I ask?

---

### Post by martinquested on 2008-07-18
Not sure how that's relevant, but as it happens we have two - both in the lounge - one of which we don't use because the remote control has been lost and it doesn't do much without one.  I used the phrase "in the lounge" to differentiate between the DVD drive in my computer and the standalone player connected to the TV.

---

### Post by martinquested on 2008-07-18
Well, it seems to be fixed, but I'm not sure exactly what did it.  Things I have done include:

- modifying the /etc/fstab so that the final line reads ```
/dev/scd0 /media/cdrom0 iso9660 ro,user=ivman 0 0
``` (YMMV especially with regard to the first entry, i.e. the actual device location in your system)

- restarting kded (in the terminal, *not* as superuser) and then the kde mediamanager (from System, System Administration, System Services)

- deactivating "autostart after mount" (System, Peripherals, Storage Media, Advanced)

- clearing out some space in my Kubuntu root partition, including the use of various tips listed [here](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html) to remove unneeded packages and identify space-hogging files

- rebooting the machine

I have a horrible and inexplicable suspicion that it was the last two steps that did it, although I can't work out quite why that would be.

---

### Post by opogon1 on 2008-11-13
I am having this same problem.  Issue started as soon as I upgraded from Hardy to Intrepid.  Disks read fine on my laptop (also running Intrepid).  DVD's play fine on my DVD player and PS3.  Tried updating FSTAB as mentioned above to no avail.  Funny thing is only certain DVD's have this issue, and only dvd's I've burned since installing Intrepid.  All DVD's burned using Hardy read fine.

All of the DVD's that have this problem have been burned using Brasero.  Something I've noticed that is funny is that the disk doesn't eject after burning on the disks this happens to.  If the DVD ejects right after burning they always read fine.  Brasero always reports the burn was successful, even if it doesn't eject after burning.  Thinking this is a finalization issue, but it doesn't make sense that they read fine on all other DVD players if they aren't finalized.  This is happening on about half the DVD's I burn.  Totally stumped, any help would be greatly appreciated.

---

