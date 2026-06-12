---
title: "Help creating a script to add samba users"
date: 2009-11-12
forum: Programming Talk
---

### Post by epicfail on 2009-11-12
Ok I should preface this by saying I have never been good with scripts or programming. So if my coding is messy I apologize.

A little back story:
I work for a business that is trying to use a new server as a samba server.
There are 133 employees in this building and each will have an individual share on the server which will sync with their "My Documents" folder on windows XP.
I have the 133 peoples requested usernames and passwords in a csv file.

I am thinking I will need a few different scripts. One to make each person a regular ubuntu user. One to make a samba user with the same name and assign that samba user their password. If there is an easier way I am open to suggestions. But for now this is what I have. 

```
#!/bin/bash
CSVFILE=/home/main/accounts1.csv
UN=`echo $i | cut -d, -f1 < '/home/main/accounts1.csv'`
for i in `cat $CSVFILE`
do
    echo adduser $UN
done
```

It echos the users in my accounts1.csv but it shows as follows

```
me@Samba:~$ '/home/me/localaddnew.sh'
adduser user1 user2 user3
adduser user1 user2 user3
adduser user1 user2 user3
```

Any suggestions on how to fix my mistakes? I have been pulling my hair out for about 2 days now. Thanks in advance.

---

