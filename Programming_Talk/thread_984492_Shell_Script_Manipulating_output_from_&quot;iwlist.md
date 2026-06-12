---
title: "Shell Script: Manipulating output from &quot;iwlist scan&quot;"
date: 2008-11-16
forum: Programming Talk
---

### Post by OldGregory on 2008-11-16
I'm trying to learn some shell scripting. 

And specifically, I want to take the output from the command "iwlist scan" and put it into some easy to use arrays, and go from there.  The command's output looks something like this:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:F3:02:04:81
                    ESSID:"Apple Network"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0217FFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003d7dfe8049
                    Extra: Last beacon: 1840ms ago
          Cell 02 - Address: 00:1D:7E:F8:15:F8
                    ESSID:"42"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-73 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007a7d5a1b80
                    Extra: Last beacon: 1616ms ago
          Cell 03 - Address: 00:1E:E5:65:C4:89
                    ESSID:"Adkins"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=84/100  Signal level:-49 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001b2460c1608
                    Extra: Last beacon: 1672ms ago

pan0      Interface doesn't support scanning.
```

Ideally, I would like some arrays (ESSID, Address, etc.) filled with their respective values ("Apple Network" "42" "Adkins").

Can you guys help me out?

---

### Post by unutbu on 2008-11-16
Would you be interested in a solution in python?

PS. Your avatar is SO cute!
[PHP]
#!/usr/bin/env python
import subprocess
import re

proc = subprocess.Popen('iwlist scan 2>/dev/null', shell=True, stdout=subprocess.PIPE, )
stdout_str = proc.communicate()[0]
stdout_list=stdout_str.split('\n')
essid=[]
address=[]
for line in stdout_list:
    line=line.strip()
    match=re.search('ESSID:"(\S+)"',line)
    if match:
        essid.append(match.group(1))
    match=re.search('Address: (\S+)',line)
    if match:
        address.append(match.group(1))

print essid
print address

[/PHP]

---

### Post by OldGregory on 2008-11-16
> **unutbu said:**
> Would you be interested in a solution in python?

PS. Your avatar is SO cute!

Yes, I wasn't sure if a shell script was the best solution anyway.

And thanks :)

---

### Post by ghostdog74 on 2008-11-16
```

iwlist scan | awk 'BEGIN{ FS=":" }
/ESSID/{ essid[e++]=$2 }
/Address/{
 gsub(/.*Address: /,"") 
 addr[d++]=$0
}
END{
 for (a in addr){   print addr[a]  }
 for (h in essid){  print essid[h] }
}
' 

```

---

### Post by eightmillion on 2008-11-17
Here's my bash version just for fun:

```

#!/bin/bash
a=0;b=0;x=0
while read line;do
  [ "`echo $line | grep ESSID`" ] && essid[$a]=`echo "$line" | cut -d : -f 2 |  grep -o '[a-z,A-Z,0-9]*'` && ((a++))
  [ "`echo $line | grep Address`" ] && address[$b]=`echo "$line" | awk '{print $5}'` && ((b++))
done < <(iwlist scan 2>/dev/null )
while [ $x -lt ${#essid[@]} ];do
  echo ${essid[$x]} --- ${address[$x]}
  (( x++ ))
done

```

As a bonus, I got to learn about variable scopes and sub processes the hard way. [img]http://img2.mysmiley.net/imgs/smile/mad/mad0228.gif[/img]

---

### Post by ghostdog74 on 2008-11-17
that's really excessive use of unnecessary subprocesses. Too much of them makes your script "slow". 
```

#!/bin/bash

a=0
b=0
x=0
iwlist scan | while read line
do   
   case $line in
    *ESSID* ) 
        line=${line#*ESSID:}
        essid[$a]=$line
        a=$((a + 1))
        ;;
    *Address*)     
        line=${line#*Address:}
        address[$b]=$line
        b=$((b + 1))
        ;;
   esac
done 

while [ $x -lt ${#essid[@]} ];do
  echo ${essid[$x]} --- ${address[$x]}
  (( x++ ))
done

```

---

### Post by eightmillion on 2008-11-17
Thanks, that's really interesting, but it doesn't quite work.
Your first while loop is executing in a subshell so when the second while echos the variables, they're unset.

This works, but the essid is surrounded by quotes:
```

#!/bin/bash

a=0
b=0
x=0
while read line
do
   case $line in
    *ESSID* )
        line=${line#*ESSID:}
        essid[$a]=${line//\"/}
        a=$((a + 1))
        ;;
    *Address*)
        line=${line#*Address:}
        address[$b]=$line
        b=$((b + 1))
        ;;
   esac
done < <(iwlist scan 2>/dev/null) #the redirect gets rid of "lo        Interface doesn't support scanning."

while [ $x -lt ${#essid[@]} ];do
  echo ${essid[$x]} --- ${address[$x]}
  (( x++ ))
done


```

Do you know of a good way to strip the quotation marks out with using an external process?

---

### Post by ghostdog74 on 2008-11-17
to strip quotation eg
```

# a='"this got quotation"'
# echo ${a//\"/} #global replacement
this got quotation


```

see my sig (adv bash guide) for more.

---

