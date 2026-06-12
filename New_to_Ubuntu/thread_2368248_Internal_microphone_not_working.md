---
title: "Internal microphone not working"
date: 2017-08-08
forum: New to Ubuntu
---

### Post by shubanshii on 2017-08-08
Hi there,

My laptop is an ASUS X550LA.  I'm running Ubuntu 17.04 on a partitioned hard drive. My internal microphone is not working.  When I click sound and go to the input section, the input level is empty.  

Can anyone help me?  Just had a Skype chat on Windows, so the microphone is definitely still functioning.

---

### Post by #&amp;thj^% on 2017-08-08
Open a terminal type:
```
 sudo apt install pavucontrol
```
Then just run it, and your microphone should show up there.

If your microphone shows up under "Input Devices"  but you're still not getting any sound, unlock the channels, and drop one of them down to zero. This worked for me, hope it helps you!

---

### Post by shubanshii on 2017-08-08
Just tried it and no luck.  It's weird.  There's a small amount of orange, and it subtly vibrates, but it doesn't increase at all when I actually talk.

---

### Post by #&amp;thj^% on 2017-08-08
Did you try unlocking the channels and slide one down to 0
See the Screenshots.

---

