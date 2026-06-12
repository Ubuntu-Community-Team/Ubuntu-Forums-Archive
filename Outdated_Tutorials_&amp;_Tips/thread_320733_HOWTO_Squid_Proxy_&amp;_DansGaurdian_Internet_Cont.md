---
title: "HOWTO: Squid Proxy &amp; DansGaurdian Internet Content Filter"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by bmathis on 2006-12-17
Hi All - 

This howto guide was created to describe setting up a Squid Proxy/DansGuardian server using Ubuntu 6.06 LTS installed with the LAMP server option. This guide assumes the user has previous knowledge of installing a LAMP server using Ubuntu and will not be covered. While each program may have a multitude of options to configure, this guide will show you how to configure the basics to get a server started.

**_***** Edgy Users: Squid Appears To Be Broken In Transparent Proxy Mode *****_**

**Installing Apache**

Start off by ensuring Apache Web Server is installed, if not, install it using this command
```
sudo aptitude install apache2
```
**Setting a Static IP Address**

Now make sure that you have a static IP address
```
sudo nano /etc/network/interfaces
```
And change the following (bold) to match your network
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet [B]static
	address	192.168.1.2
	netmask	255.255.255.0
	gateway	192.168.1.1[/B]
```
Press ctrl + x to exit, yes to save, and enter to keep the same file name. After saving the file, you must now restart the networking process
```
sudo /etc/init.d/networking restart
```
**Installing and Configuring Squid**

Next install the Squid Proxy Server
```
sudo aptitude install squid
```
If you want to change the default port that squid listens on [3128], change the http_port tag using nano, making a backup copy first
```
sudo cp /etc/squid/squid.conf /etc/squid/squid.conf_backup
sudo nano /etc/squid/squid.conf
```
OK, now we'll setup who is allowed access to the proxy. Find the http_access section (should start around line 1860) Uncomment these 2 lines and add your network allocations
```
acl our_networks src 192.168.1.0/24 192.168.2.0/24
http_access allow our_networks
```
*Optional* = if you get a startup error 'FATAL: Could not determine fully qualified hostname. Please set visible_hostname' you will also need to modify the visible_hostname tag
```
visible_hostname localhost
```
Save the file and close nano.

**Installing and Configuring DansGuardian**

To install DansGuardian, use the following command
```
sudo aptitude install dansguardian
```
Once the package is installed, edit the following lines in the conf file to match, this will set DansGuardian to do basic filtering and use Squid as its proxy server.
```
# UNCONFIGURED
filterip = 
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

```
To configure banned/exception sites based on either phrases, ip addresses, urls, mime type, etc… you would need to edit one of the following files using nano. All files are located in /etc/dansguardian/
```
bannedextensionlist
bannediplist
bannedmimetypelist
bannedphraselist
bannedregexpurllist
bannedsitelist
bannedurllist
banneduserlist

exceptioniplist
exceptionphraselist
exceptionsitelist
exceptionurllist
exceptionuserlist
exceptionvirusextensionlist
exceptionvirusmimetypelist
exceptionvirussitelist
exceptionvirusurllist
```

**Restarting Squid and DansGuardian**

Whenever a file is edited, it is good practice to restart both Squid and DansGuardian services by using the following commands
```
sudo /etc/init.d/dansguardian stop
sudo /etc/init.d/squid stop
sudo /etc/init.d/squid start
sudo /etc/init.d/dansguardian start
ps –e | grep dansguardian ## to see if the service is running
```
Now that Squid and DansGuardian are configured, test it by setting up your browser to use the proxy server with port 8080. A site that is blocked by default in DansGuardian is [www.porn.com](www.porn.com), if you get a page redirect then you’re good to go.

Again, this howto assumes that you know how to install a LAMP server yourself. There are far more features that can be configured using Squid/DG, but they are beyond the scope of this howto. I hope this helps everyone and please note, I am no where near an expert on this subject. Safe surfing!

---

### Post by Abhi Kalyan on 2007-01-28
hank you Bro,
A very clear and crisp HOW TO
Thank you once again

---

### Post by etank on 2007-01-28
I have got to set one of these up at work.

---

### Post by Abhi Kalyan on 2007-01-31
Thank you for the tip. It waorked.
Some more tweaking with the IP tables has now created a transparant proxy.
Great work thank you bro

---

### Post by bmathis on 2007-01-31
no problem... glad you could find this basic howto useful!

---

### Post by SergioLopes on 2007-02-15
Hi. 
First of all, thank you for this excellent guide, it really helped me, and i've managed to get everything up and running... 
Now, is there anyway to add a user but only with access to a restricted list of sites ? 

Thanks in advance... 

[]
SergioLopes

---

### Post by mscoxoh on 2007-02-24
When I try to do the installation of dansguardian, I'm told that there is no such package. See output below.

~$sudo aptitude install dansguardian

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "dansguardian"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Ok, what dumb thing am I doing? (I'm extremely new to ubuntu, and administering linux/unix operating systems in general.)

Michael

---

### Post by SergioLopes on 2007-02-24
Try this: 

sudo gedit /etc/apt/sources.list

find and uncomment/add this lines: 

# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) edgy universe
# deb -src [http://pt.archive.ubuntu.com/](http://pt.archive.ubuntu.com/) edgy universe

then 

sudo apt-get update
sudo aptitude install dansguardian

---

### Post by mscoxoh on 2007-02-24
Fantastic! Yes, that took care of it. Thank you for that, and thank you bmathis for the instructions. It's up and running!

---

### Post by andytof47 on 2007-03-04
hey BMATHIS,

for the rest of us that use Edgy please tell them that squid is broken in transparent proxy mode

not usre if ur using it in transparent mode but if you are at least you know - it's not an issue for 6.06 or feisty

---

### Post by bmathis on 2007-03-06
> **andytof47 said:**
> hey BMATHIS,

for the rest of us that use Edgy please tell them that squid is broken in transparent proxy mode

not usre if ur using it in transparent mode but if you are at least you know - it's not an issue for 6.06 or feisty

Thanks, I edited the original post with the info.

---

### Post by bmathis on 2007-03-06
> **SergioLopes said:**
> Hi. 
First of all, thank you for this excellent guide, it really helped me, and i've managed to get everything up and running... 
Now, is there anyway to add a user but only with access to a restricted list of sites ? 


It can be done with ACL's in squid. PM me and I can give you an ebook about Squid.

---

### Post by silentph03nix on 2007-03-07
> **andytof47 said:**
> hey BMATHIS,

for the rest of us that use Edgy please tell them that squid is broken in transparent proxy mode

not usre if ur using it in transparent mode but if you are at least you know - it's not an issue for 6.06 or feisty

I found a link on the web that works around this.  Here is the relevant portion:

> 
My current working squid.conf ends like that:
#httpd_accel_host virtual
#httpd_accel_port 80
#httpd_accel_with_proxy on
#httpd_accel_uses_host_header on

http_port 3128 transparent
always_direct allow all

The old httpd_accel directives are deprecated, transparent proxying is enabled by appending &#8220;transparent&#8221; to the http_port directive, and the (#1650) bug related to transparent interception can be avoided by &#8220;always_direct allow all&#8221;. 

[http://itreporter.bloghost.ro/2006/10/19/transparent-proxy-with-squid-26-ubuntu-edgy-caveats/]("http://itreporter.bloghost.ro/2006/10/19/transparent-proxy-with-squid-26-ubuntu-edgy-caveats/")

[http://www.squid-cache.org/mail-archive/squid-users/200607/0023.html]("http://www.squid-cache.org/mail-archive/squid-users/200607/0023.html")

HTH
Silent Ph03nix

---

### Post by SpazMan on 2007-03-28
Hi,
I'm trying to set up a Proxy Server for my office and I've followed the directions mentioned here.  They were very helpful and I got it up and running in no time.
My problem is, however, I'd like to customize the page the user sees when a site is blocked.  I modified the dansguardian.conf and changed the [COLOR="Red"]accessdeniedaddress[/COLOR] directive to point to the dansguardian.pl file on my local server.  It now looks something like this accessdeniedaddress = 'http://172.16.10.24/cgi-bin/dansguardian.pl'.
When I run a test and try to access the site 'www.porn.com' I get redirected to a URL [http://parking.ddc.com](http://parking.ddc.com).......
It looks nothing like the .pl file.
I'm running Ubuntu 6.10 server.
I would really appreciate any help.

I've attached two screenshot.  The 'nogood.jpg' illustrates the page I'm being redirected to.  The 'good.jpg' image illustrates the page I would like to be redireted to automatically when a page is denied.  If I enter the url directly in my browser it does load.

Regards.

---

### Post by nvx0270 on 2007-03-29
Thanks for the nice tutorial, 

I think I followed the all the steps but it seem dansguardian not filtering any content, I can surf to porn.com ,  what could I be done wrong?

thanks.

---

### Post by awreneau on 2007-04-10
Excellent!

A baseline for me to get a little face time w/ these tools.  Much appreciated!

---

### Post by pregnant_joe on 2007-05-10
> **mscoxoh said:**
> When I try to do the installation of dansguardian, I'm told that there is no such package. See output below.

~$sudo aptitude install dansguardian

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "dansguardian"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Ok, what dumb thing am I doing? (I'm extremely new to ubuntu, and administering linux/unix operating systems in general.)
Michael

mine..
...~# sudo aptitude install squid
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  squid-common ssl-cert
The following NEW packages will be installed:
  squid squid-common ssl-cert
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 969kB of archives. After unpacking 6320kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main squid-common 2.5.12-4ubuntu2
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ssl-cert 1.0.13
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main squid 2.5.12-4ubuntu2
  Temporary failure resolving 'archive.ubuntu.com'


i don't know how to use linux..i'm an absolute newbie..pls help me..does this have connection with the HD partition?..i'm ZERO..

---

### Post by justinchudgar on 2007-09-06
> **SpazMan said:**
> Hi,
I'm trying to set up a Proxy Server for my office and I've followed the directions mentioned here.  They were very helpful and I got it up and running in no time.
My problem is, however, I'd like to customize the page the user sees when a site is blocked.  I modified the dansguardian.conf and changed the [COLOR="Red"]accessdeniedaddress[/COLOR] directive to point to the dansguardian.pl file on my local server.  It now looks something like this accessdeniedaddress = 'http://172.16.10.24/cgi-bin/dansguardian.pl'.
When I run a test and try to access the site 'www.porn.com' I get redirected to a URL [http://parking.ddc.com](http://parking.ddc.com).......
It looks nothing like the .pl file.
I'm running Ubuntu 6.10 server.
I would really appreciate any help.

I've attached two screenshot.  The 'nogood.jpg' illustrates the page I'm being redirected to.  The 'good.jpg' image illustrates the page I would like to be redireted to automatically when a page is denied.  If I enter the url directly in my browser it does load.

Regards.

I would also like to use a customized [FONT="Courier New"]dansguardian.pl[/FONT] I have the version I want available at [FONT="Courier New"]http://<myserver>/cgi-bin/dansguardian.pl[/FONT]; and, it seems to be just fine when I point a browser directly at it. However when I change the [FONT="Courier New"]dansguardian.conf [/FONT]to reflect the URL, restart the dansguardian daemon and try a banned page; nothing changes. 

Help! Thanks.

---

### Post by Claude-Smith on 2007-09-20
Awesome writeup!  Dansguardian is now blocking porn!  But I have an issue that keeps me from using the proxy server on the network.  Our dealer management software is unable to connect while using DG, it works fine when going through squid on port 3128 but when I switch it to 8080 arkona (the dms) will not connect.  It operates on port 928.  Since it works through squid I assume it is a DG issue.  I don't know what is blocking port 928, or if it is at all.  This is the last hurdle I have to overcome before I can turn this thing on!  Thanks guys!

---

### Post by bmathis on 2007-09-24
> **justinchudgar said:**
> I would also like to use a customized [FONT="Courier New"]dansguardian.pl[/FONT] I have the version I want available at [FONT="Courier New"]http://<myserver>/cgi-bin/dansguardian.pl[/FONT]; and, it seems to be just fine when I point a browser directly at it. However when I change the [FONT="Courier New"]dansguardian.conf [/FONT]to reflect the URL, restart the dansguardian daemon and try a banned page; nothing changes. 

Help! Thanks.

If you go into dansguardian.conf, search for reportinglevel and change that to 2, then search for accessdeniedaddress and set that to what you want. This wont show the user why they were denied, but was the only way I was able to use a custom page.

---

### Post by bmathis on 2007-09-24
> **Claude-Smith said:**
> Awesome writeup!  Dansguardian is now blocking porn!  But I have an issue that keeps me from using the proxy server on the network.  Our dealer management software is unable to connect while using DG, it works fine when going through squid on port 3128 but when I switch it to 8080 arkona (the dms) will not connect.  It operates on port 928.  Since it works through squid I assume it is a DG issue.  I don't know what is blocking port 928, or if it is at all.  This is the last hurdle I have to overcome before I can turn this thing on!  Thanks guys!


In dansguardian.conf, search for Safe_ports, follow the scheme and enter the ports that you require.

---

### Post by Claude-Smith on 2007-11-09
Thank you!  I'll have to try that after I totally reinstall my server!  For some reason after a month and a half it decided to just die one day!  It wont bring the network interface up and keeps giving segmentation fualts!  I can't even log in!!  I don't know how to fix it so I'm downgrading from 7.04 to 6.10 and doing a reinstall :(

---

### Post by okej01 on 2007-11-29
I have had quite a bit of trouble setting this up on a gutsy server as clamav is outdated.  Has any one had success with gutsy?  If so please post your solution.  Thanks!

---

### Post by bmathis on 2007-12-04
> **okej01 said:**
> I have had quite a bit of trouble setting this up on a gutsy server as clamav is outdated.  Has any one had success with gutsy?  If so please post your solution.  Thanks!

you can install fresh clam and run it with the following command. ```
sudo aptitude install clamav-freshclam && sudo freshclam
```

---

### Post by CrackerNuts on 2008-01-13
I can't browse websites using my client pc (192.168.0.1)

I installed Ubuntu with lamp, followed all the directions from this thread, installed everything successfully but my client pc can't access the web. 

Here is my **network config file**
> # The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
   auto eth0
   iface eth0 inet static 
   address 11x.6x.19x.2xx
   netmask 255.255.255.224 
   gateway 11x.6x.19x.2xx

   iface eth1 inet static
   address 192.168.0.1
   netmask 255.255.255.0



**client pc:**
Ip:192.168.0.2
Sm: 255.255.255.0
gateway: 192.168.0.1
DNs: 2xx.192.1xx.3   (from our isp)
Dns: 2xx.192.1xx.4


      I can ping 192.168.0.1 from the client pc.

---

### Post by modulok on 2008-01-15
Where is the dansguardian.conf located on dapper server edition?

---

### Post by bmathis on 2008-02-02
> **modulok said:**
> Where is the dansguardian.conf located on dapper server edition?

its located in /etc/dansguardian

---

### Post by littletinman on 2008-02-13
And change the following (bold) to match your network
Code:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address	192.168.1.2
	netmask	255.255.255.0
	gateway	192.168.1.1

Press ctrl + x to exit, yes to save, and enter to keep the same file name. After saving the 

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::;;;;;;;;;;;;;;;;;;;;;;;

How do i find out what my address, netmask, and gateway are?

---

### Post by modulok on 2008-02-18
It depends one your network. Do an "ifconfig" and you can see your scheme and should be able to figure it out.

---

### Post by bmathis on 2008-02-18
you can do a ```
netstat -rn
``` to display the routing table and get your netmask/default gateway, It will look something like this 

```
bmathis@foshizzle:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.10.0    0.0.0.0        ** 255.255.255.0**   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         **192.168.10.2**    0.0.0.0         UG        0 0          0 eth0
```

for your ip address do a ```
ifconfig | grep Bcast
```which will show something like this ```
bmathis@foshizzle:~$ ifconfig | grep Bcast
         ** inet addr:192.168.10.76**  Bcast:192.168.10.255  Mask:255.255.255.0

```and look for inet addr: for your ip. make sure you have a capital B on Bcast or else it will not work. Generally, if this is a server, you would want to use an ip address that is not handed out by DHCP. On most home routers, this will be anything before xxx.xxx.xxx.100 and after xxx.xxx.xxx.200

---

### Post by modulok on 2008-02-21
I am setting up a new proxy/content filtering server. I would like to use the new Hardy Server LTS Release when it comes out in April. Using Squid3 that is now out, how would I go and do a custom --configure on the package from Ubuntu sources? Also, when Squid3.XX comes out, will the custom configured install be updated?

Also, how would I go about using Windows Authentication with accessing the Proxy? If I get that working, can the username be used in the access logs? This would be better than using a computer name. AKA using DNS for IP lookups.

I also would like some other options to reporting. Has anyone used Crystal to generate better looking reports? Is there anything better than SARG for reporting? I would like to do have some sort of drop downs to sort the data if required.

Does anyone know if/how this can be done??

Thanks a lot.

---

### Post by modulok on 2008-02-25
bump

---

### Post by modulok on 2008-02-25
OK, I have found my reporting solution...[http://surftrackr.net/](http://surftrackr.net/)

> Using Squid3 that is now out, how would I go and do a custom --configure on the package from Ubuntu sources? Also, when Squid3.XX comes out, will the custom configured install be updated?

Also, how would I go about using Windows Authentication with accessing the Proxy? If I get that working, can the username be used in the access logs? This would be better than using a computer name. AKA using DNS for IP lookups.

I still need some ideas/guidance on these two questions, thanks.

---

### Post by haryoh on 2008-06-01
Bmathis

Thanks for this wonderful tutorial. I'm wrapping my head around it and it's fun. I have my physical router running at the same time with my server and there is no conflict in any of my configurations whatsoever.

Thanks

---

### Post by snakdoc on 2008-06-21
almost done with install looking just what i was looking for

EDIT: Its all done and works great :D thanks

---

### Post by gregbazar on 2008-12-06
Awesome!  Works like a champ.

Thanks for the post.

G

---

### Post by Dibhala on 2008-12-11
Firstly hello everyone.
Secondly I need a hand with squid3+DG on ubuntu 8.10
Been searching for the solution, but I just suck with iptables.

I got dansguardian running (default config: listening on incoming 8080, working on 3128), squid3 (same 3128 listening on 80). I used firestarter to route traffic between LAN<->internet.
Eth0 gets IP from router by dhcp, eth1 is configured to 172.16.0.0/24 (but I'm going to switch it to 10.0.0.0/24)

Afair (I don't have access to it right now) when I manually configured firefox on all hosts, to use ubuntu's IP and port 8080 mature content was filtered (at least dansguardian worked, don't know if squid did anything).

The problem is, that I'd like to filter transparently all content going from LAN hosts through dansguardian -> squid.
I tried with couple iptables entries which I found, looking for DG configuration, but those didn't work for me.

Could anyone give me a solution how to configure squid3+DG to work transparently ? I ran out of ideas.
Maybe there's a program with GUI for this ? 
I just don't know how to create working iptables entry :(


ps. If I forgot to add any information, although I think I put all needed info, just mention what info should I add.


bump
anyone ?  :(

---

### Post by Abhi Kalyan on 2009-01-08
> **Dibhala said:**
> Firstly hello everyone.
Secondly I need a hand with squid3+DG on ubuntu 8.10
Been searching for the solution, but I just suck with iptables.

I got dansguardian running (default config: listening on incoming 8080, working on 3128), squid3 (same 3128 listening on 80). I used firestarter to route traffic between LAN<->internet.
Eth0 gets IP from router by dhcp, eth1 is configured to 172.16.0.0/24 (but I'm going to switch it to 10.0.0.0/24)

Afair (I don't have access to it right now) when I manually configured firefox on all hosts, to use ubuntu's IP and port 8080 mature content was filtered (at least dansguardian worked, don't know if squid did anything).

The problem is, that I'd like to filter transparently all content going from LAN hosts through dansguardian -> squid.
I tried with couple iptables entries which I found, looking for DG configuration, but those didn't work for me.

Could anyone give me a solution how to configure squid3+DG to work transparently ? I ran out of ideas.
Maybe there's a program with GUI for this ? 
I just don't know how to create working iptables entry :(


ps. If I forgot to add any information, although I think I put all needed info, just mention what info should I add.


bump
anyone ?  :(
Sorry about the very late reply, have been off on other projects and have not been able to concentrate on Ubuntu stuff for some time.

I had followed the procedure given in this thred to the dot and it just worked out right.
My feeling is that:
1. if you clear all previous User added rules and reset IPTABLES to default config then re do the entire procedure.
2. See if you have switched on IP masquerading
3. See that the DHCP server points to the Linux Box providing Internet as the Gateway.

Now Please check these areas as they had caused some delay when i was establishing the transparencey.

Please do post back for further suggestions.

Thank you for asking.

Am as of now doing implimenting this procedure in another organization.
WIll post the enitre procedure (Bit will be using 8.04 LTS). This should provide you some clarity.

You could check the forumor my personnel posts for the complete procedure

---

### Post by Dibhala on 2009-01-08
I've solved mine problem, but completely forgot to mention about it. Understanding basics of prerouting in iptables was crucial.

Hope to see Abhi's description as well, as it might be better than the one I've invented using firestarter.

---

### Post by boob11 on 2009-01-14
Thank you

---

### Post by arapozo on 2009-02-13
This howto is great thank you.
I have a question, how do I force traffic to pass through dansguardian, i have dansguardian in port 8080 and squid on port 8000, if a user changes his proxy configuration he can bypass dansguardian. I want to force every outgoing traffic to go through dansguardian. How do i do that?

---

### Post by Abhi Kalyan on 2009-02-13
[http://ubuntuforums.org/showthread.php?p=6538892#post6538892](http://ubuntuforums.org/showthread.php?p=6538892#post6538892)
An extension thread with the complete details!!
------------------------------------------------
HI!
Its actually simple to force traffic through the dansguardian,
generally all traffic goes to TCP 80.
All we need to do is tell the firewall (IPTABLES) to redirect all data from 80 to 8080 (default port where dansguardian listens.
procedure is simple:
1. install 
1a. apache
1b. php
1c. webmin
1d. squid
1c. dansguardian
1e. dansguardian modue for wedmin (download from webmin website)
2. follow the procedure given by BMATHIS and then
3. make squids transparent
# just add "transparent" - for versions > 3.
http_port 3128 transparent
#you could also make the above as
http_port 127.0.0.1:3128 transparent
#the above code makes squid listen only to local host, this prevents people from configuring thier proxy in the browser to connect through squid instead of dansguardian
4. now get into the webmin
# [https://yourservername:10000/](https://yourservername:10000/)
#>networking>linux firewall
#goto>Showing iptable: Network address translation>ADD RULE
#have added a screen shot, use that to get the settings right.
#SOurse address or network should be yours
BINGO!!
restart squid and then dansguardian
Now even without setting the proxy in your client machine you should be travelling through dansguardian,
tails the log file to see if tits working
# tail -f /var/log/dansguardian/access.log
thats about it
5. one thing though BACK UP BACK UP BACK UP
6. apply the firewall setting before testing dansguardian traffic
7. please see that the GATEWAY and Primary DNS server are set to your proxy servers address
----------------------------------------------

---

### Post by neoinmatrix on 2009-02-13
:)Thanks for the details, I have been searching for this. I am new to Linux even Ubuntu. Just one question will that same apply for Ubuntu Server 8.10 version.:confused: Thanks again.:)

---

### Post by arapozo on 2009-02-13
Sorry that I did not elaborate on my question.
I'm setting a FreeNX server for browsing so all browsing will be done locally on the same machine that has squid + dansguardian + freenx running.
My squid is listening on port 8000 and dansguardian on 8080, I've seen the screenshot you posted but I don't understand the Firewall rule.
Could you please elaborate more?

Also, I want to import some blacklists and phrases from some sites that would be free, I know that squidguard.org has some blacklists, what other sites you recommend. Do you know of any instructions on how to import them?

Thank you for your help.

---

### Post by Abhi Kalyan on 2009-02-14
> **neoinmatrix said:**
> :)Thanks for the details, I have been searching for this. I am new to Linux even Ubuntu. Just one question will that same apply for Ubuntu Server 8.10 version.:confused: Thanks again.:)

I used the above method on my 8.04 LTS Hardy Herion!!
It should work fine on 8.10 i guess.

---

### Post by Abhi Kalyan on 2009-02-14
> **arapozo said:**
> Sorry that I did not elaborate on my question.
I'm setting a FreeNX server for browsing so all browsing will be done locally on the same machine that has squid + dansguardian + freenx running.
My squid is listening on port 8000 and dansguardian on 8080, I've seen the screenshot you posted but I don't understand the Firewall rule.
Could you please elaborate more?

Also, I want to import some blacklists and phrases from some sites that would be free, I know that squidguard.org has some blacklists, what other sites you recommend. Do you know of any instructions on how to import them?

Thank you for your help.

[http://ubuntuforums.org/showthread.php?p=6538892#post6538892](http://ubuntuforums.org/showthread.php?p=6538892#post6538892)

this thread should help you

---

### Post by PMAPereira on 2009-02-18
Who can i acess to reports, such like: website visited; downloads, internet times etc...

Please, can some one help me....

Best Regards 

PMAPereira

---

### Post by Abhi Kalyan on 2009-02-18
> **PMAPereira said:**
> Who can i acess to reports, such like: website visited; downloads, internet times etc...

Please, can some one help me....

Best Regards 

PMAPereira

Webmin has all the answers to your questions.
You can have reports based on the paticulars that you ask

---

### Post by toolfan2k4 on 2009-05-29
Hello, excellent how-to thanks! Two questions, how do I set this so I can access the proxy from my work IP address. I want to bypass my jobs blocking system which won't allow us to visit some pages. For instance at work they block you tube. So lets say my work IP is 192.168.1.526 on the public side, not on my actual work PC obviously. Also if I leave out the dansguardian part of the tutorial will I cause squid to stop functioning? Since I am the one using the proxy I don't need to block any bad sites. I am smart enough to know what not to visit. :)

---

### Post by TheFuzz4 on 2009-06-28
I am not sure if this has been discussed before or not.  Does anyone have a good how to on how to make it so that your squid server is basically your default gateway?  Basically I don't want to have to go to my users and change their browsers over to the proxy I'd rather it be transparent.  This is just for a home network so I don't need anything super fancy.  Thanks.

---

### Post by liverpoolatnight on 2010-02-20
Very clear and crisp tutorial :) but is anyone good with dansgaurdian that can tell me how to block only (malware, Ads, Virus) sites.

tryed [http://linuxpoison.blogspot.com/2008/09/protection-from-malware-using-squid.html](http://linuxpoison.blogspot.com/2008/09/protection-from-malware-using-squid.html) within squid 3.0 but is bypassing?

Thanks

---

