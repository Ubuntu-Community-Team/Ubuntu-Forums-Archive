---
title: "PHP and Terminal Linux Shell combined?"
date: 2011-06-16
forum: Programming Talk
---

### Post by britoniah3480 on 2011-06-16
Hi, Is it possible for the PHP that is executed in a Terminal to send Linux Terminal commands? like clear or scan? or is it possible to send messages to PHP in a Terminal? :o

---

### Post by cgroza on 2011-06-16
I do not know about PHP, but Python has:
```
os.sysem(cmd)
```
C++ has:
```
system(const char** cmd);
```

I bet PHP has an equivalent.

---

### Post by amauk on 2011-06-16
[http://uk2.php.net/manual/en/ref.exec.php](http://uk2.php.net/manual/en/ref.exec.php)

As for executing PHP code from the terminal,
if you have the PHP CLI interpreter installed you can just do```
#!/usr/bin/php
<?php
echo "Hello"
?>
```

---

### Post by britoniah3480 on 2011-06-16
Ohh wow that was fast... but How about, hmmm

is it possible for the Linux to send parameters or commands to the PHP script while its running? thanks!

---

