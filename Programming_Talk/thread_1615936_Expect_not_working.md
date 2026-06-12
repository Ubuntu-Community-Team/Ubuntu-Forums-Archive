---
title: "Expect not working"
date: 2010-11-07
forum: Programming Talk
---

### Post by KyHx on 2010-11-07
I cannot get Expect to do my bidding, it refuses.
Wise ones what seems to be my problem?
Forgive my ignorance.

```

#!/usr/bin/expect -f

set SERVER [lindex $argv 0]
set PASSWORD [lindex $argv 1]
set COMMAND [lindex $argv 2]
set timeout -1
spawn ssh $SERVER
match_max 100000
expect "*?assword*"
send "$PASSWORD\r"
send "\r"
send "$COMMAND\r"
send "exit\r"

```

Yeilds
```

kyhx@kyhx-netbook:/media/sda1/complete$ ./expect.ssh "kyhx@192.168.1.38" "mwahahaha" "ls>didit"
spawn ssh kyhx@192.168.1.38
kyhx@192.168.1.38's password: kyhx@kyhx-netbook:/media/sda1/complete$

```

---

### Post by saulgoode on 2010-11-07
It is unclear precisely what you are expecting (NPI), but perhaps the following might provide a nudge in the right direction:

```
#!/usr/bin/expect -f

set SERVER [lindex $argv 0]
set PASSWORD [lindex $argv 1]
set COMMAND [lindex $argv 2]
set timeout 1
spawn ssh $SERVER
expect "*?assword*"
send "$PASSWORD\r"
expect "*\$$" 
send "$COMMAND\r"
expect $
```

---

### Post by KyHx on 2010-11-07
Thanks for the reply. 
Sorry let me explain. I am trying to automate a process to connect to a computer through ssh and run a command. The command "ls>didit" is for testing purpose only. 
 
The little bit you gave me got me a little farther, the new output is...
```

kyhx@kyhx-netbook:/media/sda1/complete$ ./expect.ssh "kyhx@192.168.1.38" "mwahahahawhat" "ls>didit"
spawn ssh kyhx@192.168.1.38
kyhx@192.168.1.38's password: 
Linux kyhx-media 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Sun Nov  7 18:19:37 2010 from kyhx-netbook.westell.com
kyhx@kyhx-media:~$ 

```

So now it is the expect is not being met before the command. I tried to use [expect "kyhx@kyhx-media:~$"] to no success. All that is left is to get the command to run; any idea?

> It is unclear precisely what you are expecting (NPI), but perhaps the following might provide a nudge in the right direction:
Oh it was totally intended, and I applaud you for it.=D>

---

