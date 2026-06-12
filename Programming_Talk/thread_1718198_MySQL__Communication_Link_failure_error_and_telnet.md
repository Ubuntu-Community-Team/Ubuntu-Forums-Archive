---
title: "MySQL : Communication Link failure error and telnet localhost 3306 : Connection close"
date: 2011-03-31
forum: Programming Talk
---

### Post by yannifan on 2011-03-31
Hello

Im trying to connect MYSQL db using Java where my SQL db is on localhost. 
Im facing some issues regarding communication link failure.


Program :
> 
public testfile() throws ClassNotFoundException, SQLException{
		
		Connection connection = null;
		try{
		Class.forName("com.mysql.jdbc.Driver").newInstance(); 
		connection = DriverManager.getConnection("jdbc:mysql://localhost/rts?user=root&password=password");
		System.out.println("Connected");
		}
		catch(Exception ex)
		{
			ex.printStackTrace();
		}
		finally
		{
			if(connection != null)
				connection.close();
		}
}


Stack trace :

> 
com.mysql.jdbc.CommunicationsException: Communications link failure due to underlying exception: 

** BEGIN NESTED EXCEPTION ** 

java.net.ConnectException
MESSAGE: Connection refused

STACKTRACE:

java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:327)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:193)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:180)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
	at java.net.Socket.connect(Socket.java:546)
	at java.net.Socket.connect(Socket.java:495)
	at java.net.Socket.<init>(Socket.java:392)
	at java.net.Socket.<init>(Socket.java:235)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:256)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:271)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2771)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1555)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:222)
	at test.testfile.<init>(testfile.java:18)
	at test.mainfile.main(mainfile.java:9)


** END NESTED EXCEPTION **



Last packet sent to the server was 1 ms ago.
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2847)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1555)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:222)
	at test.testfile.<init>(testfile.java:18)
	at test.mainfile.main(mainfile.java:9)


Telnet output : 
> 
telnet localhost 3306 
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.


Package/Software Info :

Eclipse Java EE IDE for Web Developers.
Version: Helios Service Release 1.
JDK6
Connector/J version 5.0.8
Ubuntu : Ubuntu 10.04 LTS- the Lucid Lynx


I have tried few things but it doesn't work ::

1. I changed port in my.cnf but no effect, I changed to 3312
same err repeats and telnet shows as follows : 

> 
shreya@shreya-laptop:~$ telnet localhost 3306
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
shreya@shreya-laptop:~$ telnet localhost 3312
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.


nmap  output : 

> 
shreya@shreya-laptop:~$ nmap localhost -p 3306

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-31 09:45 IST
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
3306/tcp closed mysql

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
shreya@shreya-laptop:~$ nmap localhost -p 3312

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-31 09:45 IST
Interesting ports on localhost (127.0.0.1):
PORT     STATE SERVICE
3312/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds


2. I tried putting entry in hosts.allow but no effect

3. I have tried reinstalling mysql. Insertion of data through mysql prompt and c program works perfectly but not through java code.

4. I tried adding rules in ip tables still it doesnt help

5. I have tried different combinations of url string. I have also tried different versions of eclipse and Connector/J jar file(latest 5.1.15)

Please help
Thank you

---

### Post by dwhitney67 on 2011-03-31
I've attempted to duplicate the anomaly that you are witnessing, however I am unable to do so.

Prior to my experimentation, I had MySQL installed, however I did not have the MySQL-java package installed; thus I had to install it.
```

sudo apt-get install libmysql-java

```
But from there, I tested code very similar to yours; of course, my database table name is different, as is the MySQL root password.

I also examined the nmap output on my system for the 3306 port; the results were similar to yours:
```

nmap localhost -p 3306

Starting Nmap 5.00 ( http://nmap.org ) at 2011-03-31 07:21 EDT
Interesting ports on localhost.localdomain (127.0.0.1):
PORT     STATE SERVICE
3306/tcp open  mysql

```
Note the Service name, mysql, is obtained from /etc/services.  When you changed your port number to 3312, the Service name is 'unknown'.

Thus all that remains uncertain between our two systems is the version of Java being used.  I am using this version:
```

java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

```


P.S.  Try the example code at this [URL]("http://marksman.wordpress.com/2009/03/01/setting-up-mysqljdbc-driver-on-ubuntu/").  Of course, replace the username (to root) and root's password.

---

### Post by yannifan on 2011-03-31
@ above

I have used the url like in the link, doesn't help.
Use
$ telnet localhost 3306, the output you see and I have posted will be different

The same code works on my friends laptop, it is some configuration in my laptop that has been changed and I haven't reverted.

---

### Post by dwhitney67 on 2011-03-31
Check your firewall settings.

---

### Post by yannifan on 2011-04-01
this is the ouput for iptables -S 
> 
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT
-N ufw-after-forward
-N ufw-after-input
-N ufw-after-logging-forward
-N ufw-after-logging-input
-N ufw-after-logging-output
-N ufw-after-output
-N ufw-before-forward
-N ufw-before-input
-N ufw-before-logging-forward
-N ufw-before-logging-input
-N ufw-before-logging-output
-N ufw-before-output
-N ufw-logging-allow
-N ufw-logging-deny
-N ufw-not-local
-N ufw-reject-forward
-N ufw-reject-input
-N ufw-reject-output
-N ufw-skip-to-policy-forward
-N ufw-skip-to-policy-input
-N ufw-skip-to-policy-output
-N ufw-track-input
-N ufw-track-output
-N ufw-user-forward
-N ufw-user-input
-N ufw-user-limit
-N ufw-user-limit-accept
-N ufw-user-logging-forward
-N ufw-user-logging-input
-N ufw-user-logging-output
-N ufw-user-output
-A INPUT -j ufw-before-logging-input 
-A INPUT -j ufw-before-input 
-A INPUT -j ufw-after-input 
-A INPUT -j ufw-after-logging-input 
-A INPUT -j ufw-reject-input 
-A INPUT -j ufw-track-input 
-A FORWARD -j ufw-before-logging-forward 
-A FORWARD -j ufw-before-forward 
-A FORWARD -j ufw-after-forward 
-A FORWARD -j ufw-after-logging-forward 
-A FORWARD -j ufw-reject-forward 
-A OUTPUT -j ufw-before-logging-output 
-A OUTPUT -j ufw-before-output 
-A OUTPUT -j ufw-after-output 
-A OUTPUT -j ufw-after-logging-output 
-A OUTPUT -j ufw-reject-output 
-A OUTPUT -j ufw-track-output 
-A ufw-after-input -p udp -m udp --dport 137 -j ufw-skip-to-policy-input 
-A ufw-after-input -p udp -m udp --dport 138 -j ufw-skip-to-policy-input 
-A ufw-after-input -p tcp -m tcp --dport 139 -j ufw-skip-to-policy-input 
-A ufw-after-input -p tcp -m tcp --dport 445 -j ufw-skip-to-policy-input 
-A ufw-after-input -p udp -m udp --dport 67 -j ufw-skip-to-policy-input 
-A ufw-after-input -p udp -m udp --dport 68 -j ufw-skip-to-policy-input 
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input 
-A ufw-after-logging-forward -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-after-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-before-forward -j ufw-user-forward 
-A ufw-before-input -i lo -j ACCEPT 
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny 
-A ufw-before-input -m state --state INVALID -j DROP 
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT 
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT 
-A ufw-before-input -j ufw-not-local 
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT 
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT 
-A ufw-before-input -j ufw-user-input 
-A ufw-before-output -o lo -j ACCEPT 
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-output -j ufw-user-output 
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] " 
-A ufw-logging-deny -m state --state INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN 
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN 
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN 
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN 
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny 
-A ufw-not-local -j DROP 
-A ufw-skip-to-policy-forward -j DROP 
-A ufw-skip-to-policy-input -j DROP 
-A ufw-skip-to-policy-output -j ACCEPT 
-A ufw-track-output -p tcp -m state --state NEW -j ACCEPT 
-A ufw-track-output -p udp -m state --state NEW -j ACCEPT 
-A ufw-user-input -s 127.0.0.1/32 -p tcp -m tcp --dport 3306 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 3306 -j DROP 
-A ufw-user-input -p udp -m udp --dport 3306 -j DROP 
-A ufw-user-input -s 127.0.0.1/32 -p tcp -m tcp --dport 3306 -j DROP 
-A ufw-user-input -s 127.0.0.1/32 -p udp -m udp --dport 3306 -j DROP 
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] " 
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable 
-A ufw-user-limit-accept -j ACCEPT 


---

### Post by dazman19 on 2011-04-04
i stopped reading as soon as i saw this:
java.net.ConnectException: Connection refused

it probably got there. 

try
mysql -u root -prootpassword 

if you can get in then you are sweet as.
if you get a connection refused then its either a few things:

1) the port is blocked (default is 3306) but it could be running on another port
2) mysql is not running
3) unlikely to be this but java cant bind to whatever port it connects from.

Have a look at what services and what ports you are running them on
netstat -a

---

### Post by dwhitney67 on 2011-04-04
> **dazman19 said:**
> 
mysql -u root -prootpassword 

NEVER enter a password on the command line.  Just use the -p option, with no other information; then you will be prompted for the password.

Information entered on the command line is recorded in ~/.bash_history, thus enabling others to see what you have typed.

@ yannifan -

It would appear that you messed with your IP tables, and thus this is probably the reason you are having an issue with port 3306.  I do not enough about how to read the output (I'm too lazy to research it too!), but this is what 'iptable -S' produces on my system:
```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT

```

---

### Post by yannifan on 2011-04-04
@dazman

mysql -u root -p
works perfectly fine

o/p for netstat -a
shreya@shreya-laptop:~$ netstat -a | grep mysql
tcp        0      0 localhost:mysql         *:*                     LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     7877     /var/run/mysqld/mysqld.sock


is it not listening at 3306, but my.cnf file says 3306 only

---

### Post by dwhitney67 on 2011-04-04
> **yannifan said:**
> 
is it not listening at 3306, but my.cnf file says 3306 only

The netstat output is normal (ie there is nothing wrong with it).

Re-verify that mysqld does indeed have a port bound to 3306.  Use this command:
```

nmap localhost -p 3306

```
You should also be able to telnet to the port:
```

telnet localhost 3306

```


P.S.  Run nmap without the -p <port>, and all open ports on your system will be listed.

---

### Post by yannifan on 2011-04-05
o/p for nmay and telnet - I have posted this earlier

shreya@shreya-laptop:~$ nmap localhost -p 3306

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-04-05 10:02 IST
Interesting ports on localhost (127.0.0.1):
PORT     STATE SERVICE
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
shreya@shreya-laptop:~$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

---

### Post by yannifan on 2011-04-05
I have used iptables -F to flush that and tried, it still shows no changes.

---

### Post by dwhitney67 on 2011-04-05
> **yannifan said:**
> I have used iptables -F to flush that and tried, it still shows no changes.

I find it easier to use 'ufw' (Ubuntu's Firewall app).

Try this:
```

sudo ufw allow 3306

```
or alternatively just reset everything:
```

sudo ufw reset

```
These commands will affect the iptables, however they will have no affect until the tables are reloaded and the network interface is restarted.  The easiest way to do this is to reboot the system.

Anyhow, you decide what you want to do with your system.  This thread has gone full-circle simply because you have a firewall rule that is preventing access to port 3306.  Correct that problem, and then everything should be just fine.

---

### Post by yannifan on 2011-04-05
output says --
shreya@shreya-laptop:~$ sudo ufw allow 3306
[sudo] password for shreya: 
Rule updated
shreya@shreya-laptop:~$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
shreya@shreya-laptop:~$ sudo ufw reset
Resetting all rules to installed defaults. Proceed with operation (y|n)? y
Backing up 'user.rules' to '/lib/ufw/user.rules.20110405_223244'
Backing up 'after6.rules' to '/etc/ufw/after6.rules.20110405_223244'
Backing up 'user6.rules' to '/lib/ufw/user6.rules.20110405_223244'
Backing up 'before6.rules' to '/etc/ufw/before6.rules.20110405_223244'
Backing up 'after.rules' to '/etc/ufw/after.rules.20110405_223244'
Backing up 'before.rules' to '/etc/ufw/before.rules.20110405_223244'

shreya@shreya-laptop:~$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
shreya@shreya-laptop:~$

---

### Post by dwhitney67 on 2011-04-05
And now, what is your Java application reporting?

P.S.  Did you reboot your system after making changes to the iptables using 'ufw'??

---

### Post by yannifan on 2011-04-06
yup rebooted and checked. still same
and the java application gives same communication link failure

---

### Post by dwhitney67 on 2011-04-06
> **yannifan said:**
> yup rebooted and checked. still same
and the java application gives same communication link failure

Did you ever set up the MySQL root account to have access to the database?  If not, read [here]("http://www.howtogeek.com/howto/programming/mysql-give-root-user-logon-permission-from-any-host/") for the easy steps to perform.

Then try your Java app again.

---

### Post by aravindants on 2011-07-07
@yannifan
Were you able to fix the issue? If yes, please share it here.
I am facing exactly the same issue, tried all those suggested in forums, yet no luck ](*,)

-Aravind

---

