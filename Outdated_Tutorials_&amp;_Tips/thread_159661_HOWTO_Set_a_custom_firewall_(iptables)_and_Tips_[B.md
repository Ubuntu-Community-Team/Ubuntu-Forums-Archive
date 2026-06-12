---
title: "HOWTO: Set a custom firewall (iptables) and Tips [Beginners edition]"
date: 2006-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by frodon on 2006-04-13
[SIZE="2"][COLOR="Red"]31/01/2008 the tutorial has been reviewed and the given script corrected, the previous given script were opening https and IRC port which was not required.[/COLOR][/SIZE]
[COLOR="DarkOrange"]For advanced users which are comfortable with this guide here is a link to another tutorial on the topic which especially written for advanced users as it explains how to set a firewall with input and output filtering :
[http://ubuntuforums.org/showthread.php?t=668148](http://ubuntuforums.org/showthread.php?t=668148)[/COLOR]


**[SIZE="3"]1- Introduction[/SIZE]**

After getting some problems with firestarter i decided to get knowledge about iptables and how to set my own firewall script and want to share this experience for users who want to set quickly a custom firewall.
The purpose of this guide is to provide a basic knowledge about iptables and then help to create a firewall script.
The final step will be to make the script running on each boot.

As another great resource you can have a look at bodhi.zazen iptables page on his website:
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)


This guide will not talk about NAT things.

**[SIZE="3"]2- Commands[/SIZE]**

The first step is to know iptables commands.

**[SIZE="2"]2.1- Main commands[/SIZE]**    

*  -A --append : Add the rule a the end of the specified chain 

```
iptables -A INPUT ...
```

* -D --delete : Allow to delete a chain. 
There's 2 way to use it, you can specify the number of the chain to delete or specify the rule to delete 

```
iptables -D INPUT 1 
iptables -D INPUT --dport 80 -j DROP
```

* -R --replace : Allow to replace the specified chain 

```
iptables -R INPUT 1 -s 192.168.0.1 -j DROP
```

* -I --insert : Allow to add a chain in a specific area of the global chain 

```
iptables -I INPUT 1 --dport 80 -j ACCEPT
```

* -L --list : Display the rules 

```
iptables -L # Display all the rules of the FILTER chains 
iptables -L INPUT # Display all the INPUT rules (FILTER)
```

* -F --flush : Delete all the rules of a chain 

```
iptables -F INPUT # Delete all the rules of the INPUT chain 
iptables -F # Delete all the rules
```

* -N --new-chain : Allow to create a new chain 
```

iptables -N LOG_DROP
```

* -X --delete-chain : Allow to delete a chain 

```
iptables -X LOG_DROP # Delete the LOG_DROP chain 
iptables -X # Delete the chains
```

* -P --policy : Allow to specify to the kernel the default policy of a chain ACCEPT, REJECT, DROP ... 
```

iptables -P INPUT DROP
```

**[SIZE="2"]2.2- Maching commands[/SIZE]**    

The character "!" can be used to specify the oposite. For example a command to avoid all incomming tcp traffic except from the IP 10.42.42.42 is written as follow :
```

iptables -A INPUT -p tcp ! --source 10.42.42.42 -j DROP
```


IP addresses could be optionally associated with their mask like that : IP-address/mask

* -p --protocol : Specify the protocol : tcp, udp, icmp, all 
Example: DROP all icmp traffic
```

iptables -A INPUT -p icmp -j DROP
```

* -m --match : Specify what you want to match : tcp, udp, state, ... 
Example: DROP tcp incomming traffic on port 143

```
iptables -A INPUT -p tcp -m tcp --sport 143 -j DROP
```

* -s --source : Specify a source address to match 
Example: Allow incoming (the INPUT chain) tcp traffic comming from the IP 192.168.42.42

```
iptables -A INPUT -p tcp -s 192.168.42.42 -j ACCEPT
```

* -d --destination : Specify a destination address 
Example : Allow port forwarding for tcp traffic to the IP 10.1.0.1

```
iptables -A FORWARD -p tcp -d 10.1.0.1 -j ACCEPT
```

* -i --in-interface : Specify an input interface (your ethernet card generally)  (only for INPUT, FORWARD and PREROUTING chains)
Example : DROP incoming icmp traffic on eth0 input interface

```
iptables -A INPUT -p icmp -i eth0 -j DROP
```

* -o --out-interface : Specify an output interface (only for OUTPUT, FORWARD and PREROUTING chains)
Example : DROP output icmp traffic on eth0 output interface

```
iptables -A OUTPUT -p icmp -o eth0 -j DROP
```

* --sport --source-port : Specify the source port or an array of ports, -m multiport allow to specify more than one port to match. 
Examples :

```
iptables -A INPUT -p tcp --sport 80 -j ACCEPT iptables -A INPUT -p udp --sport 80 -j DROP iptables -A INPUT -p tcp -m multiport --sport 3128,21,1000 -j DROP iptables -A INPUT -p tcp --sport 1024:2042 -j ACCEPT
```

* --dport --destination-port : Specify a destination port or an array of ports, -m multiport allow to specify more than one port to match. 
Examples :

```
iptables -A OUPUT -p tcp --dport 110 -j DROP iptables -A OUPUT -p udp --dport 110 -j DROP iptables -A OUPUT -p tcp -m multiport --dport 110,4242,119 -j DROP iptables -A OUPUT -p tcp --dport 4925:4633 -j ACCEPT
```

* --tcp-flags : Specify the tcp flag to match : SYN ACK FIN RST URG PSH ALL NONE 
Example : Allow tpc packets with SYN,ACK flag and source port 42
```

iptables -A INPUT -p tcp --sport 42 --tcp-flags SYN,ACK -j ACCEPT
```

* --icmp-type : Specify the icmp type to match 
Example :

```
iptables -A INPUT -p icmp --icmp-type 8 -j DROP
```

* --mac-source : Specify the MAC address to match 
Example : Drop all incoming traffic from MAC address 42:42:AA:42:42:AA

```
iptables -A INPUT --mac-source 42:42:AA:42:42:AA -j DROP
```

* --state : Allow to specify the packet state to match : 
    ESTABLISHED : packet associated to an established connection
    NEW : packet which ask for a new connection
    INVALID : Packet associated to an unknown connection
    RELATED : new connection but linked, really good for FTP connections

Examples :

```
iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state NEW,ESTABLISHED -j ACCEPT iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state ESTABLISHED -j ACCEPT
```

**[SIZE="2"]2.3- Some examples[/SIZE]**    

in those examples i assumed that your internet interface is eth0 (just replace eth0 by what it is for you).

* Setting the default rules : here is how to set the defeult rules 
```

iptables -P INPUT DROP iptables -P OUTPUT DROP 
iptables -P FORWARD DROP
```

* Allow loopback access : 

```
iptables -A INPUT -i lo -j ACCEPT 
iptables -A OUTPUT -o lo -j ACCEPT
```

* Allow web traffic : 

```
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
```

* Allow dns : 

```
iptables -A INPUT -i eth0 -p udp -m udp --sport 53 -j ACCEPT 
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 53 -j ACCEPT iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -j ACCEPT
```

* Allow FTP : 

```
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

* Allow IRC ports : 
```

iptables -A INPUT -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 6667 -j ACCEPT 
iptables -A INPUT -i eth0 -p udp -m tcp --sport 133 -j ACCEPT # identification port iptables -A OUTPUT -o eth0 -p udp -m tcp --dport 133 -j ACCEPT # identification port
```

* Allow or drop an IP : 

```
iptables -A INPUT -s 10.123.452.36 -j ACCEPT 
iptables -A INPUT -s 10.123.452.36 -j DROP
```

* Forward your internet (eth0) connection to eth1, in the example we filter incoming packets for the LAN. 

```
# Forward only established and related connections to the lan for incoming packets 
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
# Forward all OUT connections from the lan 
iptables -A FORWARD -o eth1 -i eth0 -j ACCEPT 
# hide computers behind the firewall 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward 
# then DROP all the rest 
iptables -A FORWARD -j DROP
```

* Forward your internet (eth0) connection to eth1 without any filter : 

```
iptables -A FORWARD -j ACCEPT 
# hide computers behind the firewall 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
```

For other services just open the correponding port(s), **if you don't know which port use the service you want to enable have look in the file /etc/services**. 

* Backlist a list of IPs from a file (gregor171 proposed solution) :
[http://ubuntuforums.org/showpost.php?p=7082326&postcount=263](http://ubuntuforums.org/showpost.php?p=7082326&postcount=263)


**[SIZE="3"]3- The scripts[/SIZE]**

Now it's time to write your iptables script.

**[SIZE="2"]3.1-The firewall script [/SIZE]**

**This exemple will fit the needs of most users, it blocks all incoming and forward traffic and allows : web browsers, https, amule, bittorent, ftp, gaim, IRC, mail protocols (smtp, pop, imap).**
Blocking outgoing access is not needed (incoming is enough).

* We create 2 chain the one called FIREWALL and the second is called TRUSTED 

    **FIREWALL chain** : this chain will allow related and established incoming connection (eth0 interface), then send all other packets to the TRUSTED chain and DROP all the rest. We will send in this chain all INPUT packets. 
    **TRUSTED chain** : In this chain you will add all the ports you may need to open depending on what you use on your computer. 

Now create the firewall script: 

```
sudo gedit /etc/firewall.bash
```

Now add that in the file, remove lines that are not needed for you or add some if it's needed (replace eth0 by the name of your internet interface):

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow amule
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

Make the script executable:

```
sudo chmod +x /etc/firewall.bash
```


    * What is spoofing ? : [http://en.wikipedia.org/wiki/Spoofing_attack](http://en.wikipedia.org/wiki/Spoofing_attack)
    * What is icmp ?: [http://en.wikipedia.org/wiki/Icmp](http://en.wikipedia.org/wiki/Icmp)
    * For amule : [http://www.amule.org/wiki/index.php/Firewall](http://www.amule.org/wiki/index.php/Firewall)

This should be good for most of you, if something doen't work open the port corresponding to the service you want to open (look in /etc/service to know the port number).

To open a new port just add a new rule for the TRUSTED chain like that for tcp : 
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport port_number -j ACCEPT
```
or for udp :
```
iptables -A TRUSTED -i eth0 -p udp -m udp --dport port_number -j ACCEPT
```

Well you firewall script is OK


**[SIZE="2"]3.2-The flush script [/SIZE]**

This script will allow you to delete all the rules and chains, in other words it delete your firewall.

Open the file : 

```
sudo gedit /etc/flush_iptables.bash
```


Put that in the file:

```
#!/bin/sh

#
# Set the default policy
#
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

#
# Set the default policy for the NAT table
#
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
iptables -t nat -P OUTPUT ACCEPT

#
# Delete all rules
#
iptables -F
iptables -t nat -F

#
# Delete all chains
#

iptables -X
iptables -t nat -X

# End message
echo " [End of flush]"
```

Make the file executable :

```
sudo chmod +x /etc/flush_iptables.bash
```

**[SIZE="2"]3.3-The init.d script [/SIZE]**

This script will allow you to handle your firewall like all other services.

Open the file: 

```
sudo gedit /etc/init.d/firewall
```

Edit it like that:

```
#!/bin/bash

RETVAL=0

# To start the firewall
start() {
  echo -n "Iptables rules creation: "
  /etc/firewall.bash
  RETVAL=0
}

# To stop the firewall
stop() {
  echo -n "Removing all iptables rules: "
  /etc/flush_iptables.bash
  RETVAL=0
}

case $1 in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart)
    stop
    start
    ;;
  status)
    /sbin/iptables -L
    /sbin/iptables -t nat -L
    RETVAL=0
    ;;
  *)
    echo "Usage: firewall {start|stop|restart|status}"
    RETVAL=1
esac

exit
```

Make the script executable:
```

sudo chmod +x /etc/init.d/firewall
```

Now you can use these commands to start/stop/restart/status your firewall:
```

sudo /etc/init.d/firewall start 
sudo /etc/init.d/firewall stop 
sudo /etc/init.d/firewall restart 
sudo /etc/init.d/firewall status
```

The final step is to make your script running on each boot of your computer:
```
sudo update-rc.d firewall defaults
```

Well all is done !!!!!

**[SIZE="3"]4-Test if your firewall is reliable [/SIZE]**

I strongly advice you to check your firewall just to see that all is ok.

Perform some udp and tcp scan here : 
[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)
All ports should be seen as blocked
This site is not bad too : [https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)
All port should be seen as stealth

nmap is also a good tool, to install it : 

```
sudo apt-get install nmap 
sudo apt-get install nmapfe
```

Run the GUI :

```
sudo nmapfe
```

Then put your IP as target, all ports should be seen as blocked.

**[SIZE="3"]5- Links & Credits[/SIZE]**

Links :

    * [http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)
    * [http://yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html) 
    * [http://supermikenews.blogspot.com/2006/03/roll-your-own-linux-firewall-script.html](http://supermikenews.blogspot.com/2006/03/roll-your-own-linux-firewall-script.html)

Credits :

    * Lea linux : [http://lea-linux.org/cached/index/Accueil.html](http://lea-linux.org/cached/index/Accueil.html)
    * GTX for showing the way
    * Internet
    * alexisdm (freenews forum).



Thank you for any kind feedback ;)

---

### Post by skaboss on 2006-05-21
Great job !
I met some problems too, with guarddog and firestarter, and had to manage with iptables : unfortunately it was before your excellent howto...
By the way, Kmyfirewall (in iptables interface mode)is very useful to make your own iptables script.

Best regards.

---

### Post by goodfren on 2006-07-22
This is one of the best resource for ubuntu user.

Great work, thks

---

### Post by goodfren on 2006-07-22
Everything is now able to install into it, thks. Also run remove other firewall.

I have try with shield it but i don see stealth in it, the result i get as below;

Solicited TCP Packets: RECEIVED (FAILED) &#8212; As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.



Unsolicited Packets: PASSED &#8212; No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)



Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

Is my setting correct? Thks

---

### Post by frodon on 2006-07-22
Could you post your firewall script ?

Which site did you use to test the firewall ?
You should test with this one, ports should be seen as blocked (same thing than stealth) : 
[http://scan.sygate.com/prestealthscan.html](http://scan.sygate.com/prestealthscan.html)

---

### Post by goodfren on 2006-07-24
Hi;

I now have new problems, after I reboot the system, my excess to internet is totally block, I am using adsl connection which i configure using "sudo pppoeconf", can you tell me how to set so that it will not block my internet dailup access, thks.

Since i do not know to delete the firewall due to i cannot reach to the internet to get your delete code, i have reinstall the whole system again.

---

### Post by frodon on 2006-07-24
To stop the firewall : ```
sudo /etc/init.d/firewall stop
```
To start it : ```
sudo /etc/init.d/firewall start
```
To restart it : ```
sudo /etc/init.d/firewall restart
```

Does your dialup use a specific port for connection ?
Did your internet work when you used firestarter ?

---

### Post by goodfren on 2006-07-24
I do not no which port it used, i only know that it does not use the fixed ip. Can you let me know how to check which port it used?

Even firestarter, i have the same problems, cannot excess the internet.

Thks.

---

### Post by goodfren on 2006-07-24
I guess i have forget to use/try the stop the firewall code. :-( Thks.

---

### Post by tud on 2006-07-24
I added the following three lines into /etc/firewall.bash script in order to use loopback interface (localhost)

```

# Allow loopback interface traffic
iptables -A TRUSTED -i lo -j ACCEPT
iptables -A TRUSTED -o lo -j ACCEPT

```

---

### Post by frodon on 2006-07-24
Hit tud, do you think it would help those who follow the guide to have the loopback interface allowed in the script i gave ?
I didn't put it in the example because i thought that most of the users won't need it.

---

### Post by goodfren on 2006-07-25
No it don work for the code loopback,

---

### Post by Roque on 2006-07-27
> 
 Perform the stealth, udp and tcp scan here : 
 [http://scan.sygate.com/](http://scan.sygate.com/)
 All ports should be seen as blocked

Your firewall script doesn't pass the stealth test of that site. Anyone can confirm this?

---

### Post by frodon on 2006-07-27
Are you sure the firewall is running ?
Did you customise the example i gave ?

I have no problem with my script (a bit different from the example) and i pass all the tests on this site.
BTW, what result did you get with the stealth scan ?

---

### Post by Roque on 2006-07-27
Yes, it's running. I only changed the interface (eth0) to ppp0. I didn't touch the rest.

> 
This site is not bad too : [https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)

That site sees all ports as STEALTH, but the Sygate scan only sees them as BLOCKED.

Have you tested both sites with the actual firewall you posted (I mean not your own modified version) ?

---

### Post by frodon on 2006-07-27
Ok, on the sygate site they use the term blocked for a port which is closed and stealth, it's explained on the top of the steath scan page :
[IMG]http://i7.tinypic.com/2144cox.png[/IMG]

So it's all good man 8) , and of course i tested the example with the 2 sites and also with nmap.

---

### Post by Roque on 2006-07-27
Sorry, my mistake: in my previous post I meant CLOSED (not BLOCKED). It's too late over here :confused: 

So the problem persists: somehow the scanner sees the port.

---

### Post by frodon on 2006-07-27
Hum there's something weird, i trust the sygate site more than others so if the sygate scan return the CLOSED status threre's a problem somewhere.

Just in case, post your firewall script, maybe there's a typo or a mistake somewhere.

---

### Post by dolby on 2006-07-27
> **Roque said:**
> Your firewall script doesn't pass the stealth test of that site. Anyone can confirm this?

i use this script too without the dcc & amule ports and results were:

shileds up scan : sees ports from 1023 - 1056 (scans only the first 1056 tcp ports) as closed and not blocked which results to a failed test.

sygate quick scan: sees all ports that scans for trojans as closed not blocked. all other tests (including stealth scan) pass

---

### Post by frodon on 2006-07-27
dolby, did you cut & paste from the forum or the UDSF guide ?

just to be sure that the firewall is running, run this command : sudo /etc/init.d/firewall restart
Then to check that the rules are active run a : sudo iptables -L
You should see a lot of rules.

My own script is really similar to the example but with outgoing filtering but even without outgoing filtering i pass all the tests that's why there's something which seems weird to me.
If you wish to see my own script, it is there :

---

### Post by dolby on 2006-07-27
i have copied the firewall from here.

edit: but got the same results when i used the one from USFC.

[here](http://pastebin.ca/102262) is the exact script

---

### Post by frodon on 2006-07-27
I just tested again the script given in the guide and the result of the sygate site is all ports BLOCKED.

I wonder what would make the difference for you.

---

### Post by dolby on 2006-07-27
did u run the quick scan? what about the trojan ports? did they turn up as stealthed?

---

### Post by frodon on 2006-07-27
All ports BLOCKED with the quick scan and the example i gave.

When you do a "sudo ipables -L" do you see all the rules ?

---

### Post by dolby on 2006-07-27
as far as i can tell yes i do

---

### Post by Roque on 2006-07-27
This is the script I am running: it's the same you posted but with eth0 replaced with ppp0.
```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i ppp0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i ppp0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

---

### Post by frodon on 2006-07-28
dolby & Roque, the only think IMO who could make the difference is the device you use as network controller, for me it's eth0. If you put something wrong there the rules may be apllied on a network controller which don't handle you internet connection.
If you want to be sure you can remove all the "-i eth0" options thus the rules will be applied on all the network controllers you have.

---

### Post by Roque on 2006-08-01
frodon,

Sorry for the delay. I did as you said and removed  all -i eth0 entries, but sygate keeps reporting CLOSED instead of BLOCKED in the stealth test. 

Confusing stuff.

---

### Post by emretemp on 2006-08-01
hi, 
can we merge 2 different rulesets? 

like this:

iptables -A TRUSTED -i eth0 -p tcp **-m tcp -sport 22** **-m tcp -s 10.11.1.87** -j ACCEPT


here is what i am trying to do:
1. if the source port is 22 
2. and the source ip is 10.11.1.87 

else will be dropped by the script. 


thx in adv.

---

### Post by frodon on 2006-08-01
huh, that's a good question !

I never did that, however you should write it like that : ```
iptables -A TRUSTED -i eth0 -p tcp -m tcp -dport 22 -s 10.11.1.87 -j ACCEPT
```Note that i changed sport to dport.

---

### Post by Scythe!? on 2006-08-05
> **Roque said:**
> This is the script I am running: it's the same you posted but with eth0 replaced with ppp0.
```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i ppp0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i ppp0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i ppp0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

How can I use your script? Do I download it and then run it or something?

---

### Post by hanzomon4 on 2006-08-06
Can I use a different port for bittorrent like 16881:16889?
I ask because I read that some isp will limit download rates on the default bittorrent ports.

---

### Post by frodon on 2006-08-06
Yes, you can do that, it should work without any problems.

---

### Post by hanzomon4 on 2006-08-06
One more thing how do forward my udp port for "listing" (azureus dht)
this is what I added to the script

```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 6881:6889 -j ACCEPT
```

---

### Post by dolby on 2006-08-06
u only need 1 tcp port for azureus to work. port range or udp is not needed. recommended by the azureus team is any port above 50000

example:

```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 55555 -j ACCEPT
```

---

### Post by hanzomon4 on 2006-08-06
> **dolby said:**
> u only need 1 tcp port for azureus to work. port range or udp is not needed. recommended by the azureus team is any port above 50000

example:

```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 55555 -j ACCEPT
```

Right, but for DHT I need UDP, which I got working :D

---

### Post by mtron on 2006-08-07
Thanks! 

It's often much easier to work with conf files (or scripts in this case) than clicking through guis like firestarter! 

Your explanation of Iptables rules is very good, and it was very easy to setup a home network and allow the services on my server (http, ftp) 

Great work! +++

One questin: My server (runs dnsmasq for dhcp ip adress assignment & ipmasq) connects via eth0 to the world, the hub for my home network (with some windows & ubuntu clients connect ) is on eth1.

this is my firewall.bash script. As you can see i had to modify it a bit. Especially i commented out the 
```

# Allow ESTABLISHED and RELATED incoming connection
#iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Send all package to the TRUSTED chain
#iptables -A FIREWALL -j TRUSTED
# DROP all other packets
#iptables -A FIREWALL -j DROP
```

part. As i understand it this is ok with my further settings, but due to the fact that i was running a "hardware" firewall till now, i'm not sure if this might represent a security risk to my network. Could you please share your thoughts about my rules?

thanks in advance!

complete [firewall.bash]("http://mtron.co.nr/firewall.bash.txt")

---

### Post by frodon on 2006-08-07
If you have a hardware firewall an additional software firewall is not really needed IMO.
About your script, the rules about the TRUSTED chain are useless because you send nothing to the TRUSTED chain.
In my script example the i send all the input packets in the FIREWALL chain then all the FIREWALL chain packets to the TRUSTED chain.
In your case you don't use any sub-chain therefore just use directly the input chain :```
iptables -A INPUT -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
iptables -A INPUT -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A INPUT -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# Webmin
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 10000 -j ACCEPT
```Your OUTPUT rules are useless too because the default behaviour specified by "iptables -P OUTPUT ACCEPT" allow all the OUTPUT packets.

Filter the OUTPUT packets is not really needed, most of firewalls (especially under windows) only filter incoming packets.

Except that all sounds good.

---

### Post by 89c51 on 2006-08-07
because i have trouble with firestarter and NetworkManager i want to ask a question before i go with your script

i want to make it work with both eth0 (ethernet) and eth1 (wireless) whithout having to modify it 

can i just ad the same rules for eth0 and eth1 in the same file???
will there be any problem when i go from ethernet to wireless ??(nm does this automaticaly when you plug or unplug an ethernet cable)

---

### Post by frodon on 2006-08-07
Yes you shouldn't have any problems, to make the rules works for both eth0 and eth1 just remove all the "-i eth0" options thus the rules will be applied on all the network controllers you have.

---

### Post by 89c51 on 2006-08-07
> **frodon said:**
> Yes you shouldn't have any problems, to make the rules works for both eth0 and eth1 just remove all the "-i eth0" options thus the rules will be applied on all the network controllers you have.


thanks for the lightning fast answer :-D  

Merci beacoup ;)

---

### Post by 89c51 on 2006-08-07
OK it worked

it only needed to add the loopback in the firewall bash

whithout it it was stopping when it was trying to start gnome

Thanks Again

excelent HOWTO

---

### Post by mtron on 2006-08-08
> **frodon said:**
> If you have a hardware firewall an additional software firewall is not really needed IMO.
About your script, the rules about the TRUSTED chain are useless because you send nothing to the TRUSTED chain.

Thanks for the tips & your help! 

cheers 

mtron

---

### Post by machangbing on 2006-08-08
I have deployed my firewall following your instruction, and it works very well, thx !!!:p

---

### Post by bslima on 2006-09-11
Well,
Sorry about the english but im from brazil :)
I have 2 things to ask:
1) I used your script did all the things,
but when i logged into gnome it just crash, doesnt enter gnome for nothing.
Why ? Does anyone else have this problem ?

2) I have a eth0 interface where my ppp0 connection arrives,
and i have a eth1 interface pluged in the hub, for sharing my ppp0 connection.
I managed to share the connection, but when i used your script it just stop shaaring. What can i do to continue sharing my ppp0 connection but still have  this nice firewall you built.

Thanks for any help you can give me :)

---

### Post by frodon on 2006-09-12
1) If you have problems add the loopback access :```
# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
[B]# Allow loopback access
iptables -A FIREWALL -i lo -j ACCEPT [/B]
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP
```

2) My script prevent all FORWARD packets which explains why your connection sharing don't work anymore.
Just remove this line to leave all the FORWARD packets as they were before : ```
iptables -A FORWARD -j DROP
```If you trust your network on eth1, i guess it's a local network, there's no need to apply the rules on eth1 in my opinion.

---

### Post by takin on 2006-09-12
I'm struggling with my firewall, though I'm using my own script.  I originally made it for use with DHCP on a PPP interface and static addresses on an internal wireless LAN.  Later, we moved to a static address from the ISP on an ethernet connection and it was fine.  But then I upgraded to Dapper and everything went Windowsy.

Dapper is known for not handling static IP for wireless routers, so now I have to use DHCP on the LAN, but then my firewall doesn't pass the traffic through.  So I have to switch back to static after making the wireless connection and run my firewall manually.  Then it all works, but next time I boot up, I'm in static, so I have to go through the whole process again.

How can I get it to pass traffic from DHCP addresses on the LAN side to a static address on the ISP side?  And why does it matter that it's DHCP on the LAN side?

```
#!/bin/sh
#Firewall for home network

#configuration
INET_IP="202.89.26.82"
INET_IF="eth0"
INET_BCAST="202.89.26.255"

LAN_IP="192.168.0.29"
LAN_IF="eth1"
LAN_BCAST="192.168.0.255"

SELF_IP="127.0.0.1"
SELF_IF="lo"
SELF_BCAST="127.0.0.255"

IPTABLES="/sbin/iptables"
MOD="/sbin/modprobe"

#flush tables
$IPTABLES --flush
$IPTABLES -t nat --flush
$IPTABLES --delete-chain
$IPTABLES -t nat --delete-chain

#modules
$MOD ipt_LOG
$MOD ipt_REJECT
$MOD ipt_MASQUERADE
$MOD ip_conntrack_amanda
$MOD ip_conntrack_irc
$MOD ip_conntrack_ftp
$MOD ip_conntrack_tftp
$MOD ip_nat_amanda
$MOD ip_nat_irc
$MOD ip_nat_ftp
$MOD ip_nat_tftp
$MOD ip_nat_snmp_basic
$MOD iptable_nat

#defaults to drop everything
$IPTABLES -t filter -P INPUT ACCEPT
$IPTABLES -t filter -P OUTPUT ACCEPT
$IPTABLES -t filter -P FORWARD ACCEPT
$IPTABLES -t nat -P PREROUTING ACCEPT
$IPTABLES -t nat -P OUTPUT ACCEPT
$IPTABLES -t nat -P POSTROUTING ACCEPT
$IPTABLES -t mangle -P PREROUTING ACCEPT
$IPTABLES -t mangle -P INPUT ACCEPT
$IPTABLES -t mangle -P FORWARD ACCEPT
$IPTABLES -t mangle -P OUTPUT ACCEPT
$IPTABLES -t mangle -P POSTROUTING ACCEPT

#INPUT FILTER
#allow all packets from local addresses to pass
$IPTABLES -t filter -A INPUT -i $SELF_IF -j ACCEPT
$IPTABLES -t filter -A INPUT -i $LAN_IF -j ACCEPT

#allow established and related packets from internet
$IPTABLES -t filter -A INPUT -i $INET_IF -m state --state ESTABLISHED,RELATED -j ACCEPT

#allow trace-route returns (ICMP TTL=0)
$IPTABLES -t filter -A INPUT -i $INET_IF -p ICMP --icmp-type 11 -j ACCEPT

#log all other packets
$IPTABLES -t filter -A INPUT -m limit --limit 3/minute --limit-burst 3 \
-j LOG --log-level DEBUG --log-prefix "IPT INPUT packet died: "

#FORWARD FILTER
#forward all packets from local addresses
$IPTABLES -t filter -A FORWARD -i $SELF_IF -j ACCEPT #not sure if this is necessary
$IPTABLES -t filter -A FORWARD -i $LAN_IF -j ACCEPT

#accept the return packets
$IPTABLES -t filter -A FORWARD -i $INET_IF -m state --state ESTABLISHED,RELATED -j ACCEPT

#log all other packets
$IPTABLES -t filter -A FORWARD -m limit --limit 3/minute --limit-burst 3 \
-j LOG --log-level DEBUG --log-prefix "IPT FORWARD packet died:"

#OUTPUT FILTER
#send all packets from local addresses
$IPTABLES -t filter -A OUTPUT -s $SELF_IP -j ACCEPT
$IPTABLES -t filter -A OUTPUT -s $LAN_IP -j ACCEPT
$IPTABLES -t filter -A OUTPUT -s $INET_IP -j ACCEPT # is this safe? it should already be filtered on INPUT, right?

#log all other packets
$IPTABLES -t filter -A OUTPUT -m limit --limit 3/minute --limit-burst 3 \
-j LOG --log-level DEBUG --log-prefix "IPT OUTPUT packet died:"

#DHCP ADDRESS TRANSLATION
#use masqurading to allow many pcs to access ISP with one dynamic IP address
$IPTABLES -t nat -A POSTROUTING -o $INET_IF -j MASQUERADE

#what's the command for a static ISP address?
#$IPTABLES -t nat -A POSTROUTING -s 192.168.0.0 -j SNAT -o eth0 --to-source $INET_IP  I've tried this, but it doesn't work.  why?

#enable packet forwarding by kernel
echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/ip_dynaddr

```

---

### Post by handy on 2006-10-20
Thanks **Frodon**, great HowTo, quick & easy to follow, & works perfectly! :KS 

I've just started using **BitTorent**, so I thought that perhaps now was a good time to secure my system.

I used your HowTo from the following link:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

& tested it at [Shields Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2") Faultless results on all tests. :) 

The **Sygate** tests rejected my OS, so they must have recently changed their ways?

---

### Post by Malakia on 2006-10-20
I would like to know how to add tor and privoxy, so they will work with the firewall. They run perfectly without the firewall but with it they don't work at all and time out.

---

### Post by frodon on 2006-10-20
I don't use these apps but i guess you could find useful information on how use them with a firewall on their websites.
I guess they should use some specific ports , by the way did you enable the loopback access ?
If not add this line in your script with the other rules for the FIREWALL chain : ```
iptables -A FIREWALL -i lo -j ACCEPT
```

---

### Post by handy on 2006-10-21
> **handy said:**
> Thanks **Frodon**, great HowTo, quick & easy to follow, & works perfectly! :KS 

I've just started using **BitTorent**, so I thought that perhaps now was a good time to secure my system.

I used your HowTo from the following link:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

& tested it at [Shields Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2") Faultless results on all tests. :) 

The **Sygate** tests rejected my OS, so they must have recently changed their ways?

Interestingly, after rebooting (a day later) I found that I could open but not ***use*** firefox.  I could not run the RMB *** as root scripts***, or access the Gnome Networking dialogue.

*After adding the 2 lines of **loopback code** found in previous posts to the **firewall.bash** script everything seems to be as good as gold!* :KS

Great when its that easy, though I don't understand what I did... :-k

---

### Post by frodon on 2006-10-21
I guess i should add this line in the default configuration, basically it allow access to yourself, i know my explanation isn't really clear.

Glad it works for you :)

---

### Post by handy on 2006-10-21
> **frodon said:**
> I guess i should add this line in the default configuration, basically it allow access to yourself, i know my explanation isn't really clear.

Glad it works for you :)

I just set up my 2nd machine & could not load the desktop while the Firewall was running.  So, I added the 2 loopback lines & it is all great now... :KS

I'll say thanks again **Frodon**, this is such a  nice tidy solution! :cool:

---

### Post by frodon on 2006-10-21
Thanks for the feedback all, i added these lines in the default configuration i gave in my guide.

---

### Post by linuxyousertoetags on 2006-11-08
hey thanks for the amazingly easy guide to iptables. i noticed after setting up using your default configuration that my internet speed is slowed drastically to like 5 kb/s im wondeirng if u know anything about this? my internet still works just extremely slow thanks man

---

### Post by frodon on 2006-11-09
It's strange, it shouldn't change anything.

When you say "my internet speed is slowed drastically to like 5 kb/s", are you talking of web browsing, bittorent, ...
Could you give precisions ?

---

### Post by linuxyousertoetags on 2006-11-09
with firewallon it takes forever to sign on to amsn, firefow to load, bittorrent speeds at 5k when normally way higher. but if i turn it off they go back to normal speed

---

### Post by Draaku on 2006-11-21
Hello, thanks for your firewall config. I have it running on my server, but I would like to allow some icmp (ping) to come through. could you tell me how I could go about doing that?

here is what I try to input but it still blocks ping:

# Allow some ICMP (ping)
iptables -A INPUT -p icmp --icmp-type 0 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 3 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 11 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
iptables -A INPUT -p icmp -j DROP

---

### Post by frodon on 2006-11-22
To allow ping, you can use this line :
```
iptables -A TRUSTED -p icmp -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
```If you want to allow ping but limit the ping request numbers to avoid flood you do it like that :
```
iptables -A TRUSTED -p icmp -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -p icmp -m state --state NEW -m limit --limit 10/min -j ACCEPT
```

---

### Post by argusBR on 2006-12-03
I share my internet connection with a Windows machine. I had to comment the line
```
#iptables -A FORWARD -j DROP
```
so that it would work.

After that point, I have been trying to make my DansGuardian+Squid work with a set of rules I used before. They are working in my Ubuntu machine, but the Windows machine can't access the web any more. Maybe it has something to do with the place of the script where I inserted my content filter rules? 

This is my modified script:
```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP
# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL

###FORWARD SECTION BEGINS
# Forward only established and related connections to the lan for incoming packets
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Forward all OUT connections from the lan 
iptables -A FORWARD -o eth0 -i eth1 -j ACCEPT 
# hide computers behind the firewall 
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward 
#then DROP all the rest 
#iptables -A FORWARD -j DROP
###FORWARD SECTION ENDS


###CONTENT FILTER RULES BEGIN
#The idea is that both Squid and Dansguardian processes are owned by user squid,
#so that only Squid accesses port 80, and only Dansguardian accesses Squid (port 3128).
#Dansguardian listens to port 8080.

#User "squid" accesses Internet and Squid Proxy
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT

#All other users forwarded to Dansguardian
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j REDIRECT --to 8080
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080

#If someone tries to access Squid directly he is forwarded to Dansguardian
iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 8080
###CONTENT FILTER RULES END


# Allow https
iptables -A TRUSTED -i eth1 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i eth1 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i eth1 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

---

### Post by durus on 2007-01-01
I have some questions about how this works: 
```
#!/bin/bash
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```
Do the code run row by row, but ignoring the chains (that chains is like functions that has to be called) ?
So i can move this code before all chain things.
```
# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP
```
I do use both eth0 and eth1. eth1 always against internet and eth0 sometimes against internet  and sometimes in my own lan. As it is configured right now, will all connections through eth1 be blocked, because of now roll for it ? and where in the code should i call say my new chain WLANCONNECTION that would handle eth1 ?

Thank you for helping me

---

### Post by frodon on 2007-01-01
The iptables lines are run one by one row by row so you shouldn't modify the order of the lines.

About your eth0 and eth1 interfaces, if you remove the "-i eth0" option on all the lines then the rules we be applied on all the network devices you have on your computer.

---

### Post by durus on 2007-01-01
ok, but the thing is that i want to have different roles for the cards. Sometimes i have internet on one of them and lan on the other, then i only want to send send all packets to LAN for one of the cards. like this.
# 1. normal, only one of them connected
eth1 sends all packets to TRUSTED 
eth0 sends all packet to TRUSTED

# 2. lan and intenet
eth1 sends all packets to TRUSTED 
eth0 send all packet to LAN // I only wants to change this when i'm connected to the lan

And the thing that it is read row by row, i cant understand this, first the chain FIREWALL is read, and then we are sending all input packets back to chain FIREWALL again ? Why send back packets were we have been ? are you shore that it is not read like this, but written in the other way for easy reading ?

```

#!/bin/bash
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

#################
[COLOR="Red"]# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL #JUMPS to FIREWALL ?
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP [/COLOR]
##############

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED # JUMPS to TRUSTED ?

################
[COLOR="Red"]# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT[/COLOR]
###############

# DROP all other packets
iptables -A FIREWALL -j DROP


# End message
echo " [End iptables rules setting]"
```

---

### Post by sooqing on 2007-01-04
I am a newbie to firewall. I like to ask if it is safe for me to continue using the following rules for ONLY web browsing using my house PC. So far, I have not faced any problem after 6 months of usage and my PC passed the Shield Up test.

Thanks you!

===========

iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT

---

### Post by CameronCalver on 2007-01-16
Hello i tryed to set up iptables with this website but i think i made some mistakes and i would like to clear it and start again how do i clear iptable rules and start again

---

### Post by marx2k on 2007-01-19
This is driving me up a wall.

I cannot get any specific ports open no matter what I do!! It's really getting to me.

All I want to do (to start with) is open port 64738 tcp/udp

Here is what I have for the script (everything is run on eth1)

```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth1 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
#iptables -A TRUSTED -i eth1 -p udp -m udp --dport 5349 -j ACCEPT
#iptables -A TRUSTED -i eth1 -p udp -m udp --dport 5351 -j ACCEPT
#iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow generic port for testing
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 64738 -j ACCEPT
iptables -A TRUSTED -i eth1 -p udp -m udp --dport 64738 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

This is IPTables with the firewall running:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:64738 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:64738 

```

I will even post the corresponding IPTables from my router which is forwarding 64738 to this IP:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp dpt:webcache 
DROP       tcp  --  anywhere             anywhere            tcp dpt:www 
DROP       tcp  --  anywhere             anywhere            tcp dpt:https 
DROP       tcp  --  anywhere             anywhere            tcp dpt:telnet 
DROP       tcp  --  anywhere             anywhere            tcp dpt:69 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
logdrop    0    --  anywhere             anywhere            state INVALID 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1461:65535 TCPMSS set 1460 
lan2wan    0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
logaccept  udp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 udp 
logaccept  tcp  --  anywhere             Commodore64         tcp dpt:64738 
logaccept  udp  --  anywhere             Commodore64         udp dpt:64738 
TRIGGER    0    --  anywhere             anywhere            TRIGGER type:in match:0 relate:0 
trigger_out  0    --  anywhere             anywhere            
logaccept  0    --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain advgrp_1 (0 references)
target     prot opt source               destination         

Chain advgrp_10 (0 references)
target     prot opt source               destination         

Chain advgrp_2 (0 references)
target     prot opt source               destination         

Chain advgrp_3 (0 references)
target     prot opt source               destination         

Chain advgrp_4 (0 references)
target     prot opt source               destination         

Chain advgrp_5 (0 references)
target     prot opt source               destination         

Chain advgrp_6 (0 references)
target     prot opt source               destination         

Chain advgrp_7 (0 references)
target     prot opt source               destination         

Chain advgrp_8 (0 references)
target     prot opt source               destination         

Chain advgrp_9 (0 references)
target     prot opt source               destination         

Chain grp_1 (0 references)
target     prot opt source               destination         

Chain grp_10 (0 references)
target     prot opt source               destination         

Chain grp_2 (0 references)
target     prot opt source               destination         

Chain grp_3 (0 references)
target     prot opt source               destination         

Chain grp_4 (0 references)
target     prot opt source               destination         

Chain grp_5 (0 references)
target     prot opt source               destination         

Chain grp_6 (0 references)
target     prot opt source               destination         

Chain grp_7 (0 references)
target     prot opt source               destination         

Chain grp_8 (0 references)
target     prot opt source               destination         

Chain grp_9 (0 references)
target     prot opt source               destination         

Chain lan2wan (1 references)
target     prot opt source               destination         

Chain logaccept (4 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            state NEW LOG level warning tcp-sequence tcp-options ip-options prefix `ACCEPT ' 
ACCEPT     0    --  anywhere             anywhere            

Chain logdrop (1 references)
target     prot opt source               destination         

LOG        0    --  anywhere             anywhere            state NEW LOG level warning tcp-sequence tcp-options ip-options prefix `DROP ' 
LOG        0    --  anywhere             anywhere            state INVALID LOG level warning tcp-sequence tcp-options ip-options prefix `DROP ' 
DROP       0    --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `WEBDROP ' 
REJECT     tcp  --  anywhere             anywhere            tcp reject-with tcp-reset 

Chain trigger_out (1 references)
target     prot opt source               destination         

```

(Commodore64 = this computer - to the router, 192.168.1.100)

However, even if I scan 127.0.0.1 with NMap, it says that the port 64738 tcp/udp is closed.
Any port scanning service on the web says it is closed also.

I cannot seem to open this or any port I specify to the router and it's driving me crazy. Can anyone offer ANY help to me on this?

---

### Post by frodon on 2007-01-19
It is the goal of the firewall to show your ports as closed, that don't mean you can't use this port ;)

---

### Post by marx2k on 2007-01-19
If an external application needs to reach me at a certain port (say... 64738) as in, an application on MY side needs to be listening at a certain port -- shouldn't this port be 'open'? 

That's what I'm trying to accomplish.  Let's say I need Azureus to use this port for incoming connections.  If a web based port scanner can't see this port as open, can remote Azureus clients connect to it?

---

### Post by marx2k on 2007-01-19
Strangely enough I've even taken down completely the firewall so iptables looks like this:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

and I still cant connect to any ports on my own system that I want to be open. 
I'm connected only to the cable modem and if I scan my own external IP with NMAP, it says:

All 65535 scanned ports on xx-xx-xx-xx.dhcp.mdsn.wi.charter.com (xx.xx.xx.xx) are closed

If I scan TCP internally (127.0.0.1), NMAP says:
All 65535 scanned ports on localhost (127.0.0.1) are closed

If I scan UDP internally, NMAP floods me with:
sendto in send_ip_packet: sendto(3, packet, 28, 0, 127.0.0.1, 16) => Operation not permitted

If I do a SYN scan on all of my ports internally:
```

Interesting ports on localhost (127.0.0.1):
Not shown: 65523 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
725/tcp   open  unknown
902/tcp   open  iss-realsecure-sensor
2049/tcp  open  nfs
2208/tcp  open  unknown
37570/tcp open  unknown
44509/tcp open  unknown
52137/tcp open  unknown

```

the unknown ports, I have no idea what those are and they can be seen externally also (this is with firewall down and a blank iptables)

Now when I bring the firewall up, IPTables looks like this:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:2234:2239 
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:64738 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:64738 

```

To reflect my slightly modified script:
```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

#Allow incoming Nicotine (Soulseek)
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 2234:2239 -j ACCEPT

# Allow https
iptables -A TRUSTED -i eth1 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
#iptables -A TRUSTED -i eth1 -p udp -m udp --dport 5349 -j ACCEPT
#iptables -A TRUSTED -i eth1 -p udp -m udp --dport 5351 -j ACCEPT
#iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow generic port for testing
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 64738 -j ACCEPT
iptables -A TRUSTED -i eth1 -p udp -m udp --dport 64738 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

And now the firewall is successfully refusing connections for those open ports as according to an external web based port scanner.
INTERNALLY, I still see those ports open since NMAP still gives me:
```

PORT      STATE SERVICE
22/tcp    open  ssh
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
725/tcp   open  unknown
902/tcp   open  iss-realsecure-sensor
2049/tcp  open  nfs
2208/tcp  open  unknown
37570/tcp open  unknown
44509/tcp open  unknown
52137/tcp open  unknown

```

but of course I dont have those ports open in my script so that is correct.

When I do use the script to open any chosen ports of those listed in that list, external web based apps DO see those ports (I guess my system gives a ping reply on those ports) -- so a few questions here..

Where on my system do I set what ports my system should be listening on, how do I find out why those 'unknown' ports are open, and how do I get an external web app to actually see that the port that I want to be open for external connections IS open? 

Ideally, I want port(s) 2234 through 2239 open as well as 64738

In Windows, if I dropped the firewall and basically just forwarded those ports in my router to the PC, the ports would show as being open by external web apps.  I would like that simple functionality here, but also to be able to configure the ports in the firewall script and it doesnt seem like it's happening now because if I open a port in the firewall, it definately doesnt show the port as being open externally... I guess the system needs to be 'listening' on those ports, so that's what I need to do now.

Any suggestions? (Was up pulling my hair out until 4:30 AM last night about this)

---

### Post by marx2k on 2007-01-20
Bumping this a bit since an answer on this is pretty urgent.  Anyone please let me know how to properly configure the system to create the situation I described? 

I mean, basically I want to have a port open to the outside world as seen by external apps (like SoulSeek peers) so I can connect directly with people.. at this point I cannot :(

---

### Post by marx2k on 2007-01-20
I fixed the problem. All this hair pulling and it turned out to be the smallest discrepancy (which probably amounts to a lot...)

The line I had previously:
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 2234:2239 -j ACCEPT

The change that made it work:
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 2234:2239 -j ACCEPT

I changed sport to dport

and now it works.  Who'da thunk it.

Can someone give a description as to the diff between the two?

---

### Post by pau on 2007-01-20
ahem...

can anybody adapt the script for me to block ALL incoming services but imap? :-\"

---

### Post by marx2k on 2007-01-20
And one final question.  How does script work out with MoBlock which also plays with IPTables?

---

### Post by marx2k on 2007-01-21
> **pau said:**
> ahem...

can anybody adapt the script for me to block ALL incoming services but imap? :-\"

I think this should work for you:
```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow imap
iptables -A TRUSTED -i eth1 -p udp -m udp --sport 143 -j ACCEPT
iptables -A TRUSTED -i eth1 -p tcp -m tcp --sport 143 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

---

### Post by frodon on 2007-01-21
> **marx2k said:**
> And one final question.  How does script work out with MoBlock which also plays with IPTables?Hum, it is a bad idea to use 2 different scripts to set your iptables firewall, i advice you to choose the one you prefer and use only this one.

---

### Post by marx2k on 2007-01-21
> **frodon said:**
> Hum, it is a bad idea to use 2 different scripts to set your iptables firewall, i advice you to choose the one you prefer and use only this one.

Well, the problem is that one script lets me set my firewall up easily (this one) and one keeps the MPAA/RIAA off my back by blocking selected IPs downloaded through  a daily list ( [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) )

I'm just wondering if MoBlock would be putting an added layer of protection by filtering IP's on top of this script or if it would completely break this script.

I will try to install it on Monday and see how it goes.  If anything, I can always remove it and restart this script and it will re-lay-down the correct iptables for me :)

---

### Post by frodon on 2007-01-21
Ha ok, if it does only IP blocking i think there's no problem to use both, so i would say that you shouldn't get any problems.

---

### Post by marx2k on 2007-01-21
I will give it a shot and report back because if it actually doesn't interfere, that'd be great since I find this script amazingly useful (Actually, a lot more useful and configurable in less time than firestarter - and I dont need another program to take up memory space when using this)

---

### Post by marx2k on 2007-01-24
Ok so it seems like they play well together if you start moblock AFTER the firewall script ---

Here is IPTables after the firewall script...
```

marx2k@Commodore-64:~/source/nicotine+$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:2234:2239 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:64738:64739 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:64738:64739 
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 

```

And here it is after moblock is run...
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_IN  all  --  anywhere             anywhere            state NEW 
FIREWALL   all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
MOBLOCK_FW  all  --  anywhere             anywhere            state NEW 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
MOBLOCK_OUT  all  --  anywhere             anywhere            state NEW 

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain MOBLOCK_FW (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_IN (1 references)
target     prot opt source               destination         

ACCEPT     all  --  anywhere             qb-in-f109.google.com 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain MOBLOCK_OUT (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             199.203.34.59       
ACCEPT     all  --  anywhere             198.150.221.249     
ACCEPT     all  --  anywhere             198.150.221.250     
ACCEPT     all  --  anywhere             qb-in-f109.google.com 
ACCEPT     all  --  anywhere             tricia.gtlib.gatech.edu 
ACCEPT     all  --  anywhere             mail.charter.net    
ACCEPT     all  --  anywhere             69.28.186.121       
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 0

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:2234:2239 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:64738:64739 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:64738:64739 
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 

```

So it looks like they are playing well together!

Now the only thing Im wondering, with this setup...that although I want traffic to come through on port 64738, 64739... (and it is coming through now) ...wil it still filter through moblock? I think it will. What do you, the reader, think?

---

### Post by SundaY82 on 2007-01-25
Hi!

I got the advice from another thread that i should post here about my iptables problems. So instead of retyping all here is the post, feel free to answer here or in the other post.

[http://www.ubuntuforums.org/showthread.php?p=2059884](http://www.ubuntuforums.org/showthread.php?p=2059884)

Would really appreciate all the help i can get.

---

### Post by frodon on 2007-01-25
> **marx2k said:**
> Now the only thing Im wondering, with this setup...that although I want traffic to come through on port 64738, 64739... (and it is coming through now) ...wil it still filter through moblock? I think it will. What do you, the reader, think?It depends on how moblock filter, if it filter on a IP basis then opening ports won't modify the moblock filtering.

---

### Post by frodon on 2007-01-25
> **SundaY82 said:**
> Hi!

I got the advice from another thread that i should post here about my iptables problems. So instead of retyping all here is the post, feel free to answer here or in the other post.

[http://www.ubuntuforums.org/showthread.php?p=2059884](http://www.ubuntuforums.org/showthread.php?p=2059884)

Would really appreciate all the help i can get.Your forwarding problem is not clear for me and you don't give the whole script you use.
About forwarding udp and tcp as far as i know there's no other solution than writing aline for each protocol.

---

### Post by adamonline on 2007-01-28
Hello, this is a great tool!  I send people to it all the time from IRC.

Here's a question that I figured I'd find answered in these last 9 pages, but did not: How do I allow SSH in?

As it is, on my ssh server, /etc/firewall.bash is just like in the example, but I have added this line between the sections labeled "# Allow https" and "# Allow amule".
```

# Allow SSH
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
```

I've found a few resources from Google about configuring iptables for SSH, but I get confused because I don't fully understand about chains and how they're used in this script.

I know the problem is somewhere in /etc/firewall.bash, because when I stop the firewall by typing "sudo /etc/init.d/firewall stop", I can SSH into the machine.

Can anyone tell me how to get SSH working?

Thank you!

---

### Post by frodon on 2007-01-28
Be careful ssh use both tcp and udp so you need to add a line for the udp protocol on port 22. So add the following line and tell me if it works now, if not i'll search a little bit :
```
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22 -j ACCEPT
```

---

### Post by adamonline on 2007-01-28
Frodon,

Thanks for the reply.

I added that line and it still doesn't work.

iptables -L shows both of those entries under the TRUSTED chain, if that helps.

I've also noticed that my http server (thttpd, on the same machine) is no longer accessible, so I added port 80 in another two entries, one for tcp and one for udp, but it's still not working, either.  But it, too, works fine when the script is stopped.

I've been decoding this script using the iptables man page (I'm not fluent in iptable speak yet) and it all seems to _me_ like it should work!  If you do have any further suggestions, I'll much appreciate them :)

-ADAM

---

### Post by dustman on 2007-01-28
Hi, I have installed a DC Client, Linux DC ++  version 0.674, and when I want to connect to a hub with it, I don't conect directly to the internet, but I use a passive connection, due to the fact that my internet comes though my roommate's  computer( who has shared his internet connection with me). Because of this I cannot set Linux DC to use certain ports, so I don't think I can set the ports for this program though the iptables. Tried with firestarter and guarddog, but haven't succeeded...:(....The thing is that Linux DC connects to the hub, but when somebody tries to get something from me, the application shutsdown my internet connection and I have to reboot again and again and again....Can anyone help me with this, cause I'm a little lost...:(

---

### Post by frodon on 2007-01-28
> **adamonline said:**
> Frodon,

Thanks for the reply.

I added that line and it still doesn't work.

iptables -L shows both of those entries under the TRUSTED chain, if that helps.

I've also noticed that my http server (thttpd, on the same machine) is no longer accessible, so I added port 80 in another two entries, one for tcp and one for udp, but it's still not working, either.  But it, too, works fine when the script is stopped.

I've been decoding this script using the iptables man page (I'm not fluent in iptable speak yet) and it all seems to _me_ like it should work!  If you do have any further suggestions, I'll much appreciate them :)

-ADAMYes it should work, replace the --dport option by --sport just to try if it isn't the issue but it should have worked like that even for your http server.

Paste your whole firewall script here, i'll have a look to it and see if it miss something from what i know.

---

### Post by adamonline on 2007-01-28
> **frodon said:**
> Yes it should work, replace the --dport option by --sport just to try if it isn't the issue but it should have worked like that even for your http server.

Paste your whole firewall script here, i'll have a look to it and see if it miss something from what i know.

Here's the script:
```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# I added this for debugging purposes, don't know entirely what it means though...
iptables -A FIREWALL -i eth0 -m state --state NEW,INVALID -j ACCEPT

# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT

# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow SSH # I added this, and...
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 22 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# Allow httpd # ...I added this...
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 80 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

I added a few things, as you can see.  Accepting NEW and INVALID packets (for debugging purposes), allowing ssh port 22, and allowing http port 80; both udp and tcp, and both sport and dport.

I am using the default ports for both the http and ssh daemons.

Any thoughts, Frodon?  And thanks again :D

EDIT: apt-get update didn't work, either!  But did when I disabled the firewall.  That's weird, it works fine on THIS computer and I have the same script, but without the changes you see here.

Here's the output of iptables -L:
```

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state INVALID,NEW 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp spt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5349 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5351 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5348 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp spt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:www 


```

---

### Post by adamonline on 2007-01-28
> **dustman said:**
> Hi, I have installed a DC Client, Linux DC ++  version 0.674, and when I want to connect to a hub with it, I don't conect directly to the internet, but I use a passive connection, due to the fact that my internet comes though my roommate's  computer( who has shared his internet connection with me). Because of this I cannot set Linux DC to use certain ports, so I don't think I can set the ports for this program though the iptables. Tried with firestarter and guarddog, but haven't succeeded...:(....The thing is that Linux DC connects to the hub, but when somebody tries to get something from me, the application shutsdown my internet connection and I have to reboot again and again and again....Can anyone help me with this, cause I'm a little lost...:(

Hi Dustman,

I don't know if I can help you too greatly since I'm not familiar with DC.  It sounds to me though that your internet packets have to go through your roommate's firewall before they even get to your firewall.  So (I THINK) you could open all ports on your firewall and still not get anything that can't get through his.  He can open the ports that you need to receive on _his_ firewall, and in theory, you could then access those ports.  If he doesn't want to leave that port open on his computer, he can set it so the port gets forwarded to your computer.  If he's using Windows, I don't know how that could be done.  If he's using Linux, well, I'll do the best I can with my limited understanding: 

If he's using Linux AND this script, he would have to change the line that blocks port forwarding from **iptables -A FORWARD -j DROP** to **iptables -A FORWARD -j ACCEPT** and add a block like this in the area just before "# End message":

```
# Allow DC
# These will allow all traffic to your computer on the specified port
iptables -A TRUSTED -i eth0 -o eth1 -p udp -m udp -sport <port#> -j ACCEPT
iptables -A TRUSTED -i eth0 -o eth1 -p tcp -m tcp -sport <port#> -j ACCEPT
iptables -A TRUSTED -i eth0 -o eth1 -p udp -m tcp -dport <port#> -j ACCEPT
iptables -A TRUSTED -i eth0 -o eth1 -p tcp -m tcp -dport <port#> -j ACCEPT

```

This assumes his eth0 faces the internet, and his eth1 faces your computer. It's a gross method, as it probably opens more ports on more protocols than needed, but it might work.  I believe that it will only allow the packets to go through that port that are en route to your machine, due to the "-o eth1", so he should still be secured on that port.  As an added boost to his security, he can specify that only things en-route to your ip are accepted on those protocols and ports, by adding the parameter **-d your.ip.addy.here**. If he's just using Linux without this script, he should replace all the **TRUSTED** in the above code block with **FORWARD** and enter the lines one by one at the command line.

Again, I would like to stress that I know just enough to be dangerous and can't even get my own problem fixed :D But I've been doing a helluva lot of research on iptables and that is the best advice I can give; hopefully it will make a good starting point and if anything's incorrect there somebody can chime in.

If possible, you can try disabling his firewall for a short period and seeing if you can then receive packets on the port you need.  If so, then you know his firewall is stopping the packets from even reaching your firewall :)  

As for why your internet connection stops and you have to restart... Well, that sounds unrelated to this script.  It could be a bug in Linux DC; something that doesn't handle closed ports well.  I don't know, that's the part I can't help with ;)

Good luck!

-ADAM

---

### Post by RedSquirrel on 2007-01-28
This guide was very helpful. I got everything up and running in just a few minutes and it works very well.

Thanks so much for writing this!  :D

> **frodon said:**
> [COLOR=Red][SIZE=2]It should be easier to read the guide on the UDSF[/SIZE][/COLOR] : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)



**[SIZE=2]3.1-The firewall script [/SIZE]**

**This exemple will fit the needs of most users, it blocks all incoming and forward traffic and allows : web browsers, https, amule, bittorent, ftp, gaim, IRC, mail protocols (smtp, pop, imap).**
Blocking outgoing access is not needed (incoming is enough).

* We create 2 chain the one called FIREWALL and the second is called TRUSTED 

    **FIREWALL chain** : this chain will allow related and established incoming connection (eth0 interface), then send all other packets to the TRUSTED chain and DROP all the rest. We will send in this chain all INPUT packets. 
    **TRUSTED chain** : In this chain you will add all the ports you may need to open depending on what you use on your computer. 

Now create the firewall script: 

```
sudo gedit /etc/firewall.bash
```

Minor correction:

I would use gksudo for graphical editors:

```
gksudo gedit /etc/firewall.bash
```I know it likely won't harm anything to use *sudo,* but it's just in the interest of being consistent: terminal commands use sudo; graphical programs use gksudo.

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by galeron on 2007-01-28
Hi,

I'm having some problems with my iptables configuration and outgoing SMTP (outgoing mail is sent to an external SMTP server).

My router is an Ubuntu router just set up recently. All the computers in my network can receive email, but cannot send. The settings are fine, and I know it's the router that's dropping my packets, because syslog shows that it is blocking SMTP packets.

The output of "iptables -L" is shown below

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/24          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
tcp_packets  tcp  --  anywhere             anywhere            
udp_packets  udp  --  anywhere             anywhere            
icmp_packets  icmp --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT INPUT packet died: ' 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/24          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
tcp_packets  tcp  --  anywhere             anywhere            
udp_packets  udp  --  anywhere             anywhere            
icmp_packets  icmp --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT INPUT packet died: ' 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:smtp dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:5999:x11 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT FORWARD packet died: ' 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT FORWARD packet died: ' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  localhost            anywhere            
ACCEPT     all  --  10.0.0.2             anywhere            
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT OUTPUT packet died: ' 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  localhost            anywhere            
ACCEPT     all  --  10.0.0.2             anywhere            
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT OUTPUT packet died: ' 
ACCEPT     tcp  --  10.0.0.0/24          anywhere            tcp spts:1024:65535 dpt:smtp 

Chain allowed (9 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       tcp  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       tcp  --  anywhere             anywhere            

Chain bad_tcp_packets (6 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            tcp flags:SYN,ACK/SYN,ACK state NEW reject-with tcp-reset 
LOG        tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW LOG level warning prefix `New not syn:' 
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW 
REJECT     tcp  --  anywhere             anywhere            tcp flags:SYN,ACK/SYN,ACK state NEW reject-with tcp-reset 
LOG        tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW LOG level warning prefix `New not syn:' 
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW 

Chain icmp_packets (2 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 

Chain tcp_packets (2 references)
target     prot opt source               destination         
allowed    tcp  --  anywhere             anywhere            tcp dpt:ftp 
allowed    tcp  --  anywhere             anywhere            tcp dpt:ssh 
allowed    tcp  --  anywhere             anywhere            tcp dpt:www 
allowed    tcp  --  anywhere             anywhere            tcp dpt:auth 
allowed    tcp  --  anywhere             anywhere            tcp dpt:ftp 
allowed    tcp  --  anywhere             anywhere            tcp dpt:ssh 
allowed    tcp  --  anywhere             anywhere            tcp dpt:www 
allowed    tcp  --  anywhere             anywhere            tcp dpt:auth 
allowed    tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:smtp 

Chain udp_packets (2 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp spt:domainAny help is appreciated.


```

Please help! Thanks :)

---

### Post by frodon on 2007-01-29
> **adamonline said:**
> 

I added a few things, as you can see.  Accepting NEW and INVALID packets (for debugging purposes), allowing ssh port 22, and allowing http port 80; both udp and tcp, and both sport and dport.

I am using the default ports for both the http and ssh daemons.

Any thoughts, Frodon?  And thanks again :D

EDIT: apt-get update didn't work, either!  But did when I disabled the firewall.  That's weird, it works fine on THIS computer and I have the same script, but without the changes you see here.

Try with this line for the ssh server :
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT

---

### Post by Prince James on 2007-03-07
hi guys ! what books do you recommend to get on iptables and chains ? as im really new to this and would like to write my own code but i dont have a clue what to do ! 

what i would like to desing a firewall to do all sorts of cmd's like stop ICMP so ppl can't ping me, start and stop FTP etc ! any help would be really nice

Thanks for ur time :guitar:

---

### Post by marx2k on 2007-03-15
Quick question... how do I allow a range of local IP's to connect to me? (192.168.1.*) ??

---

### Post by marx2k on 2007-03-19
Does anyone have a solution to this? Or is this not possible and I have to still work within the framework of opening per-port access even to private IP ranges for home networks?

---

### Post by frodon on 2007-03-20
Try to put a line to deny an IP and put "*" characters where it's needed, it never tested this but it may work.

---

### Post by zetetic on 2007-04-11
> **durus said:**
> 

And the thing that it is read row by row, i cant understand this, first the chain FIREWALL is read, and then we are sending all input packets back to chain FIREWALL again ? Why send back packets were we have been ? are you shore that it is not read like this, but written in the other way for easy reading ?

```

#!/bin/bash
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

#################
[COLOR="Red"]# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL #JUMPS to FIREWALL ?
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP [/COLOR]
##############

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED # JUMPS to TRUSTED ?

################
[COLOR="Red"]# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT[/COLOR]
###############

# DROP all other packets
iptables -A FIREWALL -j DROP


# End message
echo " [End iptables rules setting]"
```

Hi. I have the exact doubts expressed by durus on post #63 of this thread.

Can you please through some light on this subject?

cheers

---

### Post by frodon on 2007-04-11
Not sure to see what is not clear but i'll try to explain in a simple way (i hope :) )

First the firewall and trusted chain are created (e.g. iptables -N FIREWALL) **and not used yet**  then you describe the FIREWALL chain which is just the basic rule needed to allow the most wanted connections aka the one you open yourself and then the loopback traffic (when you connect to yourself, it's localhost) and finally send the rest (packets which are not allowed yet due the FIREWALL rules restrictions) to the TRUSTED chain for all the more specific rules.

At this step you can add the "iptables -A FIREWALL -j DROP" rule because you did all you wanted to do with the FIREWALL chain already so you just drop all in the FIREWALL chain at this step.

Then we specify to send all the INPUT packets through the FIREWALL chain (which is describe a little bit after). That means that all the INPUT packets will be handled by the FIREWALL chain.

And the last part are the specific TRUSTED rules that you may need to add depending what specific software you use on your computer.

When you start the firewall all the rules are set and the packets will follow the path you described. See iptables as a firewall description tool, lines are read one by one because you put them in a script manner but you can permute some parts to ease the reading if you wish although there's some obvious usage like to create the chain first before setting a rules on it otherwise the iptables command will return that the chain don't exist.

---

### Post by zetetic on 2007-04-11
Thank you for clarifying this issue. Now I understand the mechanics of your great script.

I have just one more question:

With a couple of simple modifications, II would like to use your own script, published here: 
The only problem is that I'm behind a router. My gateway IP address is 192.168.1.1. And my Ubuntu box IP address is 192.168.1.2.

 I would be very grateful if you could tell me what kind of changes (and where they should be introduced) I need to do to your own script, in order to have in consideration the fact that I'm behind the router.

I don't know if because of this situation I have to create another Chain of if it is only a matter of adding some line somewhere...

cheers

---

### Post by frodon on 2007-04-11
It should work like it is i think, BTW i never wanted to publish my own firewall script for obvious security reasons (at least not saying it is the script i use) so the link you put in your previous post don't exist anymore.
Try it it should work but this script filter outgoing traffic as well so it's in general less easier to use it because you need to open one by one almost each service port you use because of the outgoing traffic filtering.

---

### Post by zetetic on 2007-05-01
Hi Frodon

In your own script, which I'm following, you create a "Log Chain".
Can you please tell me where can I find all blocked connections (both input and output)?
Or what command shall I use in order to see all those blocked connections?

Note: it is very important to be able to check all blocked connections (both input and output), in order to see if I'm blocking any legitimate traffic and in order to detect any attacks.

cheers

---

### Post by frodon on 2007-05-01
I don't think the log will help you because it is a really really huge log, in my script i don't use the log generation because it takes ressources to create a log i don't need.
To generate the log replace all the DROP commands you want a log for by the LOG_DROP chain instead. Then open the /etc/syslog.conf file and add this to the bottom :
```
#IPTables logging
kern.debug;kern.info /var/log/firewall
```And restart the log daemon :
```
sudo /etc/init.d/sysklogd restart
```

---

### Post by zetetic on 2007-05-04
Thank you for your answer.
I'm struggling with this issue, but I still can't log any iptables messages.

I would like all block connections to be logged to /var/log/messages.

Perhaps the problem resides on the firewall script.
In order to try logging all blocked (dropped) connections I have been using the following entries on my firewall script:

#iptables -N LOG_DROP
#iptables -A LOG_DROP -j LOG --log-prefix '[IPTABLES DROP] : '
#iptables -A LOG_DROP -j DROP

Do you think there's something wrong with these entries? They are the only ones I use in order to try to log all block (dropped) connections to /var/log/messages.

Have a nice day.

---

### Post by frodon on 2007-05-05
Uncomment the lines (remove the # character) to allow the LOG_DROP chain creation and replace everywhere you put "DROP" by "LOG_DROP" instead so the packets will be send through the LOG_DROP chain instead of the DROP chain directly.

---

### Post by zetetic on 2007-05-06
Thanks for your reply.

I know what the "#" character mean and does. I tested the script without the "#". But because it didn't work I commented those lines. So when passing the rules to here, with the # character, I made a mistake, Sorry. :)

My intention is to know when something gets blocked against my willing.
If I replace DROP by LOG_DROP only the connections I decided on purpose to be blocked will be logged.


So, in the mean time I think I found a way to get what I want:

iptables -A INPUT -j LOG --log-prefix "In" --log-level 4 --log-tcp-options --log-ip-options
iptables -A OUTPUT -j LOG --log-prefix "Out" --log-level 4 --log-tcp-options --log-ip-options

These rules seem to work. I hope they don't introduce any security risks...

Cheers

---

### Post by juantao on 2007-05-28
I installed your scripts and after starting the firewall I could not log into my ftp server. After running the 'flush' script I could. darn.

---

### Post by frodon on 2007-05-28
Which port use your ftp server juantao ?

Eventually join your ftp server configuration file in the next post.

---

### Post by TyPhoon101 on 2007-06-17
i have been using ubuntu for a month now. i used your firewall script today and it worked excellently. thank you ! i have one problem though . i use an adsl connection and my NIC is configured to get address automatically via dhcp server when the modem is switched on,. now when the firewall is running when i put 192.168.1.1 in my browser's address bar, i can not get the modem configuration page. it says
> An error occurred while loading [http://192.168.1.1:]](http://192.168.1.1:])
Timeout on server
 Connection was to 192.168.1.1 at port 80
but if i stop the firewall , then i can get the usual login page. so what code do i need to put in the script ?
i figure it is i requesting connection at port 80 to ip 192.168.1.1 using tcp protocol ( correct me if i am wrong) via my ethernet card which is eth0. my internet interface is ppp0. so i should put
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT. besides this line , the firewall script is exactly as it is your example script. what am i doing wrong ?:(
btw i had the same problem with firestarter.

---

### Post by frodon on 2007-06-18
If 192.168.1.1 is your modem address and you need to access it often maybe you could just accept all packets from 192.168.1.1, it would make something like that :
```
iptables -A TRUSTED -i eth0 -s 192.168.1.1 -j ACCEPT
```

---

### Post by TyPhoon101 on 2007-06-18
thanks ! it worked like a charm :popcorn:

---

### Post by tommytomato on 2007-06-24
what do you do if you want to add in server stuff like ssh, stmp, pop3, www, ftp

only want to be able to access server via local network  for ssh and stmp pop3 only, I dont want others to be able to access it via the net, only web ( www )

if that makes any sence.

this is how far i got

```
!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

#Allow Web Taffic
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT

#Allow www
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 80 -j ACCEPT

# Allow FTP
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 21 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 21 -j ACCEPT

#Allow smtp
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 110 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 110 -j ACCEPT

#Allow pop3
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 25 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 25 -j ACCEPT

#Allow SSH
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 22 -j ACCEPT
```

this is not tested yet, as to me not knowing whats going on realy :(


TT

---

### Post by frodon on 2007-06-24
> **tommytomato said:**
> what do you do if you want to add in server stuff like ssh, stmp, pop3, www, ftp

only want to be able to access server via local network  for ssh and stmp pop3 only, I dont want others to be able to access it via the net, only web ( www )

if that makes any sence.

this is how far i got

Some of the ports you chose to open don't corresponf to the comment you put, for instance the port for pop3 is 110.

```
#Allow Web Taffic
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
```these lines are useless, you don't filter output in your script and the first firewall rule allows already the needed trffic on port 80 (iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT)

```
#Allow www
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 80 -j ACCEPT
```also useless for the same reasons.

```
# Allow FTP
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 21 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 21 -j ACCEPT
#Allow smtp
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 110 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 110 -j ACCEPT

#Allow pop3
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 25 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 25 -j ACCEPT
```Useless as well the first firewall rule allows already all that.

To be sure just open your /etc/services file, all the port are listed with the name of the corresponding services so just look at this file to catch the good port with the good protocol.
Here you just seems to need to open your ssh port for what you want to do.
Now for your local network matter i don't know because you didn't give enought details, do you have 2 network cards one on internet and the other on the local network or is it something else. ?

---

### Post by tommytomato on 2007-06-24
No I have one network card in the server

I use another PC on the network to access the server, I also have a router where i can open ports and point them to the server

does that make sence, I'm realy lost here :D

TT

---

### Post by tommytomato on 2007-06-24
Opps here is my latest try
later i want to be able to allow access to 25 and 110 for my network only and not the outside, would the email server still send and recive mail  ??

```
/etc/init.d/firewall status
Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
TRUSTED    all  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   all  --  anywhere             anywhere            
DROP       all  --  a83-132-97-14.cpe.netcabo.pt  anywhere            
DROP       all  --  81.199.85.110        anywhere            
DROP       all  --  218.16.120.80        anywhere            
DROP       all  --  mx4.url.com.tw       anywhere            
DROP       all  --  218.0.153.219.broad.cq.cq.dynamic.163data.com.cn  anywhere            
DROP       all  --  63-93-95-121.lsan.mdsg-pacwest.com  anywhere            
DROP       all  --  002.011.dsl.syd.iprimus.net.au  anywhere            
DROP       all  --  mail.ala-hawaii.org  anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:pop3 
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

but when i restart it i get this message

/etc/init.d/firewall restart
Removing all iptables rules:  [End of flush]
Iptables rules creation: iptables: Invalid argument
iptables: Invalid argument
iptables: Invalid argument
iptables: Invalid argument

TT

---

### Post by tommytomato on 2007-06-24
I think i fixed that error

but when i turn on the firewall i cant access the server or the site i have hosted

when i turn off the firewall i can access the server and access the sites i have hosted

TT

---

### Post by cecilmoney on 2007-07-02
I am new to ubuntu and I am barely able to find my way around it. I had firestarter installed on my computer, but after I tried to get it to boot every time i log in, it stopped working. I mean that it completely stopped working, no matter what you did it refused to open a window. After struggling with several, more complicated, firewalls I decided to try and configure my iptables according to your script. I'm pretty sure that I put everything in right and I made sure to save everything. The only problem is that now I cannot connect to the internet. Neither my ethernet, nor my wireless access will connect. 

Please post easy to follow directions on how I can get the internet again. If that is too much work, please tell me how i can undo all of the changes made to my iptables so that I can use my computer again.

Thanks!

---

### Post by tommytomato on 2007-07-02
I dont know if this is right, but just undo or delete what you have done

or turn off iptables using the command

/etc/init.d/iptables stop

or /etc/init.d/firewall stop

I'm sure others will help you out, as i'm not the best at iptables either

O yer you could post up you firewall script for others to look out

TT

---

### Post by TyPhoon101 on 2007-07-02
you can try putting ppp0 instead of eth0 in your script and restarting the firewall.i was having the same problem and this trick saved me.

---

### Post by frodon on 2007-07-03
TyPhoon101 is right check the name of your network interface, you can see that using the network tools you have available in your admin menu.

---

### Post by highfructose327 on 2007-07-12
Thanks! this answered all my questions about the use IP tables, great tutorial

---

### Post by gregor171 on 2007-07-18
Can anybody tell me, how to create a black list scrip, that would drop all incoming request from IP-s in the list deny_hosts.conf? How  to read file line by line, ignoring commented and compare IP-s to the ones from list and DROP them?

---

### Post by frodon on 2007-07-18
Give me your deny_hosts.conf and i will write you a perl script to generate the corresponding iptables lines. This script will fill a file called iptables_black_list.bash for example then all you would have to do is to add a line in your firewall script to excecute this iptables_black_list.bash file.

---

### Post by gregor171 on 2007-07-18
Great! I was struggling with bash, but it takes some time since I am nearly new to this. 
I'm actually using **ubuntu-firewal**l now, since I had some unwelcome visitors that managed to get to some server rights.
Ubuntu firewall has an option custom script file that should point to it. 
**The attached  list** *deny_hosts.txt* contains a relative small number of **bad ip-s**, but we can create some web servis, that would contain a bad list.

[ATTACH]38536[/ATTACH]

Thanks very much.

---

### Post by frodon on 2007-07-18
If you understand the guide you can write your own script rather than using ubuntu-firewall which help you to create it.

Anyway here is the script (at the bottom of the post, remove the .txt extension), download it then give it execute rights finally put it under /usr/bin/. Then to use it type this :
```
deny-ip-generator.pl <deny-ip text files> <output file>
```where the first parameter is your input text file or the path to your input text file and the second is the output file or the path to the output file which is your custom iptables script.

---

### Post by gregor171 on 2007-07-18
Thanks very much. I did write my on wall, as I started with 5.04, but adding some advanced functionality gave me a struggle. So it was easier to install ubuntu firewall. Basically I'm short of time since my basic job is coding some other stuff. I was quite shocked, that I had guests in my server but the good think is that only few of them got in. 2 to many. thx

---

### Post by Adam590 on 2007-10-02
Thanks a bunch for this great guide!

I connect to an ADSL connection via PPPoE (using pppoeconf), and none of the iptables front ends seem to let me connect. Your instructions worked perfectly, though, and now the test sites report me as completely stealthed.


A few questions about setting up rules for [Gizmo]("http://www.gizmoproject.com/index.php"):

1. On [this page]("http://support.gizmoproject.com/index.php?_a=knowledgebase&_j=questiondetails&_i=58"), they describe the ports and services needed. If I see something like this, do I need to edit the script?

2. If so, when they say some ports are for "incoming" and some for "outgoing", does that mean I need to choose between dport and sport in my rules? (Which is which?)

3. How does one specify a rule allowing for "All outgoing UDP ports above 1023"?

TIA

---

### Post by frodon on 2007-10-02
1- First try and see if the apps works, if it works no need to modify anything. If it doesn't work you will need to edit the script.

2- The script i provide in the first post only block incoming traffic so you only have to concider incoming ports.
So the rules you would have to add if it doen't work by default would be something like :
```
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5004 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5005 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 64064 -j ACCEPT
```

As for using dport or sport it depends on the context but not on the nature of the packet (incoming or outgoing), if you don't know the one to choose try one and if i don't work try the other not really painful :)

And my secret tip, because iptables is widely used if you perform a google search with "iptables" and "gizmo" as keyword i'm quite sure you will find the rules you need.
Here is what i found ;) :
[http://www.voipplanet.com/backgrounders/article.php/3638086](http://www.voipplanet.com/backgrounders/article.php/3638086)

3- In the case you are filtering outgoing traffic (what you don't) it would be :
```
iptables -A OUTPUT -p udp --dport 1024:65535 -j ACCEPT
```

---

### Post by Adam590 on 2007-10-02
Right - forgot to mention Gizmo wasn't (and still isn't) working, but it's good to know what the problem is *not*. Thanks for the info and tips. :)

---

### Post by Helbo15 on 2007-10-09
hi I'm trying to follow your firewall guide but when I try to start the firewall it either says the file does not exist or it says 
: command not found 
: command not found 
'irewall: line 6:syntax error near unexpected token '{
'irewall: line 6: 'start() {

What am I doing wrong here ?

---

### Post by Bobdaboa on 2007-10-11
Wow, great how to I put it on stumble upon so you should start getting more hits now.:)

---

### Post by darco on 2007-10-30
I lost connectivity from WINDOWS to Ubuntu after I loaded this script. I am able to view files from UBUNTU to Windows tho. What rule do I enter to see all on the 192.168.15 subnet?
thxs
dr

*Edit* oh and when I shut off the FW, I can connect

---

### Post by Retrograde77 on 2007-10-31
Great guide :)

got it all on and seems to be working, used the script and only changed the port of bittorrent, but in tests it shows my ports as closed but insecured.
```

#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 49207 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

```

akuma@Thalamus:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
TRUSTED    0    --  anywhere             anywhere            
DROP       0    --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:49207 
akuma@Thalamus:~$ 

```

Any help would be great :)

---

### Post by frodon on 2007-10-31
What test ?

---

### Post by Retrograde77 on 2007-10-31
> **frodon said:**
> What test ?

[https://grc.com/x/ne.dll?bh0bkyd2]("https://grc.com/x/ne.dll?bh0bkyd2")

Pretty much all closed, not steathed.

---

### Post by frodon on 2007-10-31
Then there's something wrong i did this test a bunch of times and i know it reports ports as stealthed when the script is up.

Just a stupid question, are you sure your network card is really called eth0 ?

---

### Post by Retrograde77 on 2007-10-31
> **frodon said:**
> Then there's something wrong i did this test a bunch of times and i know it reports ports as stealthed when the script is up.

Just a stupid question, are you sure your network card is really called eth0 ?

lol yeah it is.  actually, (a stupid question of my own) am behind a bog wireless router, and is it that, that is not doing its job?.  Have always used a software router on windows, mainly to protect what talks out.

---

### Post by frodon on 2007-10-31
Try to removing all the "-i eth0" parts everywhere so you will be sure that the rules are applied on all the network devices.

---

### Post by brazilla ray on 2007-11-10
I am having the same problem, removing "-i eth0" didn't have any effect.  Thanks for any help.

---

### Post by frodon on 2007-11-10
With so few informations, impossible to help you sorry.

---

### Post by brazilla ray on 2007-11-10
Sorry, what I meant is that I was also having this problem:
> **Retrograde77 said:**
> Great guide :)

got it all on and seems to be working, used the script and only changed the port of bittorrent, but in tests it shows my ports as closed but insecured.

with the exception that I used the script unaltered.  And for the record, I am also using [https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2), as well as nmapfe, which reports the same thing. 
Thanks.

---

### Post by frodon on 2007-11-11
To use nmapfe you should try from another computer as your all traffic on your loopback interface is allowed.
There sould be somthing wrong somewhere in your config, i tested this again now and it works so i don't really know what to say.

Please check how are called your network devices with the "ifconfig" command.

---

### Post by brazilla ray on 2007-11-11
ifconfig lists eth0 and lo.  also, the results of the tests from the Shields Up! site mention that a ping request was recieved:
> GRC Port Authority Report created on UTC: 2007-11-11 at 17:00:14

Results from scan of ports: 0-1055

    0 Ports Open
 1053 Ports Closed
    3 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be STEALTH were: 21, 23, 80

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

which I thought were supposed to be blocked.

---

### Post by frodon on 2007-11-11
Check all, i tested again with the script on first post and shield up answer that all is stealth, in addition it is a really simple script.
For the moment i don't see what could make you get this result.

---

### Post by indosupremacy on 2007-11-12
while i'm doing nmapfe,there are still open port in my ip,it is 139 and 445,how can i make it stealth / closed? thank u (i 've been using your firewall script)
thank u

---

### Post by frodon on 2007-11-12
As my script allows loopback interface you must use nmapfe from another computer to test your configuration, if you run it from your computer all you will have is wrong results.

---

### Post by indosupremacy on 2007-11-12
> **frodon said:**
> As my script allows loopback interface you must use nmapfe from another computer to test your configuration, if you run it from your computer all you will have is wrong results.

hehe,thanks bro...i have scan it from another computer,and it say nmap didnt find any open or close port,thanks bro for your posting,,,,,:)

---

### Post by kd7swh on 2007-11-12
Can you add a protocol to the trusted chain?

---

### Post by brazilla ray on 2007-11-12
> **frodon said:**
> Check all, i tested again with the script on first post and shield up answer that all is stealth, in addition it is a really simple script.
For the moment i don't see what could make you get this result.

after some further research, I think now that the results I am getting from Shields Up has to do with my modem: (from the Shields Up site)
> When a test is initiated by any system behind a NAT router, we are testing the public-side security of the router itself and not the security of the individual machines which are located behind and protected by the router.
and changing some of the filtering settings on my modem does change the results, but still nothing makes all the ports stealth. does this all sound like a reasonable possibility? I think for now I will choose not to worry about it...

update:  I'm sorry I didn't check this before, if nothing else it would have saved me a lot of time, BUT, I checked Shields Up in windows, and get the same results, so I think it really must be something with the modem.  Anyways, thanks for all your help.

---

### Post by dynamethod on 2007-11-16
well ive tried the init.d script mentioned in the how to but i get this:

```
:~$ sudo /etc/init.d/firewall restart
Shutting down firewall...
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
...done
Starting Firewall...

External Interface:
External IP: 192.168.1.243 127.0.0.1
Default GW: 192.168.1.254
 --- 
Internal Interface: eth0
Internal IP: 192.168.1.243
Internal Netmask: 255.255.255.0
Internal LAN: 192.168.1.243/255.255.255.0

Loading IPTABLES modules
 --- 
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
Setting sysctl options
 --- 
Creating user-chains
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
 --- 
Implementing firewall rules...
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
/etc/init.d/firewall: 831: /usr/sbin/iptables: not found
...done

--> IPTABLES firewall loaded/activated <--

```

so tried ```
sudo iptables -L
```
and got:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

???

also how can i get iptables to log to the system logs under System-->Administration-->System Logs 
thanks in advance

---

### Post by frodon on 2007-11-16
What firewall script do you use (post it if needed) ?

For the log there's several solutions the most standard is through syslog but you can use some other systems. However creating log spend always more ressources and except for debug or in case you are an expert there's no real point creating some IMO.

---

### Post by dynamethod on 2007-11-16
heres the script ive borrowed from this site: 

[http://www.linuxguruz.com/iptables/scripts/rc.firewall_023.txt](http://www.linuxguruz.com/iptables/scripts/rc.firewall_023.txt)

---

### Post by frodon on 2007-11-16
You should try get support from this site, if i start to debug all the iptables scripts users find on internet this will have no end and ultimatly this has no link at all with my tutorial which purpose is to teach you how to create easily the firewall script you need not to debug the script you found.
Feel free to ask for support in this thread if you decide to use the tutorial.

---

### Post by ssc351 on 2007-12-06
Is there a way to set this up for both my wireless interface(ath0) and the wired interface (eth0)?  Can I make redundant lines and just have one line by ath0 and the other eth0?  

I travel a lot, and while I use ath0 for most of my stuff, sometimes I am in hotels where I need to use my wired connection.  

Also,  I am using Virtualbox and I am forwarding ports given from this post:
[http://ubuntuforums.org/showthread.php?p=2980021&highlight=6666#post2980021](http://ubuntuforums.org/showthread.php?p=2980021&highlight=6666#post2980021)

Am I opening myself up?  Lastly, I also using the integrated Filesharing in Virtualbox...is that creating some more vulnerablilites?

Thanks!

---

### Post by frodon on 2007-12-06
Services always introduce vulnerabilities so yes opening a service introduce vulnerabilities but a good firewall reduce the risk, for your first question see post #137.

---

### Post by ssc351 on 2007-12-06
Ok, thanks.  Ya sorry about the first question...I was too lazy to read through the whole post, and when I did, 30 seconds after I posted...surprise surprise there is the answer to my question, I hate being that guy.  :)

Anyway,  after I got everything set-up I went to Shields up and found something interesting. On my wireless network, everything comes up the same as it did precustom firewall...i fail the TCP and ping requests and most ports are viewed as closed.  However, when  I connect to my neighbors wireless network, I pass the TCP request but fail the ICMP ping request, and all the ports are seen as stealth.  Why would changing what network I am connected to effect the outcome?  What can I do to fix this to pass the tests and get all ports seen as stealth?

Also, do I need to get rid of Firestarter with this or change something within Firestarter?

---

### Post by frodon on 2007-12-07
Wait a minute you have firestarter installed using this script ?

Of course you have to choose what you want to use firestarter or custom script, i can't tell you what happen if you have both but i guess you should have some unwanted side effects.
Be careful using "Shields up" if you have a router on your home network it will test the router and not your computer, it can test you computer only in case of direct access.

---

### Post by ssc351 on 2007-12-07
Ahh...i see...I would up uninstalling firestarter.  Interesting what you say about the router deal. I will have to redo my shields up try. Thanks for the info.

---

### Post by zgerrz on 2007-12-17
I'm trying to set up my ubuntu box as an SSH server so i can have my other LAN computers SSH into this ubuntu server, but i'm having trouble.. i don't know if it's my firewall rules or something else. here's my modified firewall.bash

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
#iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 41912 -j ACCEPT

# Allow SSH on port 22777
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 22777 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 22777 -j ACCEPT

# Allow Samba
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 137:139 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 137:139 -j ACCEPT

# Allow loopback interface traffic
iptables -A TRUSTED -i lo -j ACCEPT
iptables -A TRUSTED -o lo -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

I've relocated my SSH port to 22777 as you can see. I specified 22777 as my SSH port in my sshd_config, and am trying to test it but i just get this:

```
zgerrz@gutsy:~$ ssh -p 22777 localhost
ssh: connect to host localhost port 22777: Connection refused
```

I have a D-Link 604 router and have set up a rule allowing access through port 22777 with a source of 192.168.1.100/11 to destination of the same on both TCP and UDP.

I'm not sure what the problem is because i can't get access using SSH at all and i don't know where the problem is.

thanks.

---

### Post by frodon on 2007-12-18
First i would use --dport instead of --sport in your ssh iptables commands then i would restrict things a little bit more once you get the basic configuration working.
You can restrict for example the access to the IP of your other computer only and even block brute force attacks as iptables is able to block them. Example :
[http://ubuntuforums.org/showpost.php?p=3157972&postcount=5](http://ubuntuforums.org/showpost.php?p=3157972&postcount=5)

---

### Post by zgerrz on 2007-12-18
Ok,

I managed to get everything up and running just fine, thanks to your help.

I just want to take a few extra steps in securing the SSH server by only allowing LAN connections to go to port 22777 and to only allow LAN connections to connect to the SSH server.

I checked the link you posted and I like how the poster only allows three attempts from any one IP address in any five minute period with IP tables, but i'm not sure how to configure the IP tables lines to fit the script that we are using in this thread.  also, i would like to only allow connections from 192.168.100 through 192.168.1.111 to pass through port 22777. how can i turn these lines:

```
#------------------------#
# SSH daemon - tcp Port 22 - drop any more than 3 new connections from one address every 5 mins
$IPTABLES -I INPUT -p tcp -i eth0 --dport 22 -m state --state NEW -m recent --set
$IPTABLES -I INPUT -p tcp -i eth0 --dport 22 -m state --state NEW -m recent --update --seconds 300 --hitcount 3 -j DROP
$IPTABLES -A INPUT -p tcp -i eth0 --dport 22 -j ACCEPT
```

Into lines usable with this script we are making?

i want to convert these lines that i already have:

```
# Allow SSH on port 22777
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22777 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22777 -j ACCEPT
```

into lines that can only permit access from LAN computers and that will limit the number of connections as described above.

i'm trying to figure it out myself but its a little complex to me.

thanks

---

### Post by frodon on 2007-12-19
If you know which IP in your LAN network will attempt to join the server then that may not be useful to limit connection attempts.

I would jsut modify your lines as following :
```
# Allow SSH on port 22777 from ip 111.22.33.333
iptables -A TRUSTED -i eth0 -p udp -m udp -s 111.22.33.333 --dport 22777 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp -s 111.22.33.333 --dport 22777 -j ACCEPT
```If you want to make it even stronger you can filter network card mac address too, it is explained in first post.

I don't think you would need more.

---

### Post by tolmun on 2007-12-29
frodon:
To work my pppoe connection i remove "iptables -A FIREWALL -j DROP". 
Than i make tetst on [www.grc.com](www.grc.com)  and show 7 stealth and the rest blue, 
Than i remove -i eth0, and nothing change.

What can i do?

my script.

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL  -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
#iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED  -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED  -p tcp -m tcp --sport 443 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED  -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED  -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED  -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# Allow FTP
iptables -A TRUSTED  -p udp -m udp --sport 21 -j ACCEPT
iptables -A TRUSTED  -p tcp -m tcp --sport 21 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

And my  sudo iptables -L:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
TRUSTED    0    --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp spt:fsp 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp 
```

Thanks

---

### Post by frodon on 2007-12-29
The "iptables -A FIREWALL -j DROP" line is mandatory otherwise unwanted packets are not dropped, this explains why your ports are not seen as steath in this case.
Just remove the "-i eth0" part like you did and the configuration should be applied on all network devices.

---

### Post by tolmun on 2007-12-29
Thank you for your fast reply.
Now its ok.

---

### Post by ssc351 on 2007-12-30
so now for whatever reason, the iptables won't start when I reboot.  I have to go into terminal and manually start them.  Any reason for this.  I went through the howto and did everything again, but same result. 

Once I restart it manually it looks fine, it just won't start on boot now.  Anyone else have this problem? Any solutions?

---

### Post by frodon on 2008-01-02
Did you change anything in you rc.local directories or installed any other services ?

Once you booted your system type "sudo iptables -L" to see if the rules have been really loaded.
I've never heard of such problems yet, maybe you did something which broke a little bit your configuration.

---

### Post by ssc351 on 2008-01-03
Here is the output:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Then I start and get:

sudo /etc/init.d/firewall start
Iptables rules creation:  [End iptables rules setting]


Then get:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
FIREWALL   0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FIREWALL (1 references)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
TRUSTED    0    --  anywhere             anywhere            
DROP       0    --  anywhere             anywhere            

Chain TRUSTED (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5349 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5351 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5348 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:41912 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp 

Status:

/etc/init.d/firewall: line 31: /sbin/iptables: No such file or directory
/etc/init.d/firewall: line 32: /sbin/iptables: No such file or directory

The only thing I think I installed was an upgrade for Virtualbox, but honestly I can't remember.

---

### Post by frodon on 2008-01-04
Strange. I guess you already did this but could you try to do again the 3.3 part of the guide and create again the init.d script as well as the rc.local links with the update.rc command.

---

### Post by aparigraha on 2008-01-17
I'm trying to get iptables working properly on an ftp server, and it seems the --state RELATED command is not working properly. I really need some advise here to get this running. My default FTP port is 1338. Here is my firewall.bash


```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat
modprobe ip_conntrack
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow glftpd
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1338 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 57571 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 57571 -j ACCEPT

# SSH test
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 2223 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 2223 -j ACCEPT

# Allow FTP (first test)
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
#iptables -A TRUSTED -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1338 -m state --state NEW,ESTABLISHED -j ACCEPT
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1338 -m state --state ESTABLISHED -j ACCEPT
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

How do i get the ports used allowed? I have tried changing output to input, but no success so far. Any help is greatly appreciated! 
Thx!

---

### Post by frodon on 2008-01-17
You can remove all the -o eth0 and OUTPUT lines as the firewall script i gave don't filter outgoing traffic so these packets are already allowed.
In addition i would need to test this but you shouldn't have to add any rule if your ftp is on port 21 has established and related connections are allowed.

I believe i use pretty much the same rules and never got coonection issue on my FTP server.

---

### Post by aparigraha on 2008-01-17
> **frodon said:**
> You can remove all the -o eth0 and OUTPUT lines as the firewall script i gave don't filter outgoing traffic so these packets are already allowed.
In addition i would need to test this but you shouldn't have to add any rule if your ftp is on port 21 has established and related connections are allowed.

I believe i use pretty much the same rules and never got coonection issue on my FTP server.

Thx for the fast reply. And... thx for the wonderful HOWTO.
Well maybe I was a bit unclear. I get in to the ftp server from the outside, but the problem comes when other ports are being opened up and used in passive mode. Maybe I'm missing something here, but Isn't that what the argument RELATED is supposed to do?

I have removed all -o eth0 and OUTPUT lines.

This is what i get so far:
R] SYST
[R] 215 UNIX Type: L8
[R] PASV
[R] 227 Entering Passive Mode (*IP-address*,8,148)
[R] Opening data connection IP: xxx.xx.xxx.xxx PORT: 2196

So what i need help with is rather, how do i get iptables to allow the useage of newly opened ports? Thx again!!

---

### Post by frodon on 2008-01-17
It should already be the case, however now that you point this specific question i'm noticing that i the script i give on front page i don't modprobe ip_conntrack_ftp module which is made for this purpose so add the following line just below other modprobe lines and restart your firewall :
```
modprobe ip_conntrack_ftp
```

---

### Post by aparigraha on 2008-01-17
> **frodon said:**
> It should already be the case, however now that you point this specific question i'm noticing that i the script i give on front page i don't modprobe ip_conntrack_ftp module which is made for this purpose so add the following line just below other modprobe lines and restart your firewall :
```
modprobe ip_conntrack_ftp
```

modprobe ip_conntrack_ftp   is already in place ;)

had some success here actually!
when changing the ftp server port to 21 everything runs smooth. changed the line ```
# Allow glftpd
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1338 -j ACCEPT
``` to ```
# Allow glftpd
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT
```
and it seems it working perfectly. but the problem now is that i can't continue to run the ftp server on this port. i need a port above 1023, so where exactly do i specify the port 1338? Or isn't it that simple maybe? Using the first code above just doesn't do it. And changing either one of these ```
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

to port 1338 doesn't make it work either.

---

### Post by frodon on 2008-01-17
Good question !

I have my ftp server on port 21 for convenience so i don't have the answer. I think you are ready for some testing, i would try some rules and see.
Please let me know if you find the solution, i'm interested.

---

### Post by aparigraha on 2008-01-17
> **frodon said:**
> Good question !

I have my ftp server on port 21 for convenience so i don't have the answer. I think you are ready for some testing, i would try some rules and see.
Please let me know if you find the solution, i'm interested.

sweet. some testing, i'm on it. and will post the solution later.
thx again for everything so far.

---

### Post by aparigraha on 2008-01-17
OK. This is what I did to my iptables, to be able to run an FTP server from a port other than 21. I chose port 1338. I think I got this working good enough for now. But I'm still wondering about some issues, and would really like some input.

First I enabled some modules.
```
#load some modules you may need
modprobe ip_tables
modprobe ip_conntrack
modprobe ip_conntrack_ftp ports=21,1338
modprobe ip_nat_ftp ports=21,1338
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
```

From what I've read it is important to put them in the right order, since ip_nat_ftp auto-enables ip_conntrack_ftp, and ip_conntrack_ftp automatically listens to port 21 and only port 21 by default. Also keep port 21 and add your port after it (21,1338 ). ip_conntrack_ftp wont work without it, at least for me.

Then I allowed FTP on port 1338:
```
# Allow glftpd
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 1338 -j ACCEPT
```

I also allowed the ports used by the conntrack related modules:
```

# Conntrack
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1338 --dport 1338 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT 
```

and here, I'm not sure if I'm missing something, or doing smoething stupid. From what I can understand, iptables opens the port range 1024-65535 after it is RELATED to traffic from port 1338 through ip_conntrack_ftp. Is that right? Or is the port range open anyway? Would be very bad. The sport/dport thing really makes me confused :confused:

The only issue I have noticed so far, is that the ftp connection is not allowing encryption for some reason. SSL/TSL just wont work, and that is kind of strange. If anyone got any input on that, or the above issues... please let me know. Thx alot! 


And also:
@frodon

I was trying different things to get around this issue when I stumbled on an error in the HOWTO which is related to mac address filtering.
```
iptables -A INPUT --mac-source 42.42.AA.42.42.AA -j DROP
```

Didn't work for me, 

```
iptables -A INPUT -m mac --mac-source 42:42:AA:42:42:AA -j DROP
```

The above did. (Notice also the colons **[COLOR="Red"]:[/COLOR]**)
Maybe I'm doing something wrong, but I Just thought you should know... in case ;)   

Again... great HOWTO! It has helped me a lot.

---

### Post by frodon on 2008-01-18
Yep good catch for the MAC address it is a typo from my side.

I confirm your port 1024:65535 will be opened in case it is related to an established connection and not all the time, so you are safe with this if i can say safe because running services is not safe by itself :P
About TLS/SSL i'm using it too so i wonder why this would be the only thing that don't work for you.

Anyway once you get all working, try to trmove some rules just to see which one is really mandatory ;)

---

### Post by aparigraha on 2008-01-18
> **frodon said:**
> Yep good catch for the MAC address it is a typo from my side.

I confirm your port 1024:65535 will be opened in case it is related to an established connection and not all the time, so you are safe with this if i can say safe because running services is not safe by itself :P
About TLS/SSL i'm using it too so i wonder why this would be the only thing that don't work for you.

Anyway once you get all working, try to trmove some rules just to see which one is really mandatory ;)

Thx for the confirmation!

About the TLS/SSL... it seems ftps-data and ftps (FTP over SSL) use the ports 989 and 990 respectively. But I can't get it to work now anyhow it seems. Even though I change the related port to 989:65535. Strange if that is the problem, but it works when using port 21 ?! Well... I don't really have the time spending hours at this, so I guess I'll just have to open up port 21 and go with your working solution for now. 

Also found out that modprobe ip_conntrack_ftp also has it security flaws. So I guess I'll have to limit ports to specific IP's in the end :mad:

So far, a lot of work for nothing :(
But I appreciate your input!

---

### Post by aparigraha on 2008-01-20
Well I just couldn't leave it alone :)
And now I think I messed it up. I can't use a encrypted (TLS/SSL) connection at all (not even on port 21) when using the ESTABLISHED, RELATED commands. When I turn the firewall off, everything is FINE!
If anyone has any input on this, I would be very grateful.

This is my /etc/firewall.bash.... so far with two different solutions:
One with encryption that works, and one without using ESTABLISHED, RELATED commands. And I don't use them both at once... this is just an example.

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_conntrack
modprobe ip_conntrack_ftp
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

[COLOR="Red"]# Allow glftpd[/COLOR]  (Only working solution with encryption so far)

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22101:22113 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

[COLOR="Red"]# Allow FTP[/COLOR] (This only works when NOT encrypted through TLS/SSL)

iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 --dport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 22101:22113 --dport 22101:22113 -m state --state ESTABLISHED,RELATED -j ACCEPT

# End message
echo " [End iptables rules setting]"



```

The passive port range is defined in the ftp server .conf file and is currently 22101:22113.

When using only the arguments under [COLOR="Red"]# Allow glftpd[/COLOR], I can connect from the outside with both a encrypted and unencrypted connection. This is not so good as it keeps my port range narrow and open at all times.

When using the arguments under [COLOR="Red"]# Allow FTP[/COLOR], I also need the the line
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT
```.

No problem, it works, except that these arguments wont work with an encrypted connection. Why is that?

Read somewhere that conntrack_ftp doesn't handle encryption, but I'm really lost here. Does that mean I'm bound to the small port range? I've read numerous threads on this. But have come nowhere. Actually, I have gone backwards :(

Would really like some help here...

---

### Post by theslide on 2008-01-30
HI,

First off great HOWTo, I found it really informative. Just one question thought. I set up the firewall as you describe, with the only modification of allowing SSH and SAMBA connections through (both working).

My question is - before I set up the firewall I have able to connect to the computer remotely using the hostname 
e.g 
```
ssh -p2222 alex@hostname
```
but now the name cannot be resolved and I get the error 
```
ssh: hostname: Name or service not known
```

and the only way I can connect is by specifying the IP address (192.168...). I assume there is another port I have to open to allow the name to be resolved but I'm not sure which one (DNS?).

Any help would be greatly appreciated
Alex

---

### Post by frodon on 2008-01-30
I don't use ssh so i have never tested but you can try to open the dns port indeed, it is something to try :
```
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 53 -j ACCEPT
```

---

### Post by theslide on 2008-01-30
Thanks for the reply. I've been doing some fiddeling.

I have tried opening port 52 as you suggest but to know avail. Looking in the /etc/services file it lists has no listing for DNS, but list MDNS at being on port 5353. What do you know about this?

Also in your example from the last post, and in your first 'examples' section, you use the -o (out-interface) switch to open the port for DNS. Am I right in thinking that for the firewall.bash code you posted though, you only need the -i (in-interface) switch because we do not block any outgoing traffic?

I've been reading around and I think the problem might that the computer cannot register itself with the DNS. Though I'm not too sure how to fix this.

I guess more reading is needed

Alex

---

### Post by frodon on 2008-01-30
Good catch ! i mistakenly posted the wrong line, the one i posted was for output packets which is senseless here. Try with -i indeed.

I'm correcting my previous post.

Setting accurately a firewall often requires some testing but i'm sure it shouldn't be too long.

---

### Post by Viktor on 2008-01-31
Thanks for the great guide.
I have a question though. I have used the scripts on the first page but still get ports that are closed but not stealth in the shields up test. Am I missing something. I have done no changes to the script on the first page.

Is it possible to get all ports to be stealth? If so, how do I do. Thanks for the great guide by the way.

This is the output from shields up:

> GRC Port Authority Report created on UTC: 2008-01-31 at 18:09:00

Results from scan of ports: 0-1055

    0 Ports Open
    5 Ports Closed
 1051 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be CLOSED were: 0, 1, 25, 113, 443

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

---

### Post by frodon on 2008-01-31
Are you using a router ?

---

### Post by Viktor on 2008-01-31
Im connected via a cable modem. No router.

---

### Post by frodon on 2008-01-31
Then try to think what could create this false result, shieds up is only able to test your firewall if you are directly connected to internet otherwise it will test the device before your computer (most often your router).
If you didn't change anything to the script and if you are directly connected to internet without connection sharing, router, switch, ... then you should not have this result.

I have removed the uneeded https line in my script, see if it have a concequence on your closed 443 port.

EDIT: thanks to your feedback i have removed some more lines out of the given script, the one in first post now should be even more safe :)

---

### Post by Viktor on 2008-02-02
Thanks for the help, I updated the files and now 113 and 443 appear as stealth. three still remains though. Could this be caused by my cable modem?

> 
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2008-02-02 at 09:12:16

Results from scan of ports: 0-1055

    0 Ports Open
    3 Ports Closed
 1053 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be CLOSED were: 0, 1, 25

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

----------------------------------------------------------------------


/Viktor

---

### Post by shelbydz on 2008-02-09
Hi, 

Thanks for building this how-to for us! Great stuff. I do have a few questions: 

Is there a way to turn ping reply off? (it may be in the 18 pages of replies, but I didn't see it). I don't want my computer talking via ping (: 

Is there any way to secure up the bittorrent ports? When I test them (default 6881 - 6999) the site comes back with CLOSED for 6881-68889. Does this mean that those ports are in use, but closed to probing? Should I be worried or is this what I want? The rest of the ports report back as Stealth.

Thanks again,

---

### Post by frodon on 2008-02-09
Some applications like bittorrent require to open a port so you have no other choice than opening the port to get it working correctly however that don't mean that you are vulnerable because you open this ports. To be exact because you have no service running on this port the port will not answer to request and it is why it is seen as closed and not just open.
So you have not to worry too much  about that.
Any other port that you have not opened will be stealth which is even more safe than just closed.

Have you tested that you computer answer ping request with the firewall ?

---

### Post by RJ Hythloday on 2008-02-27
Thanks for this ''beginners'' firewall. It sure seems like alot of work though. Is all this really necessary or could it be done w/ less? I always thought that *nix was so safe, is a firewall needed at all? How about just my router being inline after the modem, is that good enough?
 
TIA
 
Bob

---

### Post by frodon on 2008-02-27
Wrong thread for this debate RJ Hythloday, you can create a thread in the cafe to talk about the need of firewall under linux if you wish.

This thread aims to support the tutorial only.

---

### Post by v8YKxgHe on 2008-03-26
Hey,

I've tried many times with this guide to get a working firewall, however - I can not at all. Each time I do it, everything ends up blocked. Here is my script:

```
#!/bin/bash

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i venet0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

---

### Post by frodon on 2008-03-26
I think the problem is there :
```
iptables -A FIREWALL -i venet0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```What is venet0 ? Shouldn't it be eth0 instead ?

---

### Post by v8YKxgHe on 2008-03-26
no, I have no eth0. I have venet0, venet0:0 venet0:1 etc, up to 4.

Edit: I just saw I left some of the eth0's in - I'll try changing them now.

---

### Post by frodon on 2008-03-26
Could you paste the output of "ifconfig" command here (you can hide your IP and MAC adresses, they don't matter for what i want to see) ?

---

### Post by v8YKxgHe on 2008-03-26
```
$ sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:613254 (598.8 KiB)  TX bytes:613254 (598.8 KiB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:357015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:280814707 (267.8 MiB)  TX bytes:70848027 (67.5 MiB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:1  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:2  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

venet0:3  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:xxx.xxx.xxx.xxx  P-t-P:xxx.xxx.xxx.xxx  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

```

This is with my VPS, and as you can see - has 4 IP addresses assigned.

---

### Post by frodon on 2008-03-27
wow, never saw such thing !

Anyway i'm almost 100% sure that the problem is with you interface name. Try removing any "-i ****" occurence so that rules will be applied on any interface present on your system thus you will see if it's really the problem.
Then if it is we will try to find a solution, i hope better than duplicating rules for each interface name.

---

### Post by v8YKxgHe on 2008-03-28
No luck removing the interface from it either =(

---

### Post by frodon on 2008-03-28
Hum, there's something with your configuration maybe as i don't see looking at the script how removing all "-i ***" options could block anything as the line *iptables -A FIREWALL -j ACCEPT* would allow all.

---

### Post by v8YKxgHe on 2008-03-28
frodon, I'm an iptable noob, could you create a rule for me that will allow absolutely anything in and out? I just wanna test if it is working at all.

---

### Post by Catz3705 on 2008-03-28
Admirable, well prepared work --- a boon to Ubuntu users like myself (Gutsy 7.10)  everywhere!

I have a Home LAN with eight systems running on switches and wireless bridges as well as one wifi laptop. The service provider is Verizon DSL and is routed through a Linksystems device. I've had trouble controlling Firestarter and would like to switch to custom management of iptables.

Question: What is the code for trusting a range of dynamically assigned intranet IP addresses as in 192.168.2.0 through 192.168.2.255? IOW, how is the local LAN trusted?

Thanks in advance,

-met
Catz3705

---

### Post by frodon on 2008-03-28
*iptables -A TRUSTED -p tcp -s 192.168.2.* -j ACCEPT* should do it i think.

@AlexC_, removing "-i ***" should have done that anyway if you want to stop the firewal type *sudo /etc/init.d/firewall stop*

---

### Post by Catz3705 on 2008-03-28
Thanks frodon:

> **frodon said:**
> *iptables -A TRUSTED -p tcp -s 192.168.2.* -j ACCEPT* should do it i think.

@AlexC_, removing "-i ***" should have done that anyway if you want to stop the firewal type *sudo /etc/init.d/firewall stop*


I'll certainly give this code a try.  Firestarter on my Gutsy machine blocks my network machines and won't remain stopped.  Even the XP firewalled machines don't remain stable eventhough the LAN IP's are set to be trusted. The Gutsy platform is a training deck and as such, can be sacrificial as needs be.

I appreciate the prompt response,

-met-
Catz3705

---

### Post by frodon on 2008-03-28
And if you know the computers of your network you have still the opportunity to filter using MAC address or if you want even more security you can use both but it may become long to write all these rules :)

BTW in the line i gave you i forgot the -i eth0, so it would be more something like :
```
iptables -A TRUSTED -i eth0 -p tcp -s 192.168.2.* -j ACCEPT
```

---

### Post by Catz3705 on 2008-03-28
frodon:

> **frodon said:**
> And if you know the computers of your network you have still the opportunity to filter using MAC address or if you want even more security you can use both but it may become long to write all these rules :)

BTW in the line i gave you i forgot the -i eth0, so it would be more something like :
```
iptables -A TRUSTED -i eth0 -p tcp -s 192.168.2.* -j ACCEPT
```

I kinda figured that out when executing the code returned an error message that the host could not be found.  Also in my case, the additional note about stopping Firestarter needed to be changed to read: /etc/init.d/firestarter stop. 

Security is not too big an issue since the home LAN  is not exposed to the wild. The internet only sees the IP address set by the  provider and the wireless system does not broadcast the network  SID. 

The other main task has been to get the Gutsy platform to see the Windows shares and the Windows machines be able to see and write to selected Gutsy shares. I' ve just about got that working correctly. 

I plan to convert one of the other XP platforms to Ubuntu 7.10 or 8.04 and make sure that the two Linux platforms can read and write to each other as well as relating to the rest of the LAN. The ultimate object will be to take all but two machines off Windows. 

Thanks again for taking your valuable time to post the correction,

-met-
Catz3705

---

### Post by frodon on 2008-03-29
You're welcome ;)

If you choose to use this script you should uninstall firestarter completely to avoid problems as it configures iptables too.

---

### Post by Catz3705 on 2008-03-30
frodon:

The recognition problem is persistant. Disengaging (stopping) firestarter allows the local LAN pc's to see each other and exchange data. (I did discover from other posts that the when Firestarter is stopped, the GUI should be minimized and not turned off.)

> BTW in the line i gave you i forgot the -i eth0, so it would be more something like :
Code:

iptables -A TRUSTED -i eth0 -p tcp -s 192.168.2.* -j ACCEPT

Executing the above code results in the error message :

 "iptables v1.3.6: host/network `192.168.2.*' not found"

Is it possible that the network host/router at 192.168.1.1 or the workgroup is not being referenced?

With iptables/Firestarter turned off the network shares including the Gutsy platform are interactively visible.

Your views. . .?

-met-
Catz3705

---

### Post by Catz3705 on 2008-03-30
frodon:

Additional note:

> Is it possible that the network host/router at 192.168.1.1 or the workgroup is not being referenced?

The network router dynamically assigns IP address 192.168.2.100 thru 192.168.2.255 to members of the workgroup and Windows pc's.

FYI,

-met-
Catz3705

---

### Post by frodon on 2008-03-30
It's the main problem with dynamic adresses and home network. I think the rule i gave you doesn't work but i'm sure allowing a range of IP is possible with iptables.

You can try that, i never tested this though :
```
iptables -A TRUSTED -i eth0 -m iprange --src-range 192.168.2.100-192.168.2.255 -j ACCEPT  
```

---

### Post by Catz3705 on 2008-03-30
frodon:

> **frodon said:**
> It's the main problem with dynamic adresses and home network. I think the rule i gave you doesn't work but i'm sure allowing a range of IP is possible with iptables.

You can try that, i never tested this though :
```
iptables -A TRUSTED -i eth0 -m iprange --src-range 192.168.2.100-192.168.2.255 -j ACCEPT  
```

Execution results in the error message:

"iptables: no chain/target/match by that name"

The default Gateway is 192.168.2.1, DHCP server is 192.168.2.1, DNS servers are 192.168.1.1, and the subnet mask is 255.255.255.0

The trusted IP address range on the firewall of the primary network pc is "192.168.2.1 To 192.168.2.255"(McAfee Personal Firewall, Windows XP firewall disengaged)

iptables blocks the network range of addresses unless stopped.

I also noticed that the Firestarter Local Network Device  preferences are greyed-out. ( Enable internet connection sharing and  Enable DHCP for the local network options)

Is there other information on this Gutsy platform  that I can provide that will help in diagnosing the problem?

Thanks for your patience and persistance,

-met-
Catz3705

---

### Post by frodon on 2008-03-31
First thing is to use one or the other beteween the script and firestarter as they really don't play well together.

Second you just need to find the good syntax to allow your range of ip, so i think a bit of googling should quicly give you the solution for this as i'm sure you're not the only one using iptables with a LAN network.

---

### Post by Catz3705 on 2008-03-31
frodon:

At this juncture I haven't implimented your script. I've been trying to work through the processes that are in place in v7.10. Resorting to a custom firewall (even one that is well prepared)  is another tier of effort and risk.

> **frodon said:**
> First thing is to use one or the other beteween the script and firestarter as they really don't play well together.

Second you just need to find the good syntax to allow your range of ip, so i think a bit of googling should quicly give you the solution for this as i'm sure you're not the only one using iptables with a LAN network.

I've taken some time to do preliminary Google searching on this topic with good results ---- I should have asked you about this earlier and saved us both some time and effort.

From  a discussion on "http://forums.pcper.com/showthread.php?t=432469" , I lifted the following information:

> IP Addresses

Opening up a whole interface to incoming packets may not be restrictive enough and you may want more control as to what to allow and what to reject. Lets suppose we have a small network of computers that use the 192.168.0.x private subnet. We can open up our firewall to incoming packets from a single trusted IP address (for example, 192.168.0.4):

Code:
# Accept packets from trusted IP addresses
 iptables -A INPUT -s 192.168.0.4 -j ACCEPT # change the IP address as appropriate

Breaking this command down, we first append (-A) a rule to the INPUT chain for the source (-s) IP address 192.168.0.4 to ACCEPT all packets (also note how we can use the # symbol to add comments inline to document our script with anything after the # being ignored and treated as a comment).

Obviously if we want to allow incoming packets from a range of IP addresses, we could simply add a rule for each trusted IP address and that would work fine. But if we have a lot of them, it may be easier to add a range of IP addresses in one go.

To do this, we can use a netmask or standard slash notation to specify a range of IP address. For example, if we wanted to open our firewall to all incoming packets from the complete 192.168.0.x (where x=1 to 254) range, we could use either of the following methods:

Code:
# Accept packets from trusted IP addresses
 iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT  # using standard slash notation
 iptables -A INPUT -s 192.168.0.0/255.255.255.0 -j ACCEPT # using a subnet mask

Finally, as well as filtering against a single IP address, we can also match against the MAC address for the given device. To do this, we need to load a module (the mac module) that allows filtering against mac addresses. Earlier we saw another example of using modules to extend the functionality of iptables when we used the state module to match for ESTABLISHED and RELATED packets. Here we use the mac module to check the mac address of the source of the packet in addition to it's IP address:

Code:
# Accept packets from trusted IP addresses
 iptables -A INPUT -s 192.168.0.4 -m mac --mac-source 00:50:8D:FD:E6:32 -j ACCEPT

First we use -m mac to load the mac module and then we use --mac-source to specify the mac address of the source IP address (192.168.0.4). You will need to find out the mac address of each ethernet device you wish to filter against. Running ifconfig (or iwconfig for wireless devices) as root will provide you with the mac address.

This may be useful for preventing spoofing of the source IP address as it will allow any packets that genuinely originate from 192.168.0.4 (having the mac address 00:50:8D:FD:E6:32) but will block any packets that are spoofed to have come from that address. Note I'm unsure whether mac address filtering works across the internet but it certainly works fine on a LAN.

To try out any of the above examples, simple add the appropriate line to your firewall script we made in the last installment, save and rerun it. Then test to make sure the rule is working as you would expect.

To summarize, in this installment we have seen how we can add rules to our firewall to filter against packets matching a particular interface or a source IP address. This allows full access through our firewall to certain trusted sources (machines). In the next installment we'll look at how we can filter against protocols and ports to further refine what incoming packets we allow and what we block.

Quoted with acknowledgement to:
Ned Slider, Moderator
Copyright ©2000 - 2008, Jelsoft Enterprises Ltd. 
© PC Perspective 2000 - Present 



As you can see there are some interesting lines of code to try regarding the issue of Trusted IP addressing.

I also found a tutorial on Firestarter which indicates that I probably should uninstall and restart with the purpose of resetting the Network Internet connection sharing (ref. [http://arstechnic.com/etc/linux/2003.linux.ars-12172003-3.html](http://arstechnic.com/etc/linux/2003.linux.ars-12172003-3.html)).

This, along with your assistance materials, is a lot more info to bring to bear on the problem than I had earlier.

Thanks for your really useful pointers,

-met-
Catz3705

---

### Post by frodon on 2008-03-31
Sorry but i don't know how firestarter configures iptables and what i know is that adding iptables rules on top of firestarter may not work as expected.

You have to make choice, keep firestarter and try to configure it to fit your needs or uninstall it completely and use the script provided here.

---

### Post by Catz3705 on 2008-03-31
frodon:

It makes sense that there is an element of unpredictability here. I have already experienced the problems of trying to get
around the Firestarter interface and inject code.

According to the arstechnica article, I *should* be able to configure Firestarter to do the things we've been talking about. If that ultimately fails, 
then plan "B" is to remove Firestarter and deal with iptables as you suggested. The additional codes that I listed in the previous post should also help with the solution.

I'll post additional results after I run through the alternatives.

Thanks again. I hope this exchange has been useful for both of us.

Yogi Berra, the Baseball player, once said: "It ain't over, 'til it's over. . ."

-met-
Catz3705

---

### Post by Catz3705 on 2008-03-31
frodon:

Nothing succeeds like success! It's amazing what two or three lines of code can do to change a resistant problem.

I went directly to "Plan B" and removed Firestarter and rebooted the system.

> Code:
# Accept packets from trusted IP addresses
>>>>iptables -A INPUT -s 192.168.0.4 -j ACCEPT # change the IP address as appropriate
....
Code:
# Accept packets from trusted IP addresses
iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT # using standard slash notation
>>>>iptables -A INPUT -s 192.168.0.0/255.255.255.0 -j ACCEPT # using a subnet mask
....
Finally, as well as filtering against a single IP address, we can also match against the MAC address for the given device  . . . .Here we use the mac module to check the mac address of the source of the packet in addition to it's IP address:

Code:
# Accept packets from trusted IP addresses
>>>>iptables -A INPUT -s 192.168.0.4 -m mac --mac-source 00:50:8D:FD:E6:32 -j ACCEPT
....


I entered the first two lines of code as checked with my real LAN parameters. iptables accepted the entries.  Listing the resulting iptables rules (iptables -L)  revealed that new rules were present. I followed with the third line which uses the MAC address of the source IP address as a filter to prevent spoofing.  Re-listing the iptables rules showed that all tree entries were accepted.

The LAN pc's, network icon and workgroup icon all became visible and accessible (this Gutsy platform and two other Windows platforms were running on the network for test purposes.)

Despite the steep learning curve, I believe I'm headed in the right direction and gaining fluid control of the major aspects of my network. I just received another harddisk for use in creating a second Ubuntu platform so that I can perfect Linux-to-Linux operations within the net. Solving controlled firewalling of these systems is a fundamental issue.

Thanks again for your help and pointers,

-met-
Catz3705

---

### Post by frodon on 2008-04-01
You're welcome, feel free to post your questions if you have other problems.

BTW, depending of the file sharing protocol you use you can even restrict more the access to accept traffic of the IP adress with the matching match address and only on port used by file sharing apps.
In general users with this tutorial see that configuring iptables directly is really easy for someone interested in computers and obviously it is more secure i think than using firestarter were you can't control all the created rules.

---

### Post by El_Belgicano on 2008-04-03
Hello,
I'd like to configure a basic firewall that fits my needs, I'm using the basic script Frodo provided in the first post, but I'm such a noob with iptables that I'm requesting some advice, I got Apache, MySQL installed and my main concern is that my local server could be accessible only from the local network.
I did the tests (nmap and the 2 sites provided), and apparently, my ports 80 and 23 remains open, no matters what rule I try in firewall.bash. I read about the "conflict" iptable vs firestarter, does firestarter keeps some configuration file somewhere, I had it installed some time ago, but remove it after reading this thread ...
thanks in advance ...

---

### Post by Catz3705 on 2008-04-04
frodon:

FYI . . .follow-up note. . .

> **Catz3705 said:**
> 
Despite the steep learning curve, I believe I'm headed in the right direction and gaining fluid control of the major aspects of my network. I just received another harddisk for use in creating a second Ubuntu platform so that I can perfect Linux-to-Linux operations within the net. Solving controlled firewalling of these systems is a fundamental issue.


I've set up the second Ubuntu 7.10 platform which is a pure linux install on a clean drive. The iptables rules recognizing the LAN were applied along with the appropriate Samba configuration. The result was a second immediate success and the new platform is now integrated into the LAN.  Shares are properly visable and accessible.

There are other minor technical issues, but LAN interactivity is not in the mix.

Thanks,

-met-
Catz3705

---

### Post by frodon on 2008-04-04
> **El_Belgicano said:**
> Hello,
I'd like to configure a basic firewall that fits my needs, I'm using the basic script Frodo provided in the first post, but I'm such a noob with iptables that I'm requesting some advice, I got Apache, MySQL installed and my main concern is that my local server could be accessible only from the local network.
I did the tests (nmap and the 2 sites provided), and apparently, my ports 80 and 23 remains open, no matters what rule I try in firewall.bash. I read about the "conflict" iptable vs firestarter, does firestarter keeps some configuration file somewhere, I had it installed some time ago, but remove it after reading this thread ...
thanks in advance ...
First on principle it is normal that a port you allow and where you run a service is shown as open as request on these ports are answered by your running service.
If you could paste the rules you used to allow traffic on port 80 and 23 i could help you better.
Basically you need to allow trafic for port 80 and 23 **but** as you want only this to be available for your local network then you have to restrict this to the IPs of you local network only so your case is in some way similar to Catz3705 and i would suggest you to refer to this post where he posted how he allowed traffic based on IP range :
[http://ubuntuforums.org/showpost.php?p=4625908&postcount=216](http://ubuntuforums.org/showpost.php?p=4625908&postcount=216)

> **Catz3705 said:**
> frodon:

FYI . . .follow-up note. . .



I've set up the second Ubuntu 7.10 platform which is a pure linux install on a clean drive. The iptables rules recognizing the LAN were applied along with the appropriate Samba configuration. The result was a second immediate success and the new platform is now integrated into the LAN.  Shares are properly visable and accessible.

There are other minor technical issues, but LAN interactivity is not in the mix.

Thanks,

-met-
Catz3705Thanks for the follow-up, this is really kind and appreciated :)

I'm glad to know that you are now autonomous with iptables, as you see handling iptables directly is far more powerful and not that difficult ultimately.

---

### Post by Catz3705 on 2008-04-04
frodon:

In a very quick assessment and based on some of your assertions, I elected to work directly with iptables.  Command line coding offered the most precise way to tune the firewall eventhough it required some quick training and research. I'm not a stranger to this since I've been actively programing since the early days of Microsoft BASIC and DOS. Not everyone wants to be bothered with the tediousness and precision of coding;  Firestarter GUI is one of the obvious alternatives for the lay user. 

El_Belgicano  should be able to run "iptables -l "(lower case L)  in a terminal window as root or with "sudo" and list the existing rules.  The results can be pasted between CODE tags in a message for examination. This would involve disengaging from Firestarter and directly addressing iptables. 

If El_Belgicano's server, like my system, is behind a firewalled router and ISP provided connection device, his system should not be visible to the internet at large. He could "flush" the rules and lay out an entirely new custom scheme including mutual recognition and accessibility of his network platforms.

Myabilities in network administration and technical construction lacks depth at this time and I humbly defer to those with greater skills  . . . 

To El_Belgicano: be diligent and patient; you'll get the rewards!

-met-
Catz3705

---

### Post by El_Belgicano on 2008-04-05
@ Catz3705:
You're right on the router point, most of the time I'm connected to my home network who's set up behind a firewall, but I also connect to another network and I'm not sure about the security there, firestarter gets crazy by times (when I had it)  with alerts about "connection attempt blocked" ... so I'm concerned about that network

anyway, thanks for the fast support :)

my rules:
```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

##############
iptables -A INPUT -p tcp --dport 80 -j DROP
iptables -A INPUT -p udp --dport 80 -j DROP

iptables -A TRUSTED -p udp -m udp --dport 4374 -j ACCEPT
iptables -A TRUSTED -p tcp -m tcp --dport 4374 -j ACCEPT

iptables -A INPUT -p tcp --dport 23 -j DROP
iptables -A INPUT -p udp --dport 23 -j DROP

iptables -A INPUT -p udp -m udp --sport 53 -j ACCEPT 
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --sport 53 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT
##############

# End message
echo " [End iptables rules setting]"
```

---

### Post by Catz3705 on 2008-04-05
El_Belgicano:

First of all, due to my limited expertise, It strongly suggest that you review and direct specific questions to frodon concerning your network security issues -- which are by no means trivial.

I would also suggest that you check out the tutorial moderated by Ned Slider on PC Perspectives, [http://forums.pcper.com/showthread.php?t=432469](http://forums.pcper.com/showthread.php?t=432469), "Linux Firewall (iptables) Tutorial". Just as frodon has done earlier in his tutorial, Ned Slider presents step-by-step iptables firewall preparation in uncomplicated language  illustrated with pasteable examples for direct application. ***[Note: Ned Slider is writing in the CentOS system context. Illustrations and examples found in his tutorial will have to be adapted to Ubuntu iptables command structure]***

Slider's explaination of *what* he is doing with particular coding imparts educational depth rather than exercises in blind cutting and pasting.

( In my humble experience, knowing what and why you are doing something gets you out of trouble later on and, in some instances, may prevent exposure to the malady in the first place. "Forewarned is forearmed!" (I don't know who said that, it maybe cliche,  but it's good advice. . . ))

As I see your query, you are looking to protect your personal LAN and permit Trusted contact with an external network.

I would conjecture that the examples I cited earlier in post #213  could definitely be used for your personal LAN (taking into consideration the CentOS context and where it may apply to Ubuntu) as I have directly used them successfully on an experimental setup. There are some port manipulations in the Slider article that would also be worth some study.

frodon suggested also using MAC address screening (as did Ned Slider) to give an additional tier of security to the Trusted IP recognition process. Your friendly external network would likely have to provide you with this info. I don't know if the blocking process is carried out quietly or is verbose which produces the annoying alerts that you experienced. Firewall systems typically log probe attempts that are blocked as well as deliver overt warnings. 

Eventhough I have written in generalities, I hope this brief discussion will point you to the details that you want to incorporate into your firewall development. 

A sus ordenes,

-met-
Catz3705

---

### Post by frodon on 2008-04-06
These rules :
```
##############
iptables -A INPUT -p tcp --dport 80 -j DROP
iptables -A INPUT -p udp --dport 80 -j DROP

iptables -A TRUSTED -p udp -m udp --dport 4374 -j ACCEPT
iptables -A TRUSTED -p tcp -m tcp --dport 4374 -j ACCEPT

iptables -A INPUT -p tcp --dport 23 -j DROP
iptables -A INPUT -p udp --dport 23 -j DROP

iptables -A INPUT -p udp -m udp --sport 53 -j ACCEPT 
iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --sport 53 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT
#############
```
should be rather like the following if you wanr to keep the spirit of the script :
```
iptables -A TRUSTED -p tcp --dport 80 -j DROP
iptables -A TRUSTED -p udp --dport 80 -j DROP

iptables -A TRUSTED -p udp -m udp --dport 4374 -j ACCEPT
iptables -A TRUSTED -p tcp -m tcp --dport 4374 -j ACCEPT

iptables -A TRUSTED -p tcp --dport 23 -j DROP
iptables -A TRUSTED -p udp --dport 23 -j DROP

iptables -A TRUSTED -p udp -m udp --sport 53 -j ACCEPT 
iptables -A TRUSTED -p tcp -m tcp --sport 53 -j ACCEPT

```No need to add OUTPUT chain rules as the script don't block outgoing  traffic, in the same way no need to handle INPUT chain directly as all input packets are send to the TRUSTED chain, so you can just handle the TRUSTED chain for this purpose which is how the script is suposed to be extended.

---

### Post by Catz3705 on 2008-04-06
frodon:

After some experimentation with my Ubuntu platforms with manually applied, temporary code, I've implemented your firewall solution on one of the systems for permanent use.

The initial run did not allow the home LAN to be visible (this was anticipated). Some trial and error coding brought up the two Ubuntu platforms and a final modification of your code from our first post yielded the remaining Windows XP test system:

> **frodon said:**
> *iptables -A TRUSTED -p tcp -s 192.168.2.* -j ACCEPT* should do it i think.
the firewal type *sudo /etc/init.d/firewall stop*

My changes were:

```

# Allow ip 
iptables -A TRUSTED -p tcp -s 192.168.2.0/24 -j ACCEPT
iptables -A TRUSTED -p tcp -s 192.168.2.1 -m mac --mac-source [applicable mac address inserted] -j ACCEPT

```

The results were the same as when I applied the sample codes: 

```
# Accept packets from trusted IP addresses
>>>>iptables -A INPUT -s 192.168.0.4 -j ACCEPT # change the IP address as appropriate
....
Code:
# Accept packets from trusted IP addresses
iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT # using standard slash notation
>>>>iptables -A INPUT -s 192.168.0.0/255.255.255.0 -j ACCEPT # using a subnet mask
....
Finally, as well as filtering against a single IP address, we can also match against the MAC address for the given device . . . .Here we use the mac module to check the mac address of the source of the packet in addition to it's IP address:

Code:
# Accept packets from trusted IP addresses
>>>>iptables -A INPUT -s 192.168.0.4 -m mac --mac-source 00:50:8D:FD:E6:32 -j ACCEPT
....( ref: Slider, PC Perspectives)

```

BTW this coding that you supplied did work once your firewall solution was in place:

[QUOTE= frodon]  
It's the main problem with dynamic adresses and home network. I think the rule i gave you doesn't work but i'm sure allowing a range of IP is possible with iptables.

You can try that, i never tested this though :
```

iptables -A TRUSTED -i eth0 -m iprange --src-range 192.168.2.100-192.168.2.255 -j ACCEPT
```
[/QUOTE]
....

(It picked up the Ubuntu platforms and omitted the Win XP system. 
It probably needed to be tweaked to include the full range from 192.168.2.1 thru 255.
The two lines that I mentioned above plus "iprange" addition seemed  responsible for making all the test platforms visible 
including the network and workgroup.)

I modified it and added it to the "Allow ip" section of "firewall.bash" as:

```
 
iptables -A TRUSTED -i eth0 -m iprange --src-range 192.168.2.1-192.168.2.255 -j ACCEPT

```

Rebooting the system revealed the new firewall to be active and functional. NmapFE also showed the new firewall to be functioning as to scans.

I should be able to distribute the firewall solution to the other Ubuntu platforms in my network as needed.


Thanks again for the excellent programming and tutorial --- and most of all, your considerate and timely responses,

-met-
Catz3705

---

### Post by durus on 2008-04-07
Hi I am trying to fix a rule to allow connections to my vsftpd server with TLS/SSLconnections. Do you have any idea of how i can fix this ?

---

### Post by frodon on 2008-04-07
it depends on which port you run your FTP server, anyway all the answers about your problem are in page 18 of this thread.
Always think to search in this thread using the search features, many questions have been answered already and many problem solved.

---

### Post by durus on 2008-04-08
Thank you. It works now for active connections but no passive connections with this settings
```
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```

But I do not understand how it works, can someone explain ? 
1. Why do I care about sport at all ? Is it not enough to only care about my server ports ?
2. Is not this insecure ? 
```
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT

```
Does this mean that after a connection he can connect to witch ever port he wants on my computer if he chose to use port 20 ?
I thought that I should use dport for all in trafic and sport/dport for all out traffic.

---

### Post by frodon on 2008-04-08
For the 3 first rules sport is indeed useless and one should use dport instead, sport are more used when filtering outgoing connection which is not the case here.
If you ask me i would tell you that the simple fact to run a service make your computer more vulnerable so you can limit the risk but not eradicate it.

For passive ports you may need to add the ip_conntrack module before the ip_conntrack_ftp one.

For me you don't need to allow ESTABLISHED and RELATED as they are already allowed earlier in the script so for me only the first line is useful and at home i only open dport 21 in input to allow ftp traffic.

BTW i guess ALLOWED_PORT is a chain you created right ?

---

### Post by durus on 2008-04-08
It still does not work. As you guessed ALLOWED_PORT is a chain. You can my rules here. I have not removed dose last rules as you mentioned but I will do that when every thing is working.

```
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack #added for ftp passive mode ?
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# Create chains
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N ALLOWED_PORT

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL

# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# FIREWALL Chain start _____________ 

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all packages to chains
iptables -A FIREWALL -j TRUSTED
iptables -A FIREWALL -j ALLOWED_PORT
# DROP all other packets
iptables -A FIREWALL -j DROP
# _____

# TRUSTED Chain start _____________ 
# VNC
iptables -A TRUSTED -i eth0 -s 192.168.0.2 -p tcp -m tcp --dport 5901 -j ACCEPT 

# ____

# ALLOWED_PORT chain
# SSH
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
# FTP
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT


# _____

# End message
echo " [End iptables rules setting]"
```

---

### Post by frodon on 2008-04-08
```
# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL

# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP
```This part **must** be after FIREWALL chain description.

The following rules are not needed :
```
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```

---

### Post by durus on 2008-04-08
Hmm, I can't understand why those should be after the firewall chain. But ok i tried that and it does still not work for passive connections.

```
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack #added for ftp passive mode ?
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# Create chains
iptables -N FIREWALL
iptables -N TRUSTED
iptables -N ALLOWED_PORT

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT


# FIREWALL Chain start _____________ 

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all packages to chains
iptables -A FIREWALL -j TRUSTED
iptables -A FIREWALL -j ALLOWED_PORT
# DROP all other packets
iptables -A FIREWALL -j DROP
# _____

# TRUSTED Chain start _____________ 
# VNC
iptables -A TRUSTED -i eth0 -s 192.168.0.2 -p tcp -m tcp --dport 5901 -j ACCEPT 

# ____

# ALLOWED_PORT chain
# SSH
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
# FTP
iptables -A ALLOWED_PORT -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT


# _____

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# End message
echo " [End iptables rules setting]"
```

---

### Post by frodon on 2008-04-08
I can't guaranty that where you placed the lines i told you to move it works. you should stick with original script disposition. It might work but i have not tested this so i can't guaranty it works if placed at the end of the file.

Except that you have almost the same configuration that many users uses for their FTP server so it should work without any problem.

---

### Post by durus on 2008-04-09
I tested it with the original script. And it does still not work with passive mode. I am  starting to think that it can be some other problem. So if passive mode works when I am flushing iptables sudo /etc/init.d/firewall stop, but not when i am running sudo /etc/init.d/firewall start, can I be sure that it is a iptable problem. I am using FileZilla in windows when I am testing, and I choose to connect passive or active with that program. My ftp server is vsftpd and this is my config.
```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
pasv_address=192.168.0.3
pasv_min_port=50505
pasv_max_port=50510
ftpd_banner=VÃkommen till min ftpserver
chroot_local_user=YES
ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd

## SSL - krypterad trafik
ssl_enable=YES
force_local_logins_ssl=YES
force_local_data_ssl=YES
rsa_cert_file=/etc/ssl/vsftpd/vsftpd.pem
```

You can see my new rules here. Can't someone send your rules if it is working for you, or test my rules ?
```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack #added for ftp passive mode ?
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# SSH
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
# FTP
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 21 -j ACCEPT


# End message
echo " [End iptables rules setting]"
```

Thank you for helping me
Durus

---

### Post by frodon on 2008-04-09
I have these rules or pretty much the same and it works for me although i never checked filezilla to see if i use passive mode or not, i kept the default configuration.

---

### Post by aparigraha on 2008-04-15
@durus

I had problems as well with TLS/SSL as seen on page 18 on this thread... and no, i was never able to fix it. Seems TLS/SSL uses different port ranges... (see page 18 )

But I narrowed down the ports open for ftp transfer, and i only let them be open after port-knocking. Google port-knocking. It might help u.

---

### Post by bigtoedsloth on 2008-05-11
Thanks for your help in setting up iptables ... it has made things very straightforward for me.

I had an issue starting azureus once the firewall was set.  The required port wasn't being opened.  To fix it I changed
```
# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

to

```
# Allow ESTABLISHED, RELATED and NEW incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT

```

Is that a sensible thing to do?

My rules for azureus are simply
```
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport <port> -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport <port> -j ACCEPT

```

---

### Post by frodon on 2008-05-11
You shouldn't need the NEW state in the rule, i use azureus too and don't need it.

Only the 2 TRUSTED rules should be needed.

---

### Post by bigtoedsloth on 2008-05-11
> **frodon said:**
> You shouldn't need the NEW state in the rule, i use azureus too and don't need it.


Does that mean that the port you use with azureus is already established when you start your iptables?  Doesn't NEW mean "not already established or related"?   With your original script I had to stop the firewall once azureus was running, test the port (with azureus' NAT/firewall test), then restart the firewall.

I guess I'm really trying to understand more about the rules and the iptables command-line options.  My zero knowledge of iptables led me to assume that the NEW state allowed new connections, hence why I added it in.  But that did cure my problem ...

---

### Post by frodon on 2008-05-11
You shouldn't need it, azureus just require you to open the chosen azureus port in the TRUSTED chain.
So on theory you just need to add 2 rules in the TRUSTED chain to allow the azureus input port on tcp/udp and azureus is supposed to work correctly after this.

---

### Post by bigtoedsloth on 2008-05-11
> **frodon said:**
> You shouldn't need it, azureus just require you to open the chosen azureus port in the TRUSTED chain.


OK.  Thank you for your help, and the clarification on the rules.  I will try something else to fix my azureus problem.

---

### Post by jambalaya on 2008-06-01
Hi.
Thanks for your excellent tutorial and script, worked like a charm.
However, I have a question - what about IPv6? I mean, iptables is for IPv4 only. My sshd listens on tcp6 port 22 (actually I changed that, but suppose it stayed that way), so assuming my router lets IPv6 through) is it possible that actually anyone can try to connect to that port? iptables is not blocking that. I think I have seen ip6tables mentioned somewhere. If it exists, is there any good reason why does it not come with Ubuntu as a default? IPv6 does, so shouldn't some protection for it too?
Should I have IPv6 enabled anyways? I do have that now, but is this necessary ? (I haven't experienced any delays in network usage with firefox or any other app)
Thanks you.

---

### Post by frodon on 2008-06-02
I'm not sure ip6tables is included yet in ubuntu, will check this once at home.

It is at my job on RedHat.

---

### Post by ssc351 on 2008-06-10
Do i need to do anything special for virtualbox shared folders and printing between Ubuntu and the Virtual OS (in my case XP pro)...

Here is what I did...not sure if its correct:


#Allow printing from Virtualbox
iptables -A TRUSTED -p tcp -m tcp --dport 9100 -j ACCEPT

I am not sure if I should use 9100 or 631 or if either is even neccessary or correct. (I can't test this for awhile as I am away from these printers).  But the Virtualbox shared folders seem to work without even doing anything...shouldn't I not be able to access this folder without permissions in my firewall.bash script.  Furthermore, do I need to allow an IP from the Virtual machine (mine reads the gateway as 10.0.2.2 and the ip as 10.2.2.15)

Lastly running nmap brought up these open ports...is this opening up my system to anything?  I am not even sure if I use telnet:
PORT     STATE SERVICE    VERSION
23/tcp   open  telnet?
80/tcp   open  tcpwrapped
8080/tcp open  tcpwrapped

---

### Post by frodon on 2008-06-11
Don't forget that using nmap to test your computer you must run it from another computer to get real results.
About virtual box i don't really know, i would say test and see how it works :)

---

### Post by ssc351 on 2008-06-11
> **frodon said:**
> Don't forget that using nmap to test your computer you must run it from another computer to get real results.
About virtual box i don't really know, i would say test and see how it works :)


Shouldn't I close up that telnet port if I don't use it?  Or do I use it and I don't it?

---

### Post by frodon on 2008-06-12
If you use the script given on first post then this port is already closed, that's why i asked how you used nmap to be sure it didn't report false positive.

---

### Post by ssc351 on 2008-06-12
> **frodon said:**
> If you use the script given on first post then this port is already closed, that's why i asked how you used nmap to be sure it didn't report false positive.

I just typed my ip address (which I got off shields up) into the target and hit "scan"  Didn't touch anything else.

I should I also mention I am going through a wireless router, so I am not sure if that effects anything.

---

### Post by frodon on 2008-06-12
Sure it effects if you use shields up, if you configured your router as NAT then shields up is testing your router not your computer.

That's the main problem when testing your firewall, anyway that means that you are even more protected because your router already restrict the number of ports forwarded to your computer.

If you want to test through nmap, you must test your firewall running nmap from another computer on your local network otherwise you may get wrong results.

---

### Post by steveydoteu on 2008-10-29
I have followed the guide exactly as instructed, bar adding one or two ports to allow.

But get the following error:

```
$ sudo /etc/init.d/firewall start
Iptables rules creation: iptables: Invalid argument
 [End iptables rules setting]
```

Any suggestions?

---

### Post by frodon on 2008-10-29
You have a typo or syntax error somewhere in firewall.bash.

---

### Post by steveydoteu on 2008-10-29
```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow IRC
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 6667 -j ACCEPT 
iptables -A INPUT -i eth0 -p udp -m tcp --sport 133 -j ACCEPT # identification port iptables -A OUTPUT -o eth0 -p udp -m tcp --dport 133 -j ACCEPT # identification port

iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT 
iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

---

### Post by frodon on 2008-10-29
You can first start by deleteting all OUTPUT lines which are useless since OUTPUT packets are not dropped by default in this config.

Then replace all INPUT chain rules at the end of the file by TRUSTED chain rules as in the script i provide new rules must be added TO the TRUSTED chain due to INPUT packets being all send through FIREWALL chain then finally to TRUSTED chain which aims to add your custom rules.

Finally i'm not sure if comments at the end of the line works or not, i guess yes but just in case put tyhem on a dedicated line.

---

### Post by steveydoteu on 2008-10-29
> **frodon said:**
> You can first start by deleteting all OUTPUT lines which are useless since OUTPUT packets are not dropped by default in this config.

Then replace all INPUT chain rules at the end of the file by TRUSTED chain rules as in the script i provide new rules must be added TO the TRUSTED chain due to INPUT packets being all send through FIREWALL chain then finally to TRUSTED chain which aims to add your custom rules.

Finally i'm not sure if comments at the end of the line works or not, i guess yes but just in case put tyhem on a dedicated line.

So you are telling me using the examples in the original post is not correct?

---

### Post by 080801jk on 2008-10-30
[&#21271;&#20140;&#23815;&#25991;&#21306;&#31649;&#36947;&#30095;&#36890;](http://www.datangshutong.com/bjcwqgdst.htm)[**&#21271;&#20140;&#20016;&#21488;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.datangshutong.com/bjftqgdst.htm)[**&#21271;&#20140;&#28023;&#28096;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.datangshutong.com/bjhdqgdst.htm)[**&#21271;&#20140;&#26397;&#38451;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.datangshutong.com/bjcyqgdst.htm)[**&#21271;&#20140;&#26397;&#38451;&#31649;&#36947;&#30095;&#36890;**](http://www.datangshutong.com/bjcygdst.htm)

---

### Post by frodon on 2008-10-30
> **steveydoteu said:**
> So you are telling me using the examples in the original post is not correct?The examples and the script are 2 different things. The example have for only purpose to make you understand how iptables work.


In the script i provide, i have already chosen a layout for the script so if you want to use it and tweak it you must respect the layout put in place. In the script i give INPUT chain is not supposed to be handled directly as i send all INPUT packets through FIREWALL chain which apply the rules that will allow you almost all you need then all the remaining packets (not allowed yet) are sent to the TRUSTED chain to see if one rule of the TRUSTED chain can allow them if not they are finally DROP at the end of the FIREWALL chain.
This is why in my script all custom rules MUST be added to the TRUSTED chain at the end of the file.

INPUT => FIREWALL => TRUSTED => if not allowed via previous chains then DROP

---

### Post by steveydoteu on 2008-10-30
I copy and paste the code below in to the file as instructed, yet you are now telling me that this is in fact not correct? Even though it **is **the script you speak of.

> **frodon said:**
> 
```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi 

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Allow amule
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

---

### Post by frodon on 2008-10-30
> **steveydoteu said:**
> I copy and paste the code below in to the file as instructed, yet you are now telling me that this is in fact not correct? Even though it **is **the script you speak of.No

You are a bit misleading because everything in what you posted made me think that you were using the script you posted in post #252 and now you are telling that you are not using this one but the default one.

I'm completely lost sorry, i don't understand what script you are using.

---

### Post by sanskaras on 2009-02-02
I copied and pasted the script from your advanced tutorial but am having troubles with the bittorrent download client.  Everything else works fine but the client will just sit there stalled until I stop the firewall.

Not quite sure where to look?

---

### Post by Kalle370 on 2009-03-08
hey i get this: 
root@kubuntu:~# sudo /etc/init.d/firewall start   
sudo: /etc/init.d/firewall: command not found     

what i do wrong?

---

### Post by androidkerra on 2009-03-09
very nice post, gotta try this one out :D

i'll be back with the results...

*hoping not to run on any problems :D

---

### Post by frodon on 2009-03-09
> **Kalle370 said:**
> hey i get this: 
root@kubuntu:~# sudo /etc/init.d/firewall start   
sudo: /etc/init.d/firewall: command not found     

what i do wrong?You should have forgotten one step of the tutorial. Here it seems that you either miss the /etc/init.d/firewall or it has not the +x rights.

---

### Post by mellowd on 2009-04-14
Excellent HOWTO. Good work

---

### Post by gregor171 on 2009-04-16
We had a talk about IP blacklist before, so this is what I am using now, by also changing ssh port away from 22, closing it to IP/PORT or MAC/PORT I do not have any unwelcome visits.

This is a code for blacklist:
```
# $IP_BLACKLIST is a file name with ip addresses on a row by row base
	if [ "$IP_BLACKLIST" != "" ]; then
		if [ -f $IP_BLACKLIST ]; then
			# file exists
			echo "applying custom IP blacklist...."
			$IPT -N ipblacklist #-N creates a New, user defined chain (blacklist for example).
			while read line
			do
				#echo $line
				$IPT -A ipblacklist -s $line -j DROP
			done < "$IP_BLACKLIST"
		else
			echo "Error reading custom blacklist file:"	
			echo "$IP_BLACKLIST"
		fi
	fi
```

---

### Post by frodon on 2009-04-17
Thanks all, i'm glad it helped.

---

### Post by neverMINT on 2009-04-20
Hi Frodon,

just have to say thank you for this excellent HOWTO! Your Howto is one of very few documentations which are compact, easy to understand and most important - it's easy to implement.

There's no need to spend hours with "try & error" to find out how to migrate the given examples onto my own machine! Your solution works pretty well :-)


I just have a question about NAT, because my server is also working as an NAT Server which is used by six (internal LAN) clients to connect to the internet. Working solution.

When I try to implement your firewall solution I have trouble with the other clients which can't connect to the server and to the internet anymore.
When I stop the firewall service, prevent it from starting up automatically and delete the files "firewall.bash, etc..." I still have the same problem as before. Tried several reboots but it took no effect.

The firewall is implemented exactly as you are describing it in this HOWTO - no changes or mods.
The server has been set up from the scratch and still never had any firewall installed.
The question is, if there may be any other files or hidden options to be set to make the firewall changes dissappear so that NAT will work again?

Very interresting is if there might be any way that let's the Firewall do it's job and let's the server still provide NAT Services?
I don't want to remove the firewall because it's working really good. That's why I'm searching for a solution to gets your Firewall and the NAT functionality together on one server :-)

Thank you so much in advance!!

---

### Post by frodon on 2009-04-20
In the firewall script i give in first post you can see the following :
```
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP
```It means that FORWARD packets are all dropped so this is normal than connection sharing don't work anymore.
If you want to transfer all ports to your LAN you can just comment this line and add the following instead :
```
iptables -A FORWARD -j ACCEPT 
# hide computers behind the firewall 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
```You have some basis on first post about FORWARD packets, they are those who handle/create the NAT feature.

---

### Post by neverMINT on 2009-04-20
Hi Frodon,

wow... that's what I'd call "JUST IN TIME"!!
Thanks for your very quick response! :-) Everythings running as desired, now!

Firewall AND Nat-Service are both working together on one single Server now :-) . GREAT!!

Thank you once again for your support and for this excellent HOWTO!! Helped me very much :-)

---

### Post by gregor171 on 2009-04-20
I actually used Ubuntu Firewal by Robert Pectol for his installation script log etc, but added some corrections from this great guide, ip blacklist...
and made a digg.

---

### Post by hsweet on 2009-05-01
Hi all..

I'm new to Iptables.  This has been very helpful so far.  I want to make a whitelist of sites to let my students access.  I'm still confused.  

I was able to kill Internet access totally today for the classes that just waste time playing games and turn it back on for the others. Hooray. 
Now I want to give those kids a short list of sites related to the class they can access. 

So this line will drop any site not google.
```
iptables -A INPUT -p tcp --source !  google.com -j DROP
```

Do I DROP the FORWARD chain then add rules to ACCEPT sites
or ACCEPT the FORWARD chain than add rules to DROP sites

Or am I completely confused?

---

### Post by psrivats on 2009-08-29
Frodon, thanks for the great writeup.

What do I need to do to open port 22 for ssh in addition to what you have shown?

---

### Post by frodon on 2009-08-30
As SSH is a bit specific, i mean ssh server security must be as strong as possible, i will advice you to write the rule in the way to prevent the so called "brute force" attacks.

So add these lines as the last ones of the TRUSTED chain :
```
iptables -A TRUSTED -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
iptables -A TRUSTED -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP
```
Using these rules you will allow only 8 connections per one minute window on port 22 preventing thus "brute force" attacks as well as opening port 22 ;)

---

### Post by theZoid on 2009-09-07
I would like to add my appreciation for this "how-to"  Very Good !!:)

---

### Post by ssc351 on 2009-11-13
I have been referencing your how to for my iptables and I am kinda stuck.  I have an internet VPN set-up (like bananavpn.com or strongvpn.com)  and I want to still use my firewall but I can't punch a hole in it properly.  I connect fine to the VPN without the firewall up.

From googling it looks like I need port 1723 and 47 open for pptp to pass through properly.  Also, I do not know the VPN servers address just the gateway (or is that the same thing?)  I also have port forwarded the ports on my router so I don't think that is the issue

I originally (without the firewall enabled) just used Network Manger to set it up, put in the gateway address, my username and password and i connected no problem.

Thanks for the help!

---

### Post by centered effect on 2010-02-18
How can I block all outside traffic?  I just want my home machines accessing my server using Samba and ssh for maintenance.  I will also be using my server as a web development machine as well (ie - no need to access the web).

---

### Post by frodon on 2010-02-19
You are a good candidate for my other tutorial, be warned it's a bit more tricky and require more debug effort, nothing impossible though:
[http://ubuntuforums.org/showthread.php?t=668148](http://ubuntuforums.org/showthread.php?t=668148)

---

### Post by frodon on 2010-02-19
You are a good candidate for my other tutorial, be warned it's a bit more tricky and require more debug effort, nothing impossible though:
[http://ubuntuforums.org/showthread.php?t=668148](http://ubuntuforums.org/showthread.php?t=668148)

---

### Post by savin on 2010-04-20
Here am attaching the documentation for dyniptable

---

### Post by HittingSmoke on 2010-05-30
> **frodon said:**
> 
**[SIZE="2"]2.2- Maching commands[/SIZE]**    

The character "!" can be used to specify the oposite. For example a command to avoid all incomming tcp traffic except from the IP 10.42.42.42 is written as follow :
```

iptables -A INPUT -p tcp --source ! 10.42.42.42 -j DROP
```


Just an update for your guide. This command returns an error reading

> Using intrapositioned negation ('--option ! this') is deprecated in favor of extrapositioned ('! --option this')

Had to swap the "!" and the "--source"

---

### Post by frodon on 2010-05-30
Thanks for the head up i will update this right now.

---

### Post by HittingSmoke on 2010-05-30
> **frodon said:**
> Thanks for the head up i will update this right now.

You're welcome, thanks for the great guide. iptables can be very confusing and one of the harder parts of Linux to find info on. This made setting up a basic set of rules nice and easy.

---

### Post by e-San on 2010-09-09
Still can not get it to work.

nmap local:
> Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-09-09 11:30 CEST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 991 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
3306/tcp open  mysql
9091/tcp open  unknown

Scanning from other machine:
```
san@eeepc:~$ nmap 192.168.2.25 -PN

Starting Nmap 5.00 ( http://nmap.org ) at 2010-09-09 11:29 CEST
Interesting ports on serwer.inet (192.168.2.25):
Not shown: 993 filtered ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
9091/tcp open  unknown
```

No ping response.

I am trying to set up NFS but it wont connect:
```
san@eeepc:~$ sudo mount 192.168.2.25:/home/publiczny /home/san/Publiczny -vvvvvvvvvvvvvv
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: no type was given - I'll assume nfs because of the colon
mount: spec:  "192.168.2.25:/home/publiczny"
mount: node:  "/home/san/Publiczny"
mount: types: "nfs"
mount: opts:  "(null)"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.168.2.25:/home/publiczny"
mount: external mount: argv[2] = "/home/san/Publiczny"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw"
mount.nfs: timeout set for Thu Sep  9 11:35:17 2010
mount.nfs: text-based options: 'addr=192.168.2.25'
mount.nfs: mount(2): Connection timed out
mount.nfs: text-based options: 'addr=192.168.2.25'
mount.nfs: mount(2): Connection timed out
mount.nfs: Connection timed out
```

and it DOES work from local.

As you can see, i put here everything..:
> san@serwer:~$ cat /etc/firewall.bash
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 0 > $filtre
done
fi

# No icmp
echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback traffic
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

#SSH
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT

#Transmission-WEB
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 9091 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 9091 -j ACCEPT

#HTTP
#iptables -A TRUSTED -i eth0 -p udp -m udp --dport 80 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT

#NFS
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 2049 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 2049 -j ACCEPT

#???
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 53 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 53 -j ACCEPT

iptables -A TRUSTED -i eth0 -p udp -m udp --dport 111 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 111 -j ACCEPT

iptables -A TRUSTED -i eth0 -p udp -m udp --dport 139 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 139 -j ACCEPT

iptables -A TRUSTED -i eth0 -p udp -m udp --dport 445 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 445 -j ACCEPT

iptables -A TRUSTED -i eth0 -p udp -m udp --dport 135 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 135 -j ACCEPT

#MPD
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 135 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 135 -j ACCEPT

#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow bittorrent
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"


edit.
Transmission-web works, ssh too, but nfs and mpd does not.

edit.
Forget it!
I just added ports from 'rpcinfo -p', and added right ports for MPD. Now it works just fine.

Many thanks!

---

### Post by ariunbayar on 2010-10-09
Thank you. It helped me a lot.

---

### Post by devout on 2011-07-09
Shouldn't we be using insserv instead of update-rc.d to enable the firewall init script?
Also; shouldn't we be using LSB headers in the firewall init script?

#! /bin/sh
### BEGIN INIT INFO
# Provides:          custom firewall
# Required-Start:    $remote_fs $syslog $network
# Required-Stop:     $remote_fs $syslog $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: firewall initscript
# Description:       Custom Firewall
### END INIT INFO

---

### Post by frodon on 2011-07-09
> **devout said:**
> Shouldn't we be using insserv instead of update-rc.d to enable the firewall init script?What are the advantages ?
> **devout said:**
> Also; shouldn't we be using LSB headers in the firewall init script?

#! /bin/sh
### BEGIN INIT INFO
# Provides:          custom firewall
# Required-Start:    $remote_fs $syslog $network
# Required-Stop:     $remote_fs $syslog $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: firewall initscript
# Description:       Custom Firewall
### END INIT INFOMaybe, never hear about it before.

---

### Post by devout on 2011-07-09
> **frodon said:**
> What are the advantages ?
Maybe, never hear about it before.

Provides more flexibility in regards to dependency based booting.
Finer grained control of init.d script ordering.

Have a look at:
[http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot)
[http://wiki.debian.org/LSBInitScripts/](http://wiki.debian.org/LSBInitScripts/)
The FAQ at the bottom of the above link says the following:

"Since we want to be LSB compliant, init.d scripts can be adjusted now to be LSB compliant."

[http://forums.debian.net/viewtopic.php?f=30&t=66308&start=15](http://forums.debian.net/viewtopic.php?f=30&t=66308&start=15)
"you should also refer people to insserv, and touch on LSB headers since they're now pretty much a requirement for any scripts in /etc/init.d"


I'm no authority on the matter, I'm just trying to setup my set of netfilter rules via iptables, and your example looked like the most complete example I've seen so far, so decided to use it as a starting point.
Then found some other posts of people saying we should now be using insserve instead of update-rc.d

[http://wiki.kartbuilding.net/index.php/Iptables_Firewall#insserv_v.27s_update-rc.d](http://wiki.kartbuilding.net/index.php/Iptables_Firewall#insserv_v.27s_update-rc.d)

When I run the following:
sudo update-rc.d firewall defaults
I get the following:
update-rc.d: warning: /etc/init.d/firewall missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/firewall ...
   /etc/rc0.d/K20firewall -> ../init.d/firewall
   /etc/rc1.d/K20firewall -> ../init.d/firewall
   /etc/rc6.d/K20firewall -> ../init.d/firewall
   /etc/rc2.d/S20firewall -> ../init.d/firewall
   /etc/rc3.d/S20firewall -> ../init.d/firewall
   /etc/rc4.d/S20firewall -> ../init.d/firewall
   /etc/rc5.d/S20firewall -> ../init.d/firewall



Noob question: Wondering why you use bash for /etc/firewall.bash
and /etc/init.d/firewall
but dash for /etc/flush_iptables.bash
Is this because bash provides better debugging?

Also looking at the following:
# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

Would this be neater as:

if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]; then
  echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
fi

As I think all covers all interfaces?
[http://linuxgazette.net/issue77/lechnyr.html](http://linuxgazette.net/issue77/lechnyr.html)


Have also noticed that I can run the following now:
service firewall stop/start/etc


Thoughts?

---

### Post by frodon on 2011-07-11
If LSB header removes the warning i will add it to the tutorial, at the time this i'm not sure this even existed :)

For the use of sh instead of bash no reason except that i was use to sh at the time and surely forgot to use bash for this script as it is more widely used, not really important for this script anyway.

Sorry if i can't provide all the answers to your question.

---

### Post by SUPERFITTER on 2011-07-12
[FONT=Times New Roman][SIZE=3]Moved
[/SIZE][/FONT]

---

