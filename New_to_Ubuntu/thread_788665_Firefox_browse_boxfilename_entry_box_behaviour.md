---
title: "Firefox browse box/filename entry box behaviour"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by KIAaze on 2008-05-09
Hi,

This is a problem that has been bothering me for some time now:

Previously with Firefox2, when I clicked in a "filename entry box", it behaved like a text entry box, and I could juste type/paste text into it.

Now, in Firefox 3, when I click in a "filename entry box", it automatically opens a browser winwow! WHY?

Can I deactivate this "feature" somewhere?

---

### Post by dbstraffin on 2008-05-10
It seems to be a security feature.  Mozilla developers seem to be worried that a web site could hide and fill in the textbox without the user knowing to upload a file. I didn't see any way of disabling it in about:config.  Read here: [https://bugzilla.mozilla.org/show_bug.cgi?id=258875]("https://bugzilla.mozilla.org/show_bug.cgi?id=258875")

---

### Post by KIAaze on 2008-05-10
Thanks for the info.

I tried the [exploit example]("https://bugzilla.mozilla.org/attachment.cgi?id=17860&action=view") in there and it's indeed pretty scary how you can be fooled into copy/pasting a wrong text.
People might be aware about standard e-mail phishing, but somehow people always come up with new exploits.

The browser being a bit slow to load, I hope they find better solution.

---

