---
title: "PHP's system() Function and Local Commands"
date: 2007-08-28
forum: Programming Talk
---

### Post by xluryan on 2007-08-28
I'm trying to write a very simple PHP file for my server to call a few commands on my computer. However, this seems a bit hit-or-miss right now.

Some commands work, like 'system("uptime");', or 'system("ls -l");':
```

From the uptime command:

10:45:13 up 3 days, 11:38, 2 users, load average: 0.00, 0.00, 0.00

```

But when I try and use something like 'system("cat temp.txt");', I get nothing. I know the file exists, and the permissions are rwxrwxrwx. The file is in the root directory of my apache server root (/var/www/temp.txt).

Here is my PHP file:

```

<html>
<body>
<?php
      system("cat temp.txt");
?>
</body>
</html>

```

Any ideas?

---

### Post by xluryan on 2007-08-28
Ok well, easy fix here... I moved temp.txt to the same directory as the PHP file and now it does 'cat' the contents. However, the following PHP script still doesn't work.

```

<html>
<body>
<?php
      system("gnome-screensaver-command -q");
?>
</body>
</html>

```

Any ideas with that one?

---

### Post by xluryan on 2007-08-28
Ok, well I edited that script as follows:

```

changed:
system("gnome-screensaver-command -q");

to read:
system("gnome-screensaver-command -q 2>&1");

```

That will redirect stderr to stdout, and then I get the following:

```

** Message: Failed to connect to the D-BUS daemon: Failed to execute
dbus-launch to autolaunch D-Bus session

```

Any ideas now?

---

### Post by xluryan on 2007-09-22
Bump.

---

### Post by altonbr on 2007-09-22
Why not use:

```
shell_exec("cat temp.txt");
```
instead? Or
```
`cat temp.txt`
```
as it does the same thing.

From [http://www.php.net/shell_exec:](http://www.php.net/shell_exec:) 
> shell_exec &#8212; Execute command via shell and return the complete output as a string

---

### Post by xluryan on 2007-09-22
Hmm, interesting. I'll try that and post back with the results :)

---

