---
title: "Setup mail server for PHP"
date: 2012-06-29
forum: Programming Talk
---

### Post by c2tarun on 2012-06-29
Hi friends,
I am trying to learn PHP by w3schools.com
In mails section for PHP I found this line:
 
> 
**Note:** For the mail functions to be available, PHP requires an installed and working email system. The program to be used is defined by the configuration settings in the php.ini file.

 
Can anyone please help me with this stuff, how can I create an email system on ubuntu. I don't know anything about it, so I have to start everything from scratch. Any tutorial from beginning will also help.
 
Thanks

---

### Post by c2tarun on 2012-06-29
I found this link : [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
 
Is there any better tutorial than here?

---

### Post by DJTIESTO19 on 2012-06-29
If you already have an email account (Comcast, Gmail, etc), then you can install Thunderbird Mail using the software center. It will integrate your email that you use online and link it to Thunderbird. It should do the trick.

---

### Post by c2tarun on 2012-06-29
> **DJTIESTO19 said:**
> If you already have an email account (Comcast, Gmail, etc), then you can install Thunderbird Mail using the software center. It will integrate your email that you use online and link it to Thunderbird. It should do the trick.
 
 
can we send emails using that setup by php script I am trying to write?

---

### Post by slavik on 2012-06-30
> **DJTIESTO19 said:**
> If you already have an email account (Comcast, Gmail, etc), then you can install Thunderbird Mail using the software center. It will integrate your email that you use online and link it to Thunderbird. It should do the trick.

This information does not relate to OP's question.

---

### Post by slavik on 2012-06-30
> **c2tarun said:**
> can we send emails using that setup by php script I am trying to write?
No.

On Unix, configure PHP to use sendmail, no mail server required. There is also mail, but it appears to be part of mailutils which is not default in ubuntu. Use the man pages for exact usage.

---

