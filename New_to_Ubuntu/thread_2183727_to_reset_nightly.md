---
title: "to reset nightly?"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by Matrix01 on 2013-10-26
how do u reset Nightly?

---

### Post by Skyline_8650 on 2013-10-26
Do you mean restart? You don't have to restart nightly, bi-monthly would be overkill! If you mean reset the OS to a fresh install state, the quickest way I know of would be via disk cloning or images.

---

### Post by newb85 on 2013-10-26
If you give us more details about what you need, we can give you better advice.

---

### Post by Matrix01 on 2013-10-28
[ATTACH=CONFIG]247323[/ATTACH]

there's no reset button in Nightly.

---

### Post by newb85 on 2013-10-28
Ahh, you have Firefox installed from the Nightly Builds source, and you can't find the Reset Firefox button.  That was not at all apparent from your first post.

Apparently, that missing button is a bug.  [https://bugzilla.mozilla.org/show_bug.cgi?id=749700](https://bugzilla.mozilla.org/show_bug.cgi?id=749700)  They're working on it.

The presence of a bug should come as no surprise, since you are using a browser from a testing source, though.

---

### Post by Matrix01 on 2013-10-29
when i move a scroll bar with a mouse pointer,  a grey line which is an inch wide, flashes.

---

### Post by newb85 on 2013-10-29
If this is connected to your problem with Firefox, it should really be taken up at the bug tracker I linked in my post.

If it's a separate problem, it really should be put in its own thread with an appropriate (and descriptive) title.

---

### Post by Matrix01 on 2013-11-13
> **newb85 said:**
> If this is connected to your problem with Firefox, it should really be taken up at the bug tracker I linked in my post.

If it's a separate problem, it really should be put in its own thread with an appropriate (and descriptive) title.

i clicked your link.
how do u fix this bug?

---

### Post by newb85 on 2013-11-13
If you're referring to the missing reset button, you really can't fix it.  You could switch to a more stable branch of Firefox, where it's not missing, or you can wait for the developers to fix the missing reset button bug, which doesn't look like it's going to happen any time soon.

If you don't care about the button, you just want to fix the glitchy behavior, the easiest way to reset is probably to simply create a new profile using the Profile Manager.  More info on that can be found here.  [https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

---

### Post by Matrix01 on 2013-11-14
after this netbook is restarted, 
profile manager did not appear yet.
how do u install stable one?

---

### Post by newb85 on 2013-11-14
It should be in the Software Center.  What Lubuntu release are you using?

---

### Post by SantaFe on 2013-11-14
If you mean reset nightly, like the photo below, either click on help/Troubleshooting Information.... or just type about:support in the address field.

Sure looks like there's a button there in the upper right to me. ;)

Of course, I just upgraded to 28.a1 right before I took the screenshot, so maybe it's been fixed? ;)

---

### Post by thesleash on 2013-11-15
use cron

---

### Post by newb85 on 2013-11-15
> **thesleash said:**
> use cron

Had you read a few posts in  this thread, you'd have known that nightly is the branch of Firefox the OP wants to reset, not the frequency with which they wish to reset.

---

