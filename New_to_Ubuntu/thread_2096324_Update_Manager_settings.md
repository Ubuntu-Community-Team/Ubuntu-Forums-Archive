---
title: "Update Manager settings?"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-19
Are these update manager settings correct?

Thanks.

---

### Post by Pjotr123 on 2012-12-19
They are right, but I advise to disable all source code (useless and only slows things down a bit) and to *enable* Partners.

---

### Post by Yezinki on 2012-12-19
Thanks Pjotr123 for the reply.

Source code is only checked for Other Software > Independent > Provided by 3rd party software developers......correct or any more?

What exactly do you mean by enable Partners?

---

### Post by Pjotr123 on 2012-12-19
Tab Other software - tick Canonical Partners. Some useful stuff in there. 

Source code: there's also a "semi" tick (dash in the check box) for source code on the main tab (Ubuntu software). You can safely remove that as well, thus rendering the update process a little faster.

---

### Post by Yezinki on 2012-12-19
Is this better/fine?

---

### Post by Frogs Hair on 2012-12-19
Do you need unsupported updates ? I use proposed because they end up as supported most of the time but I have never used backports.

---

### Post by Yezinki on 2012-12-19
Thanks Frogs Hair for your comments.

> Do you need unsupported updates ? I don't even know what they imply technically but are checked by default??

```

 I use proposed because they end up as supported most of the time but I have never used backports.
``` Should I check them?

---

### Post by Frogs Hair on 2012-12-19
Strange, I've never seen that before. It could be that some software you have installed requires unsupported updates. It has been recommend in the past not to enable them because they may break the system.

Proposed updates can sometimes include bug fixes that make it into official updates but it is not necessary to check the box.

---

### Post by Yezinki on 2012-12-20
Thanks again. It's a new install, could the unsupported updates be checked by default after install, cause of unsupported drivers for WiFi, BT or webcam?

---

### Post by Pjotr123 on 2012-12-20
NEVER enable Proposed, unless you're an intrepid bug hunter on a test machine:
[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Don-t-turn-on-the-software-repository-proposed-](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-Don-t-turn-on-the-software-repository-proposed-)

Otherwise your system WILL break, sooner or later. It's highly irresponsible to advise people to enable Proposed just like that. :shock:

By the way: I advise to disable the *source code* for Partners and Independent as well (each has two entries, one of them is the source code). Useless, unless you're a software developer and need the source code....

---

### Post by Yezinki on 2012-12-24
Thanks Pjotr123 does this look ok to you?

---

