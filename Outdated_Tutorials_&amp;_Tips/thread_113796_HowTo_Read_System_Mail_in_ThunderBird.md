---
title: "HowTo: Read System Mail in ThunderBird"
date: 2006-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by klineberger on 2006-01-07
If you want to read Linux System Mail with a mail client like thunderbird, you can use the following trick that may work with the other GUI clients:

   Create a subfolder in "Local Folders/Inbox" called "System", or whatever. Exit Thunderbird, move into ~/.mozilla-thunderbird/xxxx.default/Mail/Local\ Folders/Inbox.sbd/ and find a empty text file called System. Remove it and replace it with a symbolic link to /var/mail/your_user_name

cd /home/pepito/.mozilla-thunderbird/xxxx.default/Mail/Local\ Folders/Inbox.sbd/
rm System
ln -s /var/mail/pepito System

  That's it

---

### Post by Gandalf on 2006-01-19
Thats a cool trick
Thanks :D

---

### Post by ounas on 2006-01-20
Nice one thanks...

Brrr here is cold -35C

-Ounas:D

---

### Post by juantxorena on 2006-01-21
My /var/mail directory is empty :???::???::???::???:

---

### Post by george_apan on 2006-01-21
[QUOTE=juantxorena]My /var/mail directory is empty :???::???::???::???:[/QUOTE]
Mine too...

---

### Post by Chrissss on 2006-01-21
Start once e.g. the mailer mutt. After that your mbox files will be created :)

CU
 Christoph

---

### Post by george_apan on 2006-01-21
[QUOTE=Chrissss]Start once e.g. the mailer mutt. After that your mbox files will be created :)

CU
 Christoph[/QUOTE]
Sorry but this didn't help. I installed mutt (postfix was installed along with it). There were some configuration options for postfix where I just pressed enter. When I run mutt I get an error saying that there is no /var/mail/username directory. What am I doing wrong?

edit: And a Mail directory was created in my home dir.

---

### Post by stalefries on 2006-01-26
I can't for the life of me find System.

---

### Post by pbb on 2006-02-01
[QUOTE=stalefries]I can't for the life of me find System.[/QUOTE]

Did you first **create** the mailbox "System"?

[QUOTE=klineberger]Create a subfolder in "Local Folders/Inbox" called "System"[/QUOTE]

---

### Post by simplyw00x on 2006-02-18
A bit of necromancy, but I found that doing this in Evolution is even easier. Go Edit/Preferences, and create a new account. Enter anything as the email address, then on the next page choose "Standard mbox spool or directory", then enter '/var/mail/yourusername' as the directory. Click next, and choose 'sendmail' as your mail server. Finished!

---

### Post by george_apan on 2006-02-18
[QUOTE=simplyw00x]A bit of necromancy, but I found that doing this in Evolution is even easier. Go Edit/Preferences, and create a new account. Enter anything as the email address, then on the next page choose "Standard mbox spool or directory", then enter '/var/mail/yourusername' as the directory. Click next, and choose 'sendmail' as your mail server. Finished![/QUOTE]
Thanks. This worked fine! :) 

I don't understand why I have a /var/mail/username directory now while there was nothing in /var/mail before. I didn't touch anything in the meantime (I think). Maybe there was nothing in there because I had no system mail until now? :confused:

---

### Post by simplyw00x on 2006-02-18
There should definitely have been something there; the ubuntu installer sends you email to let you know when ubuntu is installed, and several dpkg warning messages also get sent there. Anacron and cron send stuff there as well.

---

### Post by george_apan on 2006-02-18
There is only one e-mail sent by Anacron in my system mail dated January 22nd anyway. Maybe the directory was created automatically with this e-mail and I just realized it. My previous attempt with thunderbird was before that date.

---

### Post by Rizado on 2006-02-18
I don't have anything in my /var/mail/ either. Running Kubuntu on this box but it's empty on another ubuntu computer too. And what the hell is mailer mutt :confused:

Anyway in thunderbird 1.5 there's no Inbox.sbd/, System is directly under Local folders so it probably works too.

---

### Post by george_apan on 2006-02-18
I'm wondering... Have you logged in at least once straight to the console instead of the gui? Maybe this is needed to create something in /var/mail/

Try pressing Ctrl+Alt+F1 while in Gnome/KDE. You'll get a text only console (tty1). Log in with your username and password and see if you get a "You have mail" notice. You can go back to your gui by pressing Ctrl+Alt+F7 any time.

---

### Post by Rizado on 2006-02-19
Loads of times. I've been using fedora and redhat before and I always got messages. Now with ubuntu it seems as if some service aren't running.

---

### Post by dcstar on 2006-02-26
[QUOTE=simplyw00x]A bit of necromancy, but I found that doing this in Evolution is even easier. Go Edit/Preferences, and create a new account. Enter anything as the email address, then on the next page choose "Standard mbox spool or directory", then enter '/var/mail/yourusername' as the directory. Click next, and choose 'sendmail' as your mail server. Finished![/QUOTE]
Also you may want to change your "Check for new mail" setting to 1 minute (it is a trivial internal file reading task, so it won't load you system too much).

And if you want the root mails sent to your own user account - so you can read them via this method - do the following:

Install the postfix package, then in a user terminal:
```
sudo gedit /etc/aliases
```
Add in a line similar to the following and save the file:

*root:	yourusername*

Then:
```
sudo newaliases
sudo /etc/init.d/postfix restart
```
Now all root mails (like the ones cron sends etc.) will be redirected to your internal e-mail account, which will then be read by your mail client.

PS, if you want ALL your internal mails to be sent to an external e-mail address, you can also use the aliases file for this (assuming you have an SMTP server set up and working).

PPS, I might make this a HOWTO on it's own for Evolution users, they may not look at this one.

---

### Post by george_apan on 2006-02-27
I get a "sudo: newaliases: command not found".

---

### Post by dcstar on 2006-02-28
[QUOTE=george_apan]I get a "sudo: newaliases: command not found".[/QUOTE]
Should be part of the postfix package.

---

### Post by george_apan on 2006-02-28
[QUOTE=dcstar]Should be part of the postfix package.[/QUOTE]
Yes, that was it. Thank you! :)

---

### Post by mezhaka on 2006-10-25
> **Rizado said:**
> I don't have anything in my /var/mail/ either. Running Kubuntu on this box but it's empty on another ubuntu computer too. And what the hell is mailer mutt :confused:

Anyway in thunderbird 1.5 there's no Inbox.sbd/, System is directly under Local folders so it probably works too.

so am i. have you figured out what was the deal?

i'm playing with "at" and "batch" and just can't find any file they send the output to...

---

### Post by mezhaka on 2006-10-27
> **mezhaka said:**
> so am i. have you figured out what was the deal?

i'm playing with "at" and "batch" and just can't find any file they send the output to...

ok, at last i've found out the root of the problem. i had no Mail Transfer Agent on my system installed. so installing postfix fixed all the stuff.

---

