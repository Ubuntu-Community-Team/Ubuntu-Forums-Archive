---
title: "Bash convert to Perl - Please help"
date: 2009-08-17
forum: Programming Talk
---

### Post by gamarga on 2009-08-17
Hi,

I use it to quickly get diagnostics from cisco routers. Is it possible to convert the following bash script to Perl? 


#!/bin/rbash


# Script Written by Gamarga
created_by="Gamarga"
version="V1.3_16th_August_2009"
# Website for info [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
# Website for info [http://ss64.com/bash/](http://ss64.com/bash/)
# Change permission: chmod =rwx diag4.sh = read/write/executable

# Check number of arguments passed to application
if [ "x$#" != "x3" ]
then
        echo >&2 "Usage: $0 <IP> <USERNAME> <PASSWORD>"
        false ; exit
fi

# Variables
host=$1
shift
username=$1
shift
password=$1
shift
WAITS_TIME=5


# Main body of Code
clear
echo
echo
printf "%-32s : %-32s \n" "Script created by" ${created_by}
printf "%-32s : %-32s \n" "Version" ${version}
echo
date
echo
echo Pinging host "$host" ....
echo

# Ping test
if ping -c 1 -w 5 "$host"               # Check that host is pingable
then                                    # If it's pingable
        echo
        echo Ping test sucessful...... "$host"
        echo 
        echo Attempting to log onto remote host "$host" to get router stats.
        echo
else
        echo
        echo Ping test to "$host" was unsucessful......
        echo Unable to connect to remote host...... "$host"
        echo Exiting
        echo
        exit 1
fi

# Telnet to remote host 

expect << EOF
set timeout ${WAITS_TIME}

spawn telnet ${host}

# Log into remote host

expect {
        "*Username:*" {send "${username}\r"}
        "*Request Denied*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Connection refused*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Unable to connect*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*telnet*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*CCCCFailed login*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Authentication failed*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*timeout expired*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Connection closed by foreign host*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit
}
        "*#" {send "\r"}
        timeout {puts "Login Timed Out.... Exiting"; exit}
        }


# expect "*Username:*"
# send "${username}\r"

expect "*Password:*"
send "${password}\r"

expect {
        "*Username:*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Request Denied*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Connection refused*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Unable to connect*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*telnet*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*CCCCFailed login*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Authentication failed*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*timeout expired*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit}
        "*Connection closed by foreign host*" {puts "Login Attempt Failed, Use another username/password.... Exiting"; exit
}
        "*#" {send "\r"}
        timeout {puts "Login Timed Out.... Exiting"; exit}
        }


expect "*#"
send "\r"

# Run these commands once logged in

expect "*#"
send "terminal length 0\r"

expect "*#"
send "\r"


expect "*#"
send "sh ver\r"

expect "*#"
send "\r"

expect "*#"
send "\r"

expect "*#"
send "sh clock\r"

expect "*#"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "sh ip int brief\r"

expect "*#"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "sh int desc\r"

expect "*#"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "sh int status\r"

expect "*#"
send "\r"

expect "*#"
send "\r"



expect "*#"
send "sh int\r"

expect "*#"
send "\r"

expect "*#"
send "\r"



expect "*#"
send "sh int summary\r"

expect "*#"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "sh caller\r"

expect "*#"
send "\r"

expect "*#"
send "\r"

expect "*#"
send "sh caller ip\r"

expect "*#"
send "\r"

expect "*#"
send "\r"


expect "*#*"
send "sh arp\r"

expect "*#*"
send "\r"

expect "*#"
send "\r"


expect "*#*"
send "sh mac-address-table\r"

expect "*#*"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "sh proc cpu | i CPU utilization\r"

expect "*#*"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "sh proc cpu history\r"

expect "*#*"
send "\r"

expect "*#"
send "\r"



expect "*#"
send "sh log\r"

expect "*#*"
send "\r"

expect "*#"
send "\r"


expect "*#"
send "clear counters\r"

expect "*#*"
send "\r"

expect "*#"
send "\r"




expect "*#"
send "terminal length 24\r"

expect "*#"
send "\r"


# Exit and log off from  host
exit

expect "*#"
Send "\r"

expect "*#"
send "\r"

EOF

echo
echo
echo Diagnostics Completed
echo
echo

---

### Post by jpkotta on 2009-08-18
[http://search.cpan.org/dist/Expect/](http://search.cpan.org/dist/Expect/)
libexpect-simple-perl & libexpect-perl packages.

---

