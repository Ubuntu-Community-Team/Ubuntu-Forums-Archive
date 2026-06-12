---
title: "can't create subfolder of INBOX in squirrelmail"
date: 2015-02-25
forum: New to Ubuntu
---

### Post by icebolt2 on 2015-02-25
Hi!
I can't create subfolder of INBOX in squirrelmail 1.4.23. I can't choose INBOX from the rolling down menu when I want to create a folder under INBOX.
Why? What is the problem?
There is a picture about it. :  [http://cubeupload.com/im/DAZgwF.png](http://cubeupload.com/im/DAZgwF.png)
I use squirrelmail 1.4.23.

---

### Post by SeijiSensei on 2015-02-25
You can only create subfolders if your IMAP server uses "[Maildir]("http://wiki2.dovecot.org/MailboxFormat/Maildir")" as its method of message storage.  The default "mbox" format treats folders as a single file containing all the folder's messages separated by blank lines. This format does not permit subfolders of folders.

You can try switching to Maildir, or you can just create folders that aren't subfolders of other folders.

---

