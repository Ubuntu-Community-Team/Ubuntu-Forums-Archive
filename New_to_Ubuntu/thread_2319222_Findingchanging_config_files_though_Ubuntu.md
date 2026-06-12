---
title: "Finding/changing config files though Ubuntu"
date: 2016-04-02
forum: New to Ubuntu
---

### Post by pipa2 on 2016-04-02
Hi There,

I have to change "/etc/php.ini" in my Ubuntu 14.0.4. to "extension_dir = /etc/php.d.

Tried to do it, but I get an error saying no such a file...

and also need to activate MySQL extension via /etc/php.d/mysql.ini

";Enable my sql extension module
extension=mysql.so"

But I don't find this directory in my Ubuntu install except for "apache2,  cgi,  cli , mods-available"

I would appreciate your help.

Thanks, Pipa.

---

### Post by mcduck on 2016-04-02
Could you give a link to the instructions you are trying to follow? Those don't really seem to make much sense, php.ini is a file, while "extension_dir = /etc/php.d" looks like a configuration option that should be added to some file. Also based on the missing file warning (which is correct,a s that's not where php.ini is located on Ubuntu) I'd guess the instructions are for some other Linux distribution. (Ubuntu has two php.ini files, one in /etc/php5/Apache2 directory, and the other in /etc/php5/cli directory. As you may guess, one is for web server, the other for running PHP scripts in command line)

...also I have the feeling that what you are trying to do is going to be simpler than the instructions you are following now. :D

---

### Post by pipa2 on 2016-04-03
Hi mcduck,

Thanks for your reply. I Just need to follow the instructions from this link and be able to re-configure my PHP,  MySQL & SNMP as per instructions here(running Cacti), I'm running Ubuntu 14.04 Desktop LTS. Would be great if you could guide me through: [http://www.cacti.net/downloads/docs/html/unix_configure_php.html](http://www.cacti.net/downloads/docs/html/unix_configure_php.html)  

Thanks, Pipa

---

### Post by bab1 on 2016-04-03
> **pipa2 said:**
>  I Just need to follow the instructions from this link and be able to re-configure my PHP,  MySQL & SNMP as per instructions ..., I'm running Ubuntu 14.04 Desktop LTS.
You would probably be better off using instructions for Linux, preferably Ubuntu, rather than BSD Unix which is what you are referring to above..  The reason you can't find the files and directories that you are looking is that they do not exist or are located elsewhere.  Unix is definitely not Linux. 

I'd try this tutorial: [**[http://lintut.com/how-to-install-cacti-monitoring-tool-on-ubuntu-linux/](http://lintut.com/how-to-install-cacti-monitoring-tool-on-ubuntu-linux/)**]("http://lintut.com/how-to-install-cacti-monitoring-tool-on-ubuntu-linux/")

---

### Post by mcduck on 2016-04-03
Agreed, that instruction looks much more likely to give you correct commands & files to edit for Ubuntu.

Also the official server guide has really good instructions (couldn't spot Cacti there, though, but should help you if you need to tweak anything with PHP or MySQL or something: [https://help.ubuntu.com/lts/serverguide/]("https://help.ubuntu.com/lts/serverguide/")

---

