---
title: "telnet and bash"
date: 2011-01-07
forum: Programming Talk
---

### Post by Drenriza on 2011-01-07
Is it possible from bash to

#1 telnet to a host
#2 automaticly type in user & password
#3 execute a command
#4 close the telnet session

Thanks on advance.
Kind Regards.

---

### Post by n~kf)}BW% on 2011-01-07
Yes, i'm sure it's possible... Look at telnet program options or perhaps a tool like netcat could help you... :popcorn:

---

### Post by Arndt on 2011-01-07
> **Drenriza said:**
> Is it possible from bash to

#1 telnet to a host
#2 automaticly type in user & password
#3 execute a command
#4 close the telnet session

Thanks on advance.
Kind Regards.

I think there is a telnet implementation in python. You could also use 'expect'.

Does it have to be telnet? If you can set up things to use 'ssh', you can execute commands remotely with it.

---

### Post by Drenriza on 2011-01-07
i have looked at expect scripting.

And are stuck. After i connect to the remote host (with telnet) how to i execute the command and close the session again?

```

#!/usr/bin/expect -f

set timeout 10
spawn telnet xx.xxx.xxx.xxx
expect "login"
send "username\r"
expect "Password"
send "password\r"

```

after the send "password\r"
i want to execute a command. But do you just type send infront of the command to send / execute it??
or how do you do it.

---

### Post by rnerwein on 2011-01-15
> **Drenriza said:**
> i have looked at expect scripting.

And are stuck. After i connect to the remote host (with telnet) how to i execute the command and close the session again?

```

#!/usr/bin/expect -f

set timeout 10
spawn telnet xx.xxx.xxx.xxx
expect "login"
send "username\r"
expect "Password"
send "password\r"

```after the send "password\r"
i want to execute a command. But do you just type send infront of the command to send / execute it??
or how do you do it.
hi
just a hint.
every hacker will be very happy if you are using telnet ( sorry if i'am wrong and you are using telenet via a
vpn ).
why you are not using the ssh ???. 
on the other side you have to look at the configuration on the oter side of your confirguration.
telnet can do that - but how are all the routers and switches are configured ?.
ciao

---

### Post by slavik on 2011-01-16
Why do I get a feeling that this is a foundation network device?

---

### Post by The Cog on 2011-01-16
> **Drenriza said:**
> i have looked at expect scripting.

And are stuck. After i connect to the remote host (with telnet) how to i execute the command and close the session again?

```

#!/usr/bin/expect -f

set timeout 10
spawn telnet xx.xxx.xxx.xxx
expect "login"
send "username\r"
expect "Password"
send "password\r"

```

after the send "password\r"
i want to execute a command. But do you just type send infront of the command to send / execute it??
or how do you do it.

I would be inclined to wait for a prompt before sending the command, maybe like```
expect "$"
send "do something awesome\n"
```and wait for some indication that it has finished before logging out:```
expect "Done"
send "logout"
```

---

### Post by Drenriza on 2011-01-18
Rnerwern. The telnet session is only local so it is limited to the trouble it can make. But im aware that telnet is very insecure :).

Slavik. Not sure what you mean.

The cog. Intersting, i will try to look at this.

---

### Post by slavik on 2011-01-19
> **Drenriza said:**
> Rnerwern. The telnet session is only local so it is limited to the trouble it can make. But im aware that telnet is very insecure :).

Slavik. Not sure what you mean.

The cog. Intersting, i will try to look at this.
foundation network device = switch, router, hub (if anyone still uses those), firewall, AP

---

### Post by slavik on 2011-01-19
> **Drenriza said:**
> Rnerwern. The telnet session is only local so it is limited to the trouble it can make. But im aware that telnet is very insecure :).

Slavik. Not sure what you mean.

The cog. Intersting, i will try to look at this.
foundation network device = switch, router, hub (if anyone still uses those), firewall, AP

---

### Post by DougC on 2011-01-19
Does it have to be telnet?

ssh will do this easily.

---

