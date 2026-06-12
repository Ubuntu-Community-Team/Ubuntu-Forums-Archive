---
title: "Running Bach script using PHP"
date: 2007-09-13
forum: Programming Talk
---

### Post by mohtasham1983 on 2007-09-13
Hi ubuntuers or linuxers,

I have been having problem executing system commands using php and haven't figured it out yet, although I have tried different ways. Let me describe my problem from the beginning.

I used the following command to execute ls command to obtain a list of files and directories in /var/www/ which is the root directory for apache:

[PHP]
$var=exec("ls",$ret);
foreach($ret as $data)
     print $data;
[/PHP]

This command works as I expect, but when I try to run a command which makes a change in the system I go in trouble. For example, creating a directory in my home directory seems to be impossible by issuing following command:

[PHP]$var=exec("mkdir /home/myname/new_directory",$ret);[/PHP]

However, issuing mkdir command when the new directory is within apache root directory creates a new directory successfully. For instance, the following command works as expect:

[PHP]$var=exec("mkdir new_directory",$ret);[/PHP]

That is, I decided to forget about running system commands using php and instead write my own script in bash, place it inside apache root directory and execute it using one php system command.

My bash script looks like this:

script.sh
```
#!/bin/bash
mkdir /home/myname/directory
```

I used the following command to execute my bash script:
[PHP]$var=exec("script.sh",$ret);[/PHP]

But, in my wonder this command doesn't create the new directory in my home directory; however, changing script to "mkdir directory" creates the new directory in the same path as php file.

I would like to mention that mkdir is just a test. Actually I want to execute a series of commands for getting information about some print jobs. I guess if I find out how to get mkdir command working, the rest would be quite easy.

I really appreciate your time reading my post.

Thanks in advance.

---

### Post by nesh87 on 2007-09-13
if i wanted to run a system command, and i do that alot (i like using php-cli) use the "`" key.
its the back tick, depending on your laptop, it should be next to number 1

[http://www.php.net/language.operators.execution](http://www.php.net/language.operators.execution)

---

### Post by Mirrorball on 2007-09-13
I think it's a permission issue. Apache doesn't have the permission to create a new directory in your home directory.

---

### Post by robert_pectol on 2007-09-13
The user under which apache runs, does not have permission to do it.  You'll need to take steps to allow the script to be executed with elevated privs.  Unfortunately this opens possible security vulnerabilities.  Perhaps with the clever use of sudo within your script, you can limit the damage potential while allowing the script to do what it needs.  Just be careful and keep security in mind otherwise someone may find a way to exploit it.  Good luck!

---

### Post by mohtasham1983 on 2007-09-13
Basically this application is used on a secure network, so there s nothing to worry about security.

As I mentioned in my post, I was just trying to test if I can execute any command outside apache directory.

In fact, I want to release print jobs held in cups using:
```
lp -i jobid -H resume
```

I also would like to mention that, there is no permission issue, since I have added the php username to sudors and gave all rights. I have tested it by issuing a root command and it was working fine for receiving information about some files that were read only by root directory. 

I really appreciate if you let me know how I can enable apache so that it can executed above command.

---

