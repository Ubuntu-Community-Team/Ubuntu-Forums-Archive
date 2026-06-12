---
title: "Help needed: Adding swap in 12.04"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by xanan on 2012-05-08
I recently dual booted my system to run both Windows 7 and Ubuntu 12.04. As I have 4Gb of RAM, I did not think it was necessary to add a separate partition/ file but I've been told by people that I should have a swap 'just in case'. 
However, I've noticed that my music player Qmmp/Rhythmbox takes an unusually long time to load up my media library (about 40k songs/ 200 Gbs). On an average, it takes about a little over half an hour whereas the same library would scan in less than 2-3 minutes on Windows with Winamp.

Also, the maximum data transfer speed I get while copying file from one drive to the other are in the range of 24 Mb/sec which is about 3 times lower than the windows speed.

I want to know if these issues are because of not specifying a swap. If yes, then I want to know how to add swap WITHOUT having to do a reinstall, if possible. I would also prefer to have a swap file rather than a dedicated partition. Currently, I have windows, ubuntu on the same drive, with about 70gb left on a separate parttion on the same drive. Ideally, the swap file should be located on this partition.

My main use of the system is browsing and listening to Music. I also do a little bit of 2d and 3d rendering, but I'm used to Photoshop and 3ds Max, so I switch over to windows when I need to use these applications.

Please understand that I've been using Ubuntu for over two years, but my usage has been limited to only browsing and listening to music, and so I'm not familiar with terminal at all. Also, the new Unity interface, although nice and different, has thrown me at a loss because I've been used to the mouse-way all this time.

Any help will be appreciated. A lot.

Thanks and regards,
Xanan

---

### Post by prshah on 2012-05-08
> **xanan said:**
> an unusually long time to load up my media library (about 40k songs/ 200 Gbs).

copying file from one drive to the other are in the range of 24 Mb/sec which is about 3 times lower than the windows speed.

I want to know if these issues are because of not specifying a swap. 
Xanan

No, the issues have nothing to do with swap. Rather, I think it is a disk performance issue, though I can't put a finger on it.

Adding swap will not help you, in this case. With 4GB of RAM, you don't need it, not unless to plan to use hibernate.

---

### Post by xanan on 2012-05-08
> **prshah said:**
> No, the issues have nothing to do with swap. Rather, I think it is a disk performance issue, though I can't put a finger on it.

Adding swap will not help you, in this case. With 4GB of RAM, you don't need it, not unless to plan to use hibernate.

I was of the same opinion, but this performance hit has come only after the I moved from 11 to 12.04. My drives perform normally in Windows 7, and also in the older distro- it is only with the 12.04 that I'm noticing slower seek/read /write issues.

Is this a known issue or something else?

---

### Post by Enigmapond on 2012-05-08
Qmmp/Rhythmbox are lousy for large libraries. I have about the same amount of files, about 200GB and I found that Guayadeque handles it best. You need to add his PPA to install it.

---

### Post by kurt18947 on 2012-05-08
You could run system monitor or better in my opinion, install htop from the repositories and run it in a terminal. Htop is much lighter though more limited than system monitor.  See how much RAM is being used by programs, not cached.  My guess is you're not RAM limited.  If a system has 512 Mb. or less RAM installed it's a different story, a swap partition is pretty much mandatory. 

You could also create a swap *file*, rather than a swap partition.  The only time you must have a swap *partition* is if you want to use hibernation/suspend-to-disk.  A hard drive can have 4 primary partitions without tricks.  I choose to not use 1 of the 4 for a swap partition and AFAIK swap cannot be a volume in an extended partition.  Here's a guide if you want to go ahead and create a  swap partition:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

This also contains a guide for creating a swap file if you choose to go that route.

---

### Post by lukeiamyourfather on 2012-05-08
I would say the issue is probably not from lack of a swap partition because the system will never use the swap until it runs out of memory. In your case if that happens it would simply halt since no swap exists. What filesystem are you using for the music library? If using a non-Linux native filesystem like NTFS that can cause poor I/O performance.

---

### Post by xanan on 2012-05-08
First of all, please accept my thanks, all of you. 

@enigmapond. Thank you for recommending Guayadeque. I had initially ignored this as I was looking for something similiar in look and feel to Winamp, but this is so much better than Qmmp. My media library was imported in less than 2 minutes and I absolutely love the smart play feature. Really helps when I'm too drunk to make a playlist. Thank you so much.

@kurt18947 Thank you for the link. I'm fairly sure I'm not RAM limited. Apparently, it was the media player at fault but I think lukeiamyourfather is right about ntfs causing the performance hit. However, this is happening to me only after the upgrade to 12.04...maybe I need to do a clean install. Will post back if that makes any difference.

I will also install htop just to confirm if I'm RAM limited or no, and make a swap file as well. I do not EVER put my system on hibernate/suspend. I make it a point to turn it off because I do not like wasting electricity. As it is, I live in a country where power cuts are quite frequent so i guess every little bit helps :)

Once again, thank you all. You're the best.

OT: What's your take on Unity though? I find it a nice change over the menu driven desktops we are so used to seeing, though the change can be a disorienting one, as I can vouch from personal experience.

---

### Post by Enigmapond on 2012-05-08
Cheers! Welcome to the forum. Please mark this thread as "Solved" in the Thread Tools above...as I think the media player has solved the issue. With 4GB RAM unless you are doing a lot of video rendering or something, you don't even need swap.

---

### Post by Cheesemill on 2012-05-08
> **Enigmapond said:**
> Qmmp/Rhythmbox are lousy for large libraries. I have about the same amount of files, about 200GB and I found that Guayadeque handles it best. You need to add his PPA to install it.

+1

Guayadeque is by far the best application for handling large music libraries.

---

### Post by Cheesemill on 2012-05-08
> **xanan said:**
> OT: What's your take on Unity though? I find it a nice change over the menu driven desktops we are so used to seeing, though the change can be a disorienting one, as I can vouch from personal experience.

When Unity first appeared I didn't find that it was polished enough for my use.
I switched to Gnome Shell instead and have never looked back.

---

