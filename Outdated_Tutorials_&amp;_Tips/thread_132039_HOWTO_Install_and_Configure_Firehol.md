---
title: "HOWTO: Install and Configure Firehol"
date: 2006-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by klepto on 2006-02-17
First of all firehol is a very powerful application. It takes basic language and turns
that into very secure iptable entries. It also includes protection from syn floods, port scans,
and other anomalies. Firehol is very easy to configure and you will be up and running
with a secure machine in no time.

Please inform me if I have made any mistakes since this is my first HOWTO:

1.) Install it via apt-get install firehol 
Find your ethernet interfaces by using "ip link show" remember these as you will
have to add them to your firehol configuration or you will not be able connect to
the internet 

2.) Enable firehol in the /etc/default/firehol:
START_FIREHOL=YES

3.) Firehol uses names for the services like ssh/scp/http as you would normally recognize them. gedit or nano /etc/firehol/firehol.conf

My Firehol.conf:

version 5 
# Requires a specific version of firehol
interface "ath0 wlan0" INTERNET 
# These are my internet interfaces
        protection strong 10/sec 10  
# We want protection from icmp/syn/frags/etc 
        server "upnp samba netbios_dgm netbios_ns netbios_ssn" accept 
#server connections are incoming
        client "upnp dns http ssh dhcp whois https time rdp vnc ntp netbios_dgm netbios_ns netbios_ssn emule irc pop3 smtp" accept 
#client connections are outgoing
        client custom mswins tcp/445 default accept 
#created my own client custom service
        server custom mswins tcp/445 default accept 
#created my own server custom service
        server custom netbios udp/30000:40000 137 accept
        
        policy deny 
#this is important, so all connections other than the above specified are blocked
UNMATCHED_INPUT_POLICY="DROP" 
#Again.. incoming other than specified drop!
UNMATCHED_OUTPUT_POLICY="DROP" 
#Again.. outgoing other than specified drop!
FIREHOL_LOG_LEVEL=4 
#Log your dropped connections for security or to find out what holes are left in your firewall.

Ok.. we are almost there..
in a console type "firehol try" and if there were any errors it will let you know then type commit as in you want to commit to the firewall changes

If you have any problems you can "firehol stop" to remove all entries in iptables or "firehol debug" to see exactly what iptables entries you have listed.

I really like firehol as compared to those gui firewalls like firestarter and guarddog. You can do exactly what you want to with firehol. If you tail -f /var/log/messages you can see that firehol will show you any irregular connections and dropped connections. This is important to watch so you can see people probing your box and combined with something like snort and/or psad you have some great analysis and protection for your box!

Please remove those comments I added from the configuration, they were just for informational purposes
For a list of services that firehol does support please go to: [http://firehol.sourceforge.net/services.html?](http://firehol.sourceforge.net/services.html?)
In just a few minutes you can have a very secure firewall up and running.
...Phew! 
Any questions about firehol please message me or go to the main firehol site

---

### Post by simplyw00x on 2006-02-19
I just wanted to say thanks, some work clearly went into this and it looks really useful. I won't be using it myself because I already have to jump through too many hoops to open and forward ports, but it would be a great solution for me in even slightly different circumstances, and could really benenfit some people.
Nice one.

---

### Post by Carcass on 2006-12-25
Very good howto :) 

I want use firehol instead of guarddog< I-m sure that are simple but I confused me about hte configuration of my linux/box.......

You can help me to configure the firehol.conf.....

On my system I use:
>internet
>thunderbird
>amule (sometimes) and torrent (in rare case)
>boinc
>amarok for cover and so on....
>gaim
> in concrete a simple configuration..........

You can help me how to change firehol.conf???

Thanks to all of you that can help me :-k

---

### Post by Quasaur on 2007-05-15
I followed the howto listed here:

[http://us.lrd.yahoo.com/_ylt=Av6kb1KUt4123sWwDJeWxQ5eDNEF;_ylv=0/SIG=11mp6aa0m/SIG=1255epint/EXP=1179275007/**http%3A//ubuntuforums.org/showthread.php%3Ft=207008](http://us.lrd.yahoo.com/_ylt=Av6kb1KUt4123sWwDJeWxQ5eDNEF;_ylv=0/SIG=11mp6aa0m/SIG=1255epint/EXP=1179275007/**http%3A//ubuntuforums.org/showthread.php%3Ft=207008)


all i really want is virus protection on the web.

this is my firehol.conf:

******************************************
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept
******************************************
and this is the error i'm getting:

calvin@vistaclm:~$ sudo /etc/init.d/firehol restart
 * Restarting Firewall configuration                                                                                                          

--------------------------------------------------------------------------------
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line 24 of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' --state NEW \! --syn -j pr_world_nosyn 
OUTPUT  : 

this error repeats 24 times

one possible clue is that i couldn't run the iptables command without sudo...but starting a service should do that automatically...right?

---

### Post by smooth_b on 2007-05-16
I to am getting the same error. Have you resolved the problem? If so how?

Any help would be appreciated.

---

### Post by Quasaur on 2007-05-16
another possible clue...

this line in /etc/firehol/firehol.conf:


transparent_squid 8080 "root root"

in other versions of the file I've seen "proxy root"

...also, "transparent_squid" raises an alarm: i'm not using Squid, i'm using tinyproxy...could that be a problem?

...anyone?

---

### Post by Quasaur on 2007-05-16
turns out this is a known bug (#78017):

[https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017)

the link has a temporary fix (sort of)...it's problem with the version of bash that runs on Ubuntu Feisty (!!).

---

### Post by Nick w on 2007-07-24
hello,

im in need of some help.  i have installed firehol but want to only have access in http on port 80.  I only want to browes the web but every thing else i want locked down.

what would the config file be?

I have only been able to deny all, and i mean everything!

---

### Post by ruibernardo on 2007-09-05
> **Nick w said:**
> i have installed firehol but want to only have access in http on port 80.  I only want to browes the web but every thing else i want locked down.

what would the config file be?

I have only been able to deny all, and i mean everything!

I think that's very simple: 
```
client http accept
```and make sure you don't have a line with "client all accept".

---

### Post by c.monty on 2010-12-08
Hi!

I have installed Firehol as part of the ["Parental control package"]("http://ubuntuforums.org/showthread.php?p=10209791#post10209791").

The problem is that service Firehol is not starting automatically with the PC. Unfortunately I have no indication why the startup fails.

When I start the service manually there's no error:
```

user@pc2-xubuntu1004:~$ sudo /etc/init.d/firehol start
 * Starting Firewall firehol                                                                [ OK ] 

```

This is configuration file:
```

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy root"

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
client all accept
#server cups accept
server "samba ssh vnc ping icmp" accept

```

---

### Post by roc1479 on 2010-12-10
C.Monty,

Do you have the following set?
vi /etc/default/firehol
START_FIREHOL=[COLOR="Red"]YES[/COLOR]

YES will cause Firehol to run at startup.

Rocky

---

### Post by c.monty on 2010-12-11
Yes, I have this setting in /etc/default/firehol

I know this setting will start Firehol as startup, but not as a service.
Or can you see a running Firehol process in the process list?

As far as I understood Firehol is executing some bash scripts configuring iptables.

Can anybody confirm this?

---

