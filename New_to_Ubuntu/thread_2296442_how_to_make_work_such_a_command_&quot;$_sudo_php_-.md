---
title: "how to make work such a command: &quot;$ sudo php -v&quot;?"
date: 2015-09-25
forum: New to Ubuntu
---

### Post by bannndi on 2015-09-25
Hi everybody,

I have installed and working PHP53 from source.

PATH is set in ~/.profile like this: "export PATH=$PATH:/usr/local/php53/bin"

$ php -v # works good
**BUT:**
$ sudo php -v # sudo: php: command not found


I needed to run "sudo composer self-update", and it gave me a message:/usr/bin/env: php: No such file or directory


$ composer -v # works good (installed globally by this manual [https://getcomposer.org/doc/00-intro.md#globally](https://getcomposer.org/doc/00-intro.md#globally)
In short: 
curl [COLOR=#A67F59]-[/COLOR]sS https[COLOR=#999999]:[/COLOR][COLOR=#A67F59]/[/COLOR][COLOR=#A67F59]/[/COLOR]getcomposer[COLOR=#999999].[/COLOR]org[COLOR=#A67F59]/[/COLOR]installer [COLOR=#A67F59]|[/COLOR] php
mv composer[COLOR=#999999].[/COLOR]phar [COLOR=#A67F59]/[/COLOR]usr[COLOR=#A67F59]/[/COLOR]local[COLOR=#A67F59]/[/COLOR]bin[COLOR=#A67F59]/[/COLOR]composer
I have similar problem with Apache22 "apachectl", but I am using full path to run with sudo. But it is a workaround, and I'd like to know, how to make it work in common.


The problem is that "$ sudo php -v" and ""sudo composer self-update"" DOES NOT WORK.

---

### Post by SeijiSensei on 2015-09-25
When you use sudo, you're using "root's" profile not your own.  Root's PATH won't have /usr/local/php53/bin in it.  You have two choices:

1) Edit or create /root/.profile and add /usr/local/php53/bin to the PATH. You'll need to use sudo to do this.

or

2) Use the complete path when you run PHP with sudo:

```
sudo /usr/local/php53/bin/php -v
```

---

### Post by bannndi on 2015-09-26
> **SeijiSensei said:**
> 
1) Edit or create /root/.profile and add /usr/local/php53/bin to the PATH. You'll need to use sudo to do this.



I added to /root/.profile new path to PHP53:
```

# ~/.profile: executed by Bourne-compatible login shells.


export PATH=$PATH:/usr/local/php53/bin


if [ "$BASH" ]; then
  if [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
fi


mesg n



```



Then I rebooted OS, and here are results for various tests:
$ echo $PATH #[COLOR=#008000] /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/apache2_2/bin:/usr/local/php53/bin[/COLOR]
$ php -v # [COLOR=#008000]works, as before[/COLOR]
$ sudo php -v # [COLOR=#ff0000]"sudo: php: command not found"
[/COLOR]

$ sudo su
# echo $PATH # /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games [COLOR=#ff0000], i.e. "export PATH=$PATH:/usr/local/php53/bin" did not have effect on $PATH.[/COLOR]
# php -v # [COLOR=#ff0000]"The program 'php' is currently not installed.  You can install it by typing:[/COLOR]
[COLOR=#ff0000]apt-get install php5-cli"[/COLOR]
# . /root/.profile 
# php -v # [COLOR=#008000]"PHP 5.3.29 (cli) (built: Sep 24 2015 13:05:17) [/COLOR]
[COLOR=#008000]Copyright (c) 1997-2014 The PHP Group[/COLOR]
[COLOR=#008000]Zend Engine v2.3.0, Copyright (c) 1998-2014 Zend Technologies"[/COLOR]

_**BUT:**_
$ sudo php -v # [COLOR=#ff0000]still, "sudo: php: command not found"[/COLOR]

As a little relief, 
$ sudo /usr/local/php53/bin/php -v # [COLOR=#008000]is working 
"PHP 5.3.29 (cli) (built: Sep 24 2015 13:05:17) 
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2014 Zend Technologies"[/COLOR]

Seems like we have at least two problems:
1. export $PATH in /root/.profile does not have effect (tested after OS reboot!)
2. even when I do "# . /root/.profile", "sudo php -v" still does not work.


OS: Ubuntu 12.04 with last updates.

[B]UPDATE:
Problem solved [/B][http://askubuntu.com/questions/678703/how-to-make-work-such-a-command-sudo-php-v](http://askubuntu.com/questions/678703/how-to-make-work-such-a-command-sudo-php-v)

---

