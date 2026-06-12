---
title: "how to allow apache run sudo commands"
date: 2007-12-13
forum: Programming Talk
---

### Post by torpe0 on 2007-12-13
Hi :)

I'm trying to activate an linux command that requires sudo from a CGI Perl script. This is for an internal website.

I have asked my friend google about this, and found different solutions, not getting anything to work properly.

In perl I run:
$return=(system("sudo iptables -F"));
The $return-value gets set to 256 when this runs.

In sudoers I have tried to add lots of different lines, without any luck so far :) What is the correct syntax here? And does sudoers REALLY need to be edited in vi, or could I sudo nano sudoers? At last - do I need a reboot or something after editing sudoers?

Thanks for all reply
--
Tor Arne

---

### Post by slavik on 2007-12-13
using sudo like that will def not work because sudo is interactive ...

what you can do though (in Perl) is something like this:

$output = `echo 'password' | sudo -S iptables -F`;

the password promt gets printed to stderr (it still appears in terminal), not sure how it affects any program you might want to run as root if they print to stderr.

---

### Post by geirha on 2007-12-13
The following are some example entries for sudoers, allowing the apache user (www-data) to run iptables, ifconfig and route without specifying a passwd. (the commands must be specified with full path)

```
User_Alias	APACHE = www-data
Cmnd_Alias	FIREWALL = /sbin/iptables, /sbin/ifconfig, /sbin/route

APACHE	ALL = (ALL) NOPASSWD: FIREWALL
```

Remember to use the visudo command to edit the sudoers file. Don't edit it directly, and run a root shell in a terminal in case you manage to make an error in the file (which would make sudo stop working).

@slavik. Piping the password to sudo won't work as sudo doesn't read the password from stdin.

---

### Post by torpe0 on 2007-12-13
Yes, that worked :) Silly me had /path/to/cgi/script as cmnd. *blush*. Thank you very much :)

--
ta

---

### Post by slavik on 2007-12-13
> **geirha said:**
> The following are some example entries for sudoers, allowing the apache user (www-data) to run iptables, ifconfig and route without specifying a passwd. (the commands must be specified with full path)

```
User_Alias	APACHE = www-data
Cmnd_Alias	FIREWALL = /sbin/iptables, /sbin/ifconfig, /sbin/route

APACHE	ALL = (ALL) NOPASSWD: FIREWALL
```

Remember to use the visudo command to edit the sudoers file. Don't edit it directly, and run a root shell in a terminal in case you manage to make an error in the file (which would make sudo stop working).

@slavik. Piping the password to sudo won't work as sudo doesn't read the password from stdin.

Are you telling me that the man page lied?

[quote=manpage]
 -S  The -S (stdin) option causes sudo to read the password from the
           standard input instead of the terminal device.
[/quote]

EDIT: I will say that your solution is better than mine. :)

---

### Post by geirha on 2007-12-13
> **slavik said:**
> Are you telling me that the man page lied?



EDIT: I will say that your solution is better than mine. :)

A lack of rtfm from my side. I stand corrected :)

---

### Post by torpe0 on 2007-12-19
I got my service up and running, now to the next problem.. My  cgi script runs an at -command, trying to schedule an scpript containing iptables commands.
So I remove www-data from at.deny, and  cgi does now run at to schedule to run script, but the commands in the script are not executed. I have tried to add /path/to/script/including/script/name in sudoers, but nothing happens. What am I missing this time?

---

### Post by geirha on 2007-12-19
Hard to say. Running ```
sudo atq
``` shows the scheduled job to be run at the correct time? What does the code that executes the at-command look like?

---

### Post by torpe0 on 2007-12-19
yes it schedules correct. Command is 
	$info=(system("sudo at -f /home/int/test $fratid"));
where $fratid is 00:30 20.12.07

now I think problem here is that it should be
	$info=(system("sudo at -f /home/int/test $fratid"));
but that gives $info=256

I added /usr/bin/at in my CmndAlias in sudoers.
hmm..

---

### Post by geirha on 2007-12-20
hm, if www-data has allowance to run at as root without password, then I don't see any reason why that shouldn't work either.

---

