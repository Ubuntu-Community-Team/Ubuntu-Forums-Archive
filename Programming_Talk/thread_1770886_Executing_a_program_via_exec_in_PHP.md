---
title: "Executing a program via exec in PHP"
date: 2011-05-29
forum: Programming Talk
---

### Post by farmdve on 2011-05-29
I am using Ubuntu 11.04 running XAMPP 1.7.4 running as sudo i.e super user.

Due to the nature of my application i need to run a program via exec. Believe me, i tried every possible combination and it did not work.

[PHP]
<?php

$blah = exec("sudo -u root | echo *mypassword* | ./myapplication commandtobepassedhere", $test);


var_dump($test);
var_dump($blah);

?>[/PHP]

This basically works OK in the Terminal, but via php it just doesnt work. I've tried direct path to the program, i copied over the binary to my htdocs folder and tried via the function above, no dice it just won't run.

The result i get is [PHP]array(0) { } string(0) ""[/PHP]. But the result i should get, is waaay more than that.

Where is the problem? Exec is not disabled, other programs like dir,whoami work,but not that one.

---

### Post by LoneWolfJack on 2011-05-29
to be blunt, the problem is that you didn't read the documentation. exec() only returns the last line of the output, which is probably empty.

use passthru() or shell_exec() instead.

---

### Post by farmdve on 2011-05-29
Passthru is even worse. It gives me just NULL.

And exec does this
> If the output argument is present, then the specified array will be filled with every line of output from the command. Trailing whitespace, such as \n, is not included in this array. Note that if the array already contains some elements, exec() will append to the end of the array. If you do not want the function to append elements, call unset() on the array before passing it to exec().

---

### Post by LoneWolfJack on 2011-05-29
try shell_exec.

also, it's possible that the PHP process is not in the sudoers list.

---

### Post by farmdve on 2011-05-29
Can you elaborate? I am still pretty new to Linux in general.

---

### Post by LoneWolfJack on 2011-05-29
my apologies, that'll teach me to never lash out at someone without having first double-checked the documentation myself. ;)

---

### Post by LoneWolfJack on 2011-05-29
only user that are on the sudoers list can use sudo.

your PHP process probably runs under the apache user, which should be www-data. if you want to use sudo through PHP, www-data needs to be on the sudoers list.

---

### Post by farmdve on 2011-05-29
I don't really want to run sudo in exec, i just want to be able to make the program run, which it doesnt.

---

### Post by farmdve on 2011-05-29
Well, i added www-data to /etc/sudoers.tmp, but still no dice. The program does not run. It is also set to run as a program in it's properties, so it's not that.

---

### Post by LoneWolfJack on 2011-05-30
have you tried breaking down your command into single parts to see where exactly it starts failing?

---

### Post by SeijiSensei on 2011-05-30
Try running the program from the command prompt as the www-data user like this:

```

$ sudo su
[enter password]
# su www-data            <== now you're becoming the www-data user
$ /path/to/the/program 
$ exit

```

Does it work?  Does the program have executable permissions for everyone?  

Also you can't pass the password to sudo via echo.

---

