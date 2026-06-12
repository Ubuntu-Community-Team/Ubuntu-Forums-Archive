---
title: "Expect scripts don't work?"
date: 2008-06-04
forum: Programming Talk
---

### Post by statistic on 2008-06-04
I'm sure I'm missing something awfully obvious here, but I'm trying to use a basic pre-made expect script, but none of the commands are recognized. I installed the expect package, but this:
```
  
  #!/usr/bin/expect #Where the script should be run from.
   set timeout 20 
   set Machine [lindex $argv 1] 
   set Username [lindex $argv 2] 
   set Password [lindex $argv 3] 
   spawn telnet $Machine 
   expect "login:" #The script expects login
   send "$Username" #The script sends the user variable 
   expect "Password:" #The script expects Password
   send "$Password" #The script sends the password variable
   send "quit"

```

just yields the following errors:

./expectTest: line 6: spawn: command not found
couldn't read file "login:": no such file or directory
./expectTest: line 8: send: command not found
couldn't read file "Password:": no such file or directory
./expectTest: line 10: send: command not found
./expectTest: line 11: send: command not found


Obviously the expect commands are being considered not commands.

Any help would be greatly appreciated.
Thanks.

---

### Post by odyniec on 2008-06-04
How are you executing the script? Based on the error messages, it appears that _bash_ is trying to run the commands, not expect.

---

### Post by statistic on 2008-06-04
Thank you for pointing out the obvious error, I thought that the #!/usr/bin/expect would make the script execute as an expect script, but I see now that I should be calling it with expect scriptName.

---

### Post by dtmilano on 2008-06-04
I'm not testing it (don't have expect right now because I've been using pexpect in python for some time) but AFAICR you should use '#! /usr/bin/expect -f' in shebang.

---

