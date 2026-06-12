---
title: "HOW TO: Get those Dapper-looks fonts back in Edgy (Fixes Firefox and OO issues)"
date: 2006-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Lem on 2006-11-04
Got font issues in Edgy?

Get back the Dapper look with;

```
sudo mv /etc/fonts /etc/fonts.backup
sudo apt-get install --reinstall --yes -o DPkg::Options::=--force-confmiss -o DPkg::Options::=--force-confnew fontconfig fontconfig-config

```

This fixed the naff fonts in Opera/Firefox and Open Office too.

---

### Post by stalefries on 2006-11-04
Could you explain what all that does? How did you figure this out?

---

### Post by Lem on 2006-11-05
First line backs up your font folder in case it doesn't work properly.
The second line reinstalls fontconfig forcing new configuration files.

I'm assuming it's just those of us that upgraded from Dapper to Edgy that are having all the fonts issues. This got my desktop looking like it did before the upgrade, including apps.

---

### Post by Lem on 2006-11-06
Does this work ok for everyone else?

---

### Post by Freddd on 2006-11-06
No, it doesn't work for me! Still same ugly fonts when writing in Open Office. ](*,)

---

### Post by Spudgun on 2006-11-06
Anyone got before and after screen shots?

---

### Post by Lem on 2006-11-06
> **Spudgun said:**
> Anyone got before and after screen shots?

No, but mine went back to exactly how I had it set up in Dapper (ie. much, much better). Unless anyone tells me different, I'm assuming this only works for those that have upgraded from Dapper to Edgy.

---

### Post by frogotronic on 2006-11-06
> **Lem said:**
> No, but mine went back to exactly how I had it set up in Dapper (ie. much, much better). Unless anyone tells me different, I'm assuming this only works for those that have upgraded from Dapper to Edgy.

Overall, much better - but OO is still not perfect; I did a log out; log in - I'll try a restart.

---

### Post by frogotronic on 2006-11-06
> **cement_head said:**
> Overall, much better - but OO is still not perfect; I did a log out; log in - I'll try a restart.

nope...still an issue with OO

---

### Post by Footer on 2006-11-07
Didn't work for me.  ](*,) ](*,) ](*,)

I did an apt-get distro-upgrade from Dapper to Edgy the day after it went final and that's when the OO fonts problem started.  I've tried many things but to no avail.  The latest was removing OO completely (man was that a pain!) and reinstalling (removed with Adept, reinstalled with apt-get at the CLI) and that didn't work either.  I even tried the trick that Lem posted but it didn't work for me.  If you want to see screen shots from my system, check out this thread (reply #3):

[http://kubuntuforums.net/forums/index.php?topic=10385.0](http://kubuntuforums.net/forums/index.php?topic=10385.0)

WHEN IS THE FIX COMING???

Any idea if an install directly from OpenOffice.org via their tarball would help???

---

### Post by Gsundbrunn on 2006-11-08
Hi,

this didn't really fix it but made it better:

1. Download an old version of libfreetype6 (The version of Dapper works perfectly)
2. copy it (I did it as root) as libfreetype.so.6 to /usr/lib/openoffice/program

Restart OpenOffice. OO still uses not the correct font, but the rendering is better.

As known from Fedora (they had the problem with the last distro 5) it took a lot time to fix it...

I'm still thinking about switching from Ubuntu to Fedora - for me OO is a showstopper...

Regards

Stefan

---

### Post by Lem on 2006-11-08
I must admit, my OO still isn't perfect, but the rest has certainly improved after the mod.

Annoyingly enough, I installed a fresh edgy cd on another box for mythtv use and the fonts were fine! Something has obviously gone awry during the upgrade process...

---

### Post by wilberfan on 2006-11-17
> **Lem said:**
> Got font issues in Edgy?

Get back the Dapper look with;

```
sudo mv /etc/fonts /etc/fonts.backup
sudo apt-get install --reinstall --yes -o DPkg::Options::=--force-confmiss -o DPkg::Options::=--force-confnew fontconfig fontconfig-config

```


Woah.   That scortched my xorg.conf file and thus my screen rez!!  Yikers!

I got xorg restored, so my screen is back to normal...   Did that undo whatever that fix was supposed to accomplish??

---

### Post by Rui Pais on 2006-11-18
> **Lem said:**
> I must admit, my OO still isn't perfect, but the rest has certainly improved after the mod.

Annoyingly enough, I installed a fresh edgy cd on another box for mythtv use and the fonts were fine! Something has obviously gone awry during the upgrade process...

Continuing the ubuntu saga of useless changes on the locations of folders on the system, edgy came with the old /usr/share/**X11/fonts/** twisted to /usr/share/**fonts/X11/**.  
So with lot of people doing they updates without change xorg.conf or plain copy the xorg.conf from old installs things can becames a little wild...

You said your updates have font problems and your box with new install are fine... you are a good candidate for this specific of problem. 
Check if paths on your xorg.conf are according to the real paths on your system.

---

### Post by r_mano on 2007-02-21
Is there any new on this? I have just now upgraded from dapper to edgy, and I have this problem. I tried all the suggestion here. It seems as if the fonts has an excessive antialiasing, but I tried to fiddle with the font property panel to no avail. 

Romano

---

### Post by James Wilford on 2007-03-05
I've got the same problem and its driving me crazy! Since upgrading from Kubuntu Dapper to Edgy, my fonts are all larger, blurrier and appear over-antialiased.

As a test I did a fresh install of Edgy in VMware, and the fonts were fine there, so I took some screenshots. Firstly here's my fonts compared to the Edgy live CD:

[http://www.flickr.com/photos/jwilf/411861059/](http://www.flickr.com/photos/jwilf/411861059/)

Here's a close-up of the font selector showing the same font at the same size being rendered differently:

[http://www.flickr.com/photos/jwilf/411861066/](http://www.flickr.com/photos/jwilf/411861066/)

And here's my fonts compared to the Mac... quite similar really but I can't say I like the Mac fonts either:

[http://www.flickr.com/photos/jwilf/411861072/](http://www.flickr.com/photos/jwilf/411861072/)

I've tried everything in this thread, as well as reconfiguring Xorg to get a fresh xorg.conf - nothing makes any difference. I've compared the files in /etc/fonts on my machine with the ones on the fresh install in VMware - also no difference.

Any ideas anyone?

---

