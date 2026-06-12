---
title: "evolution: permanently delete messages from server"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Stefanie on 2008-05-13
I use IMAP to check my mail with evolution. Every time I delete a message it disappears from my inbox but it is not removed from the server. In Outlook there is an option to remove deleted messages, how do I do this in Evolution?

---

### Post by pedro_orange on 2008-05-13
If gmail is your e-mail server; you need to check a setting on your gmail account (on the site) to say delete from server when you download them.

I'm sure other email servers work this way.

---

### Post by Stefanie on 2008-05-13
it is a university server, and I don't want to delete messages from the server when I download them, I just want the messages to be deleted from the server when I delete them in evolution.

---

### Post by Inxsible on 2008-05-13
and you are sure its an IMAP server?

---

### Post by mlentink on 2008-05-13
I'd be interested too...

I have as yet not found a way to do this in Evolution.

And, yes, I'm perfectly sure mine is an IMAP-server (I installed it myself... ;-) )

---

### Post by Stefanie on 2008-05-13
yep, i'm very sure i'm talking about an IMAP server :-)

---

### Post by vaineh on 2008-05-19
i was wondering why evolution wasn't deleting emails on my imap server...

whats the logic behind this? so i don't delete things accidently or rather can recover things accidently deleted

---

### Post by DonnieP on 2008-05-30
Same problem  here.  My email is a .Mac account.  Yes, I'm sure it's imap.  I switched back recently to using Evolution because the performance seems better than it was a couple of years ago.  But, when I checked my .Mac account from the web the other day I discovered then none of the messages I've deleted from Evolution have actually been deleted.  There's got to be a way to do this . . . otherwise I'll have to revert to another reader that actually works, or the .Mac web interface.

---

### Post by DonnieP on 2008-05-31
Just for the record, I did a bit of testing after googling some more about this Evolution/IMAP problem.  It turns out that Evolution *will* delete from the server the messages you've previously marked for deletion *in Evolution* if you select File | Empty Trash.  What's braindead about this behavior is that it's totally ignoring the trash setup you've already got on the IMAP server.  The messages Evolution has supposedly flagged for deletion are not ever moved to the appropriate trash folder on the server even though in Evolution client they show up in a 'Trash' folder that shows up in the folder list for that server - but that folder really doesn't exist on the server - the messages are still sitting in inbox on the server.  The whole point of IMAP is that *everything* is handled on the server so that I can access that account from anywhere with any client - web or otherwise - and stuff just works.  Evolution is somehow trying to "own" message deletion to the exclusion of other clients accessing the same account.

---

### Post by Stefanie on 2008-05-31
ok thanks for the information. the way evolution handles this is definitely not the way it should be...

---

