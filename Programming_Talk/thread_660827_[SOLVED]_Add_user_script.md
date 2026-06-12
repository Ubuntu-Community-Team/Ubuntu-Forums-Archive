---
title: "[SOLVED] Add user script"
date: 2008-01-07
forum: Programming Talk
---

### Post by murmel on 2008-01-07
Hello everybody! I got a problem when adding/removing users.
I would need a script who does several things for me when adding and removing users.
How do I make a script that when in use looks something like this:
"*addusername [username]*"
and it does this:
```
useradd -g ldap -m -d /home/LDAP/[username] [username]
passwd (makes me enter a password)
cat /etc/passwd | grep [username] > /etc/ldap/LDAP_DEV/[username].ldif
ldapadd -x -D 'cn=Manager,dc=domain,dc=com' -W -f [username].ldif
mkdir /home/LDAP/[username]/www/
```
Something like this. And when removed I want it to do something like this:
"*delusername [username]*"
```
ldapdelete -x -D 'cn=Manager,dc=domain,dc=com]' -W -f /etc/ldap/LDAP_DEV/[username].ldif
rm /etc/ldap/LDAP_DEV/[username].ldif
userdel -r [username]
```
and maybe and updatescript
"*upusername [username]*"
```
rm /etc/ldap/LDAP_DEV/[username].ldif
cat /etc/passwd | grep [username] > /etc/ldap/LDAP_DEV/[username].ldif
ldapmodify -x -D 'cn=Manager,dc=domain,dc=com' -W -f [username].ldif
```


It would be great if someone could tell me how to create this and make it simpler for me to add/remove/update users. Thanks!

---

### Post by ghostdog74 on 2008-01-07
you are already on the right track.
if you want to  pass  in a parameter  to the script
use $1,$2 ... 
eg
```

#!/bin/sh
username=$1
...
...
useradd -g ldap -m -d /home/LDAP/$username $username
....

```

---

### Post by murmel on 2008-01-07
> **ghostdog74 said:**
> you are already on the right track.
if you want to  pass  in a parameter  to the script
use $1,$2 ... 
eg
```

#!/bin/sh
username=$1
...
...
useradd -g ldap -m -d /home/LDAP/$username $username
....

```
Thanks! :) Where do I put the script and should I make an alias to it?

---

### Post by scruff on 2008-01-07
Check out Slackware's "superadduser" script. I always used it back in my Slack days. [http://www.slackware.com/~mozes/](http://www.slackware.com/~mozes/)

---

### Post by njparton on 2008-01-07
Try webmin if you can access your ubuntu box from another PC with a browser.

***edit***

then again you may even be able to administer a system locally with webmin by logging into [https://localhost:10000](https://localhost:10000) :wink:

---

### Post by geirha on 2008-01-07
> **murmel said:**
> Thanks! :) Where do I put the script and should I make an alias to it?

The easiest is to put it in /usr/local/bin, it should be in your path, so if you make the script executable, you can run it with ```
sudo addldapuser foo
``` Assuming you called it /usr/local/bin/addldapuser

Also, in this line, cat is not necessary: ```
cat /etc/passwd | grep [username] > ...
```
Just use grep
```
grep "^$username:" /etc/passwd > ...
```

---

### Post by murmel on 2008-01-07
Thanks everybody!
Got it working!
I added it to /sbin/addusername
and did chmod +x /sbin/addusername
Worked like a charm! =)

---

### Post by ghostdog74 on 2008-01-07
> **murmel said:**
> Thanks everybody!
Got it working!
I added it to /sbin/addusername
and did chmod +x /sbin/addusername
Worked like a charm! =)

I suggest you don't put it in /sbin. Just in case one day you decided to wipe clean your OS and you forget you have a script there.

Put it in some directory you defined. Then add it to your PATH variable.

---

### Post by murmel on 2008-01-07
> **ghostdog74 said:**
> I suggest you don't put it in /sbin. Just in case one day you decided to wipe clean your OS and you forget you have a script there.

Put it in some directory you defined. Then add it to your PATH variable.
Something like this?
I put my beautiful script in /root/myscript/scriptname and make a symlink to it like this?
ln -s /root/myscript/scriptname /sbin/scriptname .. correct?

I do also have another question.. I know it's possible to add text to an textfile (echo 'text' > textfile) but is it possible to remove/change text from an text file?
if I add a line like this when I add a user
```
echo '/home/pub /home/$username/pub none bind 0 0' > /etc/fstab
```
and when I remove the user I want it to remove this line.. Is it possible? :O
Thanks!

- Simon

---

### Post by ghostdog74 on 2008-01-07
> **murmel said:**
> Something like this?
I put my beautiful script in /root/myscript/scriptname and make a symlink to it like this?
ln -s /root/myscript/scriptname /sbin/scriptname .. correct?

its possible. Try it out and see. Its better for you this way instead of me telling you. If you have difficulty , post back your results.

> 
I do also have another question.. I know it's possible to add text to an textfile (echo 'text' > textfile)

you don't add text like this. This will overwrite whatever is in textfile. you use "append" mode  like this "echo something >> textfile "

> 
 but is it possible to remove/change text from an text file?
if I add a line like this when I add a user
```
echo '/home/pub /home/$username/pub none bind 0 0' > /etc/fstab
```
and when I remove the user I want it to remove this line.. Is it possible? :O
Thanks!

Seems like you can get started on some bash scripting. See my sig for a link of learning bash. For the record, you can use tools like sed/awk or even Perl/Python or others to do what you want. However, since shell is the most basic thing you can learn, let's start with it.
Using bash
```

while read line
do
 case $line in 
 */home/pub*none\ bind\ 0\ 0 ) continue;;
 *) echo $line;;
 esac
done < "file" > outfile

```
If you find bash is not to your taste, learn how to use sed/awk and other tools. In anyway, just spend time reading up and practice the guide in my sig for a start

---

### Post by Sam on 2008-01-07
More simplier:
```
cat /etc/fstab |sed '/^\/home\/pub/d'
```

---

### Post by ghostdog74 on 2008-01-07
> **Sam said:**
> More simplier:
```
cat /etc/fstab |sed '/^\/home\/pub/d'
```
No need for cat.
```

sed -i '/^\/home\/pub/d' /etc/fstab

```

also take note that for very large files, using sed with d modifier might be slower (in this scenario )
```

# wc -l file1
4000002 file1
# grep "delete" file1
this is line to delete
this is line to delete
# time sed '/delete/d' file1 > sedtest

real    0m8.942s
user    0m8.593s
sys     0m0.348s
# time grep -v "delete" file1 > greptest

real    0m1.078s
user    0m0.684s
sys     0m0.384s
#                 
# diff sedtest greptest
#  

```

---

### Post by murmel on 2008-01-21
I'm going to use:
```
[...]
sed -i '/$username\/pub/d' /etc/fstab
[...]
```

Thanks! =)

---

### Post by murmel on 2008-01-23
I've been having problems when using $username in dirs/echo etc like this:
```
[...]
echo '$username 's folder' >> index.php
[...]
```
or
```
[...]
mkdir /home/$username/dir
[...]
```

What should I add to make this work? =)

---

### Post by scruff on 2008-01-23
use $USER.  $username isn't an evironment variable. To see all the ENV's currently set, try printenv.

---

### Post by scruff on 2008-01-23
Also, quick tip: No need to type out /home/ - you can use - 

```

# mkdir ~/$USER/dir

```

---

### Post by rendon on 2008-01-23
Putting scripts into /bin, /usr/bin, /usr/sbin or any other such bin is stupid.

You should put the script in a location that has nothing to do with the original system architecture. and then, as mentioned previously, you should learn how to use the PATH variable.

research "linux PATH variable" or "ubuntu set change PATH variable" or something along those lines... until you find out how to use the path variable.

You might start by typing "echo $PATH" to see all of the "paths" (separated by a colon : ) 

every script that is inside the directory of one of the "paths" is a script that can be run just like a function at the command line.

so if your name is john and your ubuntu username is john, then you can make your own personal bin directory as such:
mkdir /home/john/bin


then make a script in there called "sayhello" as such:

pico /home/john/bin/sayhello
-----------------------------------
#! /bin/bash
echo "hello"
-----------------------------------

then try:
PATH="$PATH:/home/john/bin"

to add your personal bin to the PATH variable

then go ahead and type "sayhello" at the command line to see what happens...

you might also have to "chmod 755 sayhello"

---

### Post by Sam on 2008-01-23
> **scruff said:**
> Also, quick tip: No need to type out /home/ - you can use - 

```

# mkdir ~/$USER/dir

```

Ouch, that's false. It's ```
mkdir ~/dir
```

---

### Post by scruff on 2008-01-23
Heh - typo.

With regards to Rendon's comment - a good place for user written scripts and apps is /usr/loca/bin/. It's already in your PATH, and follows general convention. Of course, only put things there if you want others to be able to access it. If you have a lot of users on your machine and need to keep things private, follow Rendon's advice.

edit:
You could also `chmod 700` or the like to make it executable, readable and writeable only by you, but better off to just keep it in your own directory if you want privacy.

---

