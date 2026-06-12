---
title: "what do the ````` marks do?"
date: 2010-03-30
forum: Programming Talk
---

### Post by garyed on 2010-03-30
I know this is going to sound stupid but what do those `` marks do. All I know is they make things work but I don't know why. 
I had a php script where I wanted to execute a command that normally would work in the terminal but wouldn't work in my php script until I surrounded the command like this: `command` 

why would this work,
```
<?php `mysql -h $host -u $usr -p$pwd $db2 < $sql` ?>
```
and not this?
```
<?php exec('mysql -h $host -u $usr -p$pwd $db2 < $sql'); ?> 
```

---

### Post by nvteighen on 2010-03-30
> **garyed said:**
> I know this is going to sound stupid but what do those `` marks do. All I know is they make things work but I don't know why. 
I had a php script where I wanted to execute a command that normally would work in the terminal but wouldn't work in my php script until I surrounded the command like this: `command` 

why would this work,
```
<?php `mysql -h $host -u $usr -p$pwd $db2 < $sql` ?>
```
and not this?
```
<?php exec('mysql -h $host -u $usr -p$pwd $db2 < $sql'); ?> 
```

I have no idea on PHP, but backticks (``) are used in bash and other shell scripting languages to execute a command and pass its output into the command in which the backticked line is contained. I had no idea PHP could do this, anyway.

---

### Post by Hellkeepa on 2010-03-30
HELLo!

In PHP it's the same as "shell_exec ()", exactly the same as in bash (in fact, I wouldn't be surprised if it actually used bash as the shell).
However the reason the second block didn't work is because you used single quotes, and not double quotes. Variables are only expanded in double quotes, and not in single quotes. There they're read as litteral text, meaning that you tried to run the command *exactly* as it reads.

Though, that said: Why in $deity's name use the shell client to execute a SQL query, and not the build in methods? The method you've used will expose the password, username, and everything to "top", "ps" and all other such methods.

Happy codin'!

---

### Post by garyed on 2010-03-30
> **Hellkeepa said:**
> HELLo!

....
Though, that said: Why in $deity's name use the shell client to execute a SQL query, and not the build in methods? The method you've used will expose the password, username, and everything to "top", "ps" and all other such methods.

Happy codin'!

Funny you should ask.
I run a LAMP server on my home computer & also have a cheap web host(1and1). So cheap that their Phpmyadmin panel does not allow importing a mysql database only exporting. But uploading the msql dump files to the web host server & that php file to the same directory I can just run the php file to import my databases. I then delete the file from the server for security reasons until I need it again. There's probably a simpler way but I couldn't figure out anything better. 

Thanks again to all for the help.

---

### Post by Hellkeepa on 2010-03-30
HELLo!

Ah, then I understand.
*Pats your shoulder in sympathy.*

Happy codin'!

---

### Post by cubeist on 2010-03-30
FYI - Back ticks for command substitution are being phased out in Bash.  The alternative is
```
$(*command*)
```

---

