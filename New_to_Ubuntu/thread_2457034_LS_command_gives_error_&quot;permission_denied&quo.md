---
title: "LS command gives error &quot;permission denied&quot;. HELP!"
date: 2021-01-24
forum: New to Ubuntu
---

### Post by beekayverma on 2021-01-24
Hey guys,
 I&#8217;m a new linux user and learning ubuntu CLI. I&#8217;m trying to use &#8216;ls&#8217; command to test the user & groups things.
 so I have main user &#8216;beekay&#8217; and other 2 new ones as mentioned in the  text below. both can use the ls for /home/username directories howver  beekay can&#8217;t
please help. below are the groups, ownerships for the folders. only  problem with user beekay is that it can&#8217;t ls into /home/felipe.
 ```
beekay@beekay-Ubuntu-20:~$ ls /home/yogi_v/
beekay@beekay-Ubuntu-20:~$ su - felipe 
Password: 
felipe@beekay-Ubuntu-20:~$ ls /home/yogi_v/
felipe@beekay-Ubuntu-20:~$ ls /home/beekay/
Desktop    Downloads  notes.txt  Public  Templates
Documents  Music      Pictures   snap    Videos
felipe@beekay-Ubuntu-20:~$ logout
beekay@beekay-Ubuntu-20:~$ ls /home/yogi_v/
beekay@beekay-Ubuntu-20:~$ ls
Desktop    Downloads  notes.txt  Public  Templates
Documents  Music      Pictures   snap    Videos
beekay@beekay-Ubuntu-20:~$ ls /home/
beekay  felipe  yogi_v
beekay@beekay-Ubuntu-20:~$ ls /home/felipe/
ls: cannot open directory '/home/felipe/': Permission denied
beekay@beekay-Ubuntu-20:~$ ls -ld /home/felipe/
drwxr-x--- 2 root student 4096 jaan  24 20:50 /home/felipe/
beekay@beekay-Ubuntu-20:~$ 
beekay@beekay-Ubuntu-20:~$ ls -ld /home/felipe/
drwxr-x--- 2 root student 4096 jaan  24 20:50 /home/felipe/
beekay@beekay-Ubuntu-20:~$ ls -ld /home/yogi_v/
drwxr-xr-x 2 root student 4096 jaan  24 20:53 /home/yogi_v/
beekay@beekay-Ubuntu-20:~$ ls -ld /home/beekay/
drwxr-xr-x 17 beekay beekay 4096 jaan  24 02:00 /home/beekay/
beekay@beekay-Ubuntu-20:~$ id beekay 
uid=1000(beekay) gid=1000(beekay) groups=1000(beekay),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),131(lxd),132(sambashare),1001(student)
beekay@beekay-Ubuntu-20:~$ id felipe 
uid=1001(felipe) gid=1002(felipe) groups=1002(felipe),1001(student)
beekay@beekay-Ubuntu-20:~$ id yogi_v 
uid=1002(yogi_v) gid=1003(yogi_v) groups=1003(yogi_v),1001(student)
beekay@beekay-Ubuntu-20:~$ su - yogi_v 
Password: 
yogi_v@beekay-Ubuntu-20:~$ ls /home/felipe/
yogi_v@beekay-Ubuntu-20:~$ ls /home/beekay/
Desktop  Documents  Downloads  Music  notes.txt  Pictures  Public  snap  Templates  Videos
yogi_v@beekay-Ubuntu-20:~$ logout
beekay@beekay-Ubuntu-20:~$ su - felipe 
Password: 
felipe@beekay-Ubuntu-20:~$ ls /home/yogi_v/
felipe@beekay-Ubuntu-20:~$ ls /home/beekay/
Desktop  Documents  Downloads  Music  notes.txt  Pictures  Public  snap  Templates  Videos
felipe@beekay-Ubuntu-20:~$ logout
beekay@beekay-Ubuntu-20:~$ ls /home/yogi_v/
beekay@beekay-Ubuntu-20:~$ ls /home/felipe/
ls: cannot open directory '/home/felipe/': Permission denied
beekay@beekay-Ubuntu-20:~$
```

---

### Post by GhX6GZMB on 2021-01-24
The first thing you need to get a grip on is to not use su - "user".
It doesn't really change the user, but kind of pretends to by setting some environment variables. man su discourages the use of "su -" probably for good reasons
You can get temporary higher privileges by using sudo before a command.

That being said, you're all members of gid=1001(student), so ls not working is strange.

---

### Post by youngwarlock on 2021-01-24
This happened because beekay does not belong to the same group as felipe. beekay is therefore treated as others, and others do not have the permission to read /home/felipe/

solution: change permission by typing 
```

sudo chmod 755 /home/felipe/

```
then enter the root password.

---

### Post by GhX6GZMB on 2021-01-24
[I][COLOR=#000000]"This happened because beekay does not belong to the same group as felipe. beekay is therefore treated as others, and others do not have the permission to read /home/felipe/[/COLOR]

[COLOR=#000000]solution: change permission by typing[/COLOR]
[COLOR=#000000]Code:
sudo chmod 755 /home/felipe/
[/COLOR]
[/I][COLOR=#000000]*then enter the root password."*

Huh? All three are members of 1001(student)

My suspicion leans more towards the misspelling of "sambasha re" in the beekay group listing. If beekay's been fiddling around with the groups and accidentally inserted a space in "sambashare", this might result in the read failure of the 1001(student) group.





[/COLOR]

---

### Post by QIII on 2021-01-24
Changing permissions on the top level of a user's home directory so that another user can gain access -- even read only access -- is profoundly bad advice.

Leave the permissions alone.

---

### Post by TheFu on 2021-01-24
> **ml9104 said:**
> The first thing you need to get a grip on is to not use su - "user".
It doesn't really change the user, but kind of pretends to by setting some environment variables. man su discourages the use of "su -" probably for good reasons
You can get temporary higher privileges by using sudo before a command.

That being said, you're all members of gid=1001(student), so ls not working is strange.

News to me. Please explain.

**su - username** **is** preferred to my knowledge, as it causes a login to the other userid which sets the environment of that account. From the manpage:```

       -, -l, --login
           Provide an environment similar to what the user would expect had
           the user logged in directly.

           When - is used, it must be specified before any username. For
           portability it is recommended to use it as last option, before any
           username. The other forms (-l and --login) do not have this
           restriction.
```

However, using it to change to the root account would NOT be preferred on ubuntu systems, but that is a different use case.

Or did I misunderstand? 

For the OP, I'd use 3 different terminals, one for each userid, and show the **ls -alF** for the directories involved, including the parent. Parent directories control access inside and to all child object inside. A little whitespace would help readability too.  I didn't look too hard are the wall of text. Sorry.

Whenever permissions aren't working as expected, it is always something like ACLs or SELinux in the way, IME.

---

### Post by youngwarlock on 2021-01-25
Sorry I missed the fact that beekay and filipe shared a group. That means my earlier answer is wrong.

---

### Post by GhX6GZMB on 2021-01-25
> **TheFu said:**
> 
However, using it to change to the root account would NOT be preferred on ubuntu systems, but that is a different use case.

Or did I misunderstand? 


No,_ I _misunderstood. I read the codeblock as su to root, which is wrong. Sorry.

---

### Post by New_buntu_89 on 2021-02-01
> **beekayverma said:**
> 
 I&#8217;m a new linux user and learning ubuntu CLI. I&#8217;m trying to use &#8216;ls&#8217; command to test the user & groups things.
 so I have main user &#8216;beekay&#8217; and other 2 new ones as mentioned in the  text below. both can use the ls for /home/username directories howver  beekay can&#8217;t
please help. below are the groups, ownerships for the folders. only  problem with user beekay is that it can&#8217;t ls into /home/felipe.
...



NVM, I just noticed the bottom part of your example...

The issue looks like it's just that felipe doesn't have read access for everybody, while the other two users do. Having read access for all is usually not good practice, but I assume you have good reasons...

---

