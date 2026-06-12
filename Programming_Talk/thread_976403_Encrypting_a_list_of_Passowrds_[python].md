---
title: "Encrypting a list of Passowrds [python]"
date: 2008-11-09
forum: Programming Talk
---

### Post by karlw on 2008-11-09
Hi all,

I am looking to automating some task using python.  One of these tasks is checking my bank account statement online.  I have found urllib2, cookielib and ClientForm and I must say I have made a nice little web crawler.  But the forms that I must place information into requires my username and password, and I know I'm not to place this information as plain text anywhere on my pc.

I would like to have one "master password" that can be used to unlock the password list.  The master password could not be stored on disk anywhere, the user would have to enter it every time.  This is something similar to what happens with KeyChain (Mac OSX).  I looked into DES package, but I really couldn't find a clean way to implement this.

Also some simple Xor encryption is not preferred.

Any links or advice would be great!!

Thanks in advance,

-karl

---

### Post by Martin Witte on 2008-11-09
You can use crypt for this prpose, see [the python documentation]("http://docs.python.org/library/crypt.html")

---

### Post by Greyed on 2008-11-09
Crypt would not work.  It is one-way and he needs to be able to reverse the process so his script can enter the password into the web form.

(edit) To further clarify you're getting into  the regression problem.  Since this is an automated process to access secure information it needs to have no human interaction.  Generally when things are stored on disc in an encrypted format they require human interaction to provide the password to unlock the encrypted data.  So instead of providing a password for the on-line form you're not providing a password to get the password.  That password has to be in plain text or be encrypted which means human intervention to provide the password for the password for the password....  repeat to infinity.

Unless this is on a public machine your security for your passwords is simply not to let anyone in in the first place.  To be automated you're going to have to trust that password in the clear because any security you place around it will either be trivially weak or suffer from the same problem.

---

