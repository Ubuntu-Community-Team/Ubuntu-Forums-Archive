---
title: "script help"
date: 2010-05-16
forum: Programming Talk
---

### Post by Quashie on 2010-05-16
I am only beginner unix. I hope someone can help me for this.
I'd like to allow user to change the file permission. here is my script

echo "Do you want to change the file permission?(y/n)\c"
read answer
if test [$answer] = y
then 
echo "Input the filename:\c"
read answer
then 
                               #this line should the file permission change for user,group,other
else
sort who                            # alphabetized who 

The blank command should i put ypmatch command?
really get stuck for this.

Thanks for reading 

Thanks for helping me and I am really appreciate.

---

### Post by hannaman on 2010-05-16
Do you want them to be able to change permissions, ownership or group?
The chmod command handles permissions;
```
chmod 777 filename
```
or
```
chmod u+r filename
```
These are only examples, type "man chmod" at the command line for a more detailed explanation.

The chown command can change user and group ownership.  Some examples;
```
chown user:group filename
chown user filename
```
The chgrp command can be used to change the group ownership.

A regular user will not be able to change ownership on files that they do not own.  To do that, you would have to have sudo permissions.

For your test, you would only use the word test or the [], but not both.
```
if [ $answer = y ]; then
```

---

### Post by Quashie on 2010-05-16
> **hannaman said:**
> Do you want them to be able to change permissions, ownership or group?
The chmod command handles permissions;
```
chmod 777 filename
```
or
```
chmod u+r filename
```
These are only examples, type "man chmod" at the command line for a more detailed explanation.

The chown command can change user and group ownership.  Some examples;
```
chown user:group filename
chown user filename
```
The chgrp command can be used to change the group ownership.

A regular user will not be able to change ownership on files that they do not own.  To do that, you would have to have sudo permissions.

For your test, you would only use the word test or the [], but not both.
```
if [ $answer = y ]; then
```

When I execute my script, I want the user who run it can change the file permission whether it is owner,group or others. Then, after the user change the file permission, it should display the file new permission (ls -l filename).

thanks

---

### Post by hannaman on 2010-05-16
What do you want them to change the permissions to?  Something like
```
chmod 644 $answer
```
would set the file to -rw-r--r--.  Again a regular user would only be able to change the permissions on file that they own.  Maybe you should check to see if the user running the script owns the file before trying to change the permissions.  

The yp commands (ypmatch, etc.) are legacy NIS commands, are you doing this a NIS environment?

---

### Post by Quashie on 2010-05-16
> **hannaman said:**
> What do you want them to change the permissions to?  Something like
```
chmod 644 $answer
```
would set the file to -rw-r--r--.  Again a regular user would only be able to change the permissions on file that they own.  Maybe you should check to see if the user running the script owns the file before trying to change the permissions.  

The yp commands (ypmatch, etc.) are legacy NIS commands, are you doing this a NIS environment?

I know how to change it without doing script to execute.

The following problem is display a listing of the user's directory and allow permission change. Prompt the user to change file permission (y/n). If yes, prompt the user for the file name. Display the file's permission. Ask the user to enter the add or remove the following permission: read the user, write user, execute user, read group, write group, execute group, read other, write other and execute other. After file permission have been changed, display the file's new permission.

Here is the script :    
   ```

```   1 echo -n "Enter file name : "
      2 read file
      3 chmod 777 $file
      4 [ -w $file ] && W="write = yes" || W="Write = no"
      5 chmod 777 $file
      6 [ -x $file ] && X="Execute = yes" || X="Execute = No"
      7 chmod 777 $file
      8 [ -r $file ] && R="Read = yes" || R="Read = No"
      9 echo
     10 echo "$file permissions"
     11 echo "$W"
     12 echo "$R"
     13 echo "$X"```

```

I have been trying whole day to solve it. 

Thanks for your help.

---

### Post by soltanis on 2010-05-17
First of all, it's not very clear why you are writing a script to do this, could you clarify that for us?

Second, please enclose your code inside ```
 tags (click the # sign in the post editor); it makes it easier to read. Compare:

#!/bin/sh
echo this is code not inside a code tag
if [ -e "it is hard to read" ]; then
    echo the formatting is not so great either
fi

[code]
#!/bin/sh
echo this is code not inside a code tag
if [ -e "it is hard to read" ]; then
    echo the formatting is not so great either
fi

```

Third, if you are just trying to add or remove the read/write/execute flags I suggest that instead of using the octal modes you use the

```

chmod +x # set exec bit
chmod -x # unset exec bit, etc

```

method for running chmod.

---

### Post by Quashie on 2010-05-17
[/CODE][/CODE][/CODE]> **soltanis said:**
> First of all, it's not very clear why you are writing a script to do this, could you clarify that for us?

Second, please enclose your code inside ```
 tags (click the # sign in the post editor); it makes it easier to read. Compare:

#!/bin/sh
echo this is code not inside a code tag
if [ -e "it is hard to read" ]; then
    echo the formatting is not so great either
fi

[code]
#!/bin/sh
echo this is code not inside a code tag
if [ -e "it is hard to read" ]; then
    echo the formatting is not so great either
fi

```

Third, if you are just trying to add or remove the read/write/execute flags I suggest that instead of using the octal modes you use the

```

chmod +x # set exec bit
chmod -x # unset exec bit, etc

```

method for running chmod.

Should I put like this?
```

code]
#!/bin/sh
echo this is code not inside a code tag
if [ -e "chmod +x" ]; then
    echo ......
fi

```

---

