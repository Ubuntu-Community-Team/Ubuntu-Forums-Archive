---
title: "Adding new email account?"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by gdtw on 2011-09-13
I am trying to add a new email account with postfix.

so I do:
sudo useradd -m -s myname
..
and then i give a password.

when i su myname, I type "mail", it asks me to install mailutils, etc.
I type "sendmail" and it sends out an email. 

However, the new email account shows up as [EMAIL="myname@mail.domain.com"]myname@mail.domain.com[/EMAIL].

How do I make it [EMAIL="myname@domain.com"]myname@domain.com[/EMAIL]? (postconf mydestination does show both...)

Thanks for any help.

---

### Post by Rex Bouwense on 2011-09-13
Not sure if you read this:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by gdtw on 2011-09-13
postfix has already been installed and the email has been working for a few years. i just wanted to add a new email account.. and i thought it would be just some simple steps.. i do not want to accidentally messed up my original settings for other accounts.

---

### Post by gdtw on 2011-09-13
in main.cf, myhostname = mail.domain.com
but my other existing email accounts work just fine, e.g., [email]robert@domain.com[/email]

so obviously i cannot change this file/setting.. so where am i supposed to change to to get rid of "mail."?

---

### Post by gdtw on 2011-09-15
i guess the question is too easy to answer:
myorigin=$mydomain

and .forward has to be parallel to Maildir

---

