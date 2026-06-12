---
title: "xmodmap: key &quot;back&quot; becomes &quot;ctrl+pgdn&quot;?"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Jmob on 2012-08-21
can use xmodmap some, but not clear on this.  Can I bind a key so that its default press is the ctrl+press of another key?

Specifically, want to make the fwd and back keys on my laptop--inconveniently placed near the cursor keys so you accidentally leave the webpage with some text you were editing--with ctrl+pgup and ctrl+pgdn.  Those two function as tab switch in firefox, but the pgup and pgdn keys are hard to reach on my keyboard.  

xev returns state = 0x0 for pgdn, and state = 0x4 for ctrl+pgdn.    That's the only apparent difference.  However, I don't know how to use this in xmodmap or any other program.  Is there a way to do this?

---

