---
title: "problem with mysql, java and jdbc"
date: 2005-05-11
forum: Programming Talk
---

### Post by cristianommxp on 2005-05-11
Hi, 

I installed mysql on my machine. I'm using Linux Ubuntu Warty.

MySQL works fine when I use "mysql" client to connect them.

But, when I tryed to connect with jdbc, I have a serius problem.

Please, think with me:

I wrote a simple java code:

//------------------------------------------------------------------------------------------
try {
  conn = DriverManager.getConnection("jdbc:mysql://localhost/expert", "mestre", "chavemestra");
} catch (Exception ex) {
  ex.printStackTrace();
}
//------------------------------------------------------------------------------------------

And this code generate an exception like this:


//------------------------------------------------------------------------------------------
com.mysql.jdbc.CommunicationsException: Communications link failure due to underlying exception: 

** BEGIN NESTED EXCEPTION ** 

java.net.SocketException
MESSAGE: java.net.ConnectException: Connection refused

STACKTRACE:

java.net.SocketException: java.net.ConnectException: Connection refused
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:151)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:281)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:1696)
	at com.mysql.jdbc.Connection.<init>(Connection.java:408)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:270)
	at java.sql.DriverManager.getConnection(DriverManager.java:525)
	at java.sql.DriverManager.getConnection(DriverManager.java:171)
	at XTeste.main(XTeste.java:31)


** END NESTED EXCEPTION **


	at com.mysql.jdbc.Connection.createNewIO(Connection.java:1759)
	at com.mysql.jdbc.Connection.<init>(Connection.java:408)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:270)
	at java.sql.DriverManager.getConnection(DriverManager.java:525)
	at java.sql.DriverManager.getConnection(DriverManager.java:171)
	at XTeste.main(XTeste.java:31)
//------------------------------------------------------------------------------------------


So , I don't know what are happening. "mestre" and "chavemestre" are the true user and password. This user has all privilegies. 

I'm using the most recently jdbc driver for MySQL.

Please, can someone help me?

10ks

Cristiano

p.s.: please, excuse  me about my english.

---

### Post by bihe on 2005-05-11
the problem is, that by default mysql only uses unix sockets. jdbc needs a tcp
connection. therefor you have to disable an option in the mysql config file.

~$: sudo vi /etc/mysql/my.cnf

look for the option 'skip-networking '
place a # before the option - save && restart mysql && take a look

~$: netstat -an | grep 3306
> tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN

and now mysql is ready for connections.

p.s.: never excuse for your 'english', 
i wonder how their portuguese or german is ;)

---

### Post by cristianommxp on 2005-05-11
bihe,

10ks for help me. 

but i have 2 questions about your message:

Question 1) How I reboot MySQL server on Linux? I'm trying to reboot with the command:
-------------------------------------------------------------------------------------------------------------
$ mysqladmin shutdown
$ mydsqld
-------------------------------------------------------------------------------------------------------------

The command "mysqld" works fine, but the command line don't return to shell. How to start MySQL by command line like a "process" ?

Question 2)

Now, my Java code generate the exception bellow:

-------------------------------------------------------------------------------------------------------------
java.sql.SQLException: null,  message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"
	at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1023)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:1699)
	at com.mysql.jdbc.Connection.<init>(Connection.java:408)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:270)
	at java.sql.DriverManager.getConnection(DriverManager.java:525)
	at java.sql.DriverManager.getConnection(DriverManager.java:171)
	at XTeste.main(XTeste.java:31)
-------------------------------------------------------------------------------------------------------------

So, I ask you my friend: And now, what do I have to do??

---

### Post by LordHunter317 on 2005-05-11
For the first, use: ```
sudo /etc/init.d/mysql stop
``` and ```
sudo /etc/init.d/mysql start
``` to start the server.

---

### Post by cristianommxp on 2005-05-11
10ks LordHunter, 

but the second question is still there:

Question 2) Now, my Java code generate the exception bellow:

-------------------------------------------------------------------------------------------------------------
java.sql.SQLException: null, message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"
at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:10 23)
at com.mysql.jdbc.Connection.createNewIO(Connection.j ava:1699)
at com.mysql.jdbc.Connection.<init>(Connection.java:40
at com.mysql.jdbc.NonRegisteringDriver.connect(NonReg isteringDriver.java:270)
at java.sql.DriverManager.getConnection(DriverManager .java:525)
at java.sql.DriverManager.getConnection(DriverManager .java:171)
at XTeste.main(XTeste.java:31)
-------------------------------------------------------------------------------------------------------------

So, I ask you my friend: And now, what do I have to do??

---

### Post by bihe on 2005-05-12
[QUOTE=cristianommxp]
java.sql.SQLException: null, message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"
[/QUOTE]

you have to grant permissions to the user who connects to the db.

~$: mysql -u root -p<password>
mysql> grant all privileges on expert.* to mestre identified by 'chavemestra';
mysql> grant all privileges on expert.* to mestre@localhost identified by 'chavemestra';

it's allways the same with mysql. grant permissions for the user by 
a) the username only
b) the username@locahost

now your jdbc connection should be happy

---

### Post by kukling on 2005-05-29
[QUOTE=cristianommxp]
Question 2) Now, my Java code generate the exception bellow:

-------------------------------------------------------------------------------------------------------------
java.sql.SQLException: null, message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"
[/QUOTE]

Make sure MySQL finds "localhost", and not "localhost.localdomain" for the host.
Edit /etc/hosts and change the line 
```
127.0.0.1 localhost.localdomain localhost xxx
``` 
for
```
127.0.0.1 localhost localhost.localdomain xxx
```
This could have side effects, but for me is ok.

---

### Post by LordHunter317 on 2005-05-29
[QUOTE=bihe]
mysql> grant all privileges on expert.* to mestre identified by 'chavemestra';
mysql> grant all privileges on expert.* to mestre@localhost identified by 'chavemestra';[/quote]You missed single quotes around mestre and localhost, which are important.  This is due to the mental retardation that is MySQL.

---

### Post by judabuddhist on 2005-06-18
[QUOTE=kukling]Make sure MySQL finds "localhost", and not "localhost.localdomain" for the host.
Edit /etc/hosts and change the line 
```
127.0.0.1 localhost.localdomain localhost xxx
``` 
for
```
127.0.0.1 localhost localhost.localdomain xxx
```
This could have side effects, but for me is ok.[/QUOTE]

I tried this advice and it solved the problem with mysql, but it also seems to completely break my wireless internet. I have no idea why. I get a short fatal error messate at [Configuring Network Interfaces] at startup, and then once I'm actually using the computer it will detect the network and even work for a few minutes, but ultimately simply stop working.

Are there any alternatives to this solution with the mysql, or alternatively, is there any way to fix wireless with this solution in place?

---

### Post by LordHunter317 on 2005-06-18
You shouldn't have needed to change the hosts files.
On the same token, it shouldn't have broken your networking either.

Post your hosts file.

---

### Post by judabuddhist on 2005-06-18
[QUOTE=LordHunter317]You shouldn't have needed to change the hosts files.
On the same token, it shouldn't have broken your networking either.

Post your hosts file.[/QUOTE]
```

127.0.0.1 localhost.localdomain localhost Quincunx

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Here it is. Changing the first line as recommended allows me to run java servlets, but as far as I can tell kills my wireless. Got me.

---

### Post by LordHunter317 on 2005-06-18
There must be a misconfiguration elsewhere.  Post /etc/hostname and /etc/network/interfaces.

---

### Post by judabuddhist on 2005-06-18
[QUOTE=LordHunter317]There must be a misconfiguration elsewhere.  Post /etc/hostname and /etc/network/interfaces.[/QUOTE]

/etc/hostname
```

Quincunx

```

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth1 inet dhcp
wireless-essid <Network Name>
wireless-key <Wep Key>

```

These are what they look like with the original hosts files while the internet is working. I've never manually editted them myself.

---

### Post by LordHunter317 on 2005-06-18
It's odd the wireless interface is marked at eth1.  I'm wondering if that's related to your issues.  When the box is running, run ifconfig and see what interfaces you have.  Make sure an eth1 exists.  If not, your interfaces file is setup incorrectly.

---

### Post by judabuddhist on 2005-06-19
[QUOTE=LordHunter317]It's odd the wireless interface is marked at eth1.  I'm wondering if that's related to your issues.  When the box is running, run ifconfig and see what interfaces you have.  Make sure an eth1 exists.  If not, your interfaces file is setup incorrectly.[/QUOTE]

```


eth0      Link encap:Ethernet  HWaddr 00:11:25:2F:7B:AE
          inet6 addr: fe80::211:25ff:fe2f:7bae/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000

eth1      Link encap:Ethernet  HWaddr 00:0E:35:36:8B:D0
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe36:8bd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1515936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1331172 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:1366656137 (1.2 GiB)  TX bytes:620240336 (591.5 MiB)
          Interrupt:11 Base address:0xe000 Memory:c0210000-c0210fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6317178 (6.0 MiB)  TX bytes:6317178 (6.0 MiB)

```

wireless has always been eth1 as far as I've seen

---

### Post by ghostrifle on 2005-06-21
Hey there,

I have the same problem but the above solutions didn't help me.

I can connect through sockets but not over a TCP/IP connection. Well, I commented out skip-networking and restarted mysql. I've also changed the hosts file like this:

```

127.0.0.1 localhost localhost.localdomain ferrari

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Connecting with the mysql client using the host option doesn't work also, except I specify localhost for the host option. But in this case, I think mysql uses sockets instead of a  TCP/IP connection. Pinging localhost doesn't work also....  ](*,) 

```

ghostrifle@ferrari:~/coding/procond$ mysql -u root -p -h 192.168.0.61
Enter password:
ERROR 2003: Can't connect to MySQL server on '192.168.0.61' (22)
ghostrifle@ferrari:~/coding/procond$ mysql -u root -p -h localhost
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4 to server version: 4.0.23_Debian-3ubuntu2-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> exit
Bye
ghostrifle@ferrari:~/coding/procond$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.

--- localhost ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

ghostrifle@ferrari:~/coding/procond$   

```

... well I managed to get it working by firing up "lo" with the IP 127.0.0.1
```

sudo ifconfig lo up
sudo ifconfig lo 127.0.0.1

```

But is there a way on hoary to automate this during the startup ?? 'Cause everytime I reboot the loopback device is gone.   ](*,)

---

### Post by gertmul on 2005-10-20
I fixed the same problem, the Java/MySQL: java.sql.SQLException: null, message from server: "Host 'localhost.localdomain' is not allowed to connect to this MySQL server"

by using 'localhost.localdomain' in the grant statement in mysql:

grant all privileges on test.* to 'testuser'@'localhost.localdomain' identified by 'testpass';

---

