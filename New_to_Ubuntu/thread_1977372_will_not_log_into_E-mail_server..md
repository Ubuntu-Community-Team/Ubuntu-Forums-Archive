---
title: "will not log into E-mail server."
date: 2012-05-10
forum: New to Ubuntu
---

### Post by pensioner77 on 2012-05-10
I have just installed 12.04 as a partition with Win7 on my PC, I also have it on an old laptop with Mint 12. With all the same settings Thunderbird works on all except the newly installed 12.04 on my PC. It gives the message"Login to server imap.tiscali.co.uk failed" There is a suggestion to try a new password--but the password is the same in all cases.What can I do to get back to my E-mails??

---

### Post by Docaltmed on 2012-05-10
You've probably already covered this, but:

1. do you have connectivity in the Ubuntu partition, i.e., you can visit websites with Firefox?

2. is "imap.tiscali.co.uk" the correct name for your IMAP server?

---

### Post by pensioner77 on 2012-05-10
Yes to both questions. The set up was all semi-automatic, that is all I was asked for was my name,E-mail No. and password, then everything else was "found" but I have checked the settings and they are the same as on the Win7 and also on 12,04 installed on a laptop. So I am completly at a loss as to what to do.

---

### Post by steeldriver on 2012-05-10
can you ping imap.tiscali.co.uk?

when you checked the settings did you include 'Port', 'Connection security' and 'Authentication method' boxes?

---

### Post by pensioner77 on 2012-05-10
None of those was asked for. But strangly I have two E-mail addresses I have tried and successfully set up the second one but if I try sending a message there is no send button only a send later one. My main E-mail address was apparently set up but without all the sub files and I was trying to send a test E-mail from one to the other. The set up for the second E-mail did show all its sub files. This is all so strange.

---

### Post by steeldriver on 2012-05-10
Whether those things were asked for or not, they *are* essential and you should definitely check they are the same as on your working setups.

It's not surprising the subfolders don't show up - for imap, the folder structure is stored on the server so until you get connected it won't pull that information down.

Things can get a little complicated with imap - do you really have 2 distinct accounts, or are they aliases for the same account? do you use 'Manage Identities' to set them up?

[For example, I have a single imap mailbox with one identity <first initial><surname> and another <surname><initials>; I then have subfolders within the inbox and filters set up to separate them based on the email To: field. Then I use Thunderbird's 'Manage Identities' feature to allow me to apparently send from those 'different' adresses. To add an extra wrinkle it's possible for filters to be defined on both the server and the local computer(s)]

For the send issue, check that you also set up the 'Outgoing Server (SMTP)' settings appropriately

---

### Post by pensioner77 on 2012-05-10
This whole affair is most odd!! Since my last post about 3 hours ago,my computer has been switched off. I have just returned and on checking Thunderbird both accounts are up and working, sub files and all. Thank you all for your concern and help.

---

### Post by steeldriver on 2012-05-10
OK that's good, glad you're back up and running

---

