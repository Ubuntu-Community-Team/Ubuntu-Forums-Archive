---
title: "HOWTO: IPv6"
date: 2008-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Martje_001 on 2008-03-04
Hello,
I needed to connect to a server, which was (is) only reachable with IPv6. So, this is how I did setup my IPv6 connection.

**Step 1:**
*Download and install Freenet*
```
wget http://go6.net/4105/file.asp?file_id=150 -O go6.tar.gz
mkdir go6
cd go6
tar zxf ../go6.tar.gz
rm ../go6.tar.gz
sudo apt-get -y install libcurl4-openssl-dev openssl libcrypto++-dev libpthread-stubs0-dev build-essential
cd ./gw6c-messaging
make target=linux exportdir=../tspc-advanced export
cd ../gw6c-config
make target=linux exportdir=../tspc-advanced export
cd ../tspc-advanced
make target=linux all
sudo make target=linux installdir=/usr/local/gw6c install
cd ~
rm -r go6

```
**Step 2:**
*Create config file*
```
cd /usr/local/gw6c/bin
sudo rm gw6c.conf #If there are errors here, it's no problem.
sudo gedit gw6c.conf
```
Paste the following and save:
```
server=anon.freenet6.net
auth_method=anonymous
host_type=host
prefixlen=64
if_prefix=eth0
dns_server=208.67.222.222
gw6_dir=/usr/local/gw6c
auto_retry_connect=yes
retry_delay=30
keepalive=yes
keepalive_interval=30
tunnel_mode=v6anyv4
if_tunnel_v6v4=sit1
if_tunnel_v6udpv4=tun
if_tunnel_v4v6=sit0
client_v4=auto
client_v6=auto
template=linux
proxy_client=no
broker_list=tsp-broker-list.txt
last_server=tsp-last-server.txt
always_use_same_server=no
log_filename=gw6c.log
log_rotation=yes
log_rotation_size=32
syslog_facility=USER
```

**Step 3**:
*Run Freenet*
```
cd /usr/local/gw6c/bin
sudo ./gw6c
```
If you don't see any errors it should be fine. Wait a minute to give it start-up time and go to [this page](http://go6.net/). If you see something like 'You are using IPv6', everything went fine!

---

### Post by bhavi on 2008-03-21
Sadly If IPV6 is enabled then my internet doesnt work here... :(

---

### Post by Martje_001 on 2008-03-21
Can you ping normal sites?

```
ping google.com
```

---

### Post by bhavi on 2008-03-21
yes.. but download speed and system goes horribly slow...:)

---

### Post by Martje_001 on 2008-03-21
What is your ISP?

---

### Post by bhavi on 2008-03-21
> **Martje_001 said:**
> What is your ISP?
Its BSNL Broadband here in India... With an unlimited doenload plan..

[http://www.bsnl.co.in/service/dataone.htm](http://www.bsnl.co.in/service/dataone.htm)

---

### Post by dcstar on 2008-03-21
> **bhavi said:**
> Its BSNL Broadband here in India... With an unlimited doenload plan..

[http://www.bsnl.co.in/service/dataone.htm](http://www.bsnl.co.in/service/dataone.htm)

Unless** all **of your network envorinment is IPv6 enabled (including your ISP), I doubt you will get any connection.

If you have it enabled in Ubuntu, and Ubuntu incorrectly thinks that IPv6 is available in your local environment, then that is why things slow down (time-outs waiting for IPv6 responses that can never happen).

---

### Post by rabside on 2008-05-25
hi Martje_001!
I've followed ur guide, but in the end when I type:  ping newszilla6.xs4all.nl
i get
ping: unknown host newszilla6.xs4all.nl

isp is tiscali

---

### Post by Martje_001 on 2008-05-25
Does [this site]("http://go6.net/") says you're using IPv6?

---

### Post by Martje_001 on 2008-05-25
And more important (since newszilla6 is a NNTP server) have you tried
```
telnet newszilla6.xs4all.nl 119
```
in a terminal?

---

### Post by rabside on 2008-05-25
Interesting: telnet works with correct ip (v6)!!! 
but I can't download: always status queued, the client tell me "Cannot resolve hostname"

---

### Post by Martje_001 on 2008-05-25
What client do you use? Pan?

---

### Post by rabside on 2008-05-25
tried lottanzb e klibido. Now I'll try pan

---

### Post by rabside on 2008-05-25
I don't understand: with pan works...
bah!
thx a lot ;)

---

### Post by Ansenyi on 2008-06-17
And what about SABnzbd+?

---

### Post by Martje_001 on 2008-06-18
Works fine for me, for deb-packages (sabnzbd) see my sig.

---

### Post by superdupont on 2009-10-08
Hi. Tried this guide after having failed to get ipv6 with already compiled Gw6c v6 version...and I have problems with it too :)

ie make target=linux exportdir=../tspc-advanced export
gives me :

src/namevalueparser.cc:136: erreur: &#8216;memset&#8217; was not declared in this scope
src/namevalueparser.cc:177: erreur: &#8216;strtok&#8217; was not declared in this scope
src/namevalueparser.cc: In member function &#8216;virtual bool gw6cconfig::NameValueParser::WriteConfigurationData(const std::string&)&#8217;:
src/namevalueparser.cc:259: erreur: &#8216;strlen&#8217; was not declared in this scope
src/namevalueparser.cc:259: erreur: &#8216;strncmp&#8217; was not declared in this scope
make[2]: *** [objects/namevalueparser.o] Erreur 1
make[2]: quittant le répertoire « /home/jc/go6/gw6c-config »
make[1]: *** [export] Erreur 2
make[1]: quittant le répertoire « /home/jc/go6/gw6c-config »
make: *** [check-gw6cconfig] Erreur 2

------------------------


I feel like I need a secret ingredient here (but I did install everything else mentionned before ie the 
sudo apt-get -y install libcurl4-openssl-dev openssl libcrypto++-dev libpthread-stubs0-dev build-essential
line :)

ps : I have gcc version 4.3.3. Do I need another version ?

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for nice tutorial. How can we check that our ISPs support IPv6 connections? Is there anyway?

---

### Post by superdupont on 2009-10-10
Hi, we're still alive and not kicking :)
so, does someone know how I could make the compilation work (see 2 posts above)?

---

