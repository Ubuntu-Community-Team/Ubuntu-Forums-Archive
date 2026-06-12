---
title: "ssh interfactive login script - cron"
date: 2008-04-24
forum: Programming Talk
---

### Post by kevdog on 2008-04-24
Someone a ways back posted a solution of how in a bash shell script the script would sit and wait for the server to respond (like username), and then it would enter the username, would wait for the password statement, and then send the password.

For the life of me I can't find the post.  From what I vaguely remember is was something in the format of 

#!/bin/bash

...
...
[start interactive block here]
Wait for this specific line
Respond
Wait for next specific line
Respond
[end interactive block]
...
...

I cant remember the block headers or closures.  And the forum search isn't help me a whole bunch.

I dont think this entailed the expect command to the best of my knowledge.

Any help would be appreciated.

---

### Post by nanotube on 2008-04-24
it was probably using the "expect" program.

---

### Post by lithorus on 2008-04-24
Better yet, use ssh keys. No need to enter username or password.

---

### Post by kevdog on 2008-04-24
Dang I lost the link when the forum updated.  Most annoying.  I dont think it was expect, however any good tutorial on expect.

---

### Post by supirman on 2008-04-25
You can certainly do it with SSH keys as the previous poster mentioned.  Or, another alternative is with expect.  The following should be close to what you'd want with expect:


[PHP]
#!/usr/bin/env expect

set username yourUserNameHere
set pass yourPasswordHere
set host theIpAddressToConnectTo

spawn ssh ${username}@${host}

expect -re "password:"
send "${pass}\r"

expect -re "$"

#do whatever needs done here

send "exit\r"
expect eof  
[/PHP]

---

