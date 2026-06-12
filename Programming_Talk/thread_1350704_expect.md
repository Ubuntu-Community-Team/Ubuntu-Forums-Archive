---
title: "expect"
date: 2009-12-09
forum: Programming Talk
---

### Post by rsanchezy on 2009-12-09
Hi, I have a Cisco Switch & I want to create a script to test every port of this switch.
Is it possible create a expect script with a loop to test every port? 
I connect to my switch ok, but when my script tries to read this port =2 expect stops.
I set port variable  in 2 but i did not work.
Do you a have a link can I help me?
 
This is my script:
 
[FONT=Courier New][SIZE=2]#!/usr/bin/expect -f
[/SIZE][/FONT][FONT=Courier New][SIZE=2]# script testing ports
#  IP Sw .72
 [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]#5
set site 172.16.1.72
set passvty cisco
set passena it-passwd09
#set port 2  [/FONT]**[FONT=Wingdings][FONT=Wingdings]ß[/FONT][/FONT]****[FONT=Courier New] I tried this[/FONT]**[/SIZE]

[FONT=Courier New][SIZE=2]spawn telnet $site
#12
expect "assword:"
send "$passvty\r"

expect "uno>"
sleep 2
send "enable\r"

expect "assword:"
sleep 2
send "$passena\r"
#23
sleep 2

send "\r"
#expect "uno#"

sleep 3

[/SIZE][/FONT][SIZE=2][FONT=Courier New]send "configure terminal\r"
expect "uno(config)#"

port = 2 [/FONT]**[FONT=Wingdings][FONT=Wingdings]ß[/FONT][/FONT]****[FONT=Courier New] Try this too[/FONT]**[/SIZE]
[SIZE=2][FONT=Courier New]echo "BEFORE  LOOP"
while [ $port -lt 25 ]; do
 [/FONT][/SIZE][SIZE=2][FONT=Courier New]#### CICLO
echo "Testing el port:$port"
 [/FONT][/SIZE][SIZE=2][FONT=Courier New]send "interface F0/$port \r"
 expect "uno(config-if)#"
 send "no shutdown \r"
 echo " port up"
 expect "uno(config-if)#"
 sleep 45 
[/FONT][/SIZE][SIZE=2][FONT=Courier New] # I need to have this port up & test this port
 # for 40 segs
 [/FONT][/SIZE][SIZE=2][FONT=Courier New]send "shutdown \r"
 expect "uno(config-if)#"
 send "exit \r"
 expect "uno(config)#"

 port=$((port+1))
 done
##### END LOOP[/FONT][/SIZE]
[FONT=Courier New][SIZE=2]send "exit \r"
[/SIZE][/FONT][SIZE=2][FONT=Courier New]expect "uno#"
sleep 2
send "exit\r"
 [/FONT][/SIZE]

---

