---
title: "Symbolic Link for SSH Remote Hostname"
date: 2011-01-24
forum: Programming Talk
---

### Post by lazyrussian on 2011-01-24
Hi,

Is there a way to create a symbolic link to an off-site server, such that I don't have to type in [email]user@xxx.yyy.zzz.aaa.bbb.ccc[/email]?

Thanks!

PS: I need to know how to do this on OSX, and on Ubuntu 10.04. I'm pretty sure it's the same command.

---

### Post by geirha on 2011-01-24
If the IP is static, add an entry in /etc/hosts. E.g.
```
123.123.123.123 xxx.yyy.zzz.aaa.bbb.ccc *shortname*
```

Then you can do ```
ssh user@*shortname*
```


Another option is of course to make a shell function (or alias). 
```
sshfoo() { ssh user@xxx.yyy.zzz.aaa.bbb.ccc "$@"; }
```
Add it to the end of ~/.bashrc to make it permanent.

---

### Post by lazyrussian on 2011-01-24
Thanks! Modifying /etc/hosts worked perfectly!

---

### Post by talonmies on 2011-01-25
ssh has its own mechanism for this, you don't need to touch /etc/hosts. You can do something like in your local ssh_config

```

host shortcut
    hostkeyalias name_in_known_hosts_file
    hostname longame_or_ip_address
    port non_standard_port_number


```This tells ssh that hostname shortcut has a known_hosts keyname of *hostkeyalias*, a real ip address or DNS host name of *longame_or_ip_address*, and an ssh listen port number of *non_standard_port_number*. This entry would reduce the ssh login command from

```
ssh -p non_standard_port_number -o HostKeyAlias name_in_known_hosts_file \\
user@longame_or_ip_address
```to 
```
ssh user@shortcut
```The hostkeyalias and port entries are extremely useful if you are contacting a host via port forwarding through a gateway machine. man ssh_config for more.

---

### Post by lazyrussian on 2011-01-25
> **talonmies said:**
> ssh has its own mechanism for this, you don't need to touch /etc/hosts. You can do something like in your local ssh_config

```

host shortcut
    hostkeyalias name_in_known_hosts_file
    hostname longame_or_ip_address
    port non_standard_port_number


```This tells ssh that hostname shortcut has a known_hosts keyname of *hostkeyalias*, a real ip address or DNS host name of *longame_or_ip_address*, and an ssh listen port number of *non_standard_port_number*. This entry would reduce the ssh login command from

```
ssh -p non_standard_port_number -o HostKeyAlias name_in_known_hosts_file \\
user@longame_or_ip_address
```to 
```
ssh user@shortcut
```The hostkeyalias and port entries are extremely useful if you are contacting a host via port forwarding through a gateway machine. man ssh_config for more.

Thanks, I'll look into it later today!

---

### Post by slavik on 2011-01-25
yeah, don't use hosts for "shortcuts" for ssh, if it's needed system and DNS is not an option for w/e reason, then use hosts. otherwise, use ssh_config.

---

### Post by lazyrussian on 2011-01-26
So, why are you guys against editing /etc/hosts?

---

### Post by talonmies on 2011-01-26
[LIST=1]
[*]Because you wind up hard coding something that is potentially dynamic and might change in an important system file that directly effects TCP/IP behaviour. You can be left with really hard to diagnose network problems at some time in the future.
[*]Because it isn't always practical or possible for users to edit the hosts file, and if they did they would be propagating their personal customizations system and possibly network wide, if the host in question runs certain flavours of DHCP or caching DNS server.
[*]Because SSH already provides a secure, local user level mechanism which has no effect on other users or system/network wide TCP/IP behaviour specifically for the purpose you are asking about.
[/LIST]
Also, you mentioned OS X. Here is an interesting question: How many hosts files are there on a standard OS X installation? If the answer is more than one , which should you edit, and what happens when you reboot or install operating system upgrades? The answers to all three questions might surprise you.....

---

### Post by lazyrussian on 2011-01-26
> **talonmies said:**
> [LIST=1]
[*]Because you wind up hard coding something that is potentially dynamic and might change in an important system file that directly effects TCP/IP behaviour. You can be left with really hard to diagnose network problems at some time in the future.
[*]Because it isn't always practical or possible for users to edit the hosts file, and if they did they would be propagating their personal customizations system and possibly network wide, if the host in question runs certain flavours of DHCP or caching DNS server.
[*]Because SSH already provides a secure, local user level mechanism which has no effect on other users or system/network wide TCP/IP behaviour specifically for the purpose you are asking about.
[/LIST]
Also, you mentioned OS X. Here is an interesting question: How many hosts files are there on a standard OS X installation? If the answer is more than one , which should you edit, and what happens when you reboot or install operating system upgrades? The answers to all three questions might surprise you.....

To my knowledge, there is only one hosts file. I edited it, and everything started working. Apparently, I had edited it in the past (2 years ago). In those 2 years, I forgot that that was the file I needed to edit, and that's what prompted my initial forum post.

I am the only user on my computer, so I grant myself superuser access when I need it. I do see the problem of doing this for users who don't have SU access.

Thanks for the explanation - much appreciated!

---

### Post by talonmies on 2011-01-26
> **lazyrussian said:**
> To my knowledge, there is only one hosts file.

Try again.....

```
MacBook-Air:~ avidday$ ls -l /etc/hosts
-rw-r--r--  1 root  wheel  236 Sep 25 07:26 /etc/hosts
MacBook-Air:~ avidday$ ls -l /private/etc/hosts
-rw-r--r--  1 root  wheel  236 Sep 25 07:26 /private/etc/hosts

```

---

### Post by lazyrussian on 2011-01-26
> **talonmies said:**
> Try again.....

```
MacBook-Air:~ avidday$ ls -l /etc/hosts
-rw-r--r--  1 root  wheel  236 Sep 25 07:26 /etc/hosts
MacBook-Air:~ avidday$ ls -l /private/etc/hosts
-rw-r--r--  1 root  wheel  236 Sep 25 07:26 /private/etc/hosts

```

I stand corrected. I've never had a reason to peak into the private folder. Now I know.

Thanks!

---

