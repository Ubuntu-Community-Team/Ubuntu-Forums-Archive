---
title: "PHP Sendmail  counter?"
date: 2007-07-06
forum: Programming Talk
---

### Post by Mr-Heier on 2007-07-06
Hey guys!
I have a VBulletin forum that uses PHP Sendmail to send emails to users with various notifications. I was wondering if it is possible to count how many emails my forum sends every day? Some sort of phpsendmail counter script or something.

Anyone that knows how this can be done? Thanks in advance...

---

### Post by Mr. C. on 2007-07-06
You could certainly implement a wrapper around the mail function, but strict counting either calls to the function or the number of recipients will be error prone.  It does not take into account alias expansion, rejects, bounces, etc.

To gain such statistics, you need to look to the mail transfer progmam  (ie. MTA).  Which MTA are you using ?

MrC

---

### Post by Mr-Heier on 2007-07-06
> **Mr. C. said:**
> You could certainly implement a wrapper around the mail function, but strict counting either calls to the function or the number of recipients will be error prone.  It does not take into account alias expansion, rejects, bounces, etc.

To gain such statistics, you need to look to the mail transfer progmam  (ie. MTA).  Which MTA are you using ?

MrC

I just just sendmail php function. :D sendmail it is then?

---

### Post by Mr. C. on 2007-07-06
"sendmail" is a program, which is available in Sendmail, Postfix, etc.  It originated in Sendmail, but is standard for the most part.

My question is inquiring about whether you are using Postfix, Sendmail, etc.

Run the command line:

  ps -ef | grep postfix

for example, to see what you have running.

I ask this, because you can use your mail logs to give you the information you desire, and there are tools available to help.

MrC

---

### Post by Mr-Heier on 2007-07-09
I get this when running the command.
root      4642  4093  0 10:35 pts/0    00:00:00 grep postfix

Are there any default locations for the mail log?

Thanks for helping :)

Marius

> **Mr. C. said:**
> "sendmail" is a program, which is available in Sendmail, Postfix, etc.  It originated in Sendmail, but is standard for the most part.

My question is inquiring about whether you are using Postfix, Sendmail, etc.

Run the command line:

  ps -ef | grep postfix

for example, to see what you have running.

I ask this, because you can use your mail logs to give you the information you desire, and there are tools available to help.

MrC

---

### Post by Mr. C. on 2007-07-09
Ok, so you are not running postfix.

In Ubuntu, mail goes to /var/log/mail* ; take a look at the various files there.

Have you installed and configured any MTA?  If so, which ?

Is your email being sent and delivered ?

MrC

---

