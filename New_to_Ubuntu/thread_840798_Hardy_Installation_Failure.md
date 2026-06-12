---
title: "Hardy Installation Failure"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-06-25
Hi Ubuntu Community:

I had such a rotten hard time with gnome-rdp not working, and it was such an important application, that I decided to back up my system, download the AMD-64 iso, burn it, and then reinstall Ubuntu.

The reinstallation failed: shortly after making the choice to do the install, a moving orange zone bar came up, then followed by a cryptic message, with an option to key in the word "help."

What happened here?

What do you think I should do next?

Thanks,
Phil Smith
Duluth, GA

---

### Post by original_jamingrit on 2008-06-25
Hi,
To see what's going wrong, first try to use the Check Disc Integrity option at the LiveCD's boot menu.  Also, were you using Ubuntu 8.10 AMD 64 before, or was it a different flavour?

EDIT: Duoy, I meant 8.04, not 8.10.  Obviously.

---

### Post by Old Jimma on 2008-06-25
Hi and Thanks for your reply...

What I did not do was to do an md5sums check, nor did I burn at 4x or slower.

Nor did I check the forums very carefully.... 

Sorry to be a bother.

Many thanks for your reply, however. I'm grateful for the community.

Phil Smith
Duluth, GA

---

### Post by original_jamingrit on 2008-06-25
Not a bother at all :)

If your disc Integrity test passed, then there shouldn't be any problems with the .iso, but just in case; right click on the iso file (if you still have it) and go to the properties window.  I'm not sure, but this should calculate the MD5sum (it takes a couple seconds).  If it doesn't, find your iso on the command line and type

```
md5sum insert-name-of-iso-here.iso
```

to see if it matches 
```
8a73cf85b04f37d5d91fb436525ea395
``` (taken from here: [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)[MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)

---

### Post by original_jamingrit on 2008-06-25
By the way, when you say that the reinstall failed, do you mean you still have the previous installation untouched?  Or is it lost now?  If it is, what I said above probably isn't very helpful :-(.

---

### Post by Old Jimma on 2008-06-25
Hi Ubuntuers:

I downloaded the amd-64 iso again, did the md5sum check... it mached, and burned it with k3b (burn DVD ISO) @ 2.4x.... so I've ruled that out as the problem.

The error I get after the floating orange thingy is:

[164.779572] buffer I/O error on device sr0 logical block 15572...

or somthing like that, and it repeats and repeats and repeats.

Am I skrewed? I was able to reboot from the HD, so at least that works!

What should I do now to get the herron reinstalled?

THanks,
Phil Smith
Duluth, GA

---

### Post by original_jamingrit on 2008-06-25
I've looked around, and I'm not sure how much help I can be.  It seems that one of the causes of this message is when the disc is dirty.  That's unlikely with two freshly burned discs.  Maybe the drive itself is empty?  It would explain why you're having trouble reinstalling Ubuntu when you've been successful before.

And before trying to burn any more discs, I'd try the alternate-install disc.

Only if nothing else seems to work: There's also some stuff with DMA that might be at fault here.  I don't know enough about it, and [COLOR="DarkRed"]it might be dangerous to fiddle with[/COLOR], but take a look at this page [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA) .But do not act on any of this info unless someone else here suggests to.  I don't know enough about it to say for sure.

Good luck!

---

### Post by Old Jimma on 2008-06-25
Hi Jamin Grit:

My bet is that dirt is at the bottom of this problem. I'll get some new disks, but I agree it is weird. Maybe I should ignore my wife and just get that new duo-core AMD-64 that I've been thinking about. 

Do you think that would work?? :-)

I appreciate your help with this.

Hope I can help with you some time.

Best regards,
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2008-06-26
Here is what worked:

I unplugged my tower and opened the case... it was not very dirty.

I took the case down to the basement and used my air gun to clean it out, and cleaned out the dvd drive, also.

Then I burned the iso again, and it worked.

Thanks for your help, community... dirt is a villain.

Phil Smith
Duluth, GA

---

