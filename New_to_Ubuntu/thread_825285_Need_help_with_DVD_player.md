---
title: "Need help with DVD player"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by squirrley on 2008-06-10
I just got a used IMB Thinkpad A31 2652 p3u, and put 8.04 on it.  I'm trying to get DVDs to play properly.  I followed the steps in the [Comprehensive Multimedia/Video]("http://ubuntuforums.org/showthread.php?t=766683") thread, but whenever I try to play a DVD in VLC, its horribly garbled.  Is this a codec issue?


Any advice for a newb?

- Squirrley

---

### Post by Joeb454 on 2008-06-10
Can you try running ```
sudo apt-get install libdvdcss2
sudo /usr/share/doc/libdvdread3/install-css.sh
```

One line at a time :) I don't know if that was covered in the thread, I didn't read it :p

---

### Post by squirrley on 2008-06-10
Whoops, I meant Totem.  VLC would just crash.

I ran those two, and I got "libdvdcss2 is already the newest version."

and 

"dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1."

Now, in totem, its not garbled at all, it just plays really.... really... r e a l l y   slow with no sound. :/

---

### Post by Joeb454 on 2008-06-10
Was the bottom part the output from running the 2nd command?

And I've never messed with medibuntu repo's - so I can't be of much more help, all I know is that's what I did to get DVD playback :)

---

### Post by Linux_Man on 2008-06-10
Are you installing from the official Ubuntu repos or third-party ones? If it is third-party please tell us the site so we can better help you.


EDIT: Never mind, I read the guide and it said which repositories you were using.

---

### Post by squirrley on 2008-06-10
I'm not entirely sure.  I followed what was in that thread.

I haven't started using this comp much yet, maybe a clean install?

---

### Post by Joeb454 on 2008-06-10
That's your choice - not mine :) I'm sure there's a way to get it working without needing a reinstall though :)

---

### Post by squirrley on 2008-06-10
I'll try a bit more, but I don't have anything set up yet, so I don't really mind re-installing.  (assuming that would fix the problem =P)

So what exactly is a repository, and how does it work?

---

### Post by squirrley on 2008-06-11
Well, I got a movie(.avi) off my desktop(xp), and it plays at the same 1 frame a second type of rate.  I'm wondering if its a video card driver issue?

I think I have an ATI Mobility Radeon 7500, but I'm not entirely sure.  How can I see what I have, and/or other system specs?

---

