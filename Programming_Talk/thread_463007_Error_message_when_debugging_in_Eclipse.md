---
title: "Error message when debugging in Eclipse"
date: 2007-06-03
forum: Programming Talk
---

### Post by tiroxino on 2007-06-03
Hello,
I can't debug in Eclipse. It shows "**cannot connect to VM"** 
and the console shows:

ERROR: transport error 202: connect failed: No route to host
ERROR: JDWP Transport dt_socket failed to initialize, TRANSPORT_INIT(510)
JDWP exit error AGENT_ERROR_TRANSPORT_INIT(197): No transports initialized [../../../src/share/back/debugInit.c:690]
FATAL ERROR in native method: JDWP No transports initialized, jvmtiError=AGENT_ERROR_TRANSPORT_INIT(197)


Thanks.

---

### Post by tiroxino on 2007-06-06
I found some information about the bug: [http://forum.java.sun.com/thread.jspa?threadID=618145](http://forum.java.sun.com/thread.jspa?threadID=618145)

I tried to solve the problem editing /etc/hosts. Now it shows this:
**127.0.0.1 localhost**

but that doesn't solve the problem. I still get the same error when debugging, for example in the shell:

```
$  jdb Prueba01.java 
Initializing jdb ...
> run
run Prueba01.java
VM start exception: VM initialization failed for: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java -Xdebug -Xrunjdwp:transport=dt_socket[SIZE="3"]**,address=127.0.0.1:47663**[/SIZE],suspend=y Prueba01.java

ERROR: transport error 202: connect failed: No route to host
ERROR: JDWP Transport dt_socket failed to initialize, TRANSPORT_INIT(510)
JDWP exit error AGENT_ERROR_TRANSPORT_INIT(197): No transports initialized [../../../src/share/back/debugInit.c:690]
FATAL ERROR in native method: JDWP No transports initialized, jvmtiError=AGENT_ERROR_TRANSPORT_INIT(197)

Fatal error:
Target VM failed to initialize.
```

Can anyone help me, please?

Thanks

---

### Post by eap1935 on 2009-01-27
This problem still exists in Intrepid, so here's a workaround. This also fixes problems connecting to processes using JConsole and debugging in NetBeans.

The trouble is in /etc/hosts. Ubuntu places "127.0.0.1 <hostname-you-picked-when-you-installed>" in there by default. For whatever reason, with this default setup, Ubuntu is unable to report hostname properly. If you issue ```
hostname -i
``` to get the IP address, it reports a nonsense address, not the DHCP'd address, and not even the address of the DHCP host. So the solution is to associate your actual IP address with <hostname-you-picked-when-you-installed> in /etc/hosts.

For me, I'm behind NAT, so I set up a static IP address and I replaced the default /etc/hosts line with this:

```
127.0.0.1 localhost.localdomain localhost
192.168.1.4 toodles-laptop
```

Then when I issue hostname -i the system reports 192.168.1.4 and Java is happy making JMX and debug connections. JConsole works, and I can debug in both Eclipse and NetBeans.

This will also work using DHCP (as opposed to assigning a static IP), but only till the DHCP server gives you a new IP address. Then you'll have to update /etc/hosts again, reboot and hope you get the same IP address :) If anyone knows how to do this properly with DHCP, please correct me here.

---

### Post by chinni.joy on 2009-04-23
hi eap1935,

            you are reply is worked for me. thanq.

---

### Post by dwhitney67 on 2009-04-23
> **eap1935 said:**
> This problem still exists in Intrepid, so here's a workaround. This also fixes problems connecting to processes using JConsole and debugging in NetBeans.

The trouble is in /etc/hosts. Ubuntu places "127.0.0.1 <hostname-you-picked-when-you-installed>" in there by default. For whatever reason, with this default setup, Ubuntu is unable to report hostname properly. If you issue ```
hostname -i
``` to get the IP address, it reports a nonsense address, not the DHCP'd address, and not even the address of the DHCP host. So the solution is to associate your actual IP address with <hostname-you-picked-when-you-installed> in /etc/hosts.

For me, I'm behind NAT, so I set up a static IP address and I replaced the default /etc/hosts line with this:

```
127.0.0.1 localhost.localdomain localhost
192.168.1.4 toodles-laptop
```

Then when I issue hostname -i the system reports 192.168.1.4 and Java is happy making JMX and debug connections. JConsole works, and I can debug in both Eclipse and NetBeans.

This will also work using DHCP (as opposed to assigning a static IP), but only till the DHCP server gives you a new IP address. Then you'll have to update /etc/hosts again, reboot and hope you get the same IP address :) If anyone knows how to do this properly with DHCP, please correct me here.

Typically the localhost (and localhost.localdomain) are assigned 127.0.0.1.

Intrepid (and previous Ubuntu distros I have used), assigned one's chosen hostname to 127.0.1.1.

Of course, one is free to assign a different IP than the default 127.0.1.1 (as you have done).  As for the localhost, it should always remain as 127.0.0.1.

---

### Post by elonderin on 2009-12-03
has anybody solved this problem for DHCP ? ie. that this works automatically?

my situation is such that i use ubuntu in VM at home and at work.
my vm network is "bridged"  so others can also get to the server and as a consequence it gets quite diff. IPs assigned when i'm at work and at home.

,sure i can keep updating the hosts file but that is bothersome.

thx

---

