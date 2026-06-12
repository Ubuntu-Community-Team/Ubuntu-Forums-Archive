---
title: "Reverse DNS in BASH script"
date: 2006-09-29
forum: Programming Talk
---

### Post by paul.maddox on 2006-09-29
Hi guys,

What's the best way to do a reverse dns lookup in a bash script?

I know you can use host, dig and nslookup but they all seem to return extra information and I don't really want to have to grep/gawk/sed the output to get what I need.

The best I've come up with so far is:

HOST=$(host $IP | cut -d " " -f 5);


There must be a nicer way!

---

### Post by ghostdog74 on 2006-09-29
indeed there is, Python code:
```

>>> import socket
>>> socket.gethostbyaddr('66.249.89.104')

```

---

### Post by paul.maddox on 2006-09-29
I'm a bit confused, I'm writing a bash script not a python one.

---

### Post by freebourg on 2009-07-28
If you're interested, I wrote a small python script to reverse the ip.
(Maybe it already exists, and there is of course another way to do it, but this one works)

```
#!/usr/bin/python

def ip_reversed(ip, separator='.'):
    "Transform a.b.c.d to d.c.b.a. you can even use a.b.c.d.e.f..., and change the separator (here: the dot)."

    ipListe = ip.split(separator)
    ipListeReversed = []

    n = len(ipListe)
    while n != 0:
        ipListeReversed.append(ipListe[n-1])
        n -= 1
        continue

    return separator.join(ipListeReversed)

import sys
print( ip_reversed(sys.argv[1]) )
```

I advice you to 'chmod +x blabla.py'
and then use it like this: ./blabla.py 91.189.94.12


The code could have been simplificated, but the advantage here, is that you can use things like :
a.b.c.d, a.b.c.d.e.f.g.h, or ff:gh:00, or even "reversed more not now is text this", just specify the second argument as the separator (" " in the last sentence. "." is taken by default)

---

### Post by Kbeezie on 2011-02-10
> **freebourg said:**
> If you're interested, I wrote a small python script to reverse the ip.
(Maybe it already exists, and there is of course another way to do it, but this one works)

```
#!/usr/bin/python

def ip_reversed(ip, separator='.'):
    "Transform a.b.c.d to d.c.b.a. you can even use a.b.c.d.e.f..., and change the separator (here: the dot)."

    ipListe = ip.split(separator)
    ipListeReversed = []

    n = len(ipListe)
    while n != 0:
        ipListeReversed.append(ipListe[n-1])
        n -= 1
        continue

    return separator.join(ipListeReversed)

import sys
print( ip_reversed(sys.argv[1]) )
```

I advice you to 'chmod +x blabla.py'
and then use it like this: ./blabla.py 91.189.94.12


The code could have been simplificated, but the advantage here, is that you can use things like :
a.b.c.d, a.b.c.d.e.f.g.h, or ff:gh:00, or even "reversed more not now is text this", just specify the second argument as the separator (" " in the last sentence. "." is taken by default)


.... :shock: The Fail is Strong with This One.

---

### Post by Kbeezie on 2011-02-10
Anywho since this 4+ year old thread still shows up in google over this topic. 

apt-get install dnsutils

then incorporate the dig command into a bash script, (since dig ip will have a reverse lookup in it).

---

### Post by damormino on 2011-09-26
This bash example should print all the hosts from 192.168.1.1 throught .254.  (You could edit the IP address lines to suit your network, perhaps.)

rdns.sh:
```
#!/bin/bash
for i in {1..254}
do
  myhostname=`host 192.168.1.$i`
  if [ "$?" -eq 0 ]; then
    echo -ne $i
    echo -ne "\t"
    echo -ne "IN"
    echo -ne "\t"
    echo -ne "PTR"
    echo -ne "\t"
    echo `echo $myhostname | cut -d " " -f 5`
  fi
done
```

I use this to generate rdns (reverse dns) files for my bind9 name server:
```
bash rdns.sh >> /etc/bind/db.192
```

I still need to put the correct lines in at the top of the db.192 file (from db.empty), but it accomplishes most of what I am after.

*Normally, I would not post to an older thread, but it appears many people are landing here, and still looking for an answer.*

---

### Post by karlson on 2011-09-26
> **paul.maddox said:**
> Hi guys,

What's the best way to do a reverse dns lookup in a bash script?

I know you can use host, dig and nslookup but they all seem to return extra information and I don't really want to have to grep/gawk/sed the output to get what I need.

The best I've come up with so far is:

HOST=$(host $IP | cut -d " " -f 5);


There must be a nicer way!

have you tried using:
```

$ getent hosts <host>

```

---

### Post by peripatetic on 2012-03-06
Just found this while I was searching for something else. 

How about 
```
dig x +short domain.com
```

---

### Post by Habitual on 2012-03-06
```
host domain.com
```

---

### Post by emiller12345 on 2012-03-06
Although a true bash script would probably make use of /dev/udp/www.dns-server.com/53 to communitcate, this uses netcat.
Edit:
okay, i think this script is working now.
```

#!/bin/bash
if [ $# -ne 2 ]; then
    echo "Usage $0 <ip in question> <dns server>"
fi
TEMPFILE=$(tempfile)
TRANSACTION_ID="$(printf "\\\x%02X\\\x%02X\n" $(($RANDOM%0xFF)) $(($RANDOM%0xFF)))"
FLAGS="\x01\x00"
QUESTIONS="\x00\x01"
ANWSERS_RR="\x00\x00"
AUTHORITY_RR="\x00\x00"
ADDITIONAL_RR="\x00\x00"
PTR="\x00\x0c"
IN="\x00\x01"
BYTES_A="\\x0$(($(echo $1 | awk -F. '{print $4}' | wc -c) - 1 ))"
BYTES_B="\\x0$(($(echo $1 | awk -F. '{print $3}' | wc -c) - 1 ))"
BYTES_C="\\x0$(($(echo $1 | awk -F. '{print $2}' | wc -c) - 1 ))"
BYTES_D="\\x0$(($(echo $1 | awk -F. '{print $1}' | wc -c) - 1 ))"
echo -ne "$TRANSACTION_ID""$FLAGS""$QUESTIONS""$ANWSERS_RR""$AUTHORITY_RR""$ADDITIONAL_RR"$(echo $1 | awk -F. '{print "'$BYTES_A'"$4"'$BYTES_B'"$3"'$BYTES_C'"$2"'$BYTES_D'"$1}')"\x07in-addr\x04arpa\x00""$PTR""$IN"  > $TEMPFILE
echo "TRANSACTION_ID=$TRANSACTION_ID"
cat $TEMPFILE | /bin/nc.openbsd -i 2 -u $2 53 | hexdump -C
rm $TEMPFILE

```

---

### Post by Eiji Takanaka on 2012-03-06
> #!/bin/bash if [ $# -ne 2 ]; then     echo "Usage $0 <ip in question> <dns server>" fi TEMPFILE=$(tempfile) TRANSACTION_ID="$(printf "\\\x%02X\\\x%02X\n" $(($RANDOM%0xFF)) $(($RANDOM%0xFF)))" FLAGS="\x01\x00" QUESTIONS="\x00\x01" ANWSERS_RR="\x00\x00" AUTHORITY_RR="\x00\x00" ADDITIONAL_RR="\x00\x00" PTR="\x00\x0c" IN="\x00\x01" BYTES_A="\\x0$(($(echo $1 | awk -F. '{print $4}' | wc -c) - 1 ))" BYTES_B="\\x0$(($(echo $1 | awk -F. '{print $3}' | wc -c) - 1 ))" BYTES_C="\\x0$(($(echo $1 | awk -F. '{print $2}' | wc -c) - 1 ))" BYTES_D="\\x0$(($(echo $1 | awk -F. '{print $1}' | wc -c) - 1 ))" echo -ne "$TRANSACTION_ID""$FLAGS""$QUESTIONS""$ANWSERS_RR""$AUTHORITY_RR""$ADDITIONAL_RR"$(echo $1 | awk -F. '{print "'$BYTES_A'"$4"'$BYTES_B'"$3"'$BYTES_C'"$2"'$BYTES_D'"$1}')"\x07in-addr\x04arpa\x00""$PTR""$IN"  > $TEMPFILE echo "TRANSACTION_ID=$TRANSACTION_ID" cat $TEMPFILE | /bin/nc.openbsd -i 2 -u $2 53 | hexdump -C rm $TEMPFILEHe asked for a script for reverse dns lookup dude(ette), not the schematics for creating a new sentient life-form ;)

---

### Post by Habitual on 2012-03-07
Ask the nameservers for the A Record on record...

```
host -t ns example.com | while read dom ns server; do dig +short $dom; done
```Output:
192.0.43.10
192.0.43.10

substitute example.com for your task

---

### Post by Khayyam on 2012-03-07
Habitual ...

reverse DNS is the other way round ... 

```
host xxx.xxx.xxx.xxx | awk '{print $NF}'
```

best ... khay

---

