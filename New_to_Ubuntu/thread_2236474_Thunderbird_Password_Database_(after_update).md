---
title: "Thunderbird Password Database (after update?)"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-07-27
I'm running 14.04.  Suddenly I'm getting a message, when I launch Thunderbird, about the Password Database (see attached picture) - I assume it is because of an update.  Clicking on the Launch KeePass button does nothing so I get this message each time I 'go' into mail.  Any suggestions appreciated.

---

### Post by cressrt2 on 2014-07-27
This looks like a request for your mail password to be re-entered, I get this sort of request when the server is down or off line, but for a different mail server.

---

### Post by Quarkrad on 2014-07-28
I'm not so sure.  I have three different mail accounts all configured in Thunderbird and all accounts are questioning the Password Database.  And what is the specific question about the KeePass got to do with external email servers?

---

### Post by Quarkrad on 2014-07-28
I had an addon to Thunderbird that I think was called KeeFox - which I have now removed, but the passkey keeps coming up.

---

### Post by Quarkrad on 2014-07-29
I'm struggling now - I've purged Thunderbird including my .Thunderbird folder, reinstalled and copied my profile from backup HD and I'm still kept asking for and having to enter my passwords for both incoming and outgoing.  I've also reinstall KeeFox and now it looks like every firefox page I go to (from my bookmarks) I'm asked to **Load my password database (Launch KeePass)**.  Going to need help on this one.

---

### Post by amanchesterman on 2014-07-29
KeeFox is described as an add-on for Firefox, not Thunderbird (your post #4). There's a program called KeePass in the Ubuntu Software Center -- in fact there are two of them, I guess they are different versions. KeePass is a password manager, which stores all your passwords for mail accounts, websites etc., and KeeFox links that specifically to Firefox.
So it looks as though at some point you have installed KeePass (or maybe KeeFox installed it for you) and now all your mail accounts and password-protected pages 'expect' to find the relevant password in the KeePass database -- which, for some reason, isn't there any more, or at least is no longer available.
A simple solution might be to install KeePass from the Software Center and set it up again as it was before? I don't think that your problem is with Thunderbird or Firefox, it's the absence or non-availability of the KeePass database.

---

### Post by Quarkrad on 2014-07-30
I've purged Keepass2 from my machine and also removed KeeFox from Firefox so my thinking is I am at a base machine ('as it comes out of the box').  I've logged on/off and I'm still being asked for my passwords with the error window refering to me being logged out of the password datapass and a Launch KeePass window that does nothing.

---

### Post by Quarkrad on 2014-07-30
I've just set up one of mail accounts in Thunderbird on a 12.04 virtual machine and all is OK so there definately something wrong on my 14.04 main machine.  Although I have installed and removed KeePass2 trying to get rid of this issue to my knowledge I have never install KeePass from the Software Centre in the past - I had never heard if it.  Hence my 'questioning' when this error first arrived and there was reference to Launch KeePass in the error window.

---

### Post by Quarkrad on 2014-07-31
This is probably related(?) - firefox is no longer pre populating web pages.  When I use to log into this forum via** [https://login.ubuntu.com/BDXNWCfc4FNLdmQv/+decide](https://login.ubuntu.com/BDXNWCfc4FNLdmQv/+decide)** when I typed in the first letter of my username the full name and password was autopopulated - now it isn't.  When I look in (firefox) Edit/Preferences/Security/Saved Passwords all my usernames/passwords are there.

---

### Post by amanchesterman on 2014-07-31
I've had a quick look at the KeeFox website: have you done that? There's quite an extensive manual which includes a 'help' section with a detailed troubleshooting guide. There's also a support forum, which includes at least one lengthy thread that may be relevant: it's about KeeFox failing to connect with the KeePass database. One user reports success by 'deleting the KeeFox folder inside [his/her] Firefox profile'. I suggest you try that. More generally, you might get more help via the KeePass and KeeFox websites (or even Firefox support): I'm not convinced that your problems are really to do with Ubuntu itself.

---

### Post by Quarkrad on 2014-07-31
Thank you for your help.  Before I dive into the KeeFox web site/forums do you know what has happened to my machine for this to start?   I have never had this issue before (ubuntu user since 8.04) and as far as I'm aware I have never used KeePass(x) - (or perhaps I have but been unaware).  Do I have to use KeePass2/KeeFox in Ubuntu 14.04 - if not how do I get to back to where I was a week ago when I just launched Thunderbird and used my email without any requests for passwords?

---

### Post by Quarkrad on 2014-07-31
I just removed KeePass via synaptic (completely remove) and via sudo remove a keePass folder from /.local/share - has this completely removed my dependance on KeePass?  I fear not because my password issue is still there, including FF not autopopulating user name/passwords.  I'm happy to turn to the KeePass forums but if possible I would like to remove this KeePass dependancy from my machine.

---

### Post by Quarkrad on 2014-08-01
Solved it at last.

Thunderbird:
1. Close Thunderbird and open the prefs.js file in Notepad or another editor (make a backup copy of prefs.js first, as a precaution).
2. Find the following line: user_pref("signon.rememberSignons", false);
3. Change the value from false to true.
4. Close the Notepad or editor window and save changes.
5. On the next startup of Thunderbird you should find the checkbox for remembering the password in the password manager. 

Firefox
For some reason(?) the **Remeber passwords for sites** box was not checked in Edit/Preferences/Security!

---

### Post by amanchesterman on 2014-08-01
Well done! Glad you have sorted it at last. :p

---

