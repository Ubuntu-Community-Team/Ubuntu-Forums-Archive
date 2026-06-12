---
title: "Thinking of converting another machine to Ubuntu - is it a good candidate?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by ewangr on 2012-04-10
Have been fighting some SAMBA issues for a couple of days, and am starting to think the "easy" answer would be to switch my downstairs computer to Ubuntu as well. 

Computer is an Acer AspireRevo AR3700-U3002 ([http://www.amazon.com/Acer-AspireRevo-AR3700-U3002-Compact-Desktop/dp/B00433SP6G](http://www.amazon.com/Acer-AspireRevo-AR3700-U3002-Compact-Desktop/dp/B00433SP6G)). Key features are a 64-bit version of the Atom chip, Nvidia ION-2 graphics, and that I've upgraded it to 3 gigs of RAM.

If I did convert it, then I presume I could use NFS and stop all the SAMBA worries. My concerns are:

1) Since my current machine and this one are sharing external disks that are NTFS formatted, each disk is 4TB and has 1.5TB free, and therefore reformatting is undesirable, will I even be able to use NFS (i.e. will I have issues getting NFS and NTFS to play nice).

2) It took me a long (!) time to find a setup that plays almost all the videos I throw at this machine. It is connected to our 42" LCD TV as it's main monitor, and so serves as a sort of HTPC. Will Ubuntu be better/worse for playback.

3) Given the chipset, anything here that might be a concern for drivers?

Thanks in advance for your advice!

---

### Post by Mark Phelps on 2012-04-11
There are so many hardware difference between machines that it's simply not possible to know in advance how well Linux distros will run on a particular machine.

Sorry for the roundabout answer, but unless someone else has already installed Ubuntu on that very same machine, the only way you'll really know is to burn a LiveCD, boot the machine from that, and try it out.

---

### Post by anejo on 2012-04-11
Is a bootable USB an option? Or booting with a live-CD?
That way you would quickly determine what's works...
I travel with a 8GB usb "parasite pc" as I call it... and troubleshoot all kinds of older hardware mostly running XP, and it still amazes every time I use it that it works and I find another potential customer to convert.

---

### Post by ewangr on 2012-04-11
Appreciate the concerns, and I may try a live USB (no CD slot). While I wasn't thinking there would be many Acer Aspire folks necessarily checking this out, I was thinking that the main 3 items might be reasonably common:

Atom 2 chip (i.e. 64-bit Intel Atom)
nVidia Ion 2
NTFS external drive

So it comes down to whether the restricted nvidia driver can support the Ion 2 (can I even specify that from a live USB), and can you setup NFS to run on an NTFS-formatted drive? I'm sure I can test base functionality from the live USB, but I'm not sure I can test those two things without going ahead and doing a full install.

If someone has something even somewhat similar, I'd like to hear the story. Otherwise it will be something for my "try it list" later this week.

---

### Post by ewangr on 2012-04-15
OK, so I did the live USB boot, and quickly ran into issues where it wanted to load other items to be able to give full functionality. So ended up having to jump in with both feet and hope for the best.

Install went fine, but by default the screen resolution leaves a bit of a noticable overscan. I later did some work on that ([http://ubuntuforums.org/showthread.php?t=1957677](http://ubuntuforums.org/showthread.php?t=1957677)) which improved the UI but impacted performance. Ideal situation would be if I could adjust in the TV, but my particular setup forgets your choices once you turn the TV off...

In general things are as easy or easier than with windows (Network printer never worked under windows, does under Ubuntu). I did have to stick with SAMBA since I still have two Windows clients, an iOS client, and a couple Android clients - none of which seem to offer good NFS support. Setting up SAMBA was a bit more of a challenge than expected, but once I resigned myself to using Fixed IPs was not too horrible.

Overall I would say the combination of the 64-bit Atom and ION-2 are well supported under Ubuntu, and performance is worth the hassle.

---

