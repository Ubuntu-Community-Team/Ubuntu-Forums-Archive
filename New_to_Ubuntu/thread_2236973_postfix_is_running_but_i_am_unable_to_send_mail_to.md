---
title: "postfix is running but i am unable to send mail to gmail accounts"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by chandrasekhar3 on 2014-07-30
Hi everyone,

        I have configured postfix in ubuntu 12.04LTS through gmail smtp and postfix is running but i am unable to send mails to gmail accounts,

        Is there any configuration problem or any other, please suggest for this thread.

       sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration...                                                                                                      [ OK ]

  I am trying to send mail using this below syntax.....

echo "Test mail from postfix" | mail -s "Test Postfix" [email]fortestvt@gmail.com[/email]

postfis status, postfix check is working normally

---

### Post by llamabr on 2014-07-31
So what error do you get?

---

### Post by smtp on 2014-07-31
Please provide sudo tail -n20 /var/log/mail.info

---

### Post by chandrasekhar3 on 2014-08-01
Here I am not getting any error and postfix status is loading fine but unable to send mails, Is there any configuration problem like sudo vim /etc/postfix/main.cf or sudo vim /etc/postfix/sasl_passwd,
what you will suggest me?

---

### Post by chandrasekhar3 on 2014-08-01
Hi

    I didnot find any mail.info file in /var/log/ , so is there any configuration problem.

---

### Post by SeijiSensei on 2014-08-01
The file is called /var/log/mail.log.

Many ISPs block outbound SMTP transactions by their customers to cut down on spam.  You need to ask your ISP if they allow connections to port 25 on remote servers.  Often ISPs have Terms of Service that forbid the use of servers.  If you're on a residential rather than a business-class Internet service, you need to read your ToS and talk to your ISP.

---

### Post by nerdtron on 2014-08-01
Or if you want to use a gmail.com account to send emails from the command line, see this: [http://ubuntuforums.org/showthread.php?t=2236998](http://ubuntuforums.org/showthread.php?t=2236998)

---

