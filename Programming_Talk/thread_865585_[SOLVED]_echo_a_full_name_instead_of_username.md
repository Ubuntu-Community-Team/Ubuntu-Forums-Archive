---
title: "[SOLVED] echo a full name instead of username?"
date: 2008-07-20
forum: Programming Talk
---

### Post by tjsullivan1 on 2008-07-20
Does anyone know how to echo a user's full name instead of their username in BASH?

To give context, I am attempting to write a script that will allow sysadmins at my organization to have a template for our comments on new scripts for our systems. The script that I am having trouble with looks like this now:

echo "What would you like to name this script?"
read -e SCRIPTNAME
touch $SCRIPTNAME
echo "#!/usr/bin/perl" > $SCRIPTNAME
echo "#" >> $SCRIPTNAME
echo "# Author:		"[COLOR="Yellow"] $USER [/COLOR]>> $SCRIPTNAME 
echo "# Date Created:		" $(date) >> $SCRIPTNAME
echo "# Date Modified:	" $(date) >> $SCRIPTNAME
echo "What does this file do?"
read -e DESCRIPTION
echo "# Description:		" $DESCRIPTION >> $SCRIPTNAME
echo "#" >> $SCRIPTNAME

Right now what this does is inserts the username into the file $SCRIPTNAME, but I want it to insert the user's full name (i.e. John Doe instead of jdoe).

Thanks for you help.

---

### Post by ghostdog74 on 2008-07-20
if the full user name is defined when you created the user, you can find it in /etc/passwd
```

awk -v user="$USER" -F":" 'user==$1{print $5}' /etc/passwd 

```

---

### Post by tjsullivan1 on 2008-07-20
Thanks! I also found that changing two lines will work too:
```
echo -n "# Author:	 	" "">> $SCRIPTNAME 
cat /etc/passwd | grep $USER | awk -F : '{print $5}' >> $SCRIPTNAME

```

---

### Post by ghostdog74 on 2008-07-20
> **tjsullivan1 said:**
> Thanks! I also found that changing two lines will work too:
```
echo -n "# Author:	 	" "">> $SCRIPTNAME 
cat /etc/passwd | grep $USER | awk -F : '{print $5}' >> $SCRIPTNAME

```

the only difference is , you create 2 more processes , useless cat and grep. If you use awk, there's no need to use grep/cat because it already provides what grep/cat does.

---

### Post by WW on 2008-07-20
You can use the **getent** command to get a user's record from the passwd file:
```

getent passwd user_name_here

```
which can then be parsed many ways.  For example
```

FULLNAME=`getent passwd $USER | cut -d ":" -f 5`

```
On my system, I get extra commas after the name, so this might be nicer:
```

FULLNAME=`getent passwd $USER | cut -d ":" -f 5 | cut -d "," -f 1`

```

---

### Post by tjsullivan1 on 2008-07-20
Thanks again ghostdog.

> On my system, I get extra commas after the name

I had the same problem initially; I think that is a problem caused with the default account created when the system is installed. I just ran:

```
usermod -c "Full Name"
```

And it fixed it right up.

---

### Post by slavik on 2008-07-20
am I the only one that would use Perl to parse passwd into a hash? :)

---

### Post by tjsullivan1 on 2008-07-20
I'm actually learning perl right now. :)

---

