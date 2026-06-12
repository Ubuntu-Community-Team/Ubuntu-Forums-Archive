---
title: "Email Marketing"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by tertiusvl on 2013-02-01
Hi, i was wondering if there is any email marketing software available that runs off Ubuntu?

---

### Post by SeijiSensei on 2013-02-01
Unless you have experience running a mail server and managing databases, you are much better off with a third-party service provider like [Constant Contact](http://www.constantcontact.com/).

We'll assume that you are talking about email marketing to lists of people that have already agreed to receive mail from you, right?  Anything else is "*unsolicited* commercial e-mail" or, more commonly, spam.

---

### Post by tertiusvl on 2013-02-01
Thank you for the reply and the link, yes will only be sending to "opt-in" lists. Would like to look at a localized solution though, I have experience in database and mail server management, just the first time i am attempting this from a Ubuntu or any GNU platform ...

---

### Post by Frogs Hair on 2013-02-01
Here is a start . Use your favorite search engine , there results for both Ubuntu sever and Linux in general.

[http://ubuntu-rituranjan.blogspot.com/2013/01/lamp-linux-apache-mysql-and-php.html](http://ubuntu-rituranjan.blogspot.com/2013/01/lamp-linux-apache-mysql-and-php.html)

---

### Post by SeijiSensei on 2013-02-01
Basically if you can get an SMTP server running, you can just create an e-mail alias that points to a file with the target addresses.  One of my clients would send the occasional message to about 40K addressees.  We would build the alias file by pulling the list of addresses from their Progress database.  On the mail server we had an entry in /etc/aliases that looked like this:

```
mailing-list:      :include:/path/to/the/address/file
```

Sending an email to [email]mailing-list@example.com[/email] would distribute the message to all the addressees in the file.

That's not all that is involved, though.  A good fraction of those addresses would no longer be active, so you have to have a method for removing them from the database. 

One of the reasons I recommend ConstantContact is that they have the infrastructure in place to handle all of this, including the list and bounce management tools.

---

### Post by tgalati4 on 2013-02-01
I've used [http://www.sugarcrm.com/](http://www.sugarcrm.com/) for some email campaigns.  You can use the sugarcrm scheduler and gmail to send out 50-email blasts every 1/2 hour.  That's several hundred an evening.

---

