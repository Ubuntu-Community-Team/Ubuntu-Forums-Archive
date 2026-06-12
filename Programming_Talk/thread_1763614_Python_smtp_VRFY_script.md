---
title: "Python smtp VRFY script"
date: 2011-05-20
forum: Programming Talk
---

### Post by Andrew_Balls on 2011-05-20
Hello everyone. I'm currently taking a security course, and I'm on the information gathering chapter. My current objective is to write a program that reads users from a text file and attempts to VRFY each one of them on an SMTP server. I'm very new at python, but I've managed to write something that sort of works.

```
#!/usr/bin/python

# importing the fileinput module to read the text file containing
# user names to bruteforce, and importing socket module to create
# a socket between us and the smtp server. Also importing sys
# module to read user argument.

import fileinput
import socket
import sys

# checks for three arguments. if both aren't present, it prints the
# usage and exits.

if len(sys.argv) != 3:
        print "
[*] Usage: smtp_vrfy_brute.py <wordlist> <server>"
        print "
[*] EG: smtp_vrfy_brute.py users.txt 127.0.0.1"
        sys.exit(0)

# create the socket and connect to the target SMTP server

s=socket.socket(socket.AF_INET, socket.SOCK_STREAM)
connect=s.connect((sys.argv[2],25))

# receive and print the banner
banner=s.recv(1024)
print banner

# start the VRFY loop

for user in fileinput.input(sys.argv[1]):
        s.send('VRFY ' + user + '\r\n')
        result=s.recv(1024)
        print result


# once the last line has been processed, the socket will close and
# the program exits

s.close()

```

This is the output on a vulnerable SMTP server:

```
220 redhat.acme.com ESMTP Sendmail 8.12.8/8.12.8; Fri, 20 May 2011 17:52:07 +0300

250 2.1.5 root <root@redhat.acme.com>
500 5.5.1 Command unrecognized: ""

550 5.1.1 admin... User unknown
500 5.5.1 Command unrecognized: ""

250 2.1.5 <bob@redhat.acme.com>
500 5.5.1 Command unrecognized: ""

550 5.1.1 alice... User unknown
500 5.5.1 Command unrecognized: ""

550 5.1.1 user... User unknown
500 5.5.1 Command unrecognized: ""

550 5.1.1 www... User unknown
500 5.5.1 Command unrecognized: ""

550 5.1.1 www-data... User unknown
500 5.5.1 Command unrecognized: ""

250 2.1.5 <nobody@redhat.acme.com>
500 5.5.1 Command unrecognized: ""


```

There are two problems with my code thus far that I can't figure out how to fix. One is that once the loop reaches the end of the user list, it just hangs instead of exiting, and the other problem is the empty line that it attempts to verify in between each user. 

Once I can fix these two issues I'll work on parsing through the text and only printing valid users.

Any advice would help. Thanks!

-Andrew

---

### Post by StephenF on 2011-05-20
Never used fileinput but doesn't each line come with its terminating character (or characters) as it would when iterating directly over file objects? Your code then explicitly adds more line terminating characters resulting in a line ending of \n\r\n, which seems incorrect.

---

### Post by Andrew_Balls on 2011-05-20
Ah good idea! I'm gonna modify my code and try that. I'll let you know if it works.

---

