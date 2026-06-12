---
title: "Build Exim4 and OpenLDAP without Local/Makefile"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by peter2703 on 2012-03-27
Hi,

I am trying to make Exim4 talk to an OpenLDAP server without type command 'make' but it is so hard for me. That why I write this thread. I already tried build Exim4 with LDAP support but no success!

My idea is to use user's emails and passwords saved on OpenLDAP server to allow them sending emails on small web app written in PHP.

I already sent email but I had to write my password without any kind of encryption on text file. For security's issue, this is not recommended. 

If you know how to install and configure Exim4 to talk OpenLDAP server using command 'make', please write a script for configuring properly.

If not, I would like you suggest another solutions.

**Based on this [slide]("http://www.slideshare.net/jpmens/exim-and-ldap-1829032")**

---

### Post by Gone fishing on 2012-03-27
Obviously I don't know exactly what you want to do but if it is a mail sever with an ldap back end and you are not fixed on Exim but could use Postfix here are a couple of links I've always found the Howtoforge tutorials good.

[http://www.howtoforge.com/iredmail-0.6.1-open-source-mail-server-with-postfix-dovecot-amavisd-clamav-spamassassin-roundcube-on-ubuntu-10.04](http://www.howtoforge.com/iredmail-0.6.1-open-source-mail-server-with-postfix-dovecot-amavisd-clamav-spamassassin-roundcube-on-ubuntu-10.04)

[http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04](http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04)

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2)

---

### Post by peter2703 on 2012-03-28
Thank you for your suggestions. But it is not what I want. Imagine a scenario that you are developing a small web application (PHP).

The teacher want send emails to your students. All he needs is insert his email address, students' email address, subject and message.

But how to proceed the send? I was thinking to use SMTP server to send emails. That why I use Exim4 (Mail Transfer Agent - MTA). At same time, I want Exim4 lookup students' emails on OpenLDAP server.

I already installed and configured Exim4 and OpenLDAP Server. But what I didn't do yet is building Exim4 with LDAP support.

Am I clear to explain what is my problem?

Best regards.

---

### Post by Gone fishing on 2012-03-28
Sorry I haven't used Exim I have however, done exactly what you are doing using Postfix (Ubuntu / Opensuse) or Sendmail (FreeBSD), Squirrelmail and LDAP I also had the users were listed in Squirrelmail using LDAP including their group.

For Exim I found this 

[http://www.exim.org/exim-html-current/doc/html/spec_html/ch09.html](http://www.exim.org/exim-html-current/doc/html/spec_html/ch09.html)

---

### Post by peter2703 on 2012-03-28
OK. Thank you for your help.

I am not using EXIM anymore. I will install Postfix and build Postfix with LDAP support. 

Best Regards.

---

