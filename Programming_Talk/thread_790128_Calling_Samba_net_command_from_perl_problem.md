---
title: "Calling Samba net command from perl problem"
date: 2008-05-11
forum: Programming Talk
---

### Post by bigeyes0x0 on 2008-05-11
I use Ubuntu 7.10 and its corresponding Samba and perl packages (no time and bandwidth to upgrade to latest version currently).
I wrote this subroutine for my scripts (dealing with a system to enforce time-quota for domain users) and it doesn't work
```
#!/usr/bin/perl -w
use strict;
sub shutdown {
	my ($str, $sec, $msg, $user);	
	#set grace period (in second) before shutting down remote Windows computer
	$sec = 120;
	#set message to send to computer being shut down
	$msg = "You have run out of your alloted time. Please save your works. This computer will shut down in $sec seconds.\n";
	#set user to turn off remote machine
	$user = "root";
	$str = `net rpc shutdown -t $sec -f -C $msg -U $user -S $_[0]`;
	print $str;
}

&shutdown ("xp1");
```
It says:
```
Password:
Could not connect to server 127.0.0.1
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE
Could not connect to server 127.0.0.1
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE
sh: -U: not found
```
Calling the same command with same parameters from the shell works fine.
Any idea? Help is really appreciated.

---

### Post by tr333 on 2008-05-11
```
$str = `net rpc shutdown -t $sec -f -C $msg -U $user -S $_[0]`;
```
Try changing the backticks in this line to double quotes.  The next line should then print out the command that would have been run normally.  Copy+paste that command into a terminal and see if it has the desired effect.

E.g.

```
#!/usr/bin/perl -w
use strict;
sub shutdown {
	my ($str, $sec, $msg, $user);	
	#set grace period (in second) before shutting down remote Windows computer
	$sec = 120;
	#set message to send to computer being shut down
	$msg = "You have run out of your alloted time. Please save your works. This computer will shut down in $sec seconds.\n";
	#set user to turn off remote machine
	$user = "root";
	**$str = "net rpc shutdown -t $sec -f -C $msg -U $user -S $_[0]"**;
	print $str;
}

&shutdown ("xp1");
```

---

### Post by bigeyes0x0 on 2008-05-11
Thank you, it's my stupid mistake. Printing out the command shows me the problem. I need to change
```
$msg = "You have run out of your alloted time. Please save your works. This computer will shut down in $sec seconds.\n";
```to
```
$msg = "\"You have run out of your alloted time. Please save your works. This computer will shut down in $sec seconds.\"";
```
Well only know Perl for a few days, but I must say it's pretty powerful and easy to learn and write.

---

### Post by tr333 on 2008-05-13
You could also just as easily do this with SH:

```
#!/bin/sh

function shutdown {

# get target machine to shut down. use double-quotes to prevent malicious script injection
target="$1"

# set grace period (in seconds) before shutting down remote Windows computer
sec=120
# set messate to send out to computer being shut down
msg="You have run out of your alloted time. Please save your work. This computer will shut down in $sec seconds."
# set user to turn off remote machine
user="root"

# $1 is the first argument for this function
net rpc shutdown -t $sec -f -C $msg -U $user -S $target

}

# shutdown using first argument to script if given, otherwise use preset value of "xp1".  You can then call this script with "shutdownscript.sh <targetmachine>" or just "shutdownscript.sh" to use the preset target machine name.
if [ -z "$1" ]; then
    shutdown "xp1"
else
    shutdown "$1"
fi

```

Note: I haven't tested this code.

---

