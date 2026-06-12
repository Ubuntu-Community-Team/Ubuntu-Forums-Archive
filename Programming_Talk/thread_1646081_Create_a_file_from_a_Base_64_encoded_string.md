---
title: "Create a file from a Base 64 encoded string"
date: 2010-12-15
forum: Programming Talk
---

### Post by dotchristopher on 2010-12-15
Hi all,

Quick question. I have a base64 encoded text string which I would like to save, (through bash cli), as a file. How would I do this?

Example & Clarification:
Take the following example:
Using mutt as your email client, your have a /var/mail/[whatever] mailbox. This mailbox can be nano'd and read in plain text.
Say you received an email with attachment. The email would be present in your /var/ma.... mailbox, along with the attachment, (as a base64 string).
If this (/var/mail/...) text file was read into a script which could determine the start of the attachment's base64 string and save the string as a variable, how would tell the filesystem to save the raw binary data back as a file?

If you're interested as to why: I would like my server to handle certain filetypes sent to a certain email automatically (eg automatically printing a PDF emailed to it, or copying said PDF, or moving a .torrent file to a watched directory) and mutt, evolution, thunderbird etc all are incapable of being multi-user, dependable solutions on a (ostensibly) headless server for several reasons, including their inability to talk to local mailboxes (this machine is also the mail server). 

But that's not the point. Please don't badger me about email security, authentication etc. I want this method to be available and have accounted for the security aspects. If you can suggest a better solution (so far mutt macros, evolution plugins etc have not worked correctly), please do so.

---

### Post by saulgoode on 2010-12-15
Check out the man page for 'uuencode'.

---

### Post by dotchristopher on 2010-12-15
> **saulgoode said:**
> Check out the man page for 'uuencode'.

Ace, thanks. Knew there would be something simple, thanks for the pointer.

---

### Post by roccivic on 2010-12-17
also:
[HTML]base64 --help[/HTML]

---

