---
title: "Backing up Gmail in Evolution"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-11-09
Hello,

I enabled pop in Gmail and setup Evolution to use gmail.  I want to backup all of my files.  The problem I am having is that evolution is backing up all mail, including sent mail, into the inbox.  Is there some way that evolution could track the difference between received and sent mail?

\\:D/

---

### Post by d0cta ew on 2009-01-09
Hey there-

I've had the same problem in other devices/programs sync'ing with Gmail.  It's because of the way that Gmail sorts your mail.

All of your mail in Gmail is just in one big folder with only labels/filters separating them, so every sent mail will look like a new piece mail in Evolution, because it really is another addition to that big Gmail "folder/inbox".

To fix this, create a filter in Evolution to have all mail that has *your gmail address* in the "From:" field to skip the inbox and go to "Sent Mail".

Or however you want to do it, but thats essentially the fix for it.

Hope this helps! :D

---

