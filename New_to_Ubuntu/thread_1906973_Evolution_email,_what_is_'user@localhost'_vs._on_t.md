---
title: "Evolution email, what is 'user@localhost' vs. on this computer?"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by cackerso on 2012-01-10
My email is a pop3 account.  After I upgraded from 11.04 to 11.10 I had two sets of email folders in Evolution.    One set is under 'on this computer'.  The other is under 'user@localhost'.  My new email comes to the inbox in 'on this computer'.  There is not really much under the second set of folders so  I moved all of the emails from there to the set under 'on this computer'.  Why did I get two sets of folders after the upgrade?  Can I safely delete the "user@localhost'  ?  Can I do this by just deleting the account in Preferences>Mail accounts  ?

---

### Post by Enter t'Ibex on 2012-01-10
I have an addon question that one...
I just ADDED a hotmail account.  And it seems to have consolidated both email accounts (yahoo and hotmail) inside the 'on this computer' account.

I would like to force it to have a separate set of folders for each account, but I cant see how to do that either!

Hopefully answering one of these will answer both!

Thanks

---

### Post by cackerso on 2012-01-13
This seems like a straightforward question.  Should I move it or repost in some other category besides beginner?

---

### Post by NHclimber on 2012-01-16
evolution 2.xx stored local mail in mbox format.  evolution 3.xx uses Maildir format.

On first startup, evolution dups the old mbox mail into the new Maildir format. The 'On This Computer' account is the new Maildir-based account. The 'user@localhost' is the old, saved mbox format. evolution does this so you can make sure the migration was performed successfully.

You can delete the 'user@localhost' account once you know that everything copied -- or just leave it, just in case.

---

### Post by cackerso on 2012-01-16
Thanks for the information.  I moved the mail and deleted the localhost account.

---

