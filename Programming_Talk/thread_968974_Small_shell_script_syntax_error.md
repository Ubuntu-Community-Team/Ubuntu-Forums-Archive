---
title: "Small shell script syntax error"
date: 2008-11-03
forum: Programming Talk
---

### Post by clarkhuke on 2008-11-03
Hey, everyone.
I'm making a shell script that will take a username argument and display the username and real name associated with the username.

I keep getting a syntax error.

```

for user
do

grep "^"`echo $user":"` /etc/passwd 1> /dev/null 2>&1
if [ $? -eq 0 ]
        echo "$user: "
        grep "^"`echo $ser":"` /etc/passwd | cut -f5 -d':'
fi
done
exit 0

```

When I run it with my username, I get the following error:
```
./un.sh chuke 
./un.sh: line 8: syntax error near unexpected token `fi'
./un.sh: line 8: `fi'
```

Removing the "fi" gives me the same error only it tells me that there is an unexpected "done". Removing that, and well, nothing works.

Can anyone help?
Thanks

EDIT:
It should output the following (or similar):
chuke: Clark Huke

It should also display nothing if the username doesn't exist (that's the first grep), and can be used to do many usernames at once:
kjen: Kathy Jen
chuke: Clark Huke
bjohns: Bob Johnson
ccube:

For example.

---

### Post by dwhitney67 on 2008-11-03
An if-block requires the "then" statement.
```

if [ condition ]; then
        ...
fi

```

or

```

if [ condition ]
then
        ...
fi

```

P.S.  See if this code meets your requirements:
```

#!/bin/sh

echo -n "Enter user name: "
read user

user_info=`grep $user /etc/passwd`

if [ $? -eq 0 ]
then
        echo -n $user": "
        echo $user_info | cut -f5 -d':' | cut -f1 -d','
else
        echo "Unknown user-id ($user) given."
fi

exit 0

```

P.S.S.  If you want to display all entries in /etc/passwd:
```

#!/bin/sh

while read line
do
        user=`echo $line | cut -f1 -d':'`
        name=`echo $line | cut -f5 -d':' | cut -f1 -d','`

        echo "$user: $name"

done < "/etc/passwd"

exit 0

```

---

### Post by renzokuken on 2008-11-03
do you not need a "then" statement after the "if"......been a looooooong time since i wrote any code especially shell scripts so could (probably am) wrong

```
if [ $? -eq 0 ]
then
        echo "$user: "
        grep "^"`echo $ser":"` /etc/passwd | cut -f5 -d':'
fi
```

edit: damn, beaten to it, but i'm feeling smug for being right

---

### Post by clarkhuke on 2008-11-03
Thanks very much. 
It was just something so small that I was missing..., of course.

Appropriate thanks, were given.

---

