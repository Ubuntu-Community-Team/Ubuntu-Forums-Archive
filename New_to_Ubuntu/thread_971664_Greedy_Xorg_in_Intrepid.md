---
title: "Greedy Xorg in Intrepid"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by pzs on 2008-11-05
Since upgrading to Intrepid, I Xorg grabs all of one of my cores for 2 or 3 seconds about once every 10 seconds. When it does this, I get lag when typing in web dialogs (like this one) and other slow downs.

Is anybody else having this problem? Is there a way of finding out in more detail what it's doing?

---

### Post by stephanvaningen on 2008-11-05
1 - Do you find any specific messages in the Xorg.0.log (see System -> Administration -> System Log)?
2 - Which video card?

---

### Post by pzs on 2008-11-05
A few messages like this:

```

AUDIT: Tue Nov  4 15:01:23 2008: 5918 X: client 4 rejected from local host ( uid=0 gid=0 pid=6119 )

```

But no messages today. I haven't rebooted since yesterday.

My video card is an nVidia Quadro NVS 290 (rev a1). I did wonder if the new proprietary driver might be causing the problem. I'm using the Nvidia driver revision 177 where before I was using revision 173.

---

### Post by pzs on 2008-11-05
OK, I've figure it out. It turns out that as well as me upgrading my machine yesterday, there was also some kind of election. Since the BBC web page, my home page, is now carrying a huge flash-based slide show on its front page, my machine has to cycle through these pictures every 10 seconds, which is apparently rather resource intensive.

:oops: Talking about not seeing the wood for the trees...

---

### Post by stephanvaningen on 2008-11-06
> **pzs said:**
> :oops: Talking about not seeing the wood for the trees...
No probs ;-)
--
If all is ok now, you can mark this as complete *(right-top of page: thread tools -> mark this thread as solved)*

---

