---
title: "Using Commands over SSH using Sudo"
date: 2012-02-17
forum: Programming Talk
---

### Post by metallica1973 on 2012-02-17
I am currently in the process of writing a shell script via bash to perform backups but ran into an roadblock. What I am trying to do is execute commands over ssh that does not require a password for sudo to perform my backups:

```

ssh -o "PasswordAuthentication no" -o "HostbasedAuthentication yes" -l user 10.7.0.180 "sudo find / -depth|cpio -oacv|gzip" > /path/to/dir/file.cpio.gz
[code]

so I modified 

/etc/sudoers

[code]

user  ALL = NOPASSWD: /usr/bin/find, /bin/cpio, /bin/gzip


```

so in testing I was thinking that it wouldnt prompt me for a password but it still does prompt me for it.

```


user@mymachine:~$ ssh -t -o "PasswordAuthentication no" -o "HostbasedAuthentication yes" -l user 10.7.0.180 "sudo find / -depth"
[sudo] password for user:

```

I know my hostbased authentication works:

```

ssh -t -t -o  "PasswordAuthentication no" -o "HostbasedAuthentication yes" -l user 10.7.0.180

Linux 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
* Documentation:  https://help.ubuntu.com/

Last login: Fri Feb 17 10:30:18 2012 from 10.7.0.112
user@mymachine:~$

```

I changed /etc/sudoers to:

```

user  ALL = NOPASSWD: ALL

```

and it didnt make a difference. What could it be ?????????????
__________________

---

### Post by erind on 2012-02-18
> **metallica1973 said:**
> I am currently in the process of writing a shell script via bash to perform backups but ran into an roadblock. What I am trying to do is execute commands over ssh that does not require a password for sudo to perform my backups:

```

ssh -o "PasswordAuthentication no" -o "HostbasedAuthentication yes" -l user 10.7.0.180 "sudo find / -depth|cpio -oacv|gzip" > /path/to/dir/file.cpio.gz

```[ ... ]

I changed /etc/sudoers to:

```

user  ALL = NOPASSWD: ALL

```and it didnt make a difference. What could it be ?????????????
__________________


It's not clear, but I think you're modifying the sudoers file in the *source* machine - that needs to be done in the **destination** server. It's important to know that the (quoted) commands after ssh, are executed in a remote shell in the *destination *machine, which from your example is 10.7.0.180.

So put an entry like the following in */etc/sudoers *of 10.7.0.180: 

```
user ALL = NOPASSWD: /usr/bin/find
```[ Worked fine in my testings ].

---

### Post by metallica1973 on 2012-02-21
Thank you for your reply,

I am definately modify /etc/sudoers on the destination server. It definately has to due with what I have inside of the sudoers file:

```

ssh -t -t -o  "PasswordAuthentication no" -o "HostbasedAuthentication yes" -l user 10.7.0.180

Linux 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
* Documentation:  https://help.ubuntu.com/

user@10.7.0.180:~$ sudo find / -depth
[sudo] password for user: 

```

As you can see, after logging in, I am still getting prompted for a password.

---

### Post by metallica1973 on 2012-02-21
It was in fact /etc/sudoers and the placement of my entry, so from:

```

root	ALL=(ALL) ALL
user  ALL = NOPASSWD: /usr/bin/find, /bin/cpio, /bin/gzip

```

to 

```


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
user   ALL = NOPASSWD: /usr/bin/find, /bin/cpio, /bin/gzip, /bin/cat

```

worked like a charm.


[http://askubuntu.com/questions/100051/why-is-sudoers-nopasswd-option-not-working](http://askubuntu.com/questions/100051/why-is-sudoers-nopasswd-option-not-working)

---

