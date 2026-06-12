---
title: "how to access emails from my server using php"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by shad2 on 2014-03-06
i have managed to set up an email server on my pc ,how can i use php to retrieve the new messages recieved and 
display them.how can i access the inboxes of users to get the mails and also send them?
where  can I read/tutorials

---

### Post by Dave_L on 2014-03-06
You could start with this: [http://php.net/manual/en/book.imap.php](http://php.net/manual/en/book.imap.php)

If you browse through the functions, there are lots of examples. 

Although the function names start with "imap", they apply to both IMAP and POP3.

---

### Post by SeijiSensei on 2014-03-06
The simplest solution is to install [SquirrelMail]("https://library.linode.com/email/squirrelmail-ubuntu12.04"), a full-scale mail client written in PHP.

---

