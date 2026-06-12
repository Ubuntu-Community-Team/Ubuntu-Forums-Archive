---
title: "Postfix help...."
date: 2008-09-25
forum: New to Ubuntu
---

### Post by kmgriffith102 on 2008-09-25
Hello,

I am trying to set up a mail server using postfix.  When I try to install the packages for postfix per the Ubuntu Bible, I get the following errors:

E: postfix: subprocess post-installation script returned error exit status 75
E: mailscanner: dependency problems - leaving unconfigured
E: mailx: dependency problems - leaving unconfigured
E: postfix-mysql: dependency problems - leaving unconfigured
E: postfix-cdb: dependency problems - leaving unconfigured
E: qpopper: dependency problems - leaving unconfigured

Afterwards, i do not see postfix available in my gui menus.  I really don't know what to do.  is postfix the easiest to use?  Does it have a gui?  Are there easier alternatives?  Help :(

---

### Post by hyper_ch on 2008-09-25
how do you try to install it?

Postfix is a server... it is being started - normally - when you turn on the computer. there's no gui for it.

---

### Post by scorp123 on 2008-09-25
> **kmgriffith102 said:**
>  I am trying to set up a mail server using postfix ... Afterwards, i do not see postfix available in my gui menus. That's kind of a contradiction. Rarely any server program has a GUI ... why would it even need one? A server process is supposed to run on a server, and a server is usually a machine that has no keyboard and no mouse and no user sitting in front of it ... so why would it then need a GUI?

You can of course install server programs on your desktop system, but in that case you should at least know what you do and why you do it ... which leads me to this question: Why exactly do you think you need to install postfix and what exactly did you want to use it for?

---

### Post by kmgriffith102 on 2008-09-25
> **scorp123 said:**
> which leads me to this question: Why exactly do you think you need to install postfix and what exactly did you want to use it for?

I set up a web server with apache.  I have the site up and running, and now I want to be able to receive emails based on my domain, so I was going to use my own mail server.

After I have the server running, what do I need to be able to retreive the received emails?  how do I setup email accounts?  I thought there was a gui like exchange where you can set all parameters and mail settings for postfix.  I found some screenshots, and I thought that's what it was....

[http://cpplus.info/docs/screenshots/postfix_config_new.gif](http://cpplus.info/docs/screenshots/postfix_config_new.gif)

---

### Post by kmgriffith102 on 2008-09-25
[QUOTE=hyper_ch;5854767]how do you try to install it?[QUOTE]

I use the synaptic manager.  (is that right?)

---

### Post by hyper_ch on 2008-09-25
have a look through here:  [http://howtoforge.com/perfect-server-ubuntu8.04-lts](http://howtoforge.com/perfect-server-ubuntu8.04-lts)

---

### Post by kmgriffith102 on 2008-09-25
> **hyper_ch said:**
> have a look through here:  [http://howtoforge.com/perfect-server-ubuntu8.04-lts](http://howtoforge.com/perfect-server-ubuntu8.04-lts)

Thanks!

---

