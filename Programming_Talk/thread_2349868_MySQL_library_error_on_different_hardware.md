---
title: "MySQL library error on different hardware"
date: 2017-01-19
forum: Programming Talk
---

### Post by geohei on 2017-01-19
I compiled some C code with MySQL stuff (mybin) on a Ubuntu 14.04.

```
root@vm90:~# cat /etc/issue.net
Ubuntu 14.04.5 LTS
```

The code runs fine on my VM, but if I run this code on my hosters web space, I get:

```
./mybin: /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18: no version information available (required by ./mybin)
```

The code still runs fine!
	
```
geohei@myhoster:~$ cat /etc/issue.net
Ubuntu 12.04.5 LTS
```

Why is that?
What do I have to change in the compiler settings in order to get rid of this message?

Thanks,

---

### Post by steeldriver on 2017-01-19
Does this help?

[What does the &#8220;no version information available&#8221; error from linux dynamic linker mean?](http://stackoverflow.com/a/156387/4440445)

--

---

### Post by geohei on 2017-02-04
Not really ... I found no other solution that to install Ubuntu 12.04 (OS of my hoster) on a VM and recompile. This made (of course) the above mentioned message disappear. Not very elegant though ...

---

