---
title: "Add users with specific uid and gid using xargs"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by wmsmith on 2013-06-21
Hello everyone,
 I am trying to restore my system after a bad crash. Luckily, I had an rshapshot backup of all the home folders for the users, but now I need to readd the users so that their uid and gid match what is on their home folders. This computer is acting as a server to share a joint home folder to other computers, so I have to re-add the users with exactly the same UID and GID as before. Otherwise I will have an even bigger headache on my hands when I startup the fileshare system again.

I would eventually like to use a text file with entries:

```
-u #### -g #### USERNAME
```

where #### are the user and group id's respectively. To feed the needed arguments to xargs.
I tested it in xargs using simpler version for just adding with a given UID:

```
grep -m 1 "" useraddlist.txt | xargs -p -I{} useradd {}
```

which yielded:

```
useradd -u 1001 USERNAME ?...
```

but when I type y to accept, it gives me back the error:

```
useradd: invalid user ID ' 1001 mjhsieh'
```

If I enter the equivalent useradd command by hand it works just fine...

e.g.

```
useradd -u 1001 USERNAME
``` 

adds with no problems.

Anyone have any idea what I'm doing wrong?

---

### Post by TheFu on 2013-06-21
If you have less than 50 users, I'd just add them all, not specifying the uid/gid, then go back refering to the old /etc/passwd and /etc/group files to get all the uids/gids correct manually.  Shouldn't be that hard.

With more than 50 userids, I'd get the text file as you suggested then use vim global search and replace to insert the useradd command before each line.

My man page says that useradd needs to be in this form:
$ sudo useradd -u {UID} -g {GIU} {LOGIN}

I wouldn't use xargs for this.

Ok, so that leads me to the next question. Did you already create all the groups?  Don't those need to exist before you can add them to the password file?

Also, if a uid is already used, you need to move it outside your range.  Chances are that 1000 was used for the installation userid - right?  I'd look at the /etc/group and /etc/passwd files to see what is and isn't inside them.

---

### Post by steeldriver on 2013-06-21
I don't know what's wrong specifically, but have you considered having simple uid - gid - username entries (without the explicit -u / -g flags)

```
###  ####  USERNAME
```

in your file, and then doing something like 

```
while read -r uid gid user; do useradd -u ${uid} -g ${gid} ${user}; done < useraddlist.txt
```

---

### Post by wmsmith on 2013-06-21
> **steeldriver said:**
> I don't know what's wrong specifically, but have you considered having simple uid - gid - username entries (without the explicit -u / -g flags)

```
###  ####  USERNAME
```

in your file, and then doing something like 

```
while read -r uid gid user; do useradd -u ${uid} -g ${gid} ${user}; done < useraddlist.txt
```

Sweet! Thanks for the idea. Reading with a while loop seems to do the trick.
It complained about the input to useradd since the groups weren't already made...
Apparently, however, I don't need to worry about the group add part after all since all the groupid numbers apparently also match the userid numbers.
So everything works out ok.

I remade the .txt file appropriately and it all ran smoothly (just left out the -g ${gid} from the command)

Thanks for the help everyone!

---

### Post by SeijiSensei on 2013-06-21
Now store copies of /etc/passwd, /etc/group, and /etc/shadow on another machine in case disaster strikes once again!

---

