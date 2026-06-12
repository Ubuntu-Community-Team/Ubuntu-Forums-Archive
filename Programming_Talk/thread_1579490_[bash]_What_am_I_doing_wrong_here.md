---
title: "[bash] What am I doing wrong here?"
date: 2010-09-21
forum: Programming Talk
---

### Post by JonnyCarcinogen on 2010-09-21
This is a fairly simple script I'm using for DDNS testing purposes. The problem is I'm really more of a C guy and this has to be, for a number of silly reasons, in bash only. Well, as it happens my bash scripting sucks, and I'm kinda at wit's end here. 

The idea was to take a Dynamic DNS update script and instead have it replace the A record with a random IP address. Once it throws a random IP into an A record, we can then test/watch how quickly it propagates, what caches need to be cleared, etc. The original script works fine, assuming it has the right S-user ID and S-pass. The problem is I can't seem to make a random IP address work right and pass properly. I suspect it's mostly a syntax thing, esp. towards all the A/B/C/D variables, but I'm not really a bash guy so I think I'm missing something. Any thoughts?  

[PHP]
# This is the e-mail address that you use to login
SLUSER=[withheld]

# This is your password
SLPASS=[withheld]

#Record ID
SLID=6771353

# Obtain current ip address
#IPADDR=`ifconfig wlan0 | grep inet | awk '{print $2}' | awk -F : '{print $2}'`

# Replace with random IP
A=RANDOM%128
B=RANDOM%128
C=RANDOM%128
D=RANDOM%128
IPADDR="$A.$B.$C.$D"

if wget -q -O /proc/self/fd/1 http://www.sitelutions.com/dnsup?user=$SLUSER\&pass=$SLPASS\&id=$SLID\&ip=$IPADDR | grep success > /dev/null; then
echo IPADDR
	logger -t Sitelutions.com -s "DNS Record Updated Successfully"
else
	logger -t Sitelutions.com -s "Problem updating DNS record."
fi
[/PHP]

---

### Post by raf_kig on 2010-09-22
> **JonnyCarcinogen said:**
> 
[PHP]
# Replace with random IP
IPADDR=$(($RANDOM%256)).$(($RANDOM%256)).$(($RANDOM%256)).$(($RANDOM%255+1))
[/PHP]
There you go. 
1. RANDOM is a string, $RANDOM is a variable that gets populated with a random value.
2. $RANDOM%256 is a string that looks like that: "3423%256"
3. $(($RANDOM%256)) is an arithmetic expression that evaluates to random_number mod 256

Regards,

raf

---

### Post by JonnyCarcinogen on 2010-09-22
Thank you mon ami, I appreciate it.

---

### Post by SaintDanBert on 2010-09-22
While bash happily accepts back-quotes to enclose a string that you want to execute as a command, I prefer to use $( ... ) instead of `...`.  Notice now much
more visible one is over the other.

Cheers,
~~~ 0;-Dan

---

