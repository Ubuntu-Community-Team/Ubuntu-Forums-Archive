---
title: "Novice User Network Tools Script"
date: 2010-05-12
forum: Programming Talk
---

### Post by ravagilli on 2010-05-12
During the past 5-6 weeks I have been working in a new post as a trainee UNIX Systems Administrator.  My manager has gained a lot of confidence in my work and has asked me to prepare a set of utilities for novice users which can all be run from a single menu interface. 



Only one problem, i haven't really got any idea how to achieve the finished result!!! I've had a little go and what i've done so far is in the code box below. Any help would be greatly appreciated.





Stage 1  Must have the following functionality:

-	Produce a script which displays menus.

-	The menu must initiate commands in response to user input.

-	The following commands should be implemented:

o	List the current directory

o	List the current users on the system

o	List the current network settings

o	Display the users current user name





Stage 2  Must have the functionality of stage 1 in addition to the following:

-	The menu must loop repeatedly until the user chooses an option to quit

-	The code must be divided into appropriately named functions which are called from the menu

-	The following commands should be implemented:

o	List the current directory in detailed format listing all permissions 

o	List the current network settings with all details displayed

o	List all currently running processes 





Stage 3  Must have the functionality of stages 1 and 2 in addition to the following:

-	The menu must clear the screen before redisplaying itself 

-	Perform all the options listed in stage 2

-	Give the option to create a zipped version of a directory. The user must be given the option to supply the name of the directory to be zipped and the name of the zipped file.

-	Give the option to unzip a zipped file. The user must be given the option to supply the name of the zipped file and the directory for the contents to be extracted to.





```
#!/bin/bash

echo -n "Please select from the following:

A) List the current directory
B) List the current users on the system
C) List the current networking settings
D) Display the users current user name

:"

read ***
case $*** in
A) who ;;
B) who ;;
C) ifconfig ;;
D) whoami ;;

*)echo "Not in list:";;
esac
```

---

### Post by ravagilli on 2010-05-13
Only 41 views!! I thought this would be a simple thing and that somebody would be able to help me almost instantaneously. Oh well maybe not. Is it in the correct category??

If anybody could help or indeed point me in the right direction i would appreciate it massively!!

---

### Post by cariboo on 2010-05-16
You may get some better results here.

---

### Post by soltanis on 2010-05-17
Bash does not seem like the proper tool to do this job. Are you familiar with Perl or Python?

---

### Post by ja660k on 2010-05-17
dude, this is simple.
and can be in any scripting language, 
because you already started in bash, use bash.
**If you need to do some filtering of data... then use Perl or python**
But if you just want to print the result as the command gives, use bash

to run a command in bash, use backticks eg:
```

#!/bin/bash

echo `cat /etc/passwd`

```
in perl
```

#!/bin/perl -w
use strict;
use warnings;

print `cat /etc/passwd`

```
just an example =)
print everything in /etc/passwd, you can store this into var, do some string manipulation.

run these in terminal:

list the current directory = "ls"
list users in the system = "who"
what kinda network settings?
current username = "echo $USER"

I know all of these, but i think the point of this is for **YOU** to learn the commands and what they do...

read some man pages, do some googling, and learn. dont just ask on the forums =)

---

### Post by hannaman on 2010-05-17
If you want to use bash, take a look at the select statement.
A quick google search yielded this page which has enough information to get you started:
[http://www.softpanorama.org/Scripting/Shellorama/Control_structures/select_statements.shtml](http://www.softpanorama.org/Scripting/Shellorama/Control_structures/select_statements.shtml)

---

### Post by ravagilli on 2010-05-23
Thanks everyone for the info. It has been greatly appreciated. It has helped me massively.

---

