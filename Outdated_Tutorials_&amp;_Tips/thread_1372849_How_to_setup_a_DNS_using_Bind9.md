---
title: "How to setup a DNS using Bind9"
date: 2010-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by JGathage on 2010-01-05
**Domain Name System.**
 There are many ways of providing descriptive names to computers in a network. These are:
 	a). Editing the hosts file directly.
 	b). Using a domain name system  
 If you go for the first option this means you have to edit the hosts file for all the computers in the network. Which can be pretty tedious and impractical for a very large network.
 
[LIST=1]
[*]Editing the 	**/etc/hosts** file directly via the following command
 	**$ sudo vi 	/etc/hosts** . It will result to
 	
 	**127.0.0.1	localhost ** 	
 	
 	**# The following lines are desirable 	for IPv6 capable hosts ** 	
 	**::1     localhost ip6-localhost 	ip6-loopback ** 	
 	**fe00::0 ip6-localnet ** 	
 	**ff00::0 ip6-mcastprefix ** 	
 	**ff02::1 ip6-allnodes ** 	
 	**ff02::2 ip6-allrouters ** 	
 	**ff02::3 ip6-allhosts**
 	
[/LIST]
 The DNS implementation uses a client server model to achieve the same thing as the first option. This option involves using a central server called the domain name server to provide host name translation to client machines in the network. This a much cleaner and dynamic way of doing it. For this reason we will go for the DNS option. There are a number of DNS software out there but for our purpose we will use Bind(Bind9) which is the most popular server out there.
 

 This tutorial is going to show you how to setup a caching DNS ideal for your private organizational use.
 **Installation**
 
[LIST=1]
[*]Install bind 	9 via the following command
 	**$ sudo apt-get install bind9**
[*]It will 	create the following directories:
 	a). /etc/bind/- 	configuration files.
 	b). 	/var/cache/bind- this where we will add our zone files.
[/LIST]
 The main configuration file for bind is the **named.conf **which can be accessed via typing the following on bash
 	**$ sudo vi /etc/bind/named.conf**
 **Results:**
 **// This is the primary configuration file for the BIND DNS server named.**
 **//**
 **// Please read /usr/share/doc/bind9/README.Debian.gz for information on the ** 
 **// structure of BIND configuration files in Debian, *BEFORE* you customize ** 
 **// this configuration file.**
 **//**
 **// If you are just adding zones, please do that in /etc/bind/named.conf.local**
 **include "/etc/bind/named.conf.options";**
 **// prime the server with knowledge of the root servers**
 **zone "." {**
 **	type hint;**
 **	file "/etc/bind/db.root";**
 **};**
 

 **// be authoritative for the localhost forward and reverse zones, and for**
 **// broadcast zones as per RFC 1912**
 **zone "localhost" {**
 **	type master;**
 **	file "/etc/bind/db.local";**
 **};**
 **zone "127.in-addr.arpa" {**
 **	type master;**
 **	file "/etc/bind/db.127";**
 **};**
 **zone "0.in-addr.arpa" {**
 **	type master;**
 **	file "/etc/bind/db.0";**
 **};**
 **zone "255.in-addr.arpa" {**
 **	type master;**
 **	file "/etc/bind/db.255";**
 **};**
 **include "/etc/bind/named.conf.local";**
 

 We can go ahead and test if our DNS is working properly by entering the following command on bash.
 
[LIST=1]
[*]If you have 	installed bind in your localhost enter
 	**$ host [www.google.com]("http://www.google.com/") 	localhost. ** 	
 	**Results:**
 	**[www.google.com](www.google.com) is an alias for 	[www.l.google.com](www.l.google.com). ** 	
 	**[www.l.google.com](www.l.google.com) has address 	74.125.47.99 ** 	
 	**[www.l.google.com](www.l.google.com) has address 	74.125.47.147 ** 	
 	**[www.l.google.com](www.l.google.com) has address 	74.125.47.104 ** 	
 	**[www.l.google.com](www.l.google.com) has address 	74.125.47.103 ** 	
[/LIST]
 

 If you see the above you are good to go.
 What we are going to do is to add a zone to our DNS that is unique to our organization.
 Zones are just domains. For our case we  will use **mycompanyexample.com**. You can use a domain of your choice but remember to use that domain whenever we use mycompanyexample.com.
 

 **Rezoning.**
 Zones are defined in zone files. Zones files contain a header also called an SOA record. The SOA record is optionally followed by DNS records defining services and hosts. The header contains metainformation used by our caching DNS and any slave DNS that we may have defined. A header can be described by a number of fields. These are described  below:
 

 Field              Use  
 $ORIGIN         Defines the start of the zone  
 $TTL               Time to live, which is the default expiration for records in this zone that  
                   	 do not have their own expiration time set  
 SOA                 Start of Authority, which contains seven records of zone metadata  
 Master              Primary authoritative DNS server for this domain  
 Contact             E&#8208;mail address of the contact for this domain, with the at sign (@)  
                   	 replaced by a period  
 Serial               Defines the version of this zone file, used by slave name servers  
 Refresh            Defines how often slave servers should update their copy of this zone 
 Retry                Defines the interval between attempts to refresh a slave server  
 Expire              Defines how long a slave server is allowed to use any version of this  
                    	 zone file  
 Negative Cache TTL  Defines how long a failed lookup result may be cached  
 

 In our case we will create a forward lookup zone and reverse lookup zone. The former does host name to IP translation and the latter does IP to host name translation.
 

 **Forward Lookup Zone.**
  We are going to create our zone file in /var/cache/bind/ by entering the following in bash
 **$ sudo vi /var/cache/bind/mycompanyexample.com.db**
 

 Copy and paste the following:
 

 **$ORIGIN mycompanyexample.com.**
 **$TTL 86400**
 **@ IN  SOA mycompanyexample.com. root.mycompanyexample.com. (**
 **2010010301;Serial**
 **604800;Refresh**
 **86400; Retry**
 **2419200; Expire**
 **3600); Negative cache TTL**
 **	NS ns.mycompanyexample.com.**
 **	MX 10 mail.mycompanyexample.com.**
 

 **@ IN A 172.16.0.1**
 **mail IN A 172.16.0.1**
 **storage IN A 172.16.0.2**
 **ns IN A 172.16.0.254**
 

 **Reverse Lookup Zone.**
 This will also be created in the same path as the forward lookup. Enter the following in bash
  **sudo vi /var/cache/bind/172.16.0.db**
 

 Copy and paste the following:
 

 **$ORIGIN 0.16.172.in-addr.arpa.**
 **$TTL 86400**
 

 **@ IN  SOA mycompanyexample.com. root.mycompanyexample.com. (**
 **	2010010302;Serial**
 **	604800;Refresh**
 **	86400;Retry**
 **	2419200;Expire**
 **	3600);Negative Cache TTL**
 **	NS ns.mycompanyexample.com.**
 **1 PTR  mail.mycompanyexample.com.**
 **2  PTR storage.mycompanyexample.com.**
 **254  PTR ns.mycompanyexample.com.**
 

 To test our setup enter the following in bash to test our forward lookup zone:
 

 **$ host mycompanyexample.com localhost**
 It should result in the following:
   
 **Using domain server:**
 **Name: localhost**
 **Address: 127.0.0.1#53**
 **Aliases:**
 

 **mycompanyexample.com has address 172.16.0.1**
 **mycompanyexample.com mail is handled by 10 mail.mycompanyexample.com.**
 

 Well, that's all there is to it. Feel free to improve on this tutorial. Thanks.

---

