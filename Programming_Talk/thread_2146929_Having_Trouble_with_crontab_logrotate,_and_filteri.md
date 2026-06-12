---
title: "Having Trouble with crontab logrotate, and filtering the load-5 values in snmpd.conf"
date: 2013-05-20
forum: Programming Talk
---

### Post by khrz on 2013-05-20
I'm currently experiencing difficulty with assigning the crontab to do the following: -
Perl Script: -
```

#!/usr/bin/perl
use strict;
use warnings;

#Declares the Global Variables, and Creates the file as well as appending the values once every 5 minutes.
my($File_N,  $N_1, $N_2);
$File_N = "local";
open (FILE, ">>$File_N\.log") || die"\n Unable to create the file\.log";

#Local Time: -
print FILE "Local Timestamp: ";
print FILE `date "+%a %d %b %Y %R:%S %p\n"`;

$N_1   = `snmpget -c ICT338 -v2c -Ov  tcp:115.146.85.10:1161 iso.3.6.1.4.1.2021.100.4.0 | cut -b10-33`;
$N_2   = `snmpget -c ICT338 -v2c -Ov  tcp:115.146.85.10:1161 iso.3.6.1.4.1.2021.10.1.5.2 | cut -b10-33`;

print FILE"Server Name: Cloud Server\n";
print FILE"Server Time: $N_1";
print FILE"LOAD-5's Integer Value(s): $N_2\n";

#Closes the File: - 
close FILE;
exit

```

Output of the local.log file created by the script: -
```

Local Timestamp: Sun 19 May 2013 02:50:56 AM

Server Name: Cloud Server
Server Time: Sun May 19 06:05:49 2013
LOAD-5's Integer Value(s): 2

```

- Runs the Perl Script once every 5 minutes: -
```

crontab -e
*/1     *      *     *    *  cd /home/user/Desktop ; ./Test.pl

```

- Mails the file created from the local file(local.log) to the local system administrator. Creating the file (local.log) over there on a daily biases (at 8:30 AM): -
```

crontab -e
MAILTO=root@localhost
  */2     *      *     *    *   (don't know what to add in here yet)  


```
-Finally, assigning a logrotate to keep the local.log file created from the script formatted on a daily biases as well by using logrotate(I'm not sure what to do on this part yet).

Keep in mind that I'm using cron to run every 1-2 minutes for testing procedure.

Post away if you know an alternative to this situation :).

Also, Is there a way to filter the MIB Agent into viewing the Load Average details in a more of a specific manner using snmpd.conf as well?
(e.g. in snmpd.conf, you'd get to filter the user from accessing a part of the tree (which is the load average): -
snmpwalk -v2c -c ICT338 localhost iso.3.6.1.4.1.2021.10.1
```

iso.3.6.1.4.1.2021.10.1.1.1 = INTEGER: 1
iso.3.6.1.4.1.2021.10.1.1.2 = INTEGER: 2
iso.3.6.1.4.1.2021.10.1.1.3 = INTEGER: 3
iso.3.6.1.4.1.2021.10.1.2.1 = STRING: "Load-1"
iso.3.6.1.4.1.2021.10.1.2.2 = STRING: "Load-5"
iso.3.6.1.4.1.2021.10.1.2.3 = STRING: "Load-15"
iso.3.6.1.4.1.2021.10.1.3.1 = STRING: "0.33"
iso.3.6.1.4.1.2021.10.1.3.2 = STRING: "0.17"
iso.3.6.1.4.1.2021.10.1.3.3 = STRING: "0.33"
iso.3.6.1.4.1.2021.10.1.4.1 = STRING: "12.00"
iso.3.6.1.4.1.2021.10.1.4.2 = STRING: "12.00"
iso.3.6.1.4.1.2021.10.1.4.3 = STRING: "12.00"
iso.3.6.1.4.1.2021.10.1.5.1 = INTEGER: 33
iso.3.6.1.4.1.2021.10.1.5.2 = INTEGER: 17
iso.3.6.1.4.1.2021.10.1.5.3 = INTEGER: 33
iso.3.6.1.4.1.2021.10.1.6.1 = Opaque: Float: 0.330000
iso.3.6.1.4.1.2021.10.1.6.2 = Opaque: Float: 0.170000
iso.3.6.1.4.1.2021.10.1.6.3 = Opaque: Float: 0.330000
iso.3.6.1.4.1.2021.10.1.100.1 = INTEGER: 0
iso.3.6.1.4.1.2021.10.1.100.2 = INTEGER: 0
iso.3.6.1.4.1.2021.10.1.100.3 = INTEGER: 0
iso.3.6.1.4.1.2021.10.1.101.1 = ""
iso.3.6.1.4.1.2021.10.1.101.2 = ""
iso.3.6.1.4.1.2021.10.1.101.3 = ""

```

All I want is to display a tiny part of the Load 5 value: -
```

iso.3.6.1.4.1.2021.10.1.2.2 = STRING: "Load-5"
iso.3.6.1.4.1.2021.10.1.5.2 = INTEGER: 17

```

my snmpd.conf: -
```

##### SNMP Configuration Versions 1 and 2 #####
##### Community String #####
com2sec location localhost Test
## Security Name #####
group LocalHostGroup v2c location   
##### View of Tree #####
#load 12 14 14
view systemview included .1.3.6.1.4.1.2021.10.1.2.2
view systemview included .1.3.6.1.4.1.2021.10.1.5.2
view systemview included .3.6.1.4.1.2021.100.4.0
view systemview excluded .1 80
#####
#access LocalHostGroup "" any noauth exact systemview none none

```

I only need some of the load 5 values(Just the integer, and the value name would suffice for the whole snmpd.conf) to display everytime i call in the local host using: -

```

snmpwalk -v2c -c Test localhost

```

The same steps applies to the cloud server as well.

If there is a possibility of doing so, then that would be much appreciated if You or Anyone is able to share the answer with me.

---

