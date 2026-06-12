---
title: "Extract particular number from command output"
date: 2012-07-02
forum: Programming Talk
---

### Post by susindran on 2012-07-02
Hi All,

I want to extract and use particular number from command output.

Below command :-
I want to use groups=2006 in useradd command.Thing is below is not having secondary ID so for me gid is 2006 is enough to create user account.

```
$ id -a oracle
uid=2006(oracle) gid=2006(dba) groups=2006(dba)
$
```


Second Example :-

Below command user have secondary group and i want to create user account with secondary group.

```
$ id -a
uid=6236(test) gid=999(local) groups=999(local),9003(testadmin)
$

```

Any one know how can write script for above scenario.

useradd command :-

```
sudo /usr/sbin/useradd -u $userID -g $groupiD -G $secondory_group -c "$fullname" -m -d $HomeDirectory -s $shell $login
```


I already completed to take remaining all variables and now i am facing the problem to take out only -g $groupiD -G $secondory_group from id -a output.

Thanks,
Susi.S

---

### Post by Vaphell on 2012-07-02
how about using
**id -u oracle** to get uid number (-un for the name)
**id -g oracle** to get gid number (-gn)
**id -G oracle** to get groups numbers (-Gn)?

```
id --help
```

---

