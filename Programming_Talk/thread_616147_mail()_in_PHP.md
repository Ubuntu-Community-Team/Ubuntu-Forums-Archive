---
title: "mail() in PHP"
date: 2007-11-17
forum: Programming Talk
---

### Post by nbv4 on 2007-11-17
I'm writing a PHP/MySQL site from inside my ubuntu computer. When I get done, I'm going to move it all to a webserver so others can use it. Right now, I'm struggling with getting PHP to send an email of username/password to the user when they sign up. Right now I'm trying to keep everything simple, so here is my code:

if (mail("$email","website password","your password is <b>$password</b>")) {
  echo("<p>Message successfully sent to $email</p>");
 } else {
  echo("<p>Message delivery failed...</p>");
 }

Every time it gives me the failed delivery message. I'm thinking I need to install an email server for this to work, right? I'm not much of an expert, so I was wondering if someone could clue me in to how to do this, and have PHP be able to see the webserver so it can use it to send mail. All I want to do is mail that one message, so I don't really need anything super heavy duty.

---

### Post by nbv4 on 2007-11-22
bump?

---

### Post by smartbei on 2007-11-22
You need to install a mail daemon (I think that's what they are called) such as postfix or sendmail and edit php.ini in /etc/apache2/<some folder> so that it recognizes the mail daemon.

```

sudo aptitude install postfix

```

Heven't done this in a long time, so I am not exactly sure to tell you what exactly to put in the php.ini. Check the ini, there might be informative comments.

---

