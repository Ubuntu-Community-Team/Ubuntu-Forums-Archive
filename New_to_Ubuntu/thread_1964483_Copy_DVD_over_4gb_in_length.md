---
title: "Copy DVD over 4gb in length"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by anewguy on 2012-04-24
Forgetting the encryption (I've got that handled), I have tried Brasero, K3B, K9Copy and Handbrake and it seems they stop copying at the typical dvd size - 4.8gb.  I have a DL drive and would like to be able to copy the entire movie.  Instead, the copy either says it's complete but only 4.8gb is there, or it aborts with a read error at the same amount of data - even when going to an ISO. 

Somehow it seems none of these want to copy correctly - even going to an MP4 with Handbrake.

Does anyone know if there is way around this?  I'd prefer not to "shrink" the DVD as I would like the full 2 1/2 hours in it's normal presentation - not chopped.

Thanks in advance!
Dave ;)

---

### Post by Cheesemill on 2012-04-24
Have you tried dd to create an iso first?
```
dd bs=1MB if=/dev/cdrom of=filename.iso
```

---

### Post by anewguy on 2012-04-24
> **Cheesemill said:**
> Have you tried dd to create an iso first?
```
dd bs=1MB if=/dev/cdrom of=filename.iso
```

I'll give that a try and see what happens.  All the others fail on reading beyon 4.8gb - I think they think the DVD I'll put in will be a regular DVD and not a DL DVD.

Thanks!  I'll let you know how this goes!

Dave ;)

---

### Post by Grenage on 2012-04-24
I presume that the DVD drive you're using can actually read dual layers ok?  I've seen a few that did not.

---

### Post by 3rdalbum on 2012-04-24
They recompress the disc's content to fit 4.8 GiB of space, which is the space for a normal single-layer DVD. You don't lose any video, you only lose a small amount of picture quality (or extra languages or titles you don't want, at your option).

Doing a straight copy should work as you want. I'm pretty sure K3B will decode the video but not perform any recompression or shrinking, if you just tell it to copy the disc as you would any other sort of disc.

---

### Post by SeijiSensei on 2012-04-24
> **anewguy said:**
> I have tried Brasero, K3B, K9Copy and Handbrake and it seems they stop copying at the typical dvd size - 4.8gb.  I have a DL drive and would like to be able to copy the entire movie.

Are you sure you're using [dual-layer media]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007591%20600010559&IsNodeId=1&name=8.5GB")?

---

### Post by anewguy on 2012-04-24
Yes, using dual-layer media.  Yes, I know it should copy - it doesn't.  Yes, I know about the shrinking - what I meant by chopped up is that I have found that when it compresses 7.70gb to 4.8, there is a noticable difference, and I don't want that.  I think part of the problem is that while it is reading the DVD it assume the disk I will put in the drive will be 4.8GB and it doesn't figure on compression, so it aborts when it reaches 4.8GB read.  This even happens when I used K3B and had it create an ISO.

Cheesemill:  Interesting, that ran and created the appropriate sized ISO.  I was able to burn that ISO to a DL DVD.  But now for something I'm not sure about:  it appears that the video either got scrambled or something else happened.  The source DVD plays fine both on my PC and in my DVD player for my TV, but the copy only plays the sound while an extremely distorted version of the menu shows.  I would have thought it was a bit-by-bit copy so it should have worked.  I know when using something like dd to do the copy the decryption doesn't apply, but I still thought it would be an exact copy.

---

### Post by Cheesemill on 2012-04-24
> **anewguy said:**
> Cheesemill:  Interesting, that ran and created the appropriate sized ISO.  I was able to burn that ISO to a DL DVD.  But now for something I'm not sure about:  it appears that the video either got scrambled or something else happened.  The source DVD plays fine both on my PC and in my DVD player for my TV, but the copy only plays the sound while an extremely distorted version of the menu shows.  I would have thought it was a bit-by-bit copy so it should have worked.  I know when using something like dd to do the copy the decryption doesn't apply, but I still thought it would be an exact copy.
Odd. I use dd a lot to rip iso files, mainly of data disks but I've used it on video and audio disks and I've never had it produce anything but a bit perfect copy (unless the disk was damaged/dirty).

You could try running md5sum on both the disk and the created iso file to check if they are in fact identical:
```
md5sum /dev/cdrom
md5sum filename.iso
```

---

### Post by anewguy on 2012-04-24
well, for some reason K3B did read all the way through and create an ISO.  I'm on my netbook right now but when I get back to the desktop I'm going to try mounting the ISO and try it in movie player or vlc before3 I screw myself out of another DL DVD.


I'll let you know what happens, but I would think it should be fine since the reads in K3B should have removed the encryption.

Thanks again!

Dave ;)

---

### Post by anewguy on 2012-04-25
Okay, still strange stuff going on.  I don't know if it's linux sata DVD driver problem, a problem in the apps, or because I'm running 12.04 beta (up to date as of last weekend).  As I mentioned above, I finally got K3B to go all the way through the disk and create an ISO, so I have an ISO that doesn't have the encryption.  Next I tried burning to another DVD-R DL.  K3B's output selection screen saw it as a DVD-R DL.  When the burning got a little more than half way through (i.e., over the 4.7gb of a regular DVD) it blew out again.  This has been getting expensive, so I went to MicroCenter and got a 25 pack of cheap DVD+R DL so I wouldn't keep making coasters out of my expensive DVD DL disks.  So I try again with the DVD+R DL - same problem.  Since my Windows partition is mounted automatically in Ubuntu, I copied the ISO file to the Windows partition, booted Windows 7, used file explorer to get to the ISO, right-clicked and selected burn to disk.  Yep - went through with no problems the first try.  The disk seems to play fine - I've jumped around all over in it.

So, why can't my Ubuntu, using Handbrake, K9Copy or K3B consistenly create the ISO without a failure at the 4.7gb range?  Why can't I burn the ISO to a DL disk using K3B without getting an error at the same data length?

Seems like I've isolated it to something with how Linux runs on my box or the way the software runs.  Either way - works in Windows 7, doesn't work in Ubuntu.

I'm confused.

Dave ;)

---

### Post by alphacrucis2 on 2012-04-25
> **anewguy said:**
> Okay, still strange stuff going on.  I don't know if it's linux sata DVD driver problem, a problem in the apps, or because I'm running 12.04 beta (up to date as of last weekend).  As I mentioned above, I finally got K3B to go all the way through the disk and create an ISO, so I have an ISO that doesn't have the encryption.  Next I tried burning to another DVD-R DL.  K3B's output selection screen saw it as a DVD-R DL.  When the burning got a little more than half way through (i.e., over the 4.7gb of a regular DVD) it blew out again.  This has been getting expensive, so I went to MicroCenter and got a 25 pack of cheap DVD+R DL so I wouldn't keep making coasters out of my expensive DVD DL disks.  So I try again with the DVD+R DL - same problem.  Since my Windows partition is mounted automatically in Ubuntu, I copied the ISO file to the Windows partition, booted Windows 7, used file explorer to get to the ISO, right-clicked and selected burn to disk.  Yep - went through with no problems the first try.  The disk seems to play fine - I've jumped around all over in it.

So, why can't my Ubuntu, using Handbrake, K9Copy or K3B consistenly create the ISO without a failure at the 4.7gb range?  Why can't I burn the ISO to a DL disk using K3B without getting an error at the same data length?

Seems like I've isolated it to something with how Linux runs on my box or the way the software runs.  Either way - works in Windows 7, doesn't work in Ubuntu.

I'm confused.

Dave ;)


One option might be to try replacing cdrkit with cdrtools. See this ppa:

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

---

### Post by anewguy on 2012-04-25
I'm going to give that a try a little later tonight.

Thanks for the suggestion!

Dave ;)

---

### Post by perspectoff on 2012-06-12
I have been having the same problem for some time (including in Oneiric), but the problem for me occurs at the 3.8 GB mark on regular DVDs (DVD-R type) as well, not just on DL DVDs.

I never had these problems in Lucid (I went directly from Lucid to Oneiric).

I have no problem burning DVDs less than 3.8 GB, so the problem isn't my drive (which is the same one I've used since Hardy). The problem occurs with Brasero, k3b, or Gnomebaker, so the front-end seems to be irrelevant.

My suspicion is also that it is related to genisoimage that comes with cdrkit -- I think it is not handling large amounts of data around the 4 GB mark on DVDs. If I'm not mistaken, smaller amounts of data are handled by wodim (or cdrecord when installed) and large amounts of data (around 4 GB or more) handled by genisoimage (or mkisofs if installed).

When the cdrkit vs. cdrtools war started, Debian/(K)Ubuntu replaced cdrecord with wodim and mkisofs with genisoimage, creating symbolic links (so that front-end programs are fooled into using wodim for cdrecord and genisoimage for mkisofs).

It is a real pain to go back to the real cdrtools (instead of cdrkit) and use the real mkisofs instead of genisoimage, and cdrecord instead of wodim, as this guy did:

 [http://ubuntuforums.org/showthread.php?t=852085](http://ubuntuforums.org/showthread.php?t=852085)

Brandon Snider's .deb package for cdrecord installs ok, but not the mkisofs package, as there are lots of errors and "removal dependencies" when genisoimage is removed, which cripples the system. 

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

Ubuntu has made it very difficult to switch (back) to cdrtools. This is probably my biggest gripe with (K)Ubuntu these days.

...or perhaps the problem is not with cdrkit but has something to do with this recent (Dec 2011) update to libdvdread (i.e. maybe the problem wasn't fixed completely/correctly)?

libdvdread (4.2.0-1ubuntu3) precise; urgency=low

* Add 103-iforead-tt-srpt-pointerfix.patch: Fix read/write beyond end of
an array due to using a length value taken from the DVD, which can
exceed the allocated size, causing a segmentation fault.
(LP: #894170)

---

