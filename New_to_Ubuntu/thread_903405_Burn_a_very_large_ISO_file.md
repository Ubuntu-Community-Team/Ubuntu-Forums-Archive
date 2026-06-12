---
title: "Burn a very large ISO file"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by MaxVK on 2008-08-28
Hi there. Iv been passed an external HD with an ISO file on it for me to burn. However, the file reports as being 6.4 Gig and I'm not sure if there is any way to burn it.

Right clicking the file and selecting to burn it or open it with the DC/DVD creator gives me an error that the file is not valid. The file *is* valid, but Iv a feeling that it is too big to burn in this way.

Is there another way to burn this file - Naturally I have an 8.5 Gig DVD compatible with my burner, which is dual layer compatible etc.

Regards

Max

---

### Post by mellowd on 2008-08-28
Should burn fine on an 8gb disc

---

### Post by estamand on 2008-08-28
Just make sure you have a Dual Layer DVD Burner and DL media.

---

### Post by philinux on 2008-08-28
Try K3b to burn it.

---

### Post by dRock1286 on 2008-08-28
Yes.  K3B has been my friend in situations like this.  It has never failed me yet.

---

### Post by bumanie on 2008-08-28
Depends on what kind of .iso file it is. If it is data try k3b as suggested, if it's a video file k9copy (definitely) or devede (maybe??) should be able to handle it. Easiest solution if data, is probably to invest in a D/L disk.

---

### Post by MaxVK on 2008-08-28
Okay, thanks everyone - there are a few names there for me to try.

Regards

Max

---

### Post by egalvan on 2008-08-28
Let us know how things work out ( or don't ), 
so others can benefit.

Thanks

ErnestG

:popcorn:

---

### Post by MaxVK on 2008-08-28
Hmm. Here's a little update:

K3b has been installed, but when it loads the ISO file it shows as not being an ISO9600 (or similar number! ;) ).

The checksum is fine but when I choose to start burning I am warned that while this file is not standard (it should be!) K3b might still be able to burn it. If I continue then the whole thing stops with an Input/Output error.

I get the same error from Gnombaker.

The file should check out since it was burned from the external drive by the person who created the file. Iv tried directly from the external drive and also by copying the file to my HD.

I'm kind of lost now and I'm not sure what else to try. Any hints or ideas would be gratefully received.

Regards

Max

---

### Post by mellowd on 2008-08-28
If you mount this image does it mount correctly? If not maybe the image isn't in fact a proper iso image

---

### Post by philinux on 2008-08-28
In that case I'd use K9copy as has been suggested.

---

### Post by MaxVK on 2008-08-28
I have Gmount-ISO installed, and the image mounts fine - The Image contains a series of videos of a local band and the menu system to select them (Its a video DVD, as in, it can be played in a normal DVD player), and they play when the image is mounted.

Is K9copy still a valid suggestion, or is that only if the image did not mount?

Cheers

Max

---

### Post by mellowd on 2008-08-28
Try K9copy anyways and see what happens.


it's all a bit odd...

---

### Post by egalvan on 2008-08-28
[QUOTE=MaxVK;5681157]...(Its a video DVD, as in, it can be played in a normal DVD player), and they play when the image is mounted./QUOTE]

So this was copied from a working Dual Layer DVD?

From what I remember of some DVD-copy software, ISO9600-compliance is an option. Perhaps something to check.

But as others have said, try burning a copy anyway.

---

### Post by MaxVK on 2008-08-28
> So this was copied from a working Dual Layer DVD?

Yes. I don't know what software was used but it was done in Windows. The ISO file was burned in Windows and works (Iv seen it) and the ISO was given to me on an external HD.

Ill have to check out this setting with the person who made the ISO, which may take a little while since he's away working. In the meantime Ill try to use k9copy and see what happens.

Thanks for your input.

regards

Max

---

### Post by LowSky on 2008-08-28
if burning it does't work, why not pull the videos and create a new Video DVD. or mount the ISO and then tell K3b to do a copy instead of burning the image. Its an odd trick that sometimes works.

---

### Post by MaxVK on 2008-08-29
> if burning it does't work, why not pull the videos and create a new Video DVD

Well, it didn't work so thats an option, but Iv never had any luck doing this before either - I used DeVeDe just a little while ago, and although the video came out fine, the sound was just mashed up noise. I tried a few times and each time I made a preview the result was the same, no matter how I adjusted the sound settings.

> ... mount the ISO and then tell K3b to do a copy instead of burning the image

Now theres an idea! Ill give that a go when I get home, and if that fails I might as well try to make a Video DVD myself again.

Thanks for all your help everyone, Ill post back and keep the thread up to date so others can reference it should I actually succeed!

regards

Max

---

### Post by egalvan on 2008-08-29
> **MaxVK said:**
> Thanks for all your help everyone, Ill post back and keep the thread up to date so others can reference it should I actually succeed!
regards
Max

Actual success or not, try to keep us posted.
 Even failures are helpful when trying to succeed.
(failures can show us what roads not to take)

Thanks for your willingness to try all the ideas we've thrown out to you.

ErnestG

:popcorn:

---

### Post by lisati on 2008-08-29
I don't know if it will work with Wine, but the copy of DVDshrink I regularly use can open ISO files and shrink them to a 4.7Gb size.  (DVDshrink is a Windows program I've been known to use from time to time in conjunction with Nero)

---

### Post by MaxVK on 2008-08-29
Okay, a little update on the strangeness:

The ISO file continues to mount with Gmount-ISO and the video is playable from that. However, so far nothing has been able to burn this to a disk.

I tried to copy the mounted file with K3b, but again, this failed with an input/output error (Iv used this program to burn numerous disks, so I know its not the program having a problem).

Incidentally, this is a dual boot machine, and I have found that a Windows program called PowerISO not only runs very well under Wine (Considering that it was installed in Windows!) but that it opens the ISO file without a murmur and offers to burn the file for me, however, Wine does not seem able to see my DVD writer at this time (I'm following that up when Iv made this post).

However, all is not lost (yet!). Iv scanned the external drive and found a folder that contains all of the video files that have been included in the ISO file (A phone call has confirmed that they are all there). These files are .avi files and they can all be played in MPlayer (and probably others).

I have DeVeDe installed, and using this I should be able to put together a video DVD for myself, however, whenever I try the video using the preview function, the sound is a mass of angry hissing!

So the current situation is that I am trying to get the DVD Writer showing under Wine with the intention of trying PowerISO to burn the file, and at the same time trying to work out how the heck to I get DeVeDe to work properly!

If anyone has any ideas with either of these approaches, Ill be glad to hear them!

Regards

Max

---

### Post by MaxVK on 2008-08-31
Okay, progress report.

I am currently at the point of admitting defeat and asking my Windows using friend to burn this file for me!

No matter what I do the ISO file appears to be quite normal, but programs simply refuse to burn it. 

The individual video files are .avi files, and they all play perfectly well, but when I try to use DeVeDe to create a video disk (Which is what the ISO file is) I get a preview that has nothing but unpleasant hissing for a soundtrack. Iv actually burned one of the disks just to check that this isn't a problem that only relates to the preview, and its not!

So then. Any advice or ideas? I really don't want to ask my friend to burn me a copy of this DVD but I'm quite lost now, and I'm not an experienced Linux user by any stretch, so I simply don't know what to try next.

As much as the original emphasis of this thread was to burn the large ISO file, Id be quite happy creating a video DVD of my own.

Regards

Max

---

### Post by egalvan on 2008-09-02
See this post. it seems to be similar to your problem

[http://ubuntuforums.org/showthread.php?t=907907](http://ubuntuforums.org/showthread.php?t=907907)


[I] Re: Wine cant find Cd-rom
Quote:
Originally Posted by dRock1286 View Post
  Go to Wine configuration and under drives see if and letter corresponds to /media/cdrom0[/I]

Went there and selected "autodetect" it found the drive and it all works fine now thanks a bunch man

---

