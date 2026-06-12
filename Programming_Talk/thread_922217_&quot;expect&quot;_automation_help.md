---
title: "&quot;expect&quot; automation help"
date: 2008-09-17
forum: Programming Talk
---

### Post by aradaj on 2008-09-17
I'm trying to automate installs using expect.

I was wondering if it was possible to create an automatic response every time a specific pattern is invoked.

currently i have this:

```

#!/usr/bin/expect -f
spawn install
expect "More"
send -- " "
expect "More"
send -- " "
expect "More"
send -- " "
expect "More"
send -- " "
expect "More"
send -- " "
expect "More"
send -- " "
expect "More"
send -- " "
expect "More"
send -- " "
expect -exact "\r
Do you accept this agreement, yes or no? (y/n/h) "
send -- "y"
expect -exact "\r
Do you accept this agreement, yes or no? (y/n/h) "
send -- "y"
expect eof

```

The problem that I am running into with this script is that when I have different terminal window sizes the script basically falls apart. As there would be more "More" prompts if the terminal window size is smaller, and less "More" prompts if the terminal window size is bigger. 

Would it be possible that every time "More" is invoked it would create an automatic response?

Any advice would be greatly appreciated.

-JC Arada

---

### Post by odyniec on 2008-09-17
Try placing the expect code in a while loop and check for a specific condition to exit the loop (in your case, the condition would be eof). Something along the lines of:
```
#!/usr/bin/expect -f
spawn install
set done 0
while {$done == 0} {
    expect {
        "More" { send -- " " }
        -exact "Do you accept this agreement, yes or no? (y/n/h) " { send -- "y" }
        eof { set done 1 }
    }
}
```

---

### Post by aradaj on 2008-09-17
Thank you so much! This is exactly what I needed.

-JC Arada

---

### Post by Jws0001 on 2008-09-17
Well since your thread title is broad and your question has been answered.. I have a side issue! :P

I'm trying to automate the SSH/VPN login process... I want to open a gnome terminal and ssh into the server then automatically enter my password, then interact with the terminal.

Here's what I'm trying...

#!/sbin/sh/expect -f

gnome-terminal -e ssh -Y username@server
expect -exact "Password:"
send -- "********"
interact

Suggestions?

---

### Post by odyniec on 2008-09-17
Create a script file containing the expect code to establish a SSH connection:
```
#!/sbin/sh/expect -f
ssh -Y username@server
expect -exact "Password:"
send -- "********"
interact
```
Then, in another file, launch gnome-terminal and tell it to execute the expect script:
```
#!/bin/sh
gnome-terminal -e /your/expect/script
```
However, if you want to avoid entering passwords for SSH sessions, you should consider using public key-based authentication.

---

### Post by Jws0001 on 2008-09-17
The error I'm getting is "There was an error creating the child process for this terminal" when I try that.

I happen to have the RSA key setup already but I was hoping to get this to work with SSH so that I could then adapt it to my VPN connection that prompts for username, password, and a (y/n) prompt.  I figure start easy first.

---

### Post by odyniec on 2008-09-18
Oh, I forgot to include "spawn" in the first script. Here's the correct version:
```
#!/sbin/sh/expect -f
spawn ssh -Y username@server
expect -exact "Password:"
send -- "********"
interact
```

---

### Post by aradaj on 2008-09-18
jws0001 you could try the the autoexpect script to create an exp script for a simple logon. This script is great to generate scripts when the interaction is linear and always the same. 

you could get it from expect-dev
```
sudo apt-get install expect-dev
```

then browse to "/usr/share/doc/expect-dev/examples" and extract autoexpect.gz to your "/usr/sbin"

```

cd /usr/share/doc/expect-dev/examples
sudo cp autoexpect.gz /usr/sbin/.
cd /usr/sbin
sudo gunzip autoexpect.gz
sudo chmod +x autoexpect

```

Assuming that you did the steps above or something similar you should be able to use the script as a command now.

To use autoexpect:

```
autoexpect -f <file_to_generate> <command> <$argv>
```

Examples:
```

jc@xubuntu:~$ autoexpect -f example.exp ssh 10.0.2.15
autoexpect started, file is example.exp
jc@10.0.2.15's password: 
Linux test 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu Sep 18 00:13:33 2008 from xubuntu.local
jc@test:~$ ls
Desktop
jc@test:~$ exit
logout
Connection to 10.0.2.15 closed.
autoexpect done, file is example.exp
jc@xubuntu:~$ 

```

Autoexpect knows how to end the script when the spawned process gets done.

Generated expect file:
```

#!/usr/bin/expect -f
#
# This Expect script was generated by autoexpect on Thu Sep 18 00:14:00 2008
# Expect and autoexpect were both written by Don Libes, NIST.
#
# Note that autoexpect does not guarantee a working script.  It
# necessarily has to guess about certain things.  Two reasons a script
# might fail are:
#
# 1) timing - A surprising number of programs (rn, ksh, zsh, telnet,
# etc.) and devices discard or ignore keystrokes that arrive "too
# quickly" after prompts.  If you find your new script hanging up at
# one spot, try adding a short sleep just before the previous send.
# Setting "force_conservative" to 1 (see below) makes Expect do this
# automatically - pausing briefly before sending each character.  This
# pacifies every program I know of.  The -c flag makes the script do
# this in the first place.  The -C flag allows you to define a
# character to toggle this mode off and on.

set force_conservative 0  ;# set to 1 to force conservative mode even if
			  ;# script wasn't run conservatively originally
if {$force_conservative} {
	set send_slow {1 .1}
	proc send {ignore arg} {
		sleep .1
		exp_send -s -- $arg
	}
}

#
# 2) differing output - Some programs produce different output each time
# they run.  The "date" command is an obvious example.  Another is
# ftp, if it produces throughput statistics at the end of a file
# transfer.  If this causes a problem, delete these patterns or replace
# them with wildcards.  An alternative is to use the -p flag (for
# "prompt") which makes Expect only look for the last line of output
# (i.e., the prompt).  The -P flag allows you to define a character to
# toggle this mode off and on.
#
# Read the man page for more info.
#
# -Don


set timeout -1
spawn ssh 10.0.2.15
match_max 100000
expect -exact "jc@10.0.2.15's password: "
send -- "****\r"
expect -exact "\r
Linux test 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686\r
\r
The programs included with the Ubuntu system are free software;\r
the exact distribution terms for each program are described in the\r
individual files in /usr/share/doc/*/copyright.\r
\r
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by\r
applicable law.\r
\r
To access official Ubuntu documentation, please visit:\r
http://help.ubuntu.com/\r
Last login: Thu Sep 18 00:13:33 2008 from xubuntu.local\r\r
]0;jc@test: ~jc@test:~\$ "
send -- "ls\r"
expect -exact "ls\r
[00m[01;34mDesktop[00m\r
[m]0;jc@test: ~jc@test:~\$ "
send -- "exit\r"
expect eof


```

That should be a good enough primer for autoexpect. You can also slim down the generated expect script by just limiting the expect to the specific pattern you are looking for.

Below is the same script but slimed down:
```

#!/usr/bin/expect -f
spawn ssh 10.0.2.15
expect -exact "jc@10.0.2.15's password: "
send -- "****\r"
expect "jc@test:~\$ "
send -- "ls\r"
expect "jc@test:~\$ "
send -- "exit\r"
expect eof

```

---

### Post by Jws0001 on 2008-09-18
Ah! Thank you very much!!! The autoexpect package was immensely useful at creating scripts for my SSH and VPN connections.  It was also very helpful at showing  me what pieces of syntax I was missing.  This is great, I am highly enjoying learning how to script tools like this in linux :)

---

