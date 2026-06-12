---
title: "Auto mount SSHFS with Expect HELP NEED :("
date: 2013-05-18
forum: Programming Talk
---

### Post by baskar007 on 2013-05-18
Hi all,

I am new to bash and expect.

Now I have a expect script:
```

#!/usr/bin/expect -f
set HOST "server"
set USER "roxsoft"
set PASS "***"
set PATH "/home/roxsoft/www/"
spawn sshfs "$USER@$HOST:"  "/media/server-ssh"
expect "Are you sure you want to continue connecting (yes/no)? yes" 
send "yes\r" 
expect "roxsoft@server's password:"
send "$PASS\r"
exit

```

When I run this script I got:
```

:$ **~/server-ssh.sh**
**spawn sshfs roxsoft@server: /media/server-ssh**
**Warning: the DSA host key for 'server' differs from the key for the IP address '169.254.43.84'**
**Offending key for IP in /home/roxsoft-server/.ssh/known_hosts:1**
**Matching host key in /home/roxsoft-server/.ssh/known_hosts:2**
**Are you sure you want to continue connecting (yes/no)? yes**
**roxsoft@server's password: **:$ 

```


The problem is:
sometimes I can't access **/media/server-ssh** directory after running this script.
sometimes I can access **/media/server-ssh **but I can see only empty folder... (ie: server folder was not mounted...) 

If I run this manually I got everything working fine..
```

sshfs "USERNAME@$__IP__:"  "/media/server-ssh"

```


Whats wrong with this?????

---

### Post by baskar007 on 2013-05-18
>50 views... But no reply .... :(.
Kindly ask me if any more information is required, regarding question

---

### Post by ziekfiguur on 2013-05-18
My guess would be that you should remove the last yes from this line
```
expect "Are you sure you want to continue connecting (yes/no)? yes"
```
But it would probably be a better idea to fix your keys so you don't have to enter a password at login. Having a password in a plaintext file or script is never a good idea.

---

### Post by baskar007 on 2013-05-19
[SIZE=4]Thanks [/SIZE][COLOR=#000000][/COLOR][**[COLOR=#000000]ziekfiguur[/COLOR]**]("http://ubuntuforums.org/member.php?u=960698")[COLOR=#000000][/COLOR]

---

