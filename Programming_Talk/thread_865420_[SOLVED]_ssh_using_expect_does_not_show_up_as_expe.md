---
title: "[SOLVED] ssh using expect does not show up as expected maximized"
date: 2008-07-20
forum: Programming Talk
---

### Post by mailbinoy on 2008-07-20
I am writing an application(pygtk) that requires me to ssh to a server and interact with it. I am using expect to login automatically
My problem is if I run the following in a gnome-terminal window (unmaximized)
```
$ expect myscript.exp
```

and then after it logins to ssh if I maximized(or resize) the window, the text does not show up correctly. for e.g. If i run top the output does not scale and shows up only as half screen ( I have attatched a screenshot)

If it helps here's the myscript.exp
```

#!/usr/bin/expect -f 
set timeout -1
set server xxx.xxx.xxx.xxx
set user xxx
set passwd xxx
set port  xxx
spawn /usr/bin/ssh $user@$server -p $port
match_max 100000
expect "*(yes/no)?*" {send "yes\r"; exp_continue} \
 "*?assword:*" {send "$passwd\r"}
send "\r"
interact

```

If I run the command in a maximized window it works as expected. I am beginning to think its a problem(bug) with expect. I have tried both the repository version and the compiled it manually from the website
All I could find in google related to this was
[http://coding.derkeiler.com/Archive/Tcl/comp.lang.tcl/2005-02/0252.html](http://coding.derkeiler.com/Archive/Tcl/comp.lang.tcl/2005-02/0252.html)

---

### Post by mssever on 2008-07-20
SIGWINCH is the signal that notifies programs that their window has changed size. I wonder if that signal isn't making it through.

---

### Post by mailbinoy on 2008-07-21
> **mssever said:**
> SIGWINCH is the signal that notifies programs that their window has changed size. I wonder if that signal isn't making it through.

thanks, I tried 
kill -SIGWINCH $$
kill -WINCH $$

but both did not help. Should I file in a bug report?

---

### Post by supirman on 2008-07-21
You have to trap SIGWINCH in your expect script and propagate this to the child.

Add the following to your expect script:
```
trap {
 set rows [stty rows]
 set cols [stty columns]
 stty rows $rows columns $cols < $spawn_out(slave,name)
} WINCH

```

Take the following script for example:
```
#!/usr/bin/env expect

#trap sigwinch and pass it to the child we spawned
trap {
 set rows [stty rows]
 set cols [stty columns]
 stty rows $rows columns $cols < $spawn_out(slave,name)
} WINCH

set username yourUserNameHere
set pass yourPasswordHere
set host theIpAddressToConnectTo

spawn ssh ${username}@${host}

expect -re "password:"
send "${pass}\r"

expect -re "$"

# now interact with the session
interact

```

---

### Post by mailbinoy on 2008-07-21
> **supirman said:**
> You have to trap SIGWINCH in your expect script and propagate this to the child.

Add the following to your expect script:
```
trap {
 set rows [stty rows]
 set cols [stty columns]
 stty rows $rows columns $cols < $spawn_out(slave,name)
} WINCH

```

Take the following script for example:
```
#!/usr/bin/env expect

#trap sigwinch and pass it to the child we spawned
trap {
 set rows [stty rows]
 set cols [stty columns]
 stty rows $rows columns $cols < $spawn_out(slave,name)
} WINCH

set username yourUserNameHere
set pass yourPasswordHere
set host theIpAddressToConnectTo

spawn ssh ${username}@${host}

expect -re "password:"
send "${pass}\r"

expect -re "$"

# now interact with the session
interact

```

Ah that fixed it. Thanks guys

---

