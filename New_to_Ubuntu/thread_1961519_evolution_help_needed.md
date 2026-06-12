---
title: "evolution help needed"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by sazby on 2012-04-19
Hi All, This is my first post!

I've recently upgraded to the latest version of Ubuntu and now every time I send an email via evolution I get this message - 

The reported error was "Failed to append to mbox:///home/sarah/.local/share/evolution/mail/local#Sent: Invalid folder URI 'mbox:///home/sarah/.local/share/evolution/mail/local#Sent'
Appending to local 'Sent' folder instead.".

What can I do to sort this out please?? :confused:

---

### Post by flurospar on 2012-04-19
I can't help you much, but could you do this?

(**The following can cause problems. Make backups of the folders that I tell you to delete**)

Backup /home/sarah/.local/share/evolution/ to somewhere.

Delete /home/sarah/.local/share/evolution/ .

Set up evolution and try again. If things get screwed up even more, restore the backup.

HTH.

BTW, you might want to switch to Thunderbird, since my experience with evolution wasn't great at all, but YMMV.

---

