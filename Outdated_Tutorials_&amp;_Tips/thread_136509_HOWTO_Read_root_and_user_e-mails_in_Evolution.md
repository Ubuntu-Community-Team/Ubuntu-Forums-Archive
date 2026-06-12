---
title: "HOWTO: Read root and user e-mails in Evolution"
date: 2006-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-02-26
The first part was originally posted in a HOWTO for Thunderbird, I have expanded it to show how root and user e-mails from your Ubuntu system can be easily read in Evolution.
[QUOTE=simplyw00x]
A bit of necromancy, but I found that doing this in Evolution is even easier. Go Edit/Preferences, and create a new account. Enter anything as the email address, then on the next page choose "Standard mbox spool or directory", then enter '/var/mail/yourusername' as the directory. Click next, and choose 'sendmail' as your mail server. Finished![/QUOTE]
Also you may want to change your "Check for new mail" setting to 1 minute (it is a trivial internal file reading task, so it won't load you system too much).

And if you want the root mails sent to your own user account - so you can read them via this method - do the following (if you have the **postfix** package installed):
```
sudo gedit /etc/aliases
```
Add in a line similar to the following and save the file:

*root: yourusername*

Then:
```
sudo newaliases
sudo /etc/init.d/postfix restart
```
Now all root mails (like the ones cron sends etc.) will be redirected to your internal e-mail account, which will then be read by Evolution.

PS, if you want ALL your internal mails to be sent to an external e-mail address, you can also use the aliases file for this (assuming you have an SMTP server set up and working).

---

