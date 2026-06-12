---
title: "Evolution Sync across a number of PC's"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-11-06
Hi Folks,

Is it possible to save your evolution inbox (for example to a cloud location like ubuntu one or dropbox) so that if evolution is set up on several computers and accessed from any one of them it will sync to the current most recently changed inbox and if changes are made on any of them it will be updated/sync'd across all of them!?

I have several email accounts going to my evolution and would like to access the evolution inbox from another computer..

I'm well used to evolution at this stage and rather stick with it - however all ideas are welcome!..

---

### Post by papibe on 2012-11-06
Hi bikefreakvinnie.

There's no simple general solution for this.

Here's a few ideas:[LIST]
[*]If your email account supports IMAP, like gmail, you are almost all set. Set your account, and your client to use it, and it works wonderfully.
[*]For other accounts, like hotmail, that only support POP3, the simplest solution I can think of would be to have your profile either in a network share (nfs, smb, etc), or a USB stick.
[*]If Evolution, like Thunderbird, has an option to left the messages on the server, you may get away with pulling it from several computers (this is an idea that I haven't tested).
[*]You may try file synchronization, and sync the profile folder using something like Unison. This have several limitations, and potential problems, as it would require the last up-to-date machine to remain on, when you turn on other one in order to sync. Also, you would have to wait for the sync process to be successful before opening your mail client.
[/LIST]
Just a few thoughts. Let us know how it goes.
Regards.

---

### Post by bilkay on 2012-11-27
Wouldn't it be great if someone developed a mail client that stored everything in a mysql database which could be accessed from anywhere? Or maybe somebody already has.

---

### Post by LuciferRex on 2012-11-27
> **bikefreakvinnie said:**
> (for example to a cloud location like ubuntu one or dropbox)

Hmm....that IS an idea.  Wonder if anyone has done it with success.

---

### Post by Cheesemill on 2012-11-27
+1 for IMAP.

All of my mail accounts are set up using IMAP. That way all of the content is the same no matter whether I'm using any desktop client or webmail.

---

### Post by bikefreakvinnie on 2013-02-27
Thanks papibe and the rest of the gang, i since moved to IMAP with Thunderbird Mail! It was a shame to change from Evolution after so long but after trialling Thunderbird I made the swap...

---

### Post by audiomick on 2013-02-27
For what it is worth, I have been using Evolution to access an IMAP account from several computers for about 5 years now, and have had no problems with it.

---

### Post by gifford on 2013-02-28
Would just leaving the mail on the servers not solve the problem? That way, each time you log on the email would be current on any of the computers you use.

---

### Post by audiomick on 2013-02-28
> **gifford said:**
> Would just leaving the mail on the servers not solve the problem? 

That is why people have been suggesting IMAP. I gather it is now possible to tell a POP account to leave the mail on the server when it is downloaded. IMAP always did that, and is intended for people who access their mail accounts from several computers.

---

