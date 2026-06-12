---
title: "How To: Install a Port Knocker - FWKNOP"
date: 2008-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by kevdog on 2008-05-30
[COLOR="Red"]**[SIZE="5"]Announcements[/SIZE]**[/COLOR]

- FWKNOP version 1.9.7 released 8-25-2008.  Changes here as follows: [http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.7/ChangeLog](http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.7/ChangeLog)

- FWKNOP version 1.9.6 released 7-19-2008.  Changes/New Features will be updated once Change List is available. [http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.6/ChangeLog](http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.6/ChangeLog)

- FWKNOP version 1.9.5 (server and client versions) released 6-8-2008.  Minimal increased functionality with this release.  Updates various perl libraries.  Changes documented here: [http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.5/ChangeLog](http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.5/ChangeLog) 
Source code: [http://www.cipherdyne.org/fwknop/download/fwknop-1.9.5.tar.gz](http://www.cipherdyne.org/fwknop/download/fwknop-1.9.5.tar.gz)

- FWKNOP version 1.9.4 (server and client versions) released 6-1-2008.  Two randomization port techniques were added for the outgoing client SPA request to allow for use of a random UPD port.  Additional details on use of these advanced techniques found: [http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.4/ChangeLog](http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.4/ChangeLog)

_**[SIZE="4"]Tested Platforms[/SIZE]**_
[SIZE="2"]**Server Installations**[/SIZE]
Ubuntu, Arch
[SIZE="2"]**Client Installations**[/SIZE]
Ubuntu, Arch, Cygwin (Windows)


**[SIZE="5"]I. Overview of Port Knocking[/SIZE]**

**Port knocking** is a means of host-host communication which information flows through closed ports.  Notice this remarkably differs from most other form of communications in which a listening daemon is connected to an open port, which is accessible to the outside world.  With a **Port Knocker** daemon, since communication takes places through closed ports, the listening Port Knocker daemon is undetectable to exploitative port scanner utilities.

Although the exact implementation of each port knocking process differs between programs, the port knocking process may be thought of in general terms as:

1. A client sends a **Port Knocking** packet or "combination code -- such as a combination code used to unlock a padlock" to the listening daemon.  In many cases this "combination code" can be encrypted using a symmetric cipher, or can be encrypted utilizing asymmetric techniques such as those employed in GnuPG with the use of symmetric ciphers and hashes.

2. A monitoring daemon on the server detects the **Port Knocking** packet or "combination code".

3. Based on the **Port Knocking** implementation the **Port Knocking** "combination code" unlocks a process on the server.  In many cases the "combination code" acts to directly modify the servers firewall to open up a listening port on the server -- such as enabling port 22 providing for further communication through the OpenSSH protocol.  In other cases an executable program is directly run on the monitoring server.

4. In all cases, there is no delivery confirmation of the received packet from the monitoring daemon back to the client.  Communication is performed stealthly.  

The complexity of the **Port Knocking** sequence or "lock combination" can vary widely.  It could be as simple as a three-number unencrypted combination such as TCP port 1000, TCP port 2000, UPD port 3000.  In other applications, the combination could be encrypted and contain confirmation hashes, time-based limits to when the knock sequence expires, specific IP address limitations, or specific executable commands or code that would be run on the server upon delivery of the packet.  Also how the listening daemon actually detects the "knock sequence" -- whether through monitoring of the firewall logs, or through use of a packet capture utility such as PCAP ([http://en.wikipedia.org/wiki/Pcap](http://en.wikipedia.org/wiki/Pcap)), varies among the actual **Port Knocking** implementation.

Historically **Port Knocking** processes have been maliciously implemented in rootkits and trojans horses, and have been involved in mass-scale DNS attacks.  Based on the history of port-knocking, the wide use of **Port Knocker** utilities is a matter of controversy among security experts.

There are two however well known publicized benefits of **Port Knocking** utilities when utilized in combination of firewall IP table modification.  They ideally would protect provide and additional layer of security for other listening processes (such as the OpenSSH server) from zero-day and unpatched code vulnerabilities.  This is particularly applicable given the recent discovery ( 5-13-2008 ) of the OpenSSH exploit contained in Debian/Ubuntu distributions.  Although this exploit has now been corrected, as a result of incorrect modification of the OpenSSH psuedo-random number generator algorithm, Debian/Ubuntu systems were vulnerable for well over 1 year.  If a port knocker utility would have been in place protecting the OpenSSH server process, it is likely that exploitation of this vulnerability would have been minimized. 

[SIZE="3"]**References:**[/SIZE]

_**Port Knocking Background**_
[http://www.portknocking.org/](http://www.portknocking.org/)
[http://en.wikipedia.org/wiki/Port_knocking](http://en.wikipedia.org/wiki/Port_knocking)

**_Debian/Ubuntu OpenSSH vulnerabilty:_**
Please note all default Ubuntu Feisty,Gutsy,Hardy and Intrepid installations are considered to be at risk
[http://lists.debian.org/debian-security-announce/2008/msg00152.html](http://lists.debian.org/debian-security-announce/2008/msg00152.html)
[http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1)
[http://ubuntuforums.org/showthread.php?t=793517](http://ubuntuforums.org/showthread.php?t=793517)

**_Other References:_**
Pcap - [http://en.wikipedia.org/wiki/Pcap](http://en.wikipedia.org/wiki/Pcap)
Controversy with Use of Port Knockers as Discussed on Ubuntu Forums: [http://ph.ubuntuforums.com/showthread.php?t=758666](http://ph.ubuntuforums.com/showthread.php?t=758666)

**[SIZE="5"]II. Installation of the FWKNOP Port Knocking Application[/SIZE]**

**[SIZE="3"]FWKNOP Port Knocking Implementation[/SIZE]**

FWKNOP (FireWall KNock OPerator) - a specific port knocking application that implements Single Packet Authorization and allows for encrypted packet communication.  ([http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)).  There are other **Port Knocking** implementations ([http://www.portknocking.org/view/implementations](http://www.portknocking.org/view/implementations)), however many are proof-of-concept designs, or are not being actively maintained.  FWKNOP is under current active development. Michael Rash -- the author of the implementation -- has published several papers and books on the subject of Port Knocking and use of Linux Firewalls.  In addition he is very responsive to user questions and concerns in regards to the FWKNOP implementation. In addition the FWKNOP daemon can be installed on Linux/BSD (Mac OS X) platforms, and clients are available for Linux, BSD (Mac), and Windows(through cygwin or utilizing a native GUI client).  
  
[SIZE="3"]**Installation of FWKNOP Daemon (Server) on Ubuntu**[/SIZE]

**Install Dependencies**
```
sudo aptitude install build-essential linux-headers-$(uname -r) libpcap-dev nmap
```

**Install Additional Perl Dependencies for FWKNOP** ***Note: cpan method fails for Net::PCAP installation

```

cd ~
mkdir Source
cd Source
mkdir fwknop
cd fwknop
wget http://search.cpan.org/CPAN/authors/id/S/SA/SAPER/Net-Pcap-0.16.tar.gz
tar zxvf Net-Pcap-0.16.tar.gz
cd Net-Pcap-0.16.tar.gz
perl ./Makefile.PL
make
sudo make install

```

**Download and install FWKNOP**
```

cd ~
cd Source/fwknop
wget http://www.cipherdyne.org/fwknop/download/fwknop-1.9.3.tar.bz2
tar -jxvf fwknop-1.9.3.tar.bz2
cd fwknop-1.9.3
sudo ./install.pl  (Please answer questions with install script using pcap library)

**For users using versions <= 1.9.3 (Fixes run-level bug at startup)**
sudo update-rc.d -f fwknop remove
sudo update-rc.d fwknop defaults 99 

```

**Verifying the Installation Process**
(This is where it gets down and dirty!!)

Included in the FWKNOP sources is a test installation script to verify the FWKNOP installation and server capabilities.

By default, this process assumes there is a mail server executable located at /bin/mail.  By default the fwknop server is designed to mail the server administrator notification everytime the fwknop process executes.

The test installation script produces many errors if an executable mail transfer agent (MTA) does not exist at /bin/mail.  
--If you have a MTA (mail transfer agent) and would like to utilize this notification feature, I would recommend creating a symbolic link from /bin/mail to your preferred mailing program.  This would be performed with the following code:
```
sudo ln -s <actual MTA/executable> /bin/mail
``` 

--If you do not have a MTA (mail transfer agent) and/or do not want to implement this notification feature, create a temporary link (this will be removed later) to allow the test program to complete
```
sudo ln -s /bin/echo /bin/mail
```

Now attempt to run the FWKNOP installation test to verify server integrity:
```

cd ~/Source/fwknop/fwknop-1.9.3/test
sudo perl fwknop_test.pl

``` 

Result of my test script appeared as the following:
```

$ sudo ~/Source/fwknop/fwknop-1.9.3/test/fwknop_test.pl

[+] ==> Running fwknop test suite; firewall: iptables <==

(Setup) perl program compilation....................................pass (0)
(Setup) C program compilation.......................................pass (1)
(Setup) Command line argument processing............................pass (2)
(Setup) List iptables rules.........................................pass (3)
(Setup) System information and fwknop installation specifics........pass (4)
(Setup) Stopping any running fwknopd processes......................pass (5)
(Setup) Flushing all fwknopd iptables rules.........................pass (6)
(Setup) Deleting all fwknopd iptables chains........................pass (7)
(Basic communications) Generating SPA access packet.................pass (8)
(Basic communications) Sniffing SPA access packet...................pass (9)
(Basic communications) Verifying SPA access packet format...........pass (10)
(Basic communications) Firewall access rules exist..................pass (11)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(Basic communications) Firewall access rules removed................pass (12)
(Basic communications) Stopping all running fwknopd processes.......pass (13)
(Replay attacks, broken data) Rijndael key validity.................pass (14)
(Replay attacks, broken data) Replay detection - all digests........pass (15)
(Replay attacks, broken data) Replay detection - SHA256.............pass (16)
(Replay attacks, broken data) Replay detection - SHA1...............pass (17)
(Replay attacks, broken data) Replay detection - MD5................pass (18)
(Replay attacks, broken data) 100 random packets....................pass (19)
(Replay attacks, broken data) Truncated SPA packet..................pass (20)
(Replay attacks, broken data) Sniffing truncated SPA packet.........pass (21)
(Replay attacks, broken data) Firewall rules do not exist...........pass (22)
(Replay attacks, broken data) SPA packet with bogus key.............pass (23)
(Replay attacks, broken data) Sniffing broken SPA packet............pass (24)
(Replay attacks, broken data) Firewall rules do not exist...........pass (25)
(Internal digest alg mis-match) Generating SPA packet...............pass (26)
(Internal digest alg mis-match) Sniffing SPA packet.................pass (27)
(Internal digest alg mis-match) Verifying SPA packet format.........pass (28)
(Internal digest alg mis-match) Firewall access rules exist.........pass (29)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(Internal digest alg mis-match) Firewall access rules removed.......pass (30)
(Internal digest alg mis-match) Stopping all fwknopd processes......pass (31)
(Client timeout) Generating SPA access packet.......................pass (32)
(Client timeout) Sniffing SPA access packet.........................pass (33)
(Client timeout) Verifying SPA access packet format.................pass (34)
(Client timeout) Firewall access rules exist........................pass (35)
    (Sleeping for 10 seconds for firewall rule timeout)
    10 9 8 7 6 5 4 3 2 1 0
(Client timeout) Firewall access rules removed......................pass (36)
(Client timeout) Stopping all running fwknopd processes.............pass (37)
(Append data) Data appended to SPA packet...........................pass (38)
(Append data) Sniffing appended SPA packet..........................pass (39)
(Append data) Firewall rules exist..................................pass (40)
(Rijndael Salted__ compatibility) Generating SPA packet.............pass (41)
(Rijndael Salted__ compatibility) Sniffing SPA packet...............pass (42)
(Rijndael Salted__ compatibility) Verifying SPA format..............pass (43)
(Rijndael Salted__ compatibility) Rules exist.......................pass (44)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(Rijndael Salted__ compatibility) Rules removed.....................pass (45)
(Rijndael Salted__ compatibility) Stopping fwknopd..................pass (46)
(Non-promisc capture) Generating SPA access packet..................pass (47)
(Non-promisc capture) Sniffing SPA access packet....................pass (48)
(Non-promisc capture) Verifying sniffed SPA access packet...........pass (49)
(Non-promisc capture) Firewall access rules exist...................pass (50)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(Non-promisc capture) Firewall access rules removed.................pass (51)
(Non-promisc capture) Stopping all fwknopd processes................pass (52)
(SPA aging) Generating SPA access packet............................pass (53)
(SPA aging) Expired SPA packet detection............................pass (54)
(SPA aging) Making sure firewall rules do not exist.................pass (55)
(Require SRC) Generating SPA packet with 0.0.0.0 src addr...........pass (56)
(Require SRC) Sniffing packet with 0.0.0.0 src addr.................pass (57)
(Require SRC) Making sure firewall rules do not exist...............pass (58)
(Require user) Generating SPA packet with unauthorized user.........pass (59)
(Require user) Unauthorized user detection..........................pass (60)
(Require user) Making sure firewall rules do not exist..............pass (61)
(Permit ports) Generating unauthorized port access request..........pass (62)
(Permit ports) Unauthorized port access detection...................pass (63)
(Permit ports) Making sure firewall rules do not exist..............pass (64)
(Bogus src) Generating SPA packet from non-matching src.............pass (65)
(Bogus src) Verifying SPA access packet format......................pass (66)
(Bogus src) Non-matching SOURCE block...............................pass (67)
(Bogus src) Making sure firewall rules do not exist.................pass (68)
(Excluded src) Generating SPA packet from non-matching src..........pass (69)
(Excluded src) Verifying SPA access packet format...................pass (70)
(Excluded src) Non-matching SOURCE block............................pass (71)
(Excluded src) Making sure firewall rules do not exist..............pass (72)
(Blacklist src) Generating blacklisted SPA packet...................pass (73)
(Blacklist src) Verifying SPA access packet format..................pass (74)
(Blacklist src) Sniffing SPA packet.................................pass (75)
(Blacklist src) Making sure firewall rules do not exist.............pass (76)
(Multi-SOURCE) Generating SPA access packet.........................pass (77)
(Multi-SOURCE) Sniffing SPA access packet...........................pass (78)
(Multi-SOURCE) Verifying SPA access packet format...................pass (79)
(Multi-SOURCE) Firewall access rules exist..........................pass (80)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(Multi-SOURCE) Firewall access rules removed........................pass (81)
(Multi-SOURCE) Stopping running fwknopd processes...................pass (82)
(GnuPG) Generating SPA access packet................................pass (83)
(GnuPG) Sniffing SPA access packet to acquire access................pass (84)
(GnuPG) Verifying sniffed SPA access packet format..................pass (85)
(GnuPG) Firewall access rules exist.................................pass (86)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(GnuPG) Firewall access rules removed...............................pass (87)
(GnuPG) Stopping all running fwknopd processes......................pass (88)
(Command execution) Generating SPA command packet...................pass (89)
(Command execution) Sniffing SPA command packet and executing.......pass (90)
(Command execution) Verifying SPA command packet format.............pass (91)
(Command execution) Making sure firewall rules do not exist.........pass (92)
(Command execution) Non-matching regex command packet...............pass (93)
(Command execution) SPA command packet filtered.....................pass (94)
(Command execution) Making sure firewall rules do not exist.........pass (95)
(FORWARD chain) Stopping all running fwknopd processes..............pass (96)
(FORWARD chain) Generating FORWARD chain access packet..............pass (97)
(FORWARD chain) FORWARD request detection...........................pass (98)
(FORWARD chain) FORWARD and DNAT access rules.......................pass (99)
(FORWARD chain) Verifying SPA FORWARD access packet format..........pass (100)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(FORWARD chain) Making sure firewall rules are removed..............pass (101)
(FORWARD chain) Generating FORWARD access SPA packet................pass (102)
(FORWARD chain) Verifying SPA FORWARD access packet format..........pass (103)
(FORWARD chain) FORWARD access to restricted IP.....................pass (104)
(FORWARD chain) Firewall rules do not exist.........................pass (105)
(OUTPUT chain) Stopping all running fwknopd processes...............pass (106)
(OUTPUT chain) Generating OUTPUT chain access packet................pass (107)
(OUTPUT chain) OUTPUT access rules..................................pass (108)
(OUTPUT chain) Verifying OUTPUT access packet format................pass (109)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(OUTPUT chain) Making sure firewall rules are removed...............pass (110)
(Filesystem tcpdump capture) Sniffing over lo.......................pass (111)
(Filesystem tcpdump capture) Stopping fwknopd processes.............pass (112)
(Filesystem tcpdump capture) Generating SPA packet..................pass (113)
(Filesystem tcpdump capture) SPA communications via file............pass (114)
(Filesystem tcpdump capture) Firewall access rules exist............pass (115)
    (Sleeping for 5 (+3) seconds for firewall rule timeout)
    8 7 6 5 4 3 2 1 0
(Filesystem tcpdump capture) Rules removed..........................pass (116)
Stopping all running fwknopd processes..............................pass (117)
Deleting all fwknopd iptables chains................................pass (118)
Verifying SPA digest file format....................................pass (119)
Collecting fwknop syslog messages...................................pass (120)

[+] ==> Passed 121/121 tests against fwknop. <==
[+] This console output has been stored in: test.log


```

Please note that it is not necessary to pass all steps.  I still had one error at the conclusion of the test process (but still have a functioning server). If you receive any fails to the process above, further information regarding each particular step can be found in:
~/Source/fwknop/fwknop-1.9.3/test/output/std.stdout.<test_number>
cd ~/Source/fwknop/fwknop-1.9.3/test/output/std.stderr.<test_number>

These files are simple text files. I would recommend reading each file and post the particular debugging message in this forum if you are unable to troubleshoot the source of the error yourself.

**[SIZE="5"]III. Configuration of the FWKNOP Port Knocking Daemon[/SIZE]**

There are only two actual configuration files (fwknop.conf, access.conf) for the FWKNOP daemon process.  These files are located in /etc/fwknop.  Access to this directory can only be done as root.  To access these files do the following:

```

sudo su
cd /etc/fwknop
gksu gedit <filename>  (examples: gsku gedit fwknop.conf, gksu gedit access.conf)
exit

```

*Modification of the /etc/fwknop/fwknop.conf file* (Optional):
1. Changed ALERTING_METHODS from ALL -> noemail
---Rationale for doing this: I do not have a MTA (mail transfer agent) installed on my machine and would not like to receive email alerts everytime port knocker utility is accessed
2. Changed shCmd from /bin/sh -> /bin/bash

*Modification of the /etc/fwknop/access.conf file* **(Mandatory)**
The access.conf file is the heart of the Port Knocking Daemon.  Options in this file control who can send packets, what incoming ports to open in the firewall after verification of the port knock, the duration of time to keep the port open for incoming connections, the type of encryption method expected for the port knock (symmetric vs asymmetric), and commands are to be execute on the fwknop daemon server.  Example configurations are given in the file.  


**[SIZE="5"]IV. Putting it All Together -- An Illustrative Example[/SIZE]**
  
The following example will demonstrate setup of a FWKNOP daemon server that allows a port knocking sequence to temporarily open the ssh incoming port (port 22) for 30 seconds, to allow an incoming ssh connection.  For this first example I will assume the Single Packet Authentication (SPA) Port Knocking Sequence will be encoded using Rijndael encryption.

Requirements for Setup
1. Two separate computers - one acting as the fwknop/ssh client, and the other acting as the fwnkop/ssh daemon server.  The client must have a valid ssh account on the server.
2. A running OpenSSH daemon on the server
3. An active Iptables Firewall on the server(which is turned off by default).
4. A port scanner on the client machine to verify opening an closure of the incoming port on the server (Port 22).  Nmap will be our chosen port scanner.
5. Verification Steps to Ensure Everything is Working as Expected (Mostly applicable to server).


**[SIZE="3"]Client and Server Setup[/SIZE]**
(A Full explanation for the OpenSSH server setup may be found here: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH))

**Client Machine** 

*OpenSSH*
Client Operating System Platform:
[INDENT]Ubuntu (Linux Machine) or Mac OS X - OpenSSH client installed by default at time of installation. [/INDENT]
[INDENT]Windows - OpenSSH client provided by installation of either cygwin ([http://www.cygwin.com/](http://www.cygwin.com/)) or putty([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)).[/INDENT]
[I]
FWKNOP[/I]
Client Operating System Platform:
[INDENT]Ubuntu (Linux) / MAC OSX - Follow instructions to install server as above.  Server installation will automatically install a command line client program.[/INDENT]
[INDENT]Windows - GUI client found here: [http://www.cipherdyne.org/fwknop/download/](http://www.cipherdyne.org/fwknop/download/).  Additionally a command line cygwin client is also available by contacting the FWKNOP author.[/INDENT]


**Server Machine: Platform Ubuntu Linux**
[I]
OpenSSH Server Installation[/I]
```
sudo aptitude install openssh-server
```

The server can be further enhanced to allow key-based authentication and disallow password based authentication.  This would allow for the most secure authentication mechanism.  If using key based authentication, I would recommend at least 2048 or 4096 byte rsa keys (1024 byte keys are the default).
  
*FWKNOP Server Installation*
Please see steps mentioned previously in this guide.

**[SIZE="3"]A Listening OpenSSH Server[/SIZE]** 

By default the OpenSSH server listens on port 22.  It is recommended this default port number be changed for security reasons via alteration of the /etc/ssh/sshd_config, however this example will assume port 22.  

The OpenSSH server can be stopped and started via the following commands:
```
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start
```

Confirmation that the ssh daemon is listening is provided by netstat command providing output similar to:
```

$ sudo netstat -anlp | grep sshd
tcp6   0    0 :::22      :::*      LISTEN    4396/sshd

```
The above shows a sshd listening process on port 22.

**Please confirm that an ssh connection from client to server can be completed at this stage:**
```

Client Machine:
ssh <user>@<IP_address_server>

Example
$ ssh sue@192.168.1.102
Ubuntu 8.04
Linux sudarshan 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu May 29 22:24:58 2008 from 192.168.1.101
Linux sudarshan 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
sue@sudarshan:~$

```

**[SIZE="3"]IPTables Firewall Setup on Server Machine[/SIZE]**

***If you already have an existing Iptables firewall established, please save the old configuration via:
```
sudo iptables-save -c > /etc/iptables-save 
```

Later the iptables can be restored if needed:
```
cat /etc/iptables-save | sudo iptables-restore -c
```
****

Flush/Reset the iptables rule set to allow all ports:
```

sudo /sbin/iptables -F
sudo /sbin/iptables -F -t nat
sudo /sbin/iptables -X

```

From the client machine verify the ssh port on the server is open and visible to the outside world (Example assuming 192.168.1.102 is the IP address of the server - change depending on your configuration):

```

$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE SERVICE
**22/tcp open  ssh**
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.453 seconds

```

Note the result above demonstrates that port 22 is open on the server and the ssh service is listening.

Next establish some basic firewall rules (Note that this will close all incoming connections -- please be aware of this -- modify to your specific situation -- Please note that this is an extremely basic firewall blocking all incoming connections other than those already established.  In a production environment you would want to actually want a more fully featured firewall ruleset, but would want the default ruleset for port 22 (or ssh port) to be set to DROP ):

```

sudo /sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo /sbin/iptables -A INPUT -i ! lo -j DROP

```

Manually verify from the client that the server ssh port 22 is closed:
```

$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE    SERVICE
**22/tcp filtered ssh**
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.660 seconds

```

Notice the difference in the results of the two nmap port scans:
Open Port 22: **22/tcp open  ssh**
Closed Port 22: **22/tcp filtered ssh**

Verification could also be completed attempting to make a successful ssh connection from client to server.  With port 22 open, a connection should be established.  With port 22 closed, an attempted connection should time out:
```

$ ssh sue@192.168.1.102
ssh: connect to host 192.168.1.102 port 22: Connection timed out

```


**[SIZE="3"]Port Scanner Setup on Client Machine[/SIZE]**
If following the instructions, the nmap port scanner utility should already be installed.  If you have not installed nmap:
```
sudo aptitude install nmap
```
Using nmap please verify that port 22 on the server is currently closed (or filtered), since the fwknop daemon will later act to dynamically open the port:
```
$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE    SERVICE
22/tcp filtered ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.675 seconds
```

Please also verify that the OpenSSH server is listening on port 22 on the server behind the firewall:

On server machine:
```

$ sudo netstat -anlp | grep sshd
tcp6   0    0 :::22      :::*      LISTEN    4396/sshd

```

**[SIZE="3"]FWKNOP Daemon Setup on Server[/SIZE]**

**Configuration of the server's FWKNOP access.conf file**
For this example's purpose, we are going to consider the fwknop password = Ubuntu2008.  This password will act as the shared secret key for the Rijndael symmetric cipher.  When authenticating the password, the server will open port 22 for incoming connections for a maximum of 30 seconds to allow for an establishment of a ssh connection.

```

gksu gedit /etc/fwknop/access.conf &

At the conclusion of the examples and comments:
SOURCE: ANY;
OPEN_PORTS: tcp/22;
DATA_COLLECT_MODE: PCAP;
KEY: Ubuntu2008;
FW_ACCESS_TIMEOUT: 30;

```

**Additionally when **using the Windows Client GUI** I had to make the following modification to the server's /etc/fwknop/fwknop.conf.  This may not be applicable to your situation.
```
ENABLE_SPA_PACKET_AGING N;
```

The fwknop daemon is usually stopped/stared using the following syntax:
```

sudo /etc/init.d/fwknop stop
sudo /etc/init.d/fwknop start

```

For this tutorial, the fwknop daemon will be run in debug mode to see the process occuring on the server.  The server will be started in debug mode in the terminal and the output sent to the terminal:
```

cd ~/Source/fwknop/fwknop-1.9.3
sudo perl ./fwknopd --debug

```

To kill the server later, hit Cntl-C while in the command window.

**[SIZE="3"]Putting It All Together and Unlocking the Port[/SIZE]**

With the fwknop daemon running on the server, use the fwknop client to issue the port knock.  For command line clients (Change IP address given your particular setup -- My setup 192.168.1.101=LAN IP address of client, 192.168.1.102=LAN IP address of Server), the fwknop command has the following syntax:

fwknop -A <protocol/port> -a <client IP address> -D <server IP address>

This is one example of how to use the client.  Additional options, switches can be found here: [http://www.cipherdyne.org/fwknop/docs/manpages/fwknop.html](http://www.cipherdyne.org/fwknop/docs/manpages/fwknop.html)

```

$ fwknop -A tcp/22 -a 192.168.1.101 -D 192.168.1.102
[+] Starting fwknop client (SPA mode)...
[+] Enter an encryption key. This key must match a key in the file
    /etc/fwknop/access.conf on the remote system.

Encryption Key:

[+] Building encrypted Single Packet Authorization (SPA) message...
[+] Packet fields:

        Random data:    5817642240590499
        Username:       <username>
        Timestamp:      1212123357
        Version:        1.9.4-pre3
        Type:           1 (access mode)
        Access:         192.168.1.101,tcp/22
        SHA256 digest:  NvUBz8l+T76KPqOSwvLMJO1n6sNjTLjuScSz6IIp5m8

[+] Sending 182 byte message to 192.168.1.102 over udp/62201...


```

After performing this knocking sequence, a nmap port scan of the server should show the following (My setup 192.168.1.102=Server LAN IP address)

```

$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.407 seconds

```

However 30 seconds later the port scan shows the following:
```

$ nmap -p 22 192.168.1.102

Starting Nmap 4.62 ( http://nmap.org )

Interesting ports on 192.168.1.102:
PORT   STATE    SERVICE
22/tcp filtered ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.678 seconds

```

Again if the port knock is re-issued, an attempted ssh connection should be successful.

For debugging purposes, the contents received by the server can be visualized in the command prompt debug window.  Once the server is up and thoroughly tested, the /etc/init.d/fwkop file should be modified and the -debug parameter removed (similar to process shown above).

**[SIZE="5"]V. Summary[/SIZE]**

Again our example demonstrated use of a Rijndael Single-Packet-Authentication Encrypted Packet that altered the hosts Iptable firewall and allowed temporary access to the underlying SSH port. The nmap port scanner utility verified that the server port was closed under normal operation, however was visible after the port knock was authenticated for a 30 second interval. 

If interested I can provide additional details how-to encrypt the packet using GPG asymmetrical encryption ([http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173), [http://ubuntuforums.org/showthread.php?t=649466](http://ubuntuforums.org/showthread.php?t=649466))

Additionally I did not include examples of executing a process on the remote server, however an example of how to do this would be included in the /etc/fwknop/access.conf file.

Comments and additions are welcome.  




[SIZE="3"]**Removal of FWKNOP**[/SIZE]

Assuming directory structure used in the guide (Again if using version number other than 1.9.3 please alter according to your configuration):
```

cd ~/Source/fwknop/fwknop-1.9.3
sudo perl ./install.pl --uninstall
sudo update-rc.d -f fwknop remove

```

[SIZE="3"]**Addendum**[/SIZE]

- FWKNOP SPA (Single Packet Authentication) Raw Data Packet (What the encrypted packet actually looks like when sniffed):
```

 Raw packet data (single line): +CqkFkQUcR/9N5pdkpid6bZPnMJ60l49WOXm4/cDEDkL8xyC5nnPdmMZYCrTXkTyxWO1IsvrW6wWdyIhrOhFhOz0kEknCuHl2Iiz4rs0ZOUG4etcPczuspp1FumPXbtdmnM7KmEAbTyFuGvYCWFMwZfoXjlhI0E75q3Yl2GAi974kfJi2hbI3L

```

- Contents of Encrypted Packet
```

Packet fields:
    Random data:     7334473082601197
    Username:        <username>
    Remote time:     1212209666
    Remote ver:      1.9.4-pre3
    Action type:     1 (SPA_ACCESS_MODE)
    Action:          192.168.1.101,tcp/22
    SHA256 digest:   OmsuEDCXgYYzZ7WDnf+Jl2mt7EVYz2ixoIlLaCl2qmk

```

[SIZE=2]**Server Commands**[/SIZE]

**sudo ps -A | grep fwknop** <---Will show if fwknop daemon is up and running.  If fwknopd process is not listed then need to start fwknop daemon manually (sudo /etc/init.d/fwknop start)

[SIZE="3"]**More Fully Featured Firewall Script**[/SIZE]

```

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 -j DROP
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT

#Uncomment OutLines in RED if Logging is Required

### Create a LOGDROP chain to log dropped packets
[COLOR="Red"]#$IPTABLES -N LOGDROP[/COLOR]

### Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
[COLOR="Red"]#LOGLIMIT="2/sec"
#LOGLIMITBURST="10"[/COLOR]

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
[COLOR="Red"]#LOGLEVEL = debug[/COLOR]

[COLOR="Red"]#$IPTABLES -A LOGDROP -i ! lo -p tcp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
#$IPTABLES -A LOGDROP -i ! lo -p udp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
#$IPTABLES -A LOGDROP -i ! lo -p icmp -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "
#$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level #$LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN:  "[/COLOR]

### Log All Dropped Packets
[COLOR="Red"]#$IPTABLES -A INPUT -j LOGDROP[/COLOR]

exit


```

[SIZE="3"]**References:**[/SIZE]

**Port Knocking Description and Links to Port Knock Utilities: ** [http://www.portknocking.org/](http://www.portknocking.org/)
**Port Knocking Wiki:** [http://en.wikipedia.org/wiki/Port_knocking](http://en.wikipedia.org/wiki/Port_knocking)
**FWKNOP:** [http://www.cipherdyne.org/fwknop/](http://www.cipherdyne.org/fwknop/)
**Using GnuPG in conjunction with FWKNOP: **[http://cipherdyne.org/fwknop/docs/gpghowto.html](http://cipherdyne.org/fwknop/docs/gpghowto.html)
**List of Various Port Knocking Implementations:** [http://www.portknocking.org/view/implementations](http://www.portknocking.org/view/implementations)
**NMAP Port Scanner**: [http://nmap.org/](http://nmap.org/)
**OpenSSH server setup on Ubuntu:** [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
**GnuPG Advanced Concepts:** [http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173)
**HowTo Compile GPG (version 1 and 2) from SVN with IDEA and Camellia Ciphers: ** [http://ubuntuforums.org/showthread.php?t=687173http://ubuntuforums.org/showthread.php?t=649466](http://ubuntuforums.org/showthread.php?t=687173http://ubuntuforums.org/showthread.php?t=649466)

---

### Post by Dr Small on 2008-05-30
Very, very good, KevDog. I'm going to have to try this soon. I have always been curious about port-knocking, and this looks interesting!

---

### Post by kevdog on 2008-05-30
Dr Small

If no one else responded -- I knew you would.  I'm not sure how practical a port knocker is on an enterprise server, however it is a hobbyist's dream.

---

### Post by The Tronyx on 2008-05-31
Awesome post Kevdog.  Definitely going to be messing with this in the coming days!

:guitar:

---

### Post by Dr Small on 2008-05-31
Well, I got FWKNOP installed on my Ubuntu Server, but I can't get it installed on ArchLinux because I am missing libpcap-dev, which I can't seem to find in the repositories. :(

Maybe I should look it up and find the source.

---

### Post by kevdog on 2008-05-31
Well you probably already found this page:
[http://www.archlinux.org/packages/2502/](http://www.archlinux.org/packages/2502/)

Let me know how you would install under Arch after compiling the pcap package-- obviously you would need the header files when linking.  I'll add it to the guide in the Addendum section.

---

### Post by Dr Small on 2008-05-31
I have libpcap installed, but I didn't think it was the dev package. Anyhow, I am now trying to create a PKGBUILD file, for building an Arch Package, which I am still deguging.

If I *ever* get it done, I'll post it.

---

### Post by Dr Small on 2008-06-01
I am finding that it would just be easier to compile fwknop instead of writing it as a Arch package :D FWKOP's install.pl needs to be rewritten with different path locations, which requires alot of sed work from the package.

Fewwy on that. Just tell them to compile.
I'm going to compile it myself, now :)

---

### Post by kevdog on 2008-06-01
Dr. Small

According to the author, he is in the process or writing it as a C program rather than perl.  This will be beneficial because hopefully then it would be possible to add this to the firmware of a dd-wrt router.  I'm not sure of the time table of this re-write, however I believe its on the _distant_ horizon.

---

### Post by Dr Small on 2008-06-01
Yay. I got everything to work!
I had this nice long post wrote up, because I was having a problem, but as I was writing I solved my own problem. I love that :D

I had the ip addresses backwards in the client command, and so in never unlocked the server. lol. Well, now everything works, except one thing, and I'm not really sure it isn't doing it correctly. Anyhow, I'll ask you.

When I unlock port 22 with the FWKNOP client, it opens it for 30 seconds. I then connect via SSH to the server. When the timer ends, my SSH session freezes. Is this how it is supposed to work, or is there some SSH setting I am missing that would keep the connection alive?

But really, I guess it is working properly, as I don't think it's possible to keep the connection alive after the port has been closed.

Anyhow, this is a great guide, and a fun tool to use.
Thanks for posting this, kevdog :)

Dr Small

---

### Post by kevdog on 2008-06-01
Dr. Small

You are about 1 day behind me, because I just discovered that problem and solution yesterday.  

Here is the solution

Although the fwknop daemon modifies the iptables, it does it through some secondary process that doesn't conflict with any rules in place prior to running the program. The way I wrote the tutorial, I basically flushed and deleted the current ruleset, although in a working environment you would probably just want to keep your existing ruleset, and avoid this step. Basically if you have your iptables set up the way you want (through firestarter, by hand, what ever method) you can continue using these rules EXCEPT you would probably want to change port 22 (or whatever port you are using with fwknop) to a default DROP stance.

You also want to include the following within the iptables ruleset:

```

sudo /sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo /sbin/iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo /sbin/iptables -A INPUT -i ! lo -j DROP
sudo /sbin/iptables -F FORWARD -i ! lo -j DROP

```

These lines for example would keep open existing connections (or forwarding connection) when for example the ssh rule set after 30 seconds (or whatever you have specified) changes from ACCEPT to DROP.  That way the ssh connection will be maintained.

If you want I can extend the tutorial to work with GPG keys.  I didn't include this originally because I didn't know what kind of response I was going to get.  Its fairly easy to do however if you have worked with GnuPG before.

Also if you could either post or upload your changes or writeup changes you made to make this work on Arch, it would be great (or just submit them to the author directly).

Thanks, hopefully that clarifies things.

---

### Post by Dr Small on 2008-06-01
Thanks kevdog. You truely are a help. One thing I should note though, is that if you run:
```
/sbin/iptables -A INPUT -i ! lo -j DROP
```

It blocks all pings, and then nmap can't function properly, because it can't ping the host. Then you can't tell if the port is being filtered or not.

But I wrote a simple little script, which automates the proccess a little bit better, after you have FWKNOP installed, which is basically just juggling the firewall rules around and start / stopping the FWKNOP daemon.
**Script Updated.**
```
#!/bin/bash
# Simple Script for starting and
# stoping FWKNOP, a little better.


start()
	{
# Save current Firewall Rules
iptables-save -c > /etc/iptables-save

# Flush Existing Rules
iptables -F

# Keep existing connections open.
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
#/sbin/iptables -A INPUT -i ! lo -j DROP

# Start fwknop
/etc/init.d/fwknop start

# Disable SSH Connections
/sbin/iptables -A INPUT -p tcp --dport ssh -j DROP
	}

stop()
	{
# Stop FWKNOP
/etc/init.d/fwknop stop

# Flush Firewall rules
iptables -F

# Restore Firewall Rules
cat /etc/iptables-save | iptables-restore -c
	}

install()
	{
# Running this option, installs this script
# to init.d and rc.d while removing fwknop
# from those places. 
# Basically, this script would be the control
# operator, instead of the fwknop init script.

# Remove fwknop from rc.d
update-rc.d -f fwknop remove
echo 'FWKNOP Removed from rc.d...'

# Copy THIS script (which is not
# in init.d) to init.d
cp $0 /etc/init.d/portknock
echo $0 'copied to init.d...'

# Add portknock to rc.d
update-rc.d portknock defaults 99
echo 'portknock successfully added to rc.d...'
echo ''
echo 'Installation Complete.'
	}

remove()
	{
# Running this option will
# remove 'portknock' from 
# init.d and rc.d. fwknop will
# then be re-added back to rc.d.

# Remove portknock from rc.d
update-rc.d -f portknock remove
echo 'portknock removed from rc.d...'

# Remove portknock from init.d
rm /etc/init.d/portknock
echo 'portknock removed from init.d...'

# Restore fwknop to rc.d
update-rc.d fwknop defaults 99
echo 'fwknop restored to rc.d...'
echo ''
echo 'Portknock removed successfully.'
	}

case "$1" in

 start|restart)
   stop
   start
   ;;
 stop)
   stop
   ;;
 install)
   install
   ;;
 remove)
   remove
   ;;
 *)
   echo "usage: start|stop|restart|install|remove."
   ;;

esac
exit 0


```


As for getting FWKNOP installed on Arch, it was basically the same as it is for Debian based systems. I just meerely ended up compiling it all from source. Worked much faster. I trashed my PKGBUILD file since it wasn't turning out correctly. The same instructions you supplied can be used for installing on Arch.

I'll be expirimenting more with FWKNOP in the very near future for using GPG keys with it. It doesn't look like it will be that hard.

Dr Small

---

### Post by kevdog on 2008-06-01
If you want to allow ping requests (which are useful of course) I think you can do the following(untested as of yet):

sudo /sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo /sbin/iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo /sbin/iptables -A INPUT -p icmp --icmp-type 8 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
sudo /sbin/iptables -A INPUT -i ! lo -j DROP
sudo /sbin/iptables -F FORWARD -i ! lo -j DROP

I'll try this setup.  Since the ping rule is listed prior to the drop rule for everything else, I think rules listed first in the iptables have priority.  This I will have to check.

That script of yours is awesome -- I prefer scripts myself, but never no how they go over in a general tutorial.  Downloading, saving the script, making it executable, and then running the script always seems like such a chore for beginners.  But your script really automates a bunch of things that saves a lot of time.

---

### Post by Dr Small on 2008-06-03
I am not being able to get the GPG part of it to work. My current configuration looks like this:
```
### default Single Packet Authorization (SPA) via libpcap:
SOURCE: ANY;
OPEN_PORTS: tcp/22;   ### for ssh (change for access to other services)
#KEY: 12345678;
FW_ACCESS_TIMEOUT: 30;
### if you want to use GnuPG keys (recommended) then define the following
### variables
GPG_HOME_DIR: /root/.gnupg;
GPG_DECRYPT_ID: 7B0FE328;
GPG_DECRYPT_PW: MYPASS;
GPG_REMOTE_ID: 26FD8AF9;
```
7B0FE328 = Server's GPG Key (also has private key).
26FD8AF9 = My GPG Key (has my private key on it too).

The server key has signed my key, and my key has signed the server's key. All of this is on root's gpg keyring /root/.gnupg

Now at the client side, after I start FWKNOP, I run:
```
sudo fwknop -A tcp/22 --gpg-recip 7B0FE328 --gpg-sign 26FD8AF9 -s -k 192.168.0.70
```

And I get:
```
[+] Starting fwknop client (SPA mode)...
Can't locate Class/MethodMaker.pm in @INC (@INC contains: /usr/lib/fwknop/i686-linux-thread-multi /usr/lib/fwknop /usr/lib/perl5/site_perl/5.10.0 /usr/share/perl5/site_perl/5.10.0 /usr/lib/perl5/vendor_perl /usr/share/perl5/vendor_perl /usr/lib/perl5/core_perl /usr/share/perl5/core_perl /usr/lib/perl5/current /usr/lib/perl5/site_perl/current .) at /usr/lib/fwknop/GnuPG/Options.pm line 59.
BEGIN failed--compilation aborted at /usr/lib/fwknop/GnuPG/Options.pm line 59.
Compilation failed in require at /usr/lib/fwknop/GnuPG/Interface.pm line 28.
BEGIN failed--compilation aborted at /usr/lib/fwknop/GnuPG/Interface.pm line 28.
Compilation failed in require at /usr/bin/fwknop line 1117.

```

I even found this guide at Ubuntu Wiki which I followed, but I don't get the same output as they do:
[https://help.ubuntu.com/community/SinglePacketAuthorization](https://help.ubuntu.com/community/SinglePacketAuthorization)

Any idea where I messed up?
Dr Small

---

### Post by kevdog on 2008-06-03
I'll look at this tonight when I get home -- I had gpg working with fwknop version 1.9.3.  Over the weekend 1.9.4 was released and I haven't tried the gpg feature in 1.9.4 yet.  What version of fwknop are you running on client and server.  I believe Arch is your server and ubuntu is your client?

I you don't have 1.9.4 installed, try installing this so we are working with the same version.  It has some really neat features with NAT redirection, that will randomly assign you a ssh port.  You ssh into the random port
ssh -p <random_number_assigned> user@server

With the IPtables, the random_port_number is reassigned to port 22 (its own NAT redirection).  I thought this feature was worth mentioning.

---

### Post by Dr Small on 2008-06-03
I am running Version 1.9.3 for both client and server, currently. But I'll change that so we both are in the same boat.

ArchLinux is my desktop, and Ubuntu is running my Server.
Arch runs the client (and is 192.168.0.16).
Ubuntu is the server (and is 192.168.0.70).

Both are behind a router with several other systems on the network. That will give you an idea of how things look behing the router.

Edit: Ahoy matey! I be in da same boat as ye now :)
And by the way, it is still giving me the same errors. I must be doing something wrong :S

Dr Small

---

### Post by kevdog on 2008-06-04
I'm sure I will be of no help, since everything works for me.

But a few suggestions.

Just to let you know my setup since it differs from you.  
Client (Cygwin) = Windows
Server (Ubuntu)
All version 1.9.4

Both are behind a NAT router with 2 other computers on the LAN.  I haven't actually tried to connect from external IP address.  I'm using local IP's on all my attempted connections (port knocker program still in *beta* phase for me).

I'd just double check 
$gpg --list-keys on both server and client and make sure the keys are installed (which I'm sure they are).  Here is my output:

Client:
```

$ gpg --list-keys
gpg: WARNING: This version has been built with support for the Camellia cipher.
gpg:          It is for testing only and is NOT for production use!
gpg: WARNING: using insecure memory!
gpg: please see http://www.gnupg.org/faq.html for more information
/home/klal/.gnupg/pubring.gpg
-----------------------------
pub   4096R/7EBCE6DE 2007-11-14
uid                  KevDog (Kevdog) <email@gmail.com>
uid                  [jpeg image of size 3122]
sub   4096R/E4193E1A 2008-02-15

pub   2048R/3A3A2A81 2008-05-27
uid                  fwknopd (fwknop server key) <fwknopd@localhost>
sub   2048R/81C0D5C6 2008-05-27

```

Server:
```

root@sudarshan:/etc/fwknop# gpg --list-keys
gpg: WARNING: This version has been built with support for the Camellia cipher.
gpg:          It is for testing only and is NOT for production use!
/root/.gnupg/pubring.gpg
------------------------
pub   2048R/3A3A2A81 2008-05-27
uid                  fwknopd (fwknop server key) <fwknopd@localhost>
sub   2048R/81C0D5C6 2008-05-27

pub   4096R/7EBCE6DE 2007-11-14
uid                  Kevdog (Kevdog) <email@gmail.com>
uid                  [jpeg image of size 3122]
sub   4096R/E4193E1A 2008-02-15


```

My access.conf file (similar to yours on server -- relevant section)
```

### default Single Packet Authorization (SPA) via libpcap:
SOURCE: ANY;
OPEN_PORTS: tcp/22;   ### for ssh (change for access to other services)
#KEY: <key>;
DATA_COLLECT_MODE: PCAP;
GPG_REMOTE_ID: 7EBCE6DE;
GPG_DECRYPT_ID: 3A3A2A81;
GPG_DECRYPT_PW: <password>;
GPG_HOME_DIR: /root/.gnupg;
FW_ACCESS_TIMEOUT: 30;

```

My command line that connected from client to server (**Notice this is different than yours**):

```

$ fwknop -A tcp/22 --gpg-recip 3A3A2A81 --gpg-sign 7EBCE6DE -s -D 192.168.1.105

[+] Starting fwknop client (SPA mode)...
[+] Enter the GnuPG password for signing key: 7EBCE6DE

GnuPG signing password:

[+] Building encrypted Single Packet Authorization (SPA) message...
[+] Packet fields:

        Random data:    2659950876413823
        Username:       klal
        Timestamp:      1212585655
        Version:        1.9.4
        Type:           1 (access mode)
        Access:         0.0.0.0,tcp/22
        SHA256 digest:  l6S1cxMko5vmvc8+GQ0Ufm4nXZBTtrDqGEto94kSip8

[+] Sending 1340 byte message to 192.168.1.105 over udp/62201...

```

And resultant log on server:
```

Jun  4 08:21:03 sudarshan fwknopd: received valid GnuPG encrypted packet (signed with required key ID: "7EBCE6DE") from: 192.168.1.103, remote user: klal, client version: 1.9.4 (SOURCE line num: 115)
Jun  4 08:21:03 sudarshan fwknopd: add FWKNOP_INPUT 192.168.1.103 -> 0.0.0.0/0(tcp/22) ACCEPT rule 30 sec
Jun  4 08:21:34 sudarshan fwknop(knoptm): removed iptables FWKNOP_INPUT ACCEPT rule for 192.168.1.103 -> 0.0.0.0/0(tcp/22), 30 sec timeout exceeded

```

Testing:
To See if port was actually opened:
Client before fwknop invocation:
```

$ nmap -p 22 192.168.1.105

Starting Nmap 4.62 ( http://nmap.org ) at 2008-06-04 08:37 Central Daylight Time

Interesting ports on 192.168.1.105:
PORT   STATE    SERVICE
22/tcp filtered ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.692 seconds

```

After invocation:
```

$ nmap -p 22 192.168.1.105

Starting Nmap 4.62 ( http://nmap.org ) at 2008-06-04 08:38 Central Daylight Time

Interesting ports on 192.168.1.105:
PORT   STATE SERVICE
22/tcp open  ssh
MAC Address: 00:40:96:AF:E3:0C (Cisco Systems)

Nmap done: 1 IP address (1 host up) scanned in 0.444 seconds

```

Probably not helpful except my command line invocation was different.

---

### Post by Dr Small on 2008-06-06
Ok. Michael Rash told me to try fwknop-1.9.5-pre1, which did fix my GPG problem, as now, when I run:
```
fwknop -A tcp/22 --gpg-recip 7B0FE328 --gpg-sign 26FD8AF9 -s -D 192.168.0.70
```

I get the following:
```
[+] Starting fwknop client (SPA mode)...
[+] Enter the GnuPG password for signing key: 26FD8AF9

GnuPG signing password: 
```

I enter my password, then get this:
```
[+] Building encrypted Single Packet Authorization (SPA) message...
[+] Packet fields:

        Random data:    3490835496495545
        Username:       drsmall
        Timestamp:      1212772260
        Version:        1.9.5-pre1
        Type:           1 (access mode)
        Access:         0.0.0.0,tcp/22
        SHA256 digest:  94ZeBt99aGAdbfuPhgp4w4WHPiwUMrB29TG71pYNII0

[+] Sending 716 byte message to 192.168.0.70 over udp/62201...
```

But it never opens the port. I can't connect to the SSH server and nmap is still telling me it is filtered. Have a quick look at access.conf again. If you see nothing wrong, I contact Michael again.

```
SOURCE: ANY;
OPEN_PORTS: tcp/22;
#KEY: 12345678;
DATA_COLLECT_MODE: PCAP;
GPG_HOME_DIR: /root/.gnupg;
GPG_DECRYPT_ID: 7B0FE328;
GPG_DECRYPT_PW: <password>;
GPG_REMOTE_ID: 26FD8AF9;
FW_ACCESS_TIMEOUT: 30;
```

Dr Small

---

### Post by kevdog on 2008-06-07
where do I find the 1.9.5 pre 1 release?

---

### Post by Dr Small on 2008-06-07
Here:
[http://www.cipherdyne.org/fwknop/download/fwknop-1.9.5-pre1.tar.gz](http://www.cipherdyne.org/fwknop/download/fwknop-1.9.5-pre1.tar.gz)

Michael Rash sent it to me by email. ;)

---

### Post by Dr Small on 2008-06-08
Michael Rash helped my solve the problem. Apparently the server's clock is 1 minute or so ahead of the client's clock, so the packet was aged as soon as it was sent / received. Therefore in never opened the port.

I am now running fwknop-1.9.5-pre1 on both client and server, and have GPG working for it. Yay! Then I wrote a simple little script to connect to mycroft (since I keep port 22 blocked now):
```
#!/bin/bash
# Usage: unlock <host>

fwknop -A tcp/22 --gpg-recip 7B0FE328 --gpg-sign 26FD8AF9 -a 192.168.0.16 -D $1 && ssh -XC $1
```

I then made a launcher to it in my toolbar in IceWM and get prompted for my password at the click of a button :)

---

### Post by kevdog on 2008-06-08
Just wondering if your script should be:


fwknop -A tcp/22 --gpg-recip 7B0FE328 --gpg-sign 26FD8AF9 -a 192.168.0.16 -D $1 && ssh -XC -c blowfish $1

Are you using ssh version 1?  For version 2, the cipher list is different?

I ran into a problem with the clocks on my original setup, having to disable the timestamp feature, even though the clocks were registering the same time.  I think he told me at that time is was going to build in a time offset feature into the server software.  I'll have to get this pre-release up and working.

I'll add to the tutorial that now it has been tested and successfully used in Ubuntu,Arch,Cygwin environments.  Any other information you specifically needed to do to get it up in running in Arch?

---

### Post by kevdog on 2008-06-08
Have you had the opportunity to play with the random port or nat features yet?  Do you think I should add a section to the original guide that would detail use with GnuPG or simply refer to the GnuPg instruction page written at the fwknop website:
[http://cipherdyne.org/fwknop/docs/gpghowto.html](http://cipherdyne.org/fwknop/docs/gpghowto.html)

---

### Post by Dr Small on 2008-06-08
Yeah, that should be && after the command. Forgot about that. And as to the ssh cipher, I have just always done it like that. Bodhi told me to use that for xephyr'ing over SSH. I now see that it is used for Protocol 1. But the SSH server **is** running on Protocol 2.

No, I haven't got around to tinkering any further with it yet. I need to, so I can further understand it. Just linking to the GPG Howto page should be suficient. :)

Now... we just need to get Tronyx busy with trying this ;)

Dr Small

---

### Post by kevdog on 2008-06-08
Tronyx??  Have we met before?  Surprised Bodhi has commented on this method.  Seems like his cup of tea!

---

### Post by Dr Small on 2008-06-08
> **kevdog said:**
> Tronyx??  Have we met before?  Surprised Bodhi has commented on this method.  Seems like his cup of tea!
lol. yes :D
[http://ubuntuforums.org/showpost.php?p=5083248&postcount=4](http://ubuntuforums.org/showpost.php?p=5083248&postcount=4)

Tronyx is his IRC name, which we all call him ;)
[I seem to recall]("http://ubuntuforums.org/group.php?groupid=79") bodhi commenting something about it, recently...

---

### Post by gmendoza on 2008-06-08
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Nice write up.  FYI folks, the following guide is available on the
community documentation site [1].

I just updated it for 1.9.4, and it does include a sample firewall
script for those of you that want to try it out.  I plan to update the
guide to use ufw in the near future to keep things consistent with
Ubuntu objectives.

Cheers.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFITIceBZd5UQddvKkRApr4AKCFzdyLVjyZCfslZpRVRXY57hRwBACdGJFi
F7C+0K7tlDkmQe8BKyYJaWU=
=A/g6
-----END PGP SIGNATURE-----

[1] [https://help.ubuntu.com/community/SinglePacketAuthorization](https://help.ubuntu.com/community/SinglePacketAuthorization)

---

### Post by kevdog on 2008-06-08
gmendoza

I found your guide after I had written mine, however I had problems with the actual installation -- particularly with installing the necessary perl libraries that are needed -- particularly Net::Pcap.   This step was one of the biggest hurdles that I had with the initial install.  The code has since been patched since the way the packets are timed (packet_aging parameter) is slightly buggy.  You might want to include these steps, since they have given a few people including me a lot of problems.

---

### Post by gmendoza on 2008-06-09
KevDog

If you say you're having problems, I believe you, but I'm not quite certain why one would run into dependency issues, so long as you add libpcap-dev, build-essential, and mailx packages before hand.

I've been running fwknop for quite some time now, and run through many installations using the same method without issue.

The updated instructions outline all that is necessary to get fwknop running with the latest stable version and has been tested several times via cut and paste.  I would appreciate it if you can outline exactly where the trouble is so I can add a note accordingly.

Thanks.

---

### Post by kevdog on 2008-06-09
The guide was written against fwknop v 1.9.3.  At the time I was installing on Hardy Heron.  Despite the Net:Pcap lib that was supposed to be installed by default, for some reason this library was either corrupt, wasn't installed, or wasn't working as shown fwknop_test.pl output.  I needed to manually install this library.  This wouldn't have been such a big deal, however installation of this particular library using cpan does not work correctly (as I spent hours reading other posts documenting a similar problem before a manual installation method was defaulted to).  Again, the fwknop installation script should install the Net::Pcap library, but it did not work for me.   Additionally problematic was the fwknop_test.pl output that at times gave me errors, although the full blown installation would seemingly work.  Additionally, topics such as debugging -- running fwknop outside of init.d and by checking the system logs /var/log/messages should be covered as an addendum (in addition to the use of nmap), since these give ways to actually verify if the server has received/decrypted the spa packet.  Again a lot to cover, however as with any software package, never expect things to work as promised all the time.  A tutorial should educate the installer where to consult for error messages, and if possible some basic methods to correct/verify the errors -- of course there is always the forums, however I believe the Ubuntu forums are a peripheral support mechanism for this product.  Unfortunately the mailing lists at sourceforge for fwknop are quite dead, and really don't provide any useful feedback if you require rather rapid assistance.

---

### Post by Sef on 2008-06-09
Moved to Tips and Tutorials.

---

### Post by gmendoza on 2008-06-09
Ahh... I see now.  The problem was perhaps version specific.  Yeah, the previous version on the doc was actually 1.9.0, so obviously later versions introduced new issues.  Thanks for the info.

The good news is, 1.9.4 works well, and adds the really nice feature of accepting SPA packets on a range of ports to avoid IDS signatures, etc.

That would be cool to add to the doc as well.

---

### Post by cprofitt on 2008-06-09
Very nice -- been reading about this but not seen any application to try it...

I will have to follow this next weekend on my test server... looks like fun.

---

### Post by kevdog on 2008-07-20
Version 1.96 Released 

Awaiting update of Change List
(Will update guide once server appropriately tested with new version)

---

### Post by kevdog on 2008-09-13
Version 1.9.7 Released - [http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.7/ChangeLog](http://trac.cipherdyne.org/trac/fwknop/browser/fwknop/tags/fwknop-1.9.7/ChangeLog)

Supposedly an unofficial Debian repository has been created to simply installation of the fwknop server on Debian/Ubuntu.  I have not yet verified these steps however instructions are given here:
[http://cipherdyne.org/blog/2008/08/installing-fwknop-on-debian-and-ubuntu.html](http://cipherdyne.org/blog/2008/08/installing-fwknop-on-debian-and-ubuntu.html)

Happy Port Knocking!!

---

### Post by kevdog on 2008-10-30
For all you Arch users -- just to let you know that fwknop is being distributed:
[http://aur.archlinux.org/packages.php?ID=20630](http://aur.archlinux.org/packages.php?ID=20630)

---

### Post by krammer on 2009-02-11
Ok, so I cannot get fwknop client working for the life of me on my linux box, internally and externally...it works fine from my Windows machine, where I then use putty after the encrypted packet is sent.

On my linux box for fwknop, I use:

```
fwknop -A tcp/22 -a 192.168.1.6 -D 192.168.1.3
ssh username@192.168.1.3
```

Am I doing anything wrong here???  Does the windows client use different default options that aren't seen?  I don't have iptables running on the linux fwknop client...so nothing should be blocked.

Thanks to anyone who can help.

---

### Post by kevdog on 2009-02-12
A couple of things you might want to try:

fwknop can be run in debug mode with the --debug command line option. This will disable daemon mode execution, and print verbose information to the screen on STDERR as packets are received

Also, after issuing the first command, port 22 should be open on the server.  I would use nmap to scan the server for specifically port 22 to see if the port is open.

---

### Post by krammer on 2009-02-12
I ran an nmap scan after issuing the fwknop command, and port 22 was "filtered" not open...so something is going wrong.  I know I have the right key, and I know it's the right IP.  

I also ran it in debug mode...it didn't give me anything useful.  It just spit back some perl paths, and then the steps it went through sending the SPA.

There wasn't really any confirmation that it sent successfully...just:

[+] Sending 182 byte message to 192.168.1.3 over udp 62201...

That was the last line.  Is that right?  I guess I could always run a sniffer to see if it gets to my server.

---

### Post by kevdog on 2009-02-13
Ok, so you can confirm a packet was sent to the server from the client.

On the server I would do the following:

1. Wireshark -- A packet sniffer -- see if you get packet received from client

2. The command:
sudo iptables -L
This will list your current firewall rules.  If successful, you should see a change in this list if the packet was successful.

3. Also, I think fwknopd keeps a log.  Have you investigated this?

Also a few things:
Are you running the daemon in debug mode?: Similar to this:
sudo perl ./fwknopd --debug

If stuck can you post your script that establishes your iptables, and also your /etc/fwknop/access.conf file.

---

