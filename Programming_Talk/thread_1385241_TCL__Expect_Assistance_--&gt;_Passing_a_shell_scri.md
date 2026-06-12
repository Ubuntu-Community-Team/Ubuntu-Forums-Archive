---
title: "TCL / Expect Assistance --&gt; Passing a shell script variable into a tcl /expect script"
date: 2010-01-19
forum: Programming Talk
---

### Post by you_nix_bad_ideas on 2010-01-19
_Can someone help me read a named shell script variable into a TCL/expect script?_

I have seen numerous posts about people who pass commands from a shell script to a TCL/expect script via positional arguments (i.e. argv 1, argv 2...) but I would like to enable my TCL/expect script to read a password variable from a shell script without passing it as an argument (so it can't be displayed with the ps command).

I would write the TCL/expect script to prompt the user for the password, but since it is being called multiple times for multiple ssh sessions, it makes more sense to have the shell script prompt for the password and read the variable and then export it to the TCL/expect script.

My best effort is below but it doesn't work.

**Here's the shell (caller) script:**
#!/bin/bash
echo "username:"
read username
export username

echo "password:"
read password
export password

echo "now calling expect"
/tmp/expect_script.tcl


**Here's the TCL / expect (called) script:**
set myvarfile [ open "|[ /tmp/shell_script.sh vars ]" r ]
puts username
puts password

**Thanks for any help you can offer!**

---

### Post by silvviu on 2010-01-19
I think you can use "env" array to get the environnment variables:
puts $env(username)
puts $env(password)

---

### Post by you_nix_bad_ideas on 2010-01-19
These are not environment variables.  They are variables that are local to the calling shell script.

---

### Post by silvviu on 2010-01-19
once you "export" a name in bash, it becomes "environnment variable" for subsequent commands; I tested with bash + tcl (I'm not familiar with expect) and it works.

---

### Post by you_nix_bad_ideas on 2010-01-19
That worked!  Thanks for the help.

---

