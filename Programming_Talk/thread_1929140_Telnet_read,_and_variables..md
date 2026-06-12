---
title: "Telnet read, and variables."
date: 2012-02-21
forum: Programming Talk
---

### Post by Grenage on 2012-02-21
I need to connect to an old mail server via POP/IMAP, but for the purposes of the script, the protocol isn't relevant.  The purpose of this is to empty a mailbox of all mail.  One can return the total number of messages, and delete a message by referring to its ID; sounds simple, I just need to take the total as a variable, and use it in a loop.

This is of course where I hit the proverbial wall, as I've never gone beyond using expect to echo static strings.  Does anyone have any examples or information on how to go about this?

---

### Post by sudodus on 2012-02-21
I would try Thunderbird with the import/export tool (add-on). I have used it transfer old Outlook mails to gmail.

---

### Post by Grenage on 2012-02-21
Cheers for the feedback.  Unfortunately that's not an option as I'll be scripting it for use with Nagios! :)

---

### Post by lensman3 on 2012-02-21
If you login via

"telnet <url> pop3"  (no quotes).

And type in HELP   (in caps). Does the help return any info?  If it does you should be able to parse the number, you need.

The pop3 number can be found /etc/services, but telnet will translate it for you. 

Sorry I can't help you.  I don't have a pop server running anymore and gmail.com doesn't talk on those ports.

---

### Post by Grenage on 2012-02-22
Thanks for your suggestion. :)

This is really more of a query regarding taking text output as a variable, and using it within that instance.

---

### Post by Grenage on 2012-02-22
I got there in the end, using expect; I couldn't figure out another way of doing it.  For the record, the code that would make Gods cry:

```
#!/usr/bin/expect
#the package 'expect' must be installed.

set hostname	[lindex $argv 0]
set portnumber	[lindex $argv 1]
set username	[lindex $argv 2]
set password	[lindex $argv 3]
set output		""

if {$hostname == "" || $portnumber == "" || $username == "" || $password == ""} {
	puts "Usage: SCRIPT host port user pass\n"
	exit 1
}

#takes the exit code and specified text, then exits the
#script with the appropriate code and description
proc exitcode {chosencode chosenreason} {
	global output
	if {$chosencode == 0} {
		puts "$chosenreason |$output"
		exit 0} {
		puts "$chosenreason, check performance data|$output"
		close $spawn_id
		exit 1
	}
}

#stop data being immediately returned
log_user 0
#initialise a telnet instance
spawn telnet $hostname $portnumber

#expect an 'OK' prompt, and send username when ready
expect {
	-re {\+OK.*} {
		send "user $username\n"
		set output $expect_out(0,string)
		set output "${output}user $username\n"
	} -re {\-ERR.*} {
		exitcode 1 "Failure during initialisation"
	} timeout {
		exitcode 1 "Timeout during initialisation"
	}
}

#expect an 'OK' prompt, and send password when ready
expect {
	-re {\+OK.*} {
		send "pass $password\n"
		set output $output$expect_out(0,string)
		set output "${output}password $password\n"
	} -re {\-ERR.*} {
		exitcode 1 "Problem at username"
	} timeout {
		exitcode 1 "Timeout at username"
	}
}

#expect an 'OK' prompt, and send 'stat' to return the total number of e-mails
#this exists purely for performance data logging
expect {
	-re {\+OK.*} {
		send "stat\n"
		set output $output$expect_out(0,string)
		set output "${output}stat\n"
	} -re {\-ERR.*} {
		exitcode 1 "Problem at password"
	} timeout {
		exitcode 1 "Timeout at password"
	}
}

#expect an 'OK' prompt, and send 'stat' to return the total number of e-mails
expect {
	-re {\+OK.*} {
		send "stat\n"
		set output $output$expect_out(0,string)
	} -re {\-ERR.*} {
		exitcode 1 "Problem at stat command"
	} timeout {
		exitcode 1 "Timeout at stat command"
	}
}

#expect regex to match e-mail total, and utilise in a loop that deletes them.
#this regex will match 1-9999 e-mails, and is very imprecise.
expect {
	-re "(\[0-9]{1,4})" {
		for {set counter 1} {$counter <= $expect_out(1,string)} {incr counter 1} {
			send "dele $counter\n"
			expect {
				-re {\+OK.*} {
					if {$counter == $expect_out(1,string)} {
						set output "${output}#deletion loop executed#\n"
					}
				} -re {\-ERR.*} {
					exitcode 1
				} timeout {
					exitcode 1
				}
			}
		}
		send "quit\n"
		set output "${output}quit\n"
	} -re {\-ERR.*} {
		exitcode 1 "Error at stat command"
	} timeout {
		exitcode 1 "Timeout at stat command"
	}
}

#expect an 'OK' prompt, and exit gracefully
expect {
	-re {\+OK.*} {
		set output $output$expect_out(0,string)
		exitcode 0 "OK - [expr $counter-1] messages deleted"
	} -re {\-ERR.*} {
		exitcode 1 "Error whle exiting"
	} timeout {
		exitcode 1 "Timeout while exiting"
	}
}
```

---

