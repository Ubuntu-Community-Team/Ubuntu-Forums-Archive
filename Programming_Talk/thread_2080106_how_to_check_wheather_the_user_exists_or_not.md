---
title: "how to check wheather the user exists or not??"
date: 2012-11-03
forum: Programming Talk
---

### Post by Mohan1289 on 2012-11-03
hi how can we check weather the user exists or not??

do we have to check the /home directory??

what i want is

echo "Enter username"
read u
if [ "$u" exists "/home/$u"]; then 

echo "User Exists"

is it ok??? and how can i check whether the directory at home directory exists or not??

is checking in **home** directory enough??? or do i have to check /etc/group file??

or do i have to check something else??

---

### Post by spjackson on 2012-11-03
To check whether a directory exists, you want:
```

if [ -d "/home/$u"]; then

```
but that is not necessarily a good test for whether the user exists.

First, not all users have their home directory in /home. It is common practice for normal user accounts on Linux to be created with /home/$username to be their home directory, but this does not have to be the case. Special users, e.g. root, nobody, mysql, postgres, www-data, have their home directories elsewhere. The name of the home directory does not have to be the same as the username, but for normal user accounts, this is usually the case.

Second, there is nothing to prevent you having a directory in /home for a user who does not exist. Indeed, you can remove a user but leave their home directory intact.

You will get a definitive answer by grepping /etc/passwd or for example:
```

/usr/bin/id $u > /dev/null 2>&1
if [ $? -eq 0 ] ; then
   echo valid user
fi

```

However, this does not tell you where their home directory is. Maybe try:
```

user_home=$(sh -c "echo ~$u")
if [ -d "$user_home" ] ; then
    blah blah
fi

```

---

### Post by Mohan1289 on 2012-11-03
> **spjackson said:**
> To check whether a directory exists, you want:
```

if [ -d "/home/$u"]; then

```but that is not necessarily a good test for whether the user exists.

First, not all users have their home directory in /home. It is common practice for normal user accounts on Linux to be created with /home/$username to be their home directory, but this does not have to be the case. Special users, e.g. root, nobody, mysql, postgres, www-data, have their home directories elsewhere. The name of the home directory does not have to be the same as the username, but for normal user accounts, this is usually the case.

Second, there is nothing to prevent you having a directory in /home for a user who does not exist. Indeed, you can remove a user but leave their home directory intact.

You will get a definitive answer by grepping /etc/passwd or for example:
```

/usr/bin/id $u > /dev/null 2>&1
if [ $? -eq 0 ] ; then
   echo valid user
fi

```However, this does not tell you where their home directory is. Maybe try:
```

user_home=$(sh -c "echo ~$u")
if [ -d "$user_home" ] ; then
    blah blah
fi

```

Oh so /home directory is not reliable for determining whether the user exists or not.

what is the use of **-d** in the if condition?? what does it represent?

---

### Post by Lars Noodén on 2012-11-03
> **Mohan1289 said:**
> Oh so /home directory is not reliable for determining whether the user exists or not.

what is the use of **-d** in the if condition?? what does it represent?

The -d is a [test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html) to check whether a files both exists and is a directory.  

Probably the definitive way to check if a user exists is to look in /etc/passwd

```

#!/bin/sh

echo "Enter username"
read u
if grep -q "^$u:" /etc/passwd ; then
  echo "User Exists"
fi

```

---

### Post by Mohan1289 on 2012-11-03
> **Lars Noodén said:**
> The -d is a [test]("http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html") to check whether a files both exists and is a directory.  

Probably the definitive way to check if a user exists is to look in /etc/passwd

```

#!/bin/sh

echo "Enter username"
read u
if grep -q "^$u:" /etc/passwd ; then
  echo "User Exists"
fi

```


why you used **^$u:  **what does it do??

-q for silent or quite but what's the use of **^** ??
it means it searches for the username??

---

### Post by Lars Noodén on 2012-11-03
The [password file](http://manpages.ubuntu.com/manpages/precise/en/man5/passwd.5.html) has a specific format.  There is one record (user) per line and several fields per line.  The fields are delimited by colons (:****)  The username happens to be the first field, so it starts at the beginning of the line.  

If we don't match for the whole field, if you search for the user 'fred', you will also get the users 'alfred' and 'freddy'

[grep uses regular expressions](http://openclassroom.stanford.edu/MainFolder/VideoPage.php?course=PracticalUnix&video=grep4) to find patterns in a file.  The pattern we need to tell grep to look for is the username, held in $u, that begins at the beginning of the line (^) and continues to the end of the field, which is marked by a colon (:****)  The resulting pattern is /^$u:/  Look around for tutorials on "**regular expressions**" to find one that matches your level and interest.

---

### Post by slavik on 2012-11-03
Are all users created on the system? What about external authentication/authorization systems? (LDAP, AD, DB, etc.)

---

