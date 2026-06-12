---
title: "Access Ubuntu 12.04 remotely from Android Tablet"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by ewangr on 2012-04-09
I have used Ubuntu before, but not for some time. Just installed 12.04 beta 2 64-bit yesterday. I am aware of VNC, but not sure which version might work best with which Android application? Is there anything like PocketCloud or LogMeIn where I don't have to spend half a day poking holes through firewalls and configuring my wireless router and cable modem?

Main use case is that something acts up and I need to provide support for my home (read wife or daughter) users. Secondary use case is so I can start downloads of things to watch when I get home in the evening.

Thanks.

---

### Post by migs73 on 2012-04-09
I believe teamviewer is available for both Linux and Android, and should do what you require, although I haven't tried it my self (I might though for the same reasons as you!!).

Good luck

[http://www.teamviewer.com/en/download/index.aspx](http://www.teamviewer.com/en/download/index.aspx)

---

### Post by ewangr on 2012-04-09
Thanks for the suggestion. It was interesting to see that you click on the DL for the 64-bit Deb, and it opens the Software Center so it's a registered install. While I prefer things to come directly through the repositories, I think this is a pretty slick alternative.

Now to see how well it actually performs! :-)

---

### Post by kevdog on 2012-04-09
Are you looking for a gui or terminal program?  Connect bot is always a good ssh terminal program.

---

### Post by ewangr on 2012-04-09
> **kevdog said:**
> Are you looking for a gui or terminal program?  Connect bot is always a good ssh terminal program.

Reasonably sure that to do what I've mentioned it would have to be a GUI. With an SSH terminal I would end up effectively downloading to my tablet wouldn't I? For the support use case that "might" work but it would depend on whether I needed to see what was happening on the machine or could just pick it up from the log files...

---

### Post by migs73 on 2012-04-10
Let me know how it goes, as I said I would be interested myself.
Mike.

---

### Post by ewangr on 2012-04-10
TeamViewer works pretty well. The DEB file at the site will download through the Ubuntu Software module so it configures itself fine. The Android client is free, but you do have to register it (free, but requires name and email).

Having done that, it seems most like LogMeIn in terms of the interface and that you move the pointer rather than move the screen.

I wouldn't try to play a video while connected, but it certainly works well enough.

---

### Post by migs73 on 2012-04-11
thanks for reporting back. I know what I'll be doing tonight!

If you could now mark the thread as solved 

See here for instructions [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Mike

---

### Post by skabople on 2012-04-11
ssh -X username@host. Enable X11 forwarding and use the terminal vs connect bot with busybox ;)

---

