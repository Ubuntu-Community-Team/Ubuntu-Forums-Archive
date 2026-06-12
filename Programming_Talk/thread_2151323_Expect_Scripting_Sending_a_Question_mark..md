---
title: "Expect Scripting Sending a Question mark."
date: 2013-06-04
forum: Programming Talk
---

### Post by bjforesthowell on 2013-06-04
I'm new to expect all together, but what I'm trying to do is write a script that allows me to upgrade the IOS on my CISCO access layer devices. I keep trying to send a "dir ?" to the command line via the script, and i believe that the question mark is being interpreted as a wildcard. I've tried putting \\ in front of the character, but I still get errors when I run the script. Do I need to put the \\ at the front of the string "\\dir ?\r", or before the question mark "dir \\?\r".

[ATTACH]243491[/ATTACH]

---

### Post by ofnuts on 2013-06-04
'?' is indeed a wildcard in bash,  but only outside single or double quotes (and it would be expanded only if you have a files with single-character names. Create an empty directory and try:
```

>echo ?
? # nothing matches
>touch a b # create files
>echo ?
a b 
>echo "?"
?
>echo '?'
?

```

 So your problem may be elsewhere.

---

### Post by ofnuts on 2013-06-04
.

---

### Post by steeldriver on 2013-06-04
Have you tried just a single backslash?

```
"dir \?\r"
```

That seemed to work for me (tried it with an ssh login, after changing the remote password to have a ? in it) - it may depend exactly how you're invoking expect though i.e. how many layers of bash/Tcl shell/interpreter are involved

---

### Post by bjforesthowell on 2013-06-05
I've tried pretty much every combination. It seems like ofnuts is right, it's something wrong earlier on in my script. I've eliminated the question mark all together by sending a different command to the switch that gives me the output that I need. What I'm getting right now is this...

send: spawn id exp6 not open
     while executing
"send "dir all-filesystems\r""
      (file ./batch_ssh.exp" line 41)

When I look at the output file I created all I see is the switch doing the initial "dir flash:" Then the script times out. Here's what I've got written into the script currently.
 
```
#!/usr/bin/expect -f
# Bj Howell
# June 3, 2013
# Upgrades the IOS on a list of systems.
set timeout 700 
set host [lindex $argv 0]
set user [lindex $argv 1]
set pass [lindex $argv 2]
spawn ssh -o StrictHostKeyChecking=no $user@$host
expect "password:"
send "$pass\r"
expect "*#"

#Checks to see if it has the new code. If it does, it schedules a reboot and sets the boot statement.

send "dir flash:\r"
expect {
	"*c3750-ipservicesk9-mz.122.55.SE5"{} 
	"*c3750-ipservicesk9-mz.122-55.SE7.bin"{
	send "conf t\r"
	expect "*(config)#"
	send "boot system flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
	expect "*(config)#"
	send "exit\r"
	expect "*#"
	send "reload at 02:00 8 June\r"
	expect "System configuration has been modified. Save? [yes/no]:"
	send "yes\r"
	expect "Proceed with reload? [confirm]"
	send "\r"
	expect "*#"
	send "wr\r"
	expect "*#"
	send "exit\r"
	expect eof
	}
}

# checks to see if there are other members in the stack, and if there are it will delete the IOS off of each member.

send "dir all-filesystems\r"
expect {
	"Directory of flash:/"{
	send "delete /force /recursive flash1:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash1:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash2:/"{
	send "delete /force /recursive flash2:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash2:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash3:/"{
	send "delete /force /recursive flash3:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash3:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash4:/"{
	send "delete /force /recursive flash4:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash4:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash5:/"{
	send "delete /force /recursive flash5:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash5:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash6:/"{
	send "delete /force /recursive flash6:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash6:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash7:/"{
	send "delete /force /recursive flash7:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash7:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash8:/"{
	send "delete /force /recursive flash8:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash8:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash9:/"{
	send "delete /force /recursive flash9:c3750-ipservicesk9-mz.122-55.SE5\r"
	expect "*#"
	send "delete /force /recursive flash9:c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
}

#This deletes the IOS from a single device, then tftps the IOS to flash. If the TFTP fails it tries one more time.

send "copy tftp: flash:\r"
expect "Address or name of remote host []?"
send "204.208.204.209\r"
expect "Source filename []?"
send "c3750-ipservicesk9-mz.122-55.SE7.bin\r"
expect "Destination filename [c3750-ipservicesk9-mz.122-55.SE7.bin]?"
send "c3750-ipservicesk9-mz.122-55.SE7.bin\r"
expect {
	"[OK - 12750343 bytes]"{}
	"[timed out]"{
	send "copy tftp: flash:\r"
	expect "Address or name of remote host []?"
	send "204.208.204.209\r"
	expect "Source filename []?"
	send "c3750-ipservicesk9-mz.122-55.SE7.bin\r"
	expect "Destination filename [c3750-ipservicesk9-mz.122-55.SE7.bin]?"
	send "c3750-ipservicesk9-mz.122-55.SE7.bin\r"
	expect "[OK - 12750343 bytes]"
	}
}

# checks to see if there are other members in the stack, and if there are it will copy the ios from flash1 to the other devices.

send "dir all-filesystems\r"
expect {
	"Directory of flash2:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash2:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash3:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash3:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash4:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash4:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash5:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash5:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash6:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash6:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash7:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash7:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash8:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash8:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
	"Directory of flash9:/"{
	send "copy flash1:c3750-ipservicesk9-mz.122-55.SE7.bin flash9:\r"
	expect "Destination filename"
	send "c3750-ipservicesk9-mz.122-55.SE5.bin\r"
	expect "*#"
	}
}

# Sets the boot statement for the stack

send "conf t\r"
expect "*(config)#"
send "boot system flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
expect "*(config)#"
send "exit"
expect "*#"

#sets the reload time, writes everything to memory, then exits.

send "reload at 02:00 8 June\r"
expect "System configuration has been modified. Save? [yes/no]:"
send "yes\r"
expect "Proceed with reload? [confirm]"
send "\r"
expect "*#"
send "wr mem\r"
expect "*#"
send "exit\r"



expect eof
```

---

### Post by steeldriver on 2013-06-05
it looks like in your first block of statements you are sending an 'exit' - in which case don't you need to re-spawn the connection?

btw if you could use CODE tags when posting it would be much easier to read

---

### Post by bjforesthowell on 2013-06-05
Sorry about that, I had no clue I had to add the code tags...

I  thought that in this section that {} meant that if the screen output c3750-ipservicesk9-mz.122.55.SE5 that it would skip down to (send "dir all-filesystems\r") instead of going to the nested statements below c3750-ipservicesk9-mz.122.55.SE5. Does {} mean that if it displays "*c3750-ipservicesk9-mz.122.55.SE5" it kills the script all  together, and if it does should I re-spawn below this section?

```
send "dir flash:\r"
expect {
	"*c3750-ipservicesk9-mz.122.55.SE5"{} 
	"*c3750-ipservicesk9-mz.122-55.SE7.bin"{
	send "conf t\r"
	expect "*(config)#"
	send "boot system flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
	expect "*(config)#"
	send "exit\r"
	expect "*#"
	send "reload at 02:00 8 June\r"
	expect "System configuration has been modified. Save? [yes/no]:"
	send "yes\r"
	expect "Proceed with reload? [confirm]"
	send "\r"
	expect "*#"
	send "wr\r"
	expect "*#"
	send "exit\r"
	expect eof
	}
}
```

---

### Post by bjforesthowell on 2013-06-10
What if I was going to write a regular expression to search for the text? Something like this.

```

expect "*#"
send "dir flash:\r"
expect 
	if 
	-re \<c3750-ipservicesk9-mz\.122-55\.SE7\.bin\> #If the line ends in 3750-ipservicesk9-mz.122-55.SE7.bin then set boot statement, reload time, then exit and go to next host
	then 
		send "conf t\r"
		expect "*(config)#"
		send "boot system flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
		expect "*(config)#"
		send "exit\r"
		expect "*#"
		send "reload at 02:00 8 June\r"
		expect "System configuration has been modified. Save? [yes/no]:"
		send "yes\r"
		expect "Proceed with reload? [confirm]"
		send "\r"
		expect "*#"
		send "wr\r"
		expect "*#"
		send "exit\r
		expect eof
	elif 
	-re ^(.*)(\bc3750-ipservicesk9-mz\.122-55\.SE5\b)(.*?)$ | ^(.*)(\bc3750-ipservicesk9-mz\.122-55\.SE5\b)(.*?)$
then 
fi


```

So in the switch i wan to run this command... dir flash: which results in the following output.


```
B3757_1B133-SW1&2#dir flash:
Directory of flash:/

    3  -rwx        7192   Jun 6 2013 15:23:33 +02:00  multiple-fs
    7  drwx         192  Apr 24 2012 11:05:35 +02:00  c3750-ipservicesk9-mz.122-55.SE5
    4  -rwx        1396  Jun 13 2012 14:27:24 +02:00  vlan.dat
    5  -rwx        2410   Jun 6 2013 15:23:33 +02:00  private-config.text
    6  -rwx       50173   Jun 6 2013 15:23:33 +02:00  config.text

32514048 bytes total (15863296 bytes free)
B3757_1B133-SW1&2#

```

When I put the regex into a tester [http://regexpal.com/](http://regexpal.com/) I don't get any matches. Can someone point me in the right direction of a regex tester for Linux, or possibly let me know what I'm doing wrong when I'm writing the expression?

---

### Post by bjforesthowell on 2013-06-12
I was able to get the regular expression correct, but I don't know how to use it within expect now. He's an example of what I'm trying to do...

The regular expression is as follows.

\bc3750-ipservicesk9-mz.122-55.SE7.bin\b

I pump it into [www.myregextester.com](www.myregextester.com) along with the data i'm searching for and it's able to return a match in no time. I just don't know how to use it in expect now.


```
send "term length 0\r"
expect "*#"
send "wr mem\r"
expect "*#"
send "dir flash:\r"
expect
	regex=$1 
	if [[ $1 =~ \bc3750-ipservicesk9-mz.122-55.SE7.bin\b ]]; then {
		send "conf t\r"
		expect "*(config)#"
		send "boot system flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
		expect "*(config)#"
		send "exit\r"
		expect "*#"
		send "reload at 02:00 8 June\r"
		expect "System configuration has been modified. Save? [yes/no]:"
		send "yes\r"
		expect "Proceed with reload? [confirm]"
		send "\r"
		expect "*#"
		send "wr\r"
		expect "*#"
		send "exit\r
		expect eof
	elif [[ $1 =~ \bc3750-ipservicesk9-mz.122-55.SE5\b | $1 =~ b\c3750-ipservicesk9-mz.122-55.SE5.bin\b} ]]; then
fi
}


```

---

### Post by bjforesthowell on 2013-06-19
As it ends up, expect is written TCL (once again completely new) the correct syntax is as follows.

```
send "term length 0\r"
expect "*#"
send "wr mem\r"
expect "*#"
send "dir flash:\r"
expect {
	-re {\mc3750-ipservicesk9-mz\.122-55\.SE7\.bin\M} {
		send "conf t\r"
		expect "*(config)#"
		send "boot system switch all flash:c3750-ipservicesk9-mz.122-55.SE7.bin\r"
		expect "*(config)#"
		send "exit\r"
		expect "*#"
		send "reload at 02:00 15 June\r"
		expect "System configuration has been modified. Save?"
		send "yes\r"
		expect "Proceed with reload?"
		send "\r"
		expect "*#"
		send "wr\r"
		expect "*#"
		send "exit\r
		expect eof
		}
	-re {\mc3750-ipservicesk9-mz\.122-55\.SE5(?:\.bin)?\M}
}
```

I hope that this helps someone out!

---

