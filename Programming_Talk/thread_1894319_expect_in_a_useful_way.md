---
title: "expect in a useful way?"
date: 2011-12-12
forum: Programming Talk
---

### Post by Drenriza on 2011-12-12
So i am wondering. What is expect designed to do? Specifics please.

I have no problems with it, logging into a remote system, or downloading files from a remote site.
But when i try to edit something on a remote system, like creating a file. Nothing.

Example Note $Amount equals a decimal value with no colons or anything.
```

/usr/bin/expect - << EndMark
set timeout 1
exp_internal 1
spawn /usr/bin/ssh -f root@ip "/bin/ls /path/ |/bin/grep X_ |/usr/bin/head -n $Amount > /path/test"
sleep 1
expect "root@ip's password:"
sleep 1
send "password\r"
sleep 1
EndMark

```

But it docent create the file at the remote site.
This is the output i get

```

spawn /usr/bin/ssh -f root@ip /bin/ls /path/ |/bin/grep X_ |/usr/bin/head -n 5 > /path/test
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {4060}

expect: does "" (spawn_id exp4) match glob pattern "root@ip's password:"? no
root@ip's password: 
expect: does "root@ip's password: " (spawn_id exp4) match glob pattern "root@ip's password:"? yes
expect: set expect_out(0,string) "root@ip's password:"
expect: set expect_out(spawn_id) "exp4"
expect: set expect_out(buffer) "root@ip's password:"
send: sending "password\r" to { exp4 }

```

Why cant it run commands in expect i can run by hand?
Also is their any up-to-date useful expect guides?

Kind regards.

---

### Post by CoffeeRain on 2011-12-12
I don't have much experience with this, but it looks like it is trying to match a blank object "" (I don't know where it is coming from) with another form.

---

### Post by slavik on 2011-12-12
you are using expect wrong ... why on earth are you sticking everything you want to do into the ssh command? why not do it the way it was meant to be used?

1. log in
2. do stuff you need
3. log out

---

### Post by hakermania on 2011-12-12
Example usage of expect for updating this file: [http://wall-changer.sourceforge.net/screenshots.html](http://wall-changer.sourceforge.net/screenshots.html)
(part of the code that contains expect)
```

#!/bin/bash
/usr/bin/expect - << EndMark
set timeout -1

spawn sftp username,wall-changer@web.sourceforge.net
expect "username,wall-changer@web.sourceforge.net's password: "
send "passwd\r"
expect "Connected to web.sourceforge.net."
send "cd htdocs\r"
expect "sftp>"
send "put screenshots.html\r"
sleep 5
EndMark
exit

```

---

### Post by Drenriza on 2011-12-12
> **slavik said:**
> you are using expect wrong ... 
So what is the correct way?

shouldn't expect be able to run the ssh -f user@ip "command" command?
If no, why?

And does anyone know why i get this
> I don't have much experience with this, but it looks like it is trying to match a blank object ""

---

### Post by Drenriza on 2011-12-13
even if i do
```
#!/usr/bin/expect -f
set timeout 60
exp_internal 1

spawn ssh root@ip
sleep 1
expect "root@ip's password:"
sleep 1
send "password\r"
sleep 3
send "/bin/ls /path/ |/bin/grep X_ |/usr/bin/head -n 5 > /path/test\r"
exit
```
it still docent work. Since the file is not created.
So what am i doing wrong?

---

