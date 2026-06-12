---
title: "PHP have different behaviour inside and outside apache?"
date: 2013-04-12
forum: Programming Talk
---

### Post by rrrobles on 2013-04-12
When I run the following code through command-line PHP:

[PHP]<?php
  if ($db = ibase_connect('localhost:/opt/firebird/examples/empbuild/employee.fdb', 'sysdba',
  'masterkey')) {
    echo 'Connected to the database.';
    ibase_close($db);
  } else {
    echo 'Connection failed.';
  }
?>[/PHP]

It works.

But when I run it through Apache, in the navigator, it generates a internal server error.

If I do not use ibase functions it works.

Using Ubuntu 11.10, Firebird 2.1, Apache 2.2.20

Any ideas?:confused:

---

### Post by rrrobles on 2013-04-12
Solved by adding "ServerName localhost" at /etc/apache2/apache2.conf.

---

