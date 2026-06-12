---
title: "Execute a perl script"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by harsh_ on 2008-06-19
I have a perl script which reboots the router and i did the following...
wrote the script, saved as .pl then:
sudo chmod +x router.pl
sudo mv router.pl /usr/bin/
Then if i fire a terminal and give the command "router"
bash returns me its favourite error;
bash:router: command not found

This is the file:
#!/usr/bin/perl

$usercommand = "reboot";

$host = "192.168.1.1";

$username = "root";

$password = "admin";

use Net::Telnet();

$t = new Net::Telnet();

$t->open($host);

$t->login($username, $password);

@output = $t->cmd(String => $usercommand,
Errmode => "return",Timeout => "1");

---

### Post by phidia on 2008-06-19
What is your path? > echo $PATH and is !/usr/bin listed in that output?
You might try running it with the full path command.

---

### Post by sdennie on 2008-06-19
Try:

```

router.pl

```

---

### Post by Nepherte on 2008-06-19
This always works for my perl scripts:
```
perl router.pl
```

---

