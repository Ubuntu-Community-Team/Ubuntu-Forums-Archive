---
title: "Bash question"
date: 2007-10-17
forum: Programming Talk
---

### Post by Visti on 2007-10-17
Hi! I'm helping a friend do a bash script and I'm a bit stumped here.

He has a file with a number of IPs listed - the script then has to first ask him how many new entries he would like to make, read the last of the old entries and continue outputting new IPs from there.

A mock-up would be:

Read input for how many new IPs (Let's say input is 3)
Read last IP in file IPs.txt
Last IP is 127.0.0.3
Then 127.0.0.4, 127.0.0.5, 127.00.6 is written to the bottom of the file

I'm pretty new to scripting, so I can't really get my head around how to approach this. Can you read something like the last IP, but with the last digit as a variable and then run + 1 every time at it?

Any help would be appreciated.

---

### Post by Jacks0n on 2007-10-17
hm, try something like this

```

read -p "How many entries would you like to make? : " ENTRIES

FILE_PATH="/home/$USER/Desktop/file.txt"
LAST_IP=$(cat "$FILE_PATH" | tail -1)
LAST_IP_NUM=${LAST_IP##*'.'}
IP_NUMBER=$((LAST_IP_NUM+1))

NUM=0
while [[ $ENTRIES != $NUM ]]; do
	echo "127.0.0.${IP_NUMBER}" >> "$FILE_PATH"
	IP_NUMBER=$((IP_NUMBER+1))
	NUM=$((NUM+1))
done

```

---

### Post by Visti on 2007-10-18
Yay! Thanks a bunch. I haven't tested it yet, but it seems like it's exactly what I need.

---

### Post by Visti on 2007-10-27
Right, what I've got so far modifying the script example Jacks0n gave is this:

The file that needs to be read and appended to:
```
(..)
[snom105]
type=friend
username=snom105
secret=1234
subscribecontext=localextensions
language=dk
host=dynamic
dtmfmode=rfc2833
defaultip=192.168.230.15
mailbox=105

[snom106]
type=friend
username=snom106
secret=1234
subscribecontext=localextensions
language=dk
host=dynamic
dtmfmode=rfc2833
defaultip=192.168.230.16
mailbox=106
```

And the script I'm trying now is this:
```
#!/bin/bash
read -p "How many entries would you like to make? : " ENTRIES

LAST_NUM=$(cat "/home/devel/Desktop/sip.conf" | tail -1)
NUMBER=${LAST_NUM#*=}
NYT_NUM=$((NUMBER+1))

NUM=0
while [[ $ENTRIES != $NUM ]]; do
	echo >> "$FILE_PATH"
	echo [snom$NYT_NUM] >> "$FILE_PATH"
	echo type=friend >> "$FILE_PATH"
	echo username=snom$NYT_NUM >> "$FILE_PATH"
	echo secret=1234 >> "$FILE_PATH"
	echo subscribecontext=localextensions >> "$FILE_PATH"
	echo language=dk >> "$FILE_PATH"
	echo host=dynamic >> "$FILE_PATH"
	echo dtmfmode=rfc2833 >> "$FILE_PATH"
	echo defaultip=192.168.230.$NYT_NUM >> "$FILE_PATH"
	echo mailbox=$NYT_NUM >> "$FILE_PATH"
	NUM=$((NUM+1))
done
```

Which is hopefully quite self-explanatory. The thing is, I get a *")syntax error: invalid arithmetic operator (error token is "* error when I try to run it and I'm a bit stumped. What am I doing wrong?


Visti

---

### Post by Cappy on 2007-10-27
I just changed the lines to use double and single quotes where necessary. I can't test to see if that solved the problem atm.
```
#!/bin/bash
read -p "How many entries would you like to make? : " ENTRIES

LAST_NUM=$(cat "/home/devel/Desktop/sip.conf" | tail -1)
NUMBER=${LAST_NUM#*=}
NYT_NUM=$((NUMBER+1))

NUM=0
while [[ "$ENTRIES" != "$NUM" ]]; do
	echo >> "$FILE_PATH"
	echo '[snom'"$NYT_NUM"']' >> "$FILE_PATH"
	echo 'type=friend' >> "$FILE_PATH"
	echo 'username=snom'"$NYT_NUM" >> "$FILE_PATH"
	echo 'secret=1234' >> "$FILE_PATH"
	echo 'subscribecontext=localextensions' >> "$FILE_PATH"
	echo 'language=dk' >> "$FILE_PATH"
	echo 'host=dynamic' >> "$FILE_PATH"
	echo 'dtmfmode=rfc2833' >> "$FILE_PATH"
	echo 'defaultip=192.168.230.'"$NYT_NUM" >> "$FILE_PATH"
	echo 'mailbox='"$NYT_NUM" >> "$FILE_PATH"
	NUM=$((NUM+1))
done
```

---

### Post by Ramses de Norre on 2007-10-27
Doesn't it tell you at which line the syntax error occurs? That makes it a little easier to help.

---

### Post by ghostdog74 on 2007-10-27
and then when the last octet reaches 255 , you have to think of a way to increment the last second octet, and so on

---

### Post by Visti on 2007-10-28
> **Ramses de Norre said:**
> Doesn't it tell you at which line the syntax error occurs? That makes it a little easier to help.

Actually, no.. The error occurs exactly as I typed it, which confuses the heck out of me..

Cappy > Thanks for the attempt, I'm gonna check it later today.

Ghostdog74 > Yeah, I thought about that, but I'm trying to work out the kinks one by one at the time now. I hope that's not going to be too much trouble, though.

---

### Post by ghostdog74 on 2007-10-28
this is the awk programming language
```

awk 'BEGIN{FS="="}  # FS is internal variable called Field Separator. here we defined field separator as "="
 /defaultip/{ ip=$2 } # if the line match "defaultip" then i save the second field (ie IP address into variable called ip
 /mailbox/{mbox=$2} # if the line match "mailbox" i save the second field (ie mailbox number) into variable called mbox
 /\[.*\]/{header=$0} # if the line match open and close square brackets, and anything in between, store into variable. NB: this variable is not needed, so far that i see it.
 {print} # print each line
 END{ # this END part only executes when awk processes all lines. 
  print ""
  print "[snom"mbox+1"]"
  print "type=friend"
  print "username=snom"mbox+1
  print "secret=1234"
  print "subscribecontext=localextensions"
  print "language=dk"
  print "host=dynamic"
  print "dtmfmode=rfc2833"
  n=split(ip,ipaddr,".") # split the ip address into an array called ipaddr, using delimiter as "."
  print ipaddr[1]"."ipaddr[2]"."ipaddr[3]"."mbox+1
  print "mailbox="mbox+1
 } ' "file" > tempfile
 mv tempfile file

```

for more information , call [here ]("http://www.unix.org.ua/orelly/unix/sedawk/ch07_01.htm")

---

### Post by Visti on 2007-10-29
> **ghostdog74 said:**
> ```

awk 'BEGIN{FS="="}
 /defaultip/{ ip=$2 }
 /mailbox/{mbox=$2}
 /\[.*\]/{header=$0}
 {print}
 END{
  print ""
  print "[snom"mbox+1"]"
  print "type=friend"
  print "username=snom"mbox+1
  print "secret=1234"
  print "subscribecontext=localextensions"
  print "language=dk"
  print "host=dynamic"
  print "dtmfmode=rfc2833"
  n=split(ip,ipaddr,".")
  print ipaddr[1]"."ipaddr[2]"."ipaddr[3]"."mbox+1
  print "mailbox="mbox+1
 } ' "file" > tempfile
 mv tempfile file

```

Wow, that seems a bit different - Could I please have some comments in there to help me understand what the commands actually do? It would be greatly appreciated.

Thanks a bunch for your help!

---

