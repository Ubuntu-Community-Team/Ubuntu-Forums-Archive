---
title: "Installing a mail server to use with a webmail client?"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by Cai_Huynh on 2013-09-03
Hello people, 
I just installed Ubuntu 12.04 and I also installed Apache2, PHP5, MySQL, PHPMyAdmin, vsftpd.
Everything is working perfectly and it's very smooth and fast.

My main goal however, is to setup a mail server so that I can send and receive mail using a webmail client such as squirrel-mail, afterlogic webmail, roundcube, atmail, etc...
Now, on windows it's pretty simple...just install Hmailserver and install the webmail scripts via php and that would be it. But on Ubuntu I have no idea what to do.

What are the steps necessary to install a mail server, so I can install my PHP mail scripts to send and receive mails?
Also, how can I setup my server so that when I send emails, it won't go into the SPAM folder of other people's email? 
By the way, my Ubuntu is from digitalocean hosting, if anyone is curious.
I'm only using the terminal to access my server.

Thank you so much!

---

### Post by mastablasta on 2013-09-03
have you seen this: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
or this: [http://askubuntu.com/questions/227209/simple-method-to-install-a-mail-server](http://askubuntu.com/questions/227209/simple-method-to-install-a-mail-server)

if you have hosting setup usually they already provide some email. if you rented the server then perhaps putting Webmin or Zentyal on it might not be a bad idea, so you can configure stuff via web GUI.

edit: another interesting option and easy GUI option: [http://www.unixmen.com/setup-mail-server-in-minutes-using-iredmail-in-ubuntu-12-10-debian-6/](http://www.unixmen.com/setup-mail-server-in-minutes-using-iredmail-in-ubuntu-12-10-debian-6/)

---

### Post by TheFu on 2013-09-03
What have you tried so far?  There are many, many how-to guides available. [http://www.howtoforge.com/](http://www.howtoforge.com/) for example.

BTW, "easy" seldom means "secure."  After doing an **apt-get install** for any service, there are usually 5-50 more steps necessary to secure it. It depends on the specific setup which can be done. None of my security friends will allow php programs on the internet for many reasons, mostly because they believe the php code has 10x more security related bugs than any other project. That means it is impossible to create a secure php application, in their minds.

If you don't want your domain to be marked as a spamming domain, do not send spam - EVER.  Do not become an open relay, don't let any of your users send spam. Have a matching forward and reverse DNS lookup, and keep the same IP address for years. DHCP subnets are almost always blocked by 90% or more of email servers.  Don't get on a spam reporting service.

Sometimes I block emails from gmail - while they are spamming - so there is no way to prevent your emails from appearing like spam.

---

### Post by SeijiSensei on 2013-09-03
[iredmail]("http://www.iredmail.org/") and [Citadel]("http://www.citadel.org/") get high marks from experienced users on this forum.

---

### Post by TheFu on 2013-09-03
> **SeijiSensei said:**
> [iredmail]("http://www.iredmail.org/") and [Citadel]("http://www.citadel.org/") get high marks from experienced users on this forum.

Never tried any of those - well, I did try Citadel about 5 yrs ago. At the time, the webUI felt like 1996. I'm sure it has changed. Probably worth a look.

Ran **SquirrelMail** for a few years - it was fine for low volume email reading. Didn't care for the addressbook much.  Lots of ISPs make this available with a cPanel install. Meh.

Installed Zimbra (MS-Exchange replacement and much more) in 2008 - never looked back again.  **Zimbra is heavy**, but **extremely full featured.**  All my users get about 100-300 emails daily and access their accounts from 3+ different devices.  Zimbra has server-side filters, so all tagging and auto-folder-moves are seen the same from all devices.  Upgrades can be stressful, since there are 20+ major moving parts.  My Zimbra server is still on "Ubuntu 10.04.4 LTS" - if that gives you an idea.  Zimbra can consolidate external email boxes too.  There are 3 different webclient modes ... Fancy/AJAX mode, simple HTML and mobile.  The fancy mode rivals gmail, just without any ads. ;)  I'm not suggesting Zimbra for anyone unless they truly need an MS-Exchange replacement. It is just too hard to setup and maintain for anything less.  The requirement for 1.5G of RAM just to setup the server is another issue.  OTOH, it uses all the F/LOSS tools we already know - postfix, tomcat, amavis, cyrus, jetty, openldap, openssl, dspam, clamav, mysql ... but each version is tightly coupled in the total Zimbra solution making it practically impossible to use different versions.

I'll never use POP again. Started using IMAP in 2000 or so - I'm completely addicted.  I have access to emails from 1996 inside my Zimbra system and searching them happens on the server-side, not the client, so searching is FAST.

More and more, I look for systems that can be easily installed via APT and don't need external PPAs.  Modifying a few config files isn't a big deal to add single-authentication store from a central LDAP DB.  Most email systems can do that too.

I need to check out the recommendations by @SeijiSensei before my next upgrade.

---

