---
title: "useradd &amp; smbpasswd script"
date: 2008-03-17
forum: Programming Talk
---

### Post by ant2ne on 2008-03-17
Basically what I'm wanting to do is create a script to help automate adding users to the samba system. 
```
#!/bin/sh
#smbadd.sh
echo "Please enter the new system and samaba user's name:"
   read name
echo "Please enter password for $name:"
   read pass
   echo "Making $name a system  and samba user"
echo $pass > useradd -p $name 
echo $pass > smbpasswd -a -s  $name

```

Problems...

1> Obviously this script has some lines that require sudo. I'd like to run this script with the sudo command by entering "sudo smbadd.sh" in the terminal. Then it would prompt me for my password, and then continue the script.

2> It seems that useradd or adduser doesn't take variables well... or I'm doing something wrong here.

---

### Post by mssever on 2008-03-17
> **ant2ne said:**
> 
```
 echo $pass > useradd -p $name 
echo $pass > smbpasswd -a -s  $name
```

Try this: ```
echo "$pass" | useradd -p "$name"
echo "$pass" | smbpasswd -as "$name"
```> is for redirecting to a file descripter. | is for pipes, which is what you want.

Also, be sure to quote your variables. They could contain spaces and mess up your script.

EDIT: Re: problem 1--Just do as you said, and all will be fine.

---

