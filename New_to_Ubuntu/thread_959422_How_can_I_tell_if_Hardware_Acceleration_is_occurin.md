---
title: "How can I tell if Hardware Acceleration is occuring?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-10-26
I am running Ubuntu 8.04 with a Radeon 9600 card.  I am using the restricted drivers per the icon on my bar, but when I use Totem, the movies, etc are still pretty blocky, especially in full screen mode.

I went to the ATI website and downloaded the latest .RUN file.  Before I install it, I want to see if it is necessary, and also if anyone else has gone through it and how easy or nightmarish it was.  It mentions removing the proprietary drivers, etc.

Oh yeah...do I need a separate DVD codec for the movie player?  I popped in a DVD the other day and it wouldn't play.  It was the first time I had used a DVD so I wasn't sure.

Thanks in Advance

---

### Post by cariboo on 2008-10-26
I'm not sure about your video driver but the ATI drivers seem to be a work in progress.

To enable DVD playback you need libdvdcss2 the file is available from the Medibuntu repositories, go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and follow the instructions for adding the Medibuntu repositories, be sure to scroll to the bottom of the instructions to download the Medibuntu keys.

Once you have updated the menu.list, open synaptic and search for libdvdcss2 and install it. You should now be able to play DVDs.

Jim

---

### Post by J0hnnyBr@v0 on 2008-10-26
Thanks for the heads up.  I'll give the DVD playback a try....

---

### Post by J0hnnyBr@v0 on 2008-10-26
Jim,

I did exactly what you suggested and still won't play DVDs.  Are there other dependencies required?

When I explore the DVD in the Video_TS folder, it is empty, it doesn't see any of the VOB's or IFOs.

Any other suggestions?

Thanks

---

