---
title: "Install phpbrew into system-wide environment"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by numan2 on 2015-03-19
Hi All,
**Install phpbrew into system-wide environment**

I'm following this guide: [https://github.com/phpbrew/phpbrew/wiki/Cookbook#install-phpbrew-into-system-wide-environment](https://github.com/phpbrew/phpbrew/wiki/Cookbook#install-phpbrew-into-system-wide-environment)

I ran the following command below and got phpbrew to install and I haven't used the switch command yet.
phpbrew install 5.4.38 +default +gd +bcmath +curl +hash +imap +json +mbstring +openssl +zip +zlib +apxs2 +dbs

And I'm getting stuck here:

[COLOR=#333333][FONT=Helvetica Neue]Now your php(s) will be installed under the /opt/phpbrew path, To let your users can use php(s) built by phpbrew, you need to export PHPBREW_ROOT environment in /etc/bashrc or in /etc/profile.d/phpbrew for bash users, before they load the phpbrew/bashrc file.
[/FONT][/COLOR]
export PHPBREW_ROOT=/opt/phpbrew
source /opt/phpbrew/bashrc

The error I'm getting is: -bash: /opt/phpbrew/bashrc: No such file or directory

I'm stuck...

Any help would be great!

---

