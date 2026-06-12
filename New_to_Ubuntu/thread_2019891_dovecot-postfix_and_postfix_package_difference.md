---
title: "dovecot-postfix and postfix package difference?"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by newn on 2012-07-07
What is the difference between these two?  P.S. Yes, I do want to take no postfix, even though I'm a beginner. :)

---

### Post by SeijiSensei on 2012-07-07
Postfix is a "mail transfer agent."  It's used to exchange mail with other accounts on the local server and with remote mail servers around the world.

Dovecot provides POP3 or IMAP4 access to your mail.  It is the server software that a client like Thunderbird connects to so you can read your mail.

If all you want to do is send mail, then you just need Postfix.  If, however, you want to build a mail server with local accounts, mail folders, and the like, you'll need dovecot as well.

---

### Post by newn on 2012-07-07
I meant two packages - "dovecot-postfix" and "postfix," though thanks for the explanation about them both in general. :)

P.S. I'd still like to know the answer to the original question though.

---

### Post by SeijiSensei on 2012-07-07
$ sudo apt-get dovecot-postfix

The following NEW packages will be installed:
  dovecot-core dovecot-imapd dovecot-managesieved dovecot-pop3d dovecot-postfix
  dovecot-sieve mail-stack-delivery postfix


$ sudo apt-get install postfix

The following NEW packages will be installed:
  postfix


So, rather unsurprisingly, dovecot-postfix installs both packages, while postfix alone installs... postfix.

---

### Post by newn on 2012-07-07
Thanks!

---

