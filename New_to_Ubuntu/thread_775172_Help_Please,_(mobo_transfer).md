---
title: "Help Please, (mobo transfer)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Ballping on 2008-04-29
Hello all.

Kinda a long story, i'll try and be brief, sorry. :-(

I installed Ubuntu on a dual boot system and was battling with attempting to get my drivers installed on it when my mother board died on me. I was in the process of building a new system so i went ahead and finished building it with my two hard drives.

Changes i made:

Brand new Motherboard and Memory, brand new processor, and brand new GFX card.

I've managed to get windows XP working and updated on my new setup, however Ubuntu will not boot for me. I keep getting an error message:

ata 4.00 (or ata 6.00): failed to set xfermode (err_mask = 0x40)

Sometimes i get this message that follows, sometimes not:

Buffer I/O error on device fd0, logical block 0

These messages will repeat several times and then Ubuntu will continue to boot. Eventually it will get to the point where it says that its loading device graphics (or something to that effect, can't remember exactly) When it gets to this point an error screen will show up saying:

Failed to start x-server, it is likely that it is not setup correctly.

I thought i'd go ahead and just attempt to re-install Ubuntu, however when i load up the Ubuntu Live CD to attempt this i get the ata 6.00:failed to set xfermode (err_mask = 0x40) error and then the install program will kick out.

Could someone please help explain this problem to me and give me what steps i can take to resolve this or would i be better off formatting the partitions from windows and attempting the re-install on clean partitions?

Thanks.

---

### Post by bilal.17 on 2008-04-29
since you completely changed you mobo, etc. Try from the liveCD and if it works i'd advise for you to do a fresh install.

---

### Post by iSplicer on 2008-04-29
I suggest that you make a full clean re-installation on all partitions just to be sure. But if you want to try and fix your XServer, boot into recovery mode and type:

sudo dpkg-reconfigure xserver-xorg

Good luck!

---

### Post by Ballping on 2008-04-30
Well unfortunately neither step worked for me. the reconfigure xserver ended in some weird random errors, and when i attempted a clean install i got the same errors i was originally getting. IE:

ata 4.00: failed to set xfermode (err_mask = 0x40)

and

Buffer I/O error on device fd0, logical block 0.

Anyone have any ideas on how i can fix this? I'm about ready to pull my hair out heh.

Thanks.

---

### Post by Ballping on 2008-05-01
Well I've been playing around with this a bit more, i haven't really gotten any further with it but i think i'm getting closer to the answer about whats going on.

I went through and deleted the partitions i had Ubuntu on. After i did that i got a little further with the live CD. The two errors went away but i still got the "Failed to start x-server" error. I attempted to run the "Sudo dpkg-reconfigure xserver-xorg" fix and after i was done with that the install restarted and boom, i got the 2 errors again, so this leads me to believe that I'm doing the settings in the dpkg wrong. Specifically i'm thinking i'm entering the PCI settings for the video card.

My question is where would i find the correct settings to plug into the dpkg thing if this is indeed my issue. If it's not could someone please point me in the right direction?

Thanks.

---

### Post by Ballping on 2008-07-24
Well after months of trying to get this to work i finally think i found whats going wrong. Apparently Ubuntu doesn't support the IP35 chipset that my new mobo runs so it looks like i'm SOL. 

It makes me sad because i really wanted to get into Linux but unfortunately it doesn't look like Linux is keeping up with the advances of hardware fast enough. :-(

---

### Post by kansasnoob on 2008-07-24
It certainly appears that you're correct:

[http://www.linux-mips.org/wiki/IP35](http://www.linux-mips.org/wiki/IP35)

I always check compatibility before buying any hardware. I especially search for actual user reviews.

---

