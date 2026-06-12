---
title: "&quot;The specified location is not mounted&quot; problem between 14.04lts and 14.04 server."
date: 2015-04-25
forum: New to Ubuntu
---

### Post by bengy103 on 2015-04-25
Hi All,

I have to transfer files from my Ubuntu 14.04 server in the attic to a second hdd on my office machine running ubuntu 14.04, over my little domestic 10MiB wired network.
I can't copy and paste because paste is not available to me at the destination on a right click.
I can't drag and drop because of the message in the header bar.
I know it's mounted because I unmounted it and then re-mounted it. It's at /media/dad. I did a sudo nautilus to change properties to ME so I reckon I should have rights to do whatever I please here.

I don't remember this problem with 12.04, and I'm sure I did this transfer on 12.04 in the past.

Can anyone help here, preferably without having to edit files, to enable this transfer please.

I have googled the above message but come up with nothing that seems to have anything to do with this problem. The "Check if Already Posted" didn't show anything either.

regards,

brawd.

---

### Post by dino99 on 2015-04-25
installing x2go for remote job

[https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/](https://www.howtoforge.com/tutorial/x2go-server-ubuntu-14-04/)

---

### Post by bengy103 on 2015-05-07
Hi all,

I tried to install x2go but the server could not find the repositories. It also was getting stuck at the initramfs bit of the bootup procedure. The solutions for this that I've looked at via Google seem pretty horrendous and have plenty of scope to trash my server. Anyway I can get around this by repeatedly pressing the reset button on the server until eventually it completes the boot sequence. Just to make matters worse my everyday machine started to corrupt letters, particularly 'S'. All in all my home network was in a mess.

I chose to redo the entire setup, even with my reservations about Ubuntu 14.04 LTS.

I was not able to download my files from the server to another Ubuntu machine but I could download to Windows machines, so that's what I did.

Once that was done I used Hiren's boot disk to wipe my server, then used the Youtube to find the Urban Penguin and Goguda55 to re-install the server in a Raid 1 array and at this time I'm sending my files back from the Windows machines to the server. I still have difficulties with it getting stuck at Initramfs but now I've got it up and don't intend to switch it off anytime soon.

I re-installed Ubuntu 14.04 to my everyday machine and I still have problems with corrupted characters on screen, though it no longer seems to target 'S' in particular, instead it seems to corrupt characters in a more random fashion. I suspect that this may be due to my motherboard sending me a warning that it's about to give up the ghost, or it just doesn't like Ubuntu 14.04 LTS. I don't intend to replace my motherboard so if it gets much worse I'll try a Ubuntu 12.04 LTS, both on the server and my everyday machine as I think it would be too coincidental that both machines have components that fail at the same time.

It's not a satisfactory outcome by any means but it is working - sort of.

If it all fails then at least I still have the files on the Windows machines which sort of defeats the purpose of having a server in the first place.

I also noticed under 14.04 that its a lot more difficult to link my two printers from the server to Ubuntu machines. My old HP Laserjet shows on screen but won't actually print, just leaving my Canon Pixma to do all the work, a more expensive print option for Black and White than the Laserjet.

To be honest even as I type this I'm thinking of wiping everything off both machines and going back to 12.04 LTS.

regards,

brawd.

---

