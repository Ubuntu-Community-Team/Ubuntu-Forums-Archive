---
title: "[SOLVED] What command in terminal do I use to make a file executable?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-13
I've got this error coming up on someones computer and I'd like to be able to tell them how to fix it with one command in Terminal.  Here's the error:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69960&stc=1&d=1210724134[/IMG]

---

### Post by JoshuaRL on 2008-05-13
Did this person add themselves as a VM user in Users and Groups?  It might be that simple.

---

### Post by drs305 on 2008-05-13
nevermind, I just answered the title:
```
chmod a+x <filename>
```

---

### Post by vexorian on 2008-05-13
Try virtual box.

vmware apparentally is amazingly hard to setup.

---

### Post by diablo75 on 2008-05-13
> **vexorian said:**
> Try virtual box.

vmware apparentally is amazingly hard to setup.

Personally, I could say the same about Virtual Box from my own experience, though I should give it another try.  I've used VMware for a while now and am very familiar with it's quirks.  This error kind of puzzled me because I set the software up for this person completely, and had no problem starting up a virtual machine that he had made a long time ago.  We just had to reinstall VMware after the upgrade to 8.04 because the VMware people haven't yet updated their code to take advantage of the latest kernel.  Starting it up from terminal as well as from the Applications menu did not produce an error.  Often times, he'll fiddle with something afterwards and not tell me what he did....

---

### Post by JoshuaRL on 2008-05-13
Well, at least you got it fixed.

Kind of stormy looking outside your window huh?

(I live there too.)

---

