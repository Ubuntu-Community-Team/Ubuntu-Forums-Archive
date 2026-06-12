---
title: "Ubuntu's Insane Apache Configuration System"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by cheesedude on 2014-06-27
I'm an Ubuntu newbie.  I was excited to discover that Ubuntu supported Apache 2.4 and PHP 5.5 with 14.04 LTS because a few months ago only ancient Apache 2.2 and PHP 5.3 was in the repo for 12.04 LTS.  Then I installed Apache via apt-get and was appalled when I found out about Ubuntu's ridiculous method of changing configuration settings.  I cannot believe that anyone took something as simple as removing a pound sign from a line in a configuration file and turned it into a2enmod, a2dismod, a2ensite, a2dissite, and a2enconf, a2disconf and dozens of (instead of a few) config files.  Is the best part that many of the config files only contain one line or that you have to have a symlink in one folder to activate the configuration in the other folder?

Who in their right mind would have conceived of something like this?  They took something so simple a child could understand it and made a monstrosity out of it.  Is there any way to disable this insanity and go back to the simple, basic Apache configuration files?  Installing programs with the apt-get package manager is very easy.  Compiling Apache is a headache I wanted to avoid.  When I compiled Apache, the compilation process may have been time consuming and fraught with errors, but at least the final product was something simple and basic.  I cannot understand why anybody would take something like a basic Apache setup and mess it all up.

I was hoping to avoid compiling my own software.  But stuff like this blows my mind.  I need a direction to go in.  Am I stuck compiling everything myself so I can have something that hasn't been turned into a monster?

---

### Post by tgalati4 on 2014-06-27
Frameworks change over time.  Perhaps the change was made to better support virtual machines or cloud computing.  A similar thing happened to /etc/network/interfaces and sleep/suspend scripts, upstart and init.d.  Simple frameworks don't have the flexibility to work with new computing architectures--so the frameworks get complicated.

Compiling an older version to maintain compatibility might be your only option.  Or learn the new framework.

---

### Post by monkeybrain20122 on 2014-06-27
> **cheesedude said:**
> 
Who in their right mind would have conceived of something like this?  They took something so simple a child could understand it and made a monstrosity out of it.  Is there any way to disable this insanity and go back to the simple, basic Apache configuration files?  Installing programs with the apt-get package manager is very easy.  Compiling Apache is a headache I wanted to avoid.  When I compiled Apache, the compilation process may have been time consuming and fraught with errors, but at least the final product was something simple and basic.  I cannot understand why anybody would take something like a basic Apache setup and mess it all up.


It is Debian. But it has its advantages once you get the hang of it, it keeps things modular and the advantage comes when you have a lot of modules. I wouldn't want to look at a huge httpd config file.

---

### Post by SeijiSensei on 2014-06-27
If you want a more vanilla Apache installation, I suggest switching to a RedHat-flavored distribution like [CentOS]("http://www.centos.org/").

---

### Post by tgalati4 on 2014-06-27
Or use a [http://bitnami.org](http://bitnami.org) stacks approach and install a semi-configured application with most of the configuration already done--just add eyebrows.

---

### Post by bobnn on 2014-06-28
I too have been amazed/puzzled at what Debian does to the configurations of "standard" middleware.  What they did to the eminently readable Postfix configuration main.cf should be illegal.

Still, it's hard to beat these repositories.

---

