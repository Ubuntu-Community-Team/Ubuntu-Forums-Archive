---
title: "Dolphin forgets copied content"
date: 2014-11-03
forum: New to Ubuntu
---

### Post by kyrawertho on 2014-11-03
Hello,

I have a strange and annoying problem. If I copy or cut a file in Dolpin, then close the window and go where I want to drop my file, it's impossible to paste.
If I keep the source window open, pasting is possible... It there a fix for this problem or are there any file managers that do handle copy/pasting correctly?

Thanks/

---

### Post by deadflowr on 2014-11-03
Not sure.
Where are you trying to paste, and are you right clicking paste or have you set a mouse gesture to click and paste?

I just looked at this, and I opened Dolphin, copied a file, then closed dolphin, then opened kate, konsole, and a web browser tab and was able to paste into all three without problems.

Edit: I should point out that this is Kubuntu 14.04(trusty)

---

### Post by kyrawertho on 2014-11-03
I'm using both ctrl+x/c/v and right click. Also, I just noticed it's the same for every program. If I copy a text in kate, for example, I can't paste this text after closing kate.

---

### Post by yancek on 2014-11-03
The behavior you describe is definitely not the expected behavior and I don't have any problem doing what you describe using dolphin.  Have you made any changes recently?  Is this a new install?  Kubuntu?  Did it work previously?

---

### Post by kyrawertho on 2014-11-03
It's a new install and I think this problem has been around since the beginning. Obviously I have done some tweaking/installing/deleting after the install so I couldn't say exactly what I did then. I did remove clippy/clipper or something but I imagine copy/paste should be a basic function that should work without having to install extra software.

---

### Post by marco-parillo on 2014-11-03
I tested copying or cutting, closing the application,  and pasting text to this post, using rekonq on a pretty stock Kubuntu 14.10 installation. All worked with text from

Firefox to rekonq (ctrl x > ctrl v)
Chrome to rekonq  (ctrl c > ctrl v)
Konsole to rekonq (edit copy >  ctrl v)
Kate to rekonq (ctrl x > ctrl v)

---

### Post by kyrawertho on 2014-11-05
I found out it's a known Ubuntu bug: [https://bugs.launchpad.net/ubuntu/+bug/106644](https://bugs.launchpad.net/ubuntu/+bug/106644) and [https://bugs.launchpad.net/ubuntu/+bug/11334](https://bugs.launchpad.net/ubuntu/+bug/11334). I just had to find the right Google keywords :)

Anyway, reinstalling klipper should work so I'll try that one again.

---

