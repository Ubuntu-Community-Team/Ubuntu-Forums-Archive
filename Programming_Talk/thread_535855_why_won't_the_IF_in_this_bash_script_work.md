---
title: "why won't the IF in this bash script work?"
date: 2007-08-27
forum: Programming Talk
---

### Post by MustNotSleep on 2007-08-27
i'm trying to get this to work with my limited programming/bash know-how and i just can't seem to pull it off..

here's what i have so far:```
#!/bin/bash

S1='10.0.0.151'
S2='10.0.0.190'
if [ "ifconfig eth0 | grep 'inet addr' | awk -F: '{ print $2 }' | awk '{ print $1 }'" = $S1 ]
	then echo"yes"
else echo "no"
#purple-remote setstatus?status=away
fi
```what i want to do, if you can tell by the commented-out line, is check to see what my current LAN IP is, and if it matches a certain IP, set a desired state in Pidgin accordingly.. i plan to use it as a Pidgin startup script so the proper status is set if i'm at home or in the office..

but what's eluding me is that if i execute [FONT="Courier New"]ifconfig eth0 | grep 'inet addr' | awk -F: '{ print $2 }' | awk '{ print $1 }'[/FONT] from a terminal i get the IP output i want (and i checked for \n or non-print characters; grep and awk seem to take care of it), so i'm sure the output matches the string i set in the script.. so what gives? :confused:

feel free to correct any newbie mistakes i might make.. the regex' were thrown together on a trial-and-error basis, so i'm quite sure there's a more efficient way of achieving this.. i just want the output of my current LAN IP, nothing else..

any ideas? tips? suggestions?

thanks in advance!

---

### Post by cilynx on 2007-08-27
```

#!/bin/bash

S1='10.0.0.151'
if [ `ifconfig eth0 | grep 'inet addr' | awk -F: '{ print $2 }' | awk '{ print $1 }'` == $S1 ]
then echo "yes"
else echo "no"
   #purple-remote setstatus?status=away
fi

```

EDIT

and for those of us who prefer perl to awk...

```

ifconfig eth0|grep inet|perl -pe s/^.*:\(.*\)\ .*$/\$1/

```

The two errors from above:

== is a comparitor.  You are checking for equality.
= is an operator.  You are assigning a value.

"" go around a pretty string
'' go around an ugly string
`` go around a command where what you care about is the command

---

### Post by MustNotSleep on 2007-08-27
YES!

what was the culprit? the " instead of `? or the comparison character ==, though i *did* try it before and it didn't work..

thanks for your help!

---

### Post by cwaldbieser on 2007-08-27
> **MustNotSleep said:**
> i'm trying to get this to work with my limited programming/bash know-how and i just can't seem to pull it off..

here's what i have so far:```
#!/bin/bash

S1='10.0.0.151'
S2='10.0.0.190'
if [ "ifconfig eth0 | grep 'inet addr' | awk -F: '{ print $2 }' | awk '{ print $1 }'" = $S1 ]
	then echo"yes"
else echo "no"
#purple-remote setstatus?status=away
fi
```what i want to do, if you can tell by the commented-out line, is check to see what my current LAN IP is, and if it matches a certain IP, set a desired state in Pidgin accordingly.. i plan to use it as a Pidgin startup script so the proper status is set if i'm at home or in the office..

but what's eluding me is that if i execute [FONT="Courier New"]ifconfig eth0 | grep 'inet addr' | awk -F: '{ print $2 }' | awk '{ print $1 }'[/FONT] from a terminal i get the IP output i want (and i checked for \n or non-print characters; grep and awk seem to take care of it), so i'm sure the output matches the string i set in the script.. so what gives? :confused:

feel free to correct any newbie mistakes i might make.. the regex' were thrown together on a trial-and-error basis, so i'm quite sure there's a more efficient way of achieving this.. i just want the output of my current LAN IP, nothing else..

any ideas? tips? suggestions?

thanks in advance!

It looks like your pipeline in the test brackets is quoted with double quotes rather that backticks or $() syntax.  Could that be the problem?

---

### Post by eentonig on 2007-08-27
there's still a newline in the output from the ifconfig... line.

---

### Post by MustNotSleep on 2007-08-27
> **eentonig said:**
> there's still a newline in the output from the ifconfig... line.
i solved the problem and the script is working as i wanted it to (thanks to the helpful bunch in this thread!), but i'm just curious: how can you tell there's still a newline char outputted by ifconfig? i saved the output to a file and there's just a single line without spaces.. i'm interested to know if there's an easier way to track '\n'..

thanks for the explanation cilynx and the cool perl script, i reallly should've known the comparator stuff from my short experience with C.. but who thought enclosing a line with backticks would be a smart thing to do? might as well make it a ° or a &#729;...

---

### Post by MustNotSleep on 2007-08-27
> **cilynx said:**
> ```

#!/bin/bash

S1='10.0.0.151'
if [ `ifconfig eth0 | grep 'inet addr' | awk -F: '{ print $2 }' | awk '{ print $1 }'` == $S1 ]
then echo "yes"
else echo "no"
   #purple-remote setstatus?status=away
fi

```

EDIT

and for those of us who prefer perl to awk...

```

ifconfig eth0|grep inet|perl -pe s/^.*:\(.*\)\ .*$/\$1/

```

The two errors from above:

== is a comparitor.  You are checking for equality.
= is an operator.  You are assigning a value.

"" go around a pretty string
'' go around an ugly string
`` go around a command where what you care about is the command
here's what i get with your perl script.. it's picking up the broadcast address and some gibberish.. :-S

---

### Post by cilynx on 2007-08-27
Oops, Screwed up my greedyness qualifiers:

```

rcw@tranq:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:07:E9:5D:FE:E1
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xac00 Memory:fc9e0000-fca00000

rcw@tranq:~$ ifconfig eth0|grep inet|perl -pe s/^.*?:\(.*?\)\ .*$/\$1/
10.0.0.1
rcw@tranq:~$

```

---

