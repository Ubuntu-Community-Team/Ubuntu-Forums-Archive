---
title: "[SOLVED] How to left email in server"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-05
I set GMAIL in Evolution using IMAP because I would like to sync reading status (read in Evolution to be reflected back in Gmail server). However, when I do this, all the emails are tranferred to Evolution, so I can not view them in Gmail. This is a problem for me because sometime I need to check my email from other computer. How do I configure my Evolution to leave the emails in Gmail (like in POP). I can not find related setting for it (see attachment)

---

### Post by dca on 2008-08-05
Is this what you're talking about?
 
[http://ubuntuforums.org/showthread.php?t=743722](http://ubuntuforums.org/showthread.php?t=743722)

---

### Post by dca on 2008-08-05
Don't think that's an option (or function) in IMAP server settings, though, only POP...  I'm trying to relate this through me using Thunderbird and not knowing where settings are in Evolution...

---

### Post by wariskampar on 2008-08-05
"Leave email in Server" only available for POP. However, the trade off is syncing status, that why I convert to IMAP. Maybe I have to choose between these features. Anyway, I really hope there is some tweaking that can be made:)

---

### Post by chrisod on 2008-08-05
Have you looked in the "All Mail" folder in Gmail? You may have it set to move all mail there after it is downloaded. Shouldn't happen that way in IMAP, but it sounds like you are really using POP.

---

### Post by y@w on 2008-08-05
Uh, IMAP by design syncs folders between the local client and what's on the server. A POP server will download and delete (depending upon the setting). Ditto what chrisod said.. 

I see that POP is enabled on your gmail account. I'd strongly suggest turning it off.. If you accidentally do setup your account using POP and it downloads your messages, you have to push them all back up. It's a huge pain.. I've not used POP for years because of this.

---

### Post by wariskampar on 2008-08-05
Problem solved!@chrisod is right. All the emails are transferred to All Mail. I conclude that if I haven't read the email in Evolution, I can read it in Gmail online. If I have read the email, it will go to All Mail (this one need to confirm first!). Anyway, thanks to all

---

