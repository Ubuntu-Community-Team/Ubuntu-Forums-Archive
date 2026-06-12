---
title: "Network Content Filter"
date: 2007-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by andytof47 on 2007-02-25
Hey all got a nice HOWTO happening with a little explanation on the errors that one might receive when installing transparent proxy filter e.g Squid and Dansguardian.

For a single machine Ubuntu Christian edition works extremly well, however the only let down is that the proxy programme used Tinyproxy by default is not configured as a Transparent proxy and nobody has replied with a decent answer on how to create a .deb and besides I don't have the time I'm at uni now:) 

So because it is not a Transparent proxy this means Manual browser configuration must be performed on each machine that is supposed to go through the proxy:(  not a very effective solution

So enter Squid and Dansguardian
DO NOT DOWNLOAD SQUID FROM THE REPOSITORIES IF YOU ARE USING EDGY THE PACKAGE IS BROKEN AND HAS NOT BEEN FIXED YET THIS IS VERY CRAPPY MAINTENANCE BUT THATS A MATTER TO BE TAKEN UP WITH THE MAINTAINERS AND NOT FOR THIS POST GET UR SQUID [HERe]("http://www.stgraber.org/download/ubuntu/packages/") OR [HERe]("http://www.adam.com.au/andytof47/linux/ubuntu/edgy/") 

READ ABOUT THE PROBLEM [HERE]("https://launchpad.net/ubuntu/+source/squid/+bug/68818")


```
apt-get install squid
```

```
sudo gedit /etc/squid/squid.conf
```

We want to do 3 things to get squid happy

Just check that 
```
 http_port 3128 transparent
```
```
visible_hostname whatever_you_want
```
```
acl home_network src 192.168.1.0/24
```(whatever your network is it needs to match this)
```
acl allow home_network
```
```
cache_effective_user squid
```
```
cache_effective_group squid
```(It's important to run squid as squid especially if you plan to transparently proxy all traffic including the one that squid is running on. If you don't you will run into the Access Denied page and quite possibly if you check the
 ```
sudo gedit /var/log/squid/cache.log 
```
you will find an error similar to this - Warning forwarding loop found for http:blah blah blah

I would say to keep things simple just check that you have squid running by manually configuring you browser to go through the squid proxy now edit---->preferences-->advanced--->network

(also by checking step by step you can greatly reduce the chances of messing things up)

first make sure squid is going (there is a commond for this but I can't remember it so just )
```
sudo /etc/init.d/squid restart
```
if that doesn't work
```
sudo /etc/init.d/squid start
```
if that doesn't work check

```
sudo gedit /var/log/squid/cache.log 
```
and the error will be there

If it started just configure it for http proxy and enter
127.0.0.1 for the address and port 3128 for the port



then access some wonderful website like 
```
www.ubuntuforums.org
```
if the forums come up it probably wokred and then you can proceed to the next step
to be sure just check

```
sudo gedit /var/log/squid/access.log 
```
and you should see that squid was hit yippee:) :popcorn: 

```
sudo apt get install dansguardian
```

Dansguardian Important settings
#unconfigured (add a comment that is the # symbol for those who don't know)
filterip = 192.168.1.2 (Keep in mind this is your network card connected to the router assuming that the router is 192.168.1.1)
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
daemonuser = 'nobody'
daemongroup = 'nobody'

fix these settings and then restart or start Dansguardian

```
/sudo /etc/init.d/dansguardian restart
```

or

```
sudo /etc/init.d/dansguardian start
```

So hopefully you have squid running in tandem with dansguardian

check if you do by fireing up your browser and type in something obscene

such as ummmmmm
```
www.microsoft.com
```:) 

It should be blocked no really IT SHOULD BE BLOCKED:) 

It won't block that site but actually you don't need to type in anything obscene just check you squid logs again and check that squid was hit again, if it was and both programms are running then you can bet that that a more questionable site would be blocked.

This is where most Howto's end ahh hah but not this one

There is still the little issue of transparency - the whole reason I started this tutorial

ok just set your browser back to direct connect to the internet and allow it to do it's thing

Squid will not be hit likewise Dansguardian will not filter - kind of makes sense doesn't it

just set up iptables to redirect all web traffic to go through Squid and DG automatically

```
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT
```(very Important this is why we have squid running as squid otherwise we would get errors)

```
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT
```(same as above)

```
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080
```(this directs all web traffic to do it's thang via our setup)

then check it by trying your browser at any site then a questionable one aswell

all should be well now just direct all the other computers to go through your transparent proxy and add whatever limitations you want

hope this helps

Credits
The reason I am still using Ubuntu is this site having the available package [check it out]("http://www.stgraber.org/")
he doesn't know me or me him but he has the goods so cheers

- this HOWTO is the combination of many different howto's but the main ones are 
[here]("http://desktops.linux.com/desktops/04/07/01/1833212.shtml?tid=49&tid=99&tid=13")
and [here]("http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:proxy")

To make things really dandy there is a beautiful GUI interface for Dansguadian that simplifies things and that can be found by searching in the forums or by going to the downloads section of [this site]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html")

there is an updated version of the GUI kicking around the forums and I like the look of it more  - better buttons more functional:) 

really hope this helps

Check your logs if something doesn't work and enjoy

God Bless (yes I am a Christian if ur wondering)

---

### Post by andytof47 on 2007-03-02
PS After many many Hours I have one more thing to add

If you continuously get a port forwarding loop then use these rules for your firewall instead of the above rules.

First of all as a test just get rid of any existing firewall rules untill rebooting

```
iptables -F
```

then

```
iptables -t nat -F
```
I'm not sure if the first flush flushes all rules but to be safe I included this...

ok the adjusted rules for iptables

```
iptables -t nat -A OUTPUT -p tcp -m tcp --dport 8080 -m owner --uid-owner squid -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp -m tcp --dport 80 -m owner --uid-owner squid -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080 
```

slight difference is the addition of -m

you can read up about it but it helped me greatly :) 

ok peace out

---

### Post by stgraber on 2007-05-19
> **andytof47 said:**
> 
Credits
The reason I am still using Ubuntu is this site having the available package [check it out]("http://www.stgraber.org/")
he doesn't know me or me him but he has the goods so cheers


Well, now I do :)
Thank you (btw, I've uploaded the fixed package to Edgy, it's in edgy-proposed for now)

---

### Post by Abhi Kalyan on 2007-11-22
Thank You Pal, Thats a wonderfull howto, and funny too, cudoes.
Hope i could write like you, a lot of brain with a pinch of salt and pepper!!
All the best

---

### Post by gregsheu on 2009-01-26
Hi:
  I am running Edgy with NAT router, and I do need to add the dans to filter my subnet. I download the squid from the link you listed and install it. But it complains that the cache_effective_user squid is not valid. I have to change the user back to proxy which is the default in order to start the squid. But the dans and squid seem not work. Can you help? Thank you.

---

### Post by gregsheu on 2009-01-27
Can this also be a NAT router? Thanks

---

