---
title: "Evolution : Failed to append to mbox"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by freelancer1995 on 2008-10-11
i recently replaced my desktop pc and as part of the move, i took a backup of my evolution 2.22.3.1 setting and mailbox, on restoring the mailbox, into a different account name, i keeping getting the following error.

> Error while performing operation.

Failed to append to mbox:/home/sysadmin/.evolution/mail/local#Sent: Cannot get folder: /home/sysadmin/.evolution/mail/local: No such file or directory
Appending to local `Sent' folder instead.

is there a way to update this setting to reflect the new user name?

thanks in advance

---

### Post by mejy on 2008-10-11
This isn't a very nice way to do things (that is, it will work fine but isn't very clean), but will at least get your mailbox functioning.
```
sudo mkdir /home/sysadmin
sudo ln -s ~/.evolution /home/sysadmin/.evolution/ 
```
If you figure out another solution, you can undo this with
```
sudo rm -rf /home/sysadmin
```
assuming you have nothing else left in that directory.

---

### Post by freelancer1995 on 2008-10-11
actually the lack of the directories doesn't prevent the email client working, it defaults to the new user accounts directories, so getting it work isn't the problem as you say i am look for a clean solution :)

---

### Post by freelancer1995 on 2008-10-12
solved, [http://www.debuntu.org/how-to-fixing-evolution-after-home-directory-changed-failed-to-append-to-mbox](http://www.debuntu.org/how-to-fixing-evolution-after-home-directory-changed-failed-to-append-to-mbox)

i used the graphical method.

> the open gconf-editor and go to /apps/evolution/mail, double click the entry accounts and edit one by one the list of values to change /home/olduser by /home/newuser. To the same with the entry signatures.

no more errors :)

---

