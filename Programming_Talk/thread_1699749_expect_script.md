---
title: "expect script"
date: 2011-03-04
forum: Programming Talk
---

### Post by Drenriza on 2011-03-04
Hi all.

I have been trying to figur expect script out. And was wondering if anyone could take a look at what i have so far.

What i want to do. Is get the script to login to a remote server. execute a bash command, and exit.

#!/bin/expect -f

##variables
##password part.
set password "password"
set ipaddress "ipaddress"

##email part.
set email "example@example.com"
set name "e-mail"

set timeout 10
spawn ssh user@ipaddress

expect "password"
send "$password\r"

send "ls ~/path/to/folder >> | /usr/bin/mail -s "$e-mail" $email"
send "ls ~/path/to/folder >> | /usr/bin/mail -s "$e-mail" $email"

My questions are.

#1 will the login (ssh) part work?
#2 does the expect password and send password look correct?
#3 can you send a bash command, by putting the send "infront"
hope it makes sense.
#4 how do i send an exit command to terminate the connection?

---

