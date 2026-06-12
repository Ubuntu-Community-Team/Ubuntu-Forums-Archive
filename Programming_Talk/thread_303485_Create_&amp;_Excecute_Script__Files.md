---
title: "Create &amp; Excecute Script  Files"
date: 2006-11-20
forum: Programming Talk
---

### Post by usrtom1 on 2006-11-20
I have written 100's of data collection and sorting Unix Scripts but can't get to 1st base w/ Dapper Drake  6.06.1. Ought to be easy.

Need help and working simple examples
1  Visual Text Editor How to obtain?

2  Ability to create executable script files in /usr/tom
   Want to use 'for file in'  constructs

3  Ability to become su: Does sudo do the job.

Thanks, Tom

---

### Post by Ramses de Norre on 2006-11-20
1) gedit or kate, one of these should be installed by default.
2) give them the right extension and give them x permissions (through nautilus or chmod).
3) sudo -s

---

### Post by usrtom1 on 2006-11-20
Thanks for the hint on gedit and sudo -s
I have created 'test' in /usr/tom with gedit, which now contains:

echo "Hello World"
exit

I have changed its mode with sudo chmod +x test

when I type from withing /usr/tom 'sudo test'
Nothing happens, no error, etc.??  I assme stdout
is the default.

---

### Post by dbott67 on 2006-11-20
You have to prefix the file with './'

For example, to execute the file 'test', you would type:
```
./test
```

---

### Post by usrtom1 on 2006-11-20
At last!!!  Thanks a bunch!!  this reminds me of the famous topic: 'Things you don't learn at the Harvard Business School'
Now I belong to the secret society of scripters.

---

### Post by dbott67 on 2006-11-20
You're welcome.

For those coming across this thread in the future, by default Linux only searches certain directories when trying to execute files:
```
dbott@edgy:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

Linux does not search the current working directory, so your need to do one of 3 things:

1. Type in the complete path to the file: /path/to/file

2. Preface the file with './' (assuming the file is in the current directory)

3. Add the present working directory to the '[search path]("http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=329")' variable (found in ~/.bash_profile) using [this method]("http://heron.tc.clarkson.edu/~horn/classes/comm444/bash_profile.html").

-Dave

---

### Post by Ramses de Norre on 2006-11-20
> **usrtom1 said:**
> Thanks for the hint on gedit and sudo -s
I have created 'test' in /usr/tom with gedit, which now contains:

echo "Hello World"
exit

I have changed its mode with sudo chmod +x test

when I type from withing /usr/tom 'sudo test'
Nothing happens, no error, etc.??  I assme stdout
is the default.

That's why I told you to give them the right extension, if you call the file test.sh you will be able to call it with test.sh.

---

### Post by dbott67 on 2006-11-20
> **Ramses de Norre said:**
> That's why I told you to give them the right extension, if you call the file test.sh you will be able to call it with test.sh.

You still need the ./ unless you save the file in one of the 'search paths'.

```
dbott@edgy:~$ echo "hello world" > test.sh

dbott@edgy:~$ chmod 755 test.sh

dbott@edgy:~$ ls -all test.sh
-rwxr-xr-x 1 dbott dbott 20 2006-11-20 16:46 test.sh

dbott@edgy:~$ test.sh
-bash: test.sh: command not found

dbott@edgy:~$ ./test.sh
hello world
```

-Dave

---

### Post by Ramses de Norre on 2006-11-20
Ow it seems you're right, I'm sorry =)

---

### Post by dbott67 on 2006-11-20
> **Ramses de Norre said:**
> Ow it seems you're right, I'm sorry =)

I figure if I answer enough threads, I'm bound to be right one of these times! :)

---

### Post by mssever on 2006-11-20
I always use a shebang line in every executable script file. That way the script is portable and is executed by the proper interpreter. (A shebang line is the first line in the file. It begins with #! and the path to the interpreter.)

Some examples: 
```
#!/bin/bash
#!/usr/bin/env ruby
#!/usr/bin/env perl
#!/usr/bin/env python
```

BTW, extensions in Linux are merely for the convenience of humans looking at files. Linux ignores them when attempting to determine their type. That's what the shebang is for. Since Linux executables traditionally are extensionless. I never use extensions in executable scripts. But you're welcome to do it however you like; Linux doesn't care. You could use bash_script.jpg for that matter.

---

