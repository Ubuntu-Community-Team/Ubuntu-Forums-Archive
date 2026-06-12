---
title: "[SOLVED] Ebook Download problems"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by zaivala on 2008-07-17
I participated in a trial at my company, to see how well the new order system worked.  Well, the order system worked fine, but I got a download error, something that said "the associated helper application does not exist."  It was a PDF file being downloaded... apparently the program running the download was looking ONLY for Adobe Reader.

Any clues what I can do about this?  Screenshot attached

Hugs,
Moss

---

### Post by RomeReactor on 2008-07-17
Hi. Try saving the file instead of trying to open it; you can then double click the downloaded file to open it in Evince. Or you can configure Firefox to open the files in Evince (in 'Edit->Preferences->Applications' search for PDF and choose **Use document viewer**).

---

### Post by zaivala on 2008-07-17
Not an option, apparently this whole system is automatic.  I think that is controlled by PayPal.

I did get my boss to change it to where the buyer has 3 attempts to download the file, and the second attempt is triggered by an email (already in the system), where I could have that option.

Any other ideas?

Hugs,
Moss

---

### Post by RomeReactor on 2008-07-17
Have you tried changing the preferences so that the PDF opens with Evince? (see my previous post).

---

### Post by zaivala on 2008-07-17
That MIGHT help... except I went to Edit > Preferences > Applications, and there is NOTHING listed for PDF files...  and I don't see an "Add" button.  Any more hints...?

Hugs,
Moss

---

### Post by RomeReactor on 2008-07-17
Does your preferences window look like the attachment?

What happens when you click on a PDF link? Do you get a choice of what to do with it--download it, open it?

---

### Post by zaivala on 2008-07-17
Nope, not quite.  It looks like this (expanded full screen to show more of the box contents).

I had not previously noted a problem when opening a PDF file.  This, however, is a download looking for the reader.

Moss

---

### Post by RomeReactor on 2008-07-17
If you get a dialog asking what to with it, select 'Open with...' and I think it should give a choice of applications to open it with. Make sure you mark the box to do this every time, and you should then see the PDF in the preferences. Otherwise, you might have to backup and move/delete your Firefox preferences to get a clean start.

---

### Post by zaivala on 2008-07-18
> **RomeReactor said:**
> If you get a dialog asking what to with it, select 'Open with...' and I think it should give a choice of applications to open it with. Make sure you mark the box to do this every time, and you should then see the PDF in the preferences. Otherwise, you might have to backup and move/delete your Firefox preferences to get a clean start.

OK, I went to a website that I knew had a PDF file to download, and downloaded it.  The dialog box came up, Open with... Document Viewer.  I checked the box "Do this with all files of this type" (paraphrase)... and lo and behold, PDF showed up in my Preferences with Document Viewer as the handler.

I will now go write my boss, bless her heart, and try this again.

Hugs,
Moss

---

### Post by RomeReactor on 2008-07-18
Glad you sorted it out!

Just as a comment, from now on all PDF files will open in Evince instead of giving you a choice of what to do (unless you right-click and select 'Save as...' from the context menu), but you can now change that behavior in Firefox's preferences.

Also, if this solved the problem you can mark the thread as 'Solved' by going to 'Thread Tools' above your first post.

---

### Post by zaivala on 2008-07-18
Never saw the word "Evince" anywhere, but you're right, it's Evince Document Viewer 2.22.2 (I can count to 2 scoops)

Hugs,
Moss

---

