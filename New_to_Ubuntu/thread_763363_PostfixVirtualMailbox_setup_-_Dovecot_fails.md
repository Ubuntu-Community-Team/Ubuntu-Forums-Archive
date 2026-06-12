---
title: "PostfixVirtualMailbox setup - Dovecot fails"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by sagor on 2008-04-22
Ok, I've been following the PostfixVirtualMailboxClamSmtpHowto posted in the Community documents.
My problem is, that though everything seems to go along ok, when I try to log in via Pop3 or Imap in the guide (via Telnet), the login is successful but immediately disconnects. The dovcot log shows:

dovecot: 2008-04-22 21:59:03 Fatal: chdir(/home/vmail/mywebsite.com/) failed with uid 5000: Permission denied.
dovecot: 2008-04-22 21:59:03 Error: child 8723 (pop3) returned error 89

Looking at the permissions, the vmail directory is owned by "vmail" but the directory "mywebsite.com" is owned by root. The "user" folder below this is also owned by "vmail" (ie: /home/vmail/mywebsite.com/user).

Seems to me that dovecot is trying to access by the group 5000 (as per guide), but the "mywebsite.com" folder, being owned by root (and folder group is root too...), dovecot cannot access this folder.

Earlier in the guide, there was a simple test via telnet to create a mail for a user, to test the Maildir/ syntax and both the user and the site folder are owned by "vmail" (ie: /home/vmail/test/tst and /home/vmail/test where test is virtual domain and tst is user).

This is my first crack at Ubuntu (or any *inux) for a web LAMP server, and having howtos that fail is very discouraging (I even cut and paste commands, and check syntax such as bad quote marks common in these howtos)

Any help would be appreciated...

I suspect something is missing in the "adddovecotuser" file as specified in the guide. Should there be a chown on the directory as a separate line?

...Just to update info - the system is Ubuntu 7.10 server, with gnome desktop loaded, but otherwise stock image...

---

### Post by meltindar on 2008-05-16
Hi Sagor,

If you have manually created the mywebsite.com folder as root(and maybe in other cases) this will help you:

```

chown -R vmail:your_group /home/vmail/mywebsite.com/

```

your_group is the group with the ID 5000.
Howto probabaly presumed that you will create this folder as non-root user but who knows maybe it really misses the line.
HTH

Meltindar

---

