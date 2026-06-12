---
title: "Backing out updates"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Jaoqua on 2008-08-14
Hi, I recently added the Medibuntu repository to Synaptic in a (failed, as it happens) attempt to install Adobe Reader. Later that day I had a set of updates to install, which I accepted, but it was only as they were installing that I noticed they were all Medibuntu ones. I immediately removed Medibuntu from Synaptic, but how can I back out those updates?

(BTW I usually use Evince Document Viewer, but I'd really like a simple tool to search through the text of a folder full of pdfs, and I can't find a free one. Hence downloading Adobe Reader. Any ideas?)

---

### Post by kostkon on 2008-08-15
> **Jaoqua said:**
> Hi, I recently added the Medibuntu repository to Synaptic in a (failed, as it happens) attempt to install Adobe Reader. Later that day I had a set of updates to install, which I accepted, but it was only as they were installing that I noticed they were all Medibuntu ones. I immediately removed Medibuntu from Synaptic, but how can I back out those updates?

(BTW I usually use Evince Document Viewer, but I'd really like a simple tool to search through the text of a folder full of pdfs, and I can't find a free one. Hence downloading Adobe Reader. Any ideas?)
Why you don't want to have these updates?!

---

### Post by ibuclaw on 2008-08-15
Medibuntu is a trusted repository, it is safe to install the packages from it.

What are you trying to do with Adobe Reader?

If you wish to view pdf documents in your browser, install the acroread-plugins/mozilla-acroread packages.

```
sudo apt-get install acroread-plugins mozila-acroread
```

If you were trying to view pdf's on your hard-drive, then you might have to change the "open with" properties on that file.
If it doesn't show up, just search for acroread in your /usr/bin folder.

Regards
Iain

---

