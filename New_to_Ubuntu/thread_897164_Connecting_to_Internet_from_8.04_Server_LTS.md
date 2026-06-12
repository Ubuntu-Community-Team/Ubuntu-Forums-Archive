---
title: "Connecting to Internet from 8.04 Server LTS"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-08-21
Hello,

I have just installed Ubuntu 8.04 Server on a clean 10gb hard drive. The system has another hard drive with XP installed. The installation went well, However I have not been able to connect to the internet.  The system is connected to another XP Box via a Cat 5 cable and the 2 systems will communicate XP to XP but not thru UBuntu. So I know my network card is working.   The other desktop using XP is connected to my DSL Modem with a live connection to the internet.  This is what I've tried so far at the Ubunto prompt.

$ipconfig
results     Link encap:Local Loopback
            inet addr:127 .o.o.1 Mask:255.0.0.0
		UP LOOPBACK RUNNING MTU:16436 Metric:1
		RX packets: 38 errors:0 dropped:0 overruns:0 frame:0
		TX packets: 38 errors: 0 dropped:0 overruns:0 carrier:0
		collisions:0 txquelen:0
		RX bytes:3064 (2.9 KB) tx bytes:3064 (2.9 KB)

$ping	-c 3 localhost	   
statistics
		3 packets transmitted, 3 received, 0% packet loss, time 1998 ms
		rtt min/avg/max/mdev = 0.019/0.049/0.0.091/0.031 ms

$ netstat
results		Active Internet connections (w/o servers)
			Proto Recv-Q Send-Q Local Address			Foreign Address		State
			Active Unix domain sockets (w/o servers)
			Proto RefCnt Flags	Type	State				I-Node	Path
			unix 2 [ ]              DGRAM					5734		@/com/ubuntu/upstart
			unix 5 [ ]              DGRAM					10570		/dev/log
			unix 2 [ ]              DGRAM					5866		@/org/kernel/udev/ude
			vd
			unix 2 [ ]              DGRAM					10672
			unix 2 [ ]              DGRAM					10665
			unix 2 [ ]              DGRAM					10620


I sure hope this helps somebody know what my problem is or someone may have some suggestions of something else I need to try.

Thank ya'll in advance

---

### Post by fedex1993 on 2008-08-23
it sounds like someone didn't have an ethernet cable plugged in while setting up the server hmm.

---

### Post by Iowan on 2008-08-23
Post your **/etc/network/interfaces** file or at least check the settings.    There should be an "auto" line for eth0.  Some other information depends on whether you install static address or use DHCP (most servers should have static address - or static lease).

From my server:
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.4.2
        netmask 255.255.255.0
        network 192.168.4.0
        broadcast 192.168.4.255
        gateway 192.168.4.1
        dns-nameservers 192.168.4.1

My workstation:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

---

### Post by JKHinton CPBD on 2008-08-24
Hello Fedex1993, you are correct as a matter of fact there was not a network card in this old machine when I first installed Ubuntu server.  I have since installed the network card and hooked up the cat 5 cable.  I told you before I am a newbie at this Ubuntu and did not realize that it was necessary to start with, guess I should have known this would have to be in place first.  Will it be easier to start over with a fresh install?

Thanks for the response.

Hello Iowan,  OK I tried typing /etc/network/interfaces at the :~$ prompt I received this

-bash: /etc/network/interfaces: Permission denied

? Do I have to type in a change directory command before issueing this command?  Please bear with me I am a absolute beginner with Ubuntu.

Thank you for the help.

---

### Post by mgranet on 2008-08-24
You need to run system commands prefaced with ```
sudo
``` Also, you need to open that file with a text editor. The command you would want to run would be ```
sudo gedit /etc/network/interfaces
``` If you are running KDE, replace 'gedit' with 'nano'.

---

### Post by JKHinton CPBD on 2008-08-24
OK Iowan,

I found out that to change directories is just like the old DOS command cd /etc/network/ which I tried and it worked but I am missing still the interfaces part I tried entering interfaces as another directory behind /etc/network/interfaces interfaces is not a valid directory.  I tried interfaces as a command I get interfaces command not found.  I also tried sudo interfaces same problem command not found.

Thanks again for the help.

---

### Post by JKHinton CPBD on 2008-08-24
Hey Mgranet,

I am running Ubuntu Server 8.04 LTS.  I tried entering 
sudo gedit /etc/network/interfaces I get command not found.

Thanks for your help on this you know anything else I can try?

---

### Post by mgranet on 2008-08-24
My bad. I forgot the server edition is sans Desktop environment. You should replace 'gedit' with 'pico'.

---

### Post by JKHinton CPBD on 2008-08-25
Here's my results after running 
sudo pico /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

I noticed that I don't have a primary network interface or
any IP addresses.

There has to be a command to make Ubuntu recognize the network card that I installed after the Ubuntu Server installation.

Does anyone have any ideas? whats the next step to getting UBuntu on line?

---

### Post by JKHinton CPBD on 2008-08-26
Ok we are still digging,

I reinstalled Ubuntu 8.04 Server on clean hard disk with Network card installed and Cat 5 DSL cable hooked up. Now when I run 
sudo pico /etc/network/interfaces
I get 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

When I run ifconfig
I get
etho0 Link encap:Ethernet hwaddr 00:c0:f0:29:33:d9
inet addr:10.0.0.6 Bcast:10.255.255.255 Mask:255.0.0.0
inet6 addr: fe80::2c0:f0ff:fe29:33d9/64 Scope:Link
UP BRAODCAST RUNNING MULTICAST MTU:1500 Metric:1
RX paclets:18 errors:0 dropped:0 overruns:0 frame:0
TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2191 (2.1 KB) TX bytes:1706 (1.6 KB)
Interrupt:11 Base address:Oxe000

lo 
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:504 (504.0 B) TX bytes:504 (504.0.B)

When I run 
$ping -c 3 localhost

I get 
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.088ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.028ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.018ms

localhost ping statistics
3 packets transmitted, 3 received, 0% packet loss, time 1998 ms
rtt min/avg/max/mdev = 0.018/0.044/0.0.088/0.031 ms

$ netstat
results Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address Foreign Address State
Active Unix domain sockets (w/o servers)
Proto RefCnt Flags Type State I-Node Path
unix 2 [ ] DGRAM 5742 @/com/ubuntu/upstart
unix 2 [ ] DGRAM 5874 @/org/kernel/udev/ude
vd
unix 4 [ ] DGRAM 10712 /dev/log
unix 2 [ ] DGRAM 10802 
unix 2 [ ] DGRAM 10762

I sure hope this helps somebody out there know whats going on 
with my internet service under Ubuntu????

Any help will be appreciated.

---

