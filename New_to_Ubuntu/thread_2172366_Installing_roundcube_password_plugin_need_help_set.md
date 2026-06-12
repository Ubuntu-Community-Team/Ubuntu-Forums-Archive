---
title: "Installing roundcube password plugin: need help setting it up"
date: 2013-09-04
forum: New to Ubuntu
---

### Post by frankoo on 2013-09-04
Hi, i installed a mailserver on my ubuntu 12.04 server using this great tutorial: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
I even installed the roundcube mail client via: "apt-get install roundcube roundcube-mysql roundcube-plugins roundcube-plugins-extra".

During the mail-server installation i created a mail database called 'maildb' (as desrcibed near the top of the above tutorial) and after installing roundcube and adding it to my apache i just had to edit the following settings in the /etc/roundcube/main.inc.php

```

$rcmail_config['default_host'] = 'ssl://localhost:993';
$rcmail_config['smtp_server'] = 'ssl://localhost';
$rcmail_config['smtp_port'] = 465;
# keep as default or change to your mail server name
$rcmail_config['smtp_helo_host'] = '*mail.example.com*';
$rcmail_config['create_default_folders'] = TRUE;

```

It seems that roundcube allready knew where my user data was stored because it worked right from the start, without any problems.

But then i wanted to add the password plugin to allow users to change their passwords from within the roundcube client.
Basicly i had to copy the /usr/share/roundcube/plugins/password/config.inc.php.dist to /etc/roundcube/plugins/password/config.inc.php
and had to add "password" to the plugins array in the /etc/roundcube/main.inc.php.

But now to my problem, there are two settings in the /etc/roundcube/plugins/password/config.inc.php i do not know how to setup:
```

$rcmail_config['password_db_dsn'] = '';
$rcmail_config['password_query'] = 'SELECT update_passwd(%c, %u)';

```

i tried this:
```

$rcmail_config['password_db_dsn'] = 'mysql://roundcube:pass@localhost/maildb';
$rcmail_config['password_query'] = "UPDATE `users` SET `crypt` = encrypt(%c) WHERE id=%u LIMIT 1";

```

'pass' is replaced by the roundcube user password which i was forced to type in during the roundcube installation (but this worked, as i said roundcube worked right from the start).

I think there is something generally wrong with the settings. Can anyone help? And where can i find the related logs?

---

