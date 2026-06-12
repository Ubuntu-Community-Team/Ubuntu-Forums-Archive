---
title: "HOWTO: Save Streaming Videos with MPlayer"
date: 2008-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by edmondt on 2008-04-18
1. Copy the url of the streaming video mms://etc... or [http://.](http://.)..
2. Open up a terminal.
3. mplayer -dumpstream -dumpfile stream_video_name.wmv mms://etc...
4. Wait for the stream dump.

enjoy :popcorn:

---

### Post by libihero on 2010-01-05
how to u put your username and password if its required?

---

### Post by andrew.46 on 2010-01-05
Hi libihero,

> **libihero said:**
> how to u put your username and password if its required?

Looks like you would need to use:

```
mplayer -user *[COLOR="Red"]your_username[/COLOR]* -passwd *[COLOR="Red"]your_password[/COLOR]* etc etc 
```

I am not completely sure if this will work with every stream that requires authentication but it is certainly the syntax available to MPlayer...

All the best,

Andrew

---

### Post by libihero on 2010-01-06
i'm having trouble downloading the link because when i normally access the file i have to put my password twice
i can save the streaming link on my computer as a .asx file.  how do i make mplayer save a file that initiates streaming saved on my computer?

---

