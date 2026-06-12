---
title: "[SOLVED] &amp;quot;Tick&amp;quot; from hard drive"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by sokopok on 2008-10-10
I've been getting an annoying tick from my harddrive lately, imho most of the time (but not limited to) when my disk is getting crammed (i have a 120GB partition mounted on /home that sometimes gets filled up to near 100%). So I was getting worried. Is this anything like what you experience? I was just reading [http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570) and this thread seems to talk about related fixes. Is it also the same problem?

---

### Post by bodhi.zazen on 2008-10-10
I moved your post to a more visible location. You really should start your own threads rather then posting in an un-related thread.

Hard to know if the noise means much of anything. Best back up your data just in case ;)

---

### Post by sumguy231 on 2008-10-10
It does indeed sound like the hard drive heads parking. Be aware that that is completely normal behavior if it is only happening occasionally. But if it's happening constantly (once a minute or more) you are affected by the issue in that thread and should seek a workaround. How often does it occur?

And of course, it could be the bad kind of noise I suppose. Back up your data no matter what if you can. This is a laptop drive, right?

---

### Post by sokopok on 2008-10-11
I've had disks die on me before and I don't think I have the same symptoms now.
The ticking doesn't occur constantly, it usually starts under heavy load or when the disk is like I said nearly full. Typical scenario: downloading large files from internet (at 2.5MB/s) and perform disk-intensive operations simultaeously. So disk parking, probably not...
Apologies for replying and not creating a new post. I was browsing the forums and read adhanali,s post so I just wanted to check if this was what he was experiencing (if so this would shortcut my search considerably).

---

### Post by dhughes on 2008-10-11
Yeah it's hard to say, but as the others have said it's better to be safe than sorry, back up important files. Right now.

 Recently I've had a brand new Seagate fail soon after buying it, there weren't any signs at all just one day it failed. When I came home it sounded like a loud buzz coming from it, it failed when I was out. I tried the freezer trick, put the HD in a bag in the freezer at -20C for a couple of hours and it worked long enough for me to get an important file off it.

---

### Post by HavocXphere on 2008-10-11
> **sokopok said:**
> I've been getting an annoying tick from my harddrive lately, imho most of the time (but not limited to) when my disk is getting crammed
Make a back-up of the important data on that harddrive ASAP. Last time I had a harddrive that suddenly started ticking, it was dead within a day. The drive had to go to a lab with a clean-room for recovery...cost loads of $$$ and only got 70% of the data back.

Ticking drives *can* survive for years without disaster...but one would be pushing one's luck imo.

There are some kinds of ticking sounds that indicate imminent disaster and others that are less worrying. Either way, its not worth risking mission-critical data.

---

### Post by niteshifter on 2008-10-11
Hi,

If this ticking is always occurring on a nearly full disk then it's thrashing (normal). That you're starting to hear it now - assuming you've had it near full before and did not hear it - could be bad.
 
If the drive is a SMART drive. run smartctl on the drive. Search here and elsewhere for SMART related info on that model drive.

And yes, do back it up. Always back it up. Trust me on this - I've dealt with many a storage failure over the years - they aren't always so polite as to announce impending failure in the error logs, diag runs or with sounds.

---

### Post by sokopok on 2008-10-11
Thanks for the replies fellows. I,ve been using all kinds of dev, alpha, beta, systems for years, and always loved 'tinkering' with them, so I've had my share of screwups in the past. So the backups were already in place before the ticking started (and get updated daily) :)
Let's pray to <insert name of devine being here> I don't need them.

---

### Post by zephyrcat on 2008-10-11
If the drive is either fairly old or very new, unlesss your backups are very frequent, I would consider just replacing the drive as a precaution (assuming the computer you have makes that possible).

---

### Post by sokopok on 2008-10-18
Cleaned up my HD (got a fancy new TB external), so I have some more free space now. The ticks have completely disappeared.
I suppose the ticking was due to the heads zooming back and forth too much, too fast under heavy load. I'll close this thread.

---

