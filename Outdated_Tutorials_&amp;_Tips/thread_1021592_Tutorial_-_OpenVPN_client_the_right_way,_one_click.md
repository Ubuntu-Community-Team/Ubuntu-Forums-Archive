---
title: "Tutorial - OpenVPN client the right way, one click with gopenvpn"
date: 2008-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by TalynOne on 2008-12-25
**_Last Updated:_** December 26th, 2008.

**_My Setup:_**

**Tested Clients:** Ubuntu Intrepid Ibex (8.10) 32bit & 64bit, running Gnome, gopenvn SVN revision 5, and OpenVPN v2.1 RC11. I have also tested similar setups on Hardy 32bit & 64bit.

**Tested OpenVPN Server(s) :** Windows Server 2003 running OpenVPN v2.1, Linksys WRT54-GL router running DD-WRT v23 SP2 (09/15/06) vpn edition.

**_Goal:_**

In one click, use [gopenvpn]("http://gopenvpn.sourceforge.net/") to logon to an OpenVPN server and access local & remote machines by both IP address & name!

**_Preface:_**

Network Manager is pretty nice for certain things, such as connecting/maintaining WiFi connections and profiles. However, the Network Manager OpenVPN plugins only expose a subset of OpenVPN's feature set. This design leads to connectivity issues and the need to execute additional commands to properly and fully bring up a client VPN connection.

Instead of Network Manager we'll be using gopenvpn to manage and connect to OpenVPN servers. gopenvpn is a nice lightweight Gnome tray application that leverages the native OpenVPN configuration files, so that, unlike with the Network Manager OpenVPN plug-in, we'll have the full OpenVPN feature set available to us. gopenvpn can co-exist with Network Manager. In fact, in my setup, Network Manager is handling my WiFi, LAN & PPTP connections, while gopenvpn is handling my OpenVPN connections.

Don't let the length of this guide deter you. I find it's better to have too much information than not enough, because of this I will probably get into more detail than you might need. 


**_Prerequisites_**

[list]

[*] Properly configured OpenVPN server on a different subnet from the client subnet.

[/list]

**_Prerequisites To Be Able To Resolve Remote Hosts By Name_**

[list]

[*] Remote and local networks configured with DNS suffix.

[*] Query-able DNS server aware of remote computer host names and DNS suffixes.

[*] OpenVPN server configured to provide OpenVPN clients with DNS suffix and server values.

[/list]


**_ Recommendations_**

[list]

[*] Comfort with the Ubuntu Terminal

[*] Understanding of OpenVPN concepts

[*] Understanding of networking concepts (IP addressing, subnets, DNS resolution, DNS suffixes, and VPN routing concepts).

[/list]

**_Part 1 - get gopenvpn build dependencies and source code_**

[list=1]
[*] Make sure you have a valid Internet connection 

[*] Start a Terminal (**Applications->Accessories->Terminal**)

[*] To get the dependencies needed to build gopenvpn, execute the following commands (answer yes (Y) to any prompts):
    
```

sudo apt-get subversion
sudo apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libgnome-keyring-dev gksu gedit
sudo apt-get install intltool
sudo apt-get build-dep gtkpod
sudo apt-get install automake1.9

```

[*] Execute the following to download the latest gopenvpn SVN source code:
    
	```
svn co https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn gopenvpn
```
[/list]


**Part 2 - modify gopenvpn source to support OpenVPN v2.1 rc7+**

Starting with OpenVPN v2.1 rc7, a new argument, **--script-security** has been added. The source code for gopenvpn needs to be modified so that it accounts for this breaking change by specifying **--script-security 2**. This is needed so gopenvpn can execute the up/down script calls defined in the .ovpn/.conf client connection configuration files. The up/down calls are needed to properly set connection specific IP addreses, domain search order, etc..., on client connection/disconnection.

The "--script-security" switch is documented in the OpenVPN man page:
> 
0 -- Strictly no calling of external programs.

1 -- (Default) Only call built-in executables such as ifconfig, ip, route, or netsh.

2 -- Allow calling of built-in executables and user-defined scripts.

3 -- Allow passwords to be passed to scripts via environmental variables (potentially unsafe).


To accommodate for this change, two gopenvpn source code files (gopenvpn.c and gopenvpnstart.c) need to be modified. At the same Terminal, from part 1, execute:

[list=1]

[*] ```
cd gopenvpn/trunk/gopenvpn/
```

[*] Edit the first file by executing:

```
gedit ./src/gopenvpn.c
```

[*] This will open up a text editor, find the following block of code:
```

#ifdef USE_GKSU
command = g_strdup_printf("%s --management-query-passwords --cd %s "
                          "--daemon --management-hold "
			   "--management 127.0.0.1 %d --config %s",

```

And change it to this:
```

#ifdef USE_GKSU
command = g_strdup_printf("%s --management-query-passwords --cd %s "
                          "--daemon --management-hold "
			   "[COLOR=Blue]--script-security 2[/COLOR] --management 127.0.0.1 %d --config %s",

```			  

[*] Save the changes (On the menu, File->Save) & Exit (File->Quit)


[*] Edit the second file by executing:

```
gedit ./src/gopenvpnstart.c
```

[*] This will open up a text editor, find the following block of code:
```

/* Execute OpenVPN */
execl(OPENVPN_BINARY_PATH,
	  OPENVPN_BINARY_PATH,
	  "--management-query-passwords",
	  "--cd",
	  CONFIG_PATH,
	  "--daemon",

```	  

And change it to this:
```

/* Execute OpenVPN */
execl(OPENVPN_BINARY_PATH,
	  OPENVPN_BINARY_PATH,
	  "--management-query-passwords",
	  "--cd",
	  CONFIG_PATH,
	  "--daemon",
         [COLOR=Blue]"--script-security",
         "2",[/COLOR]

```	  

[*] Save the changes (On the menu, File->Save) & Exit (File->Quit)

[/list]

**_Part 3 - Configure gopenvpn build_** 


[list=1]
[*] Execute the following commands ("./autogen.sh" needs to be called twice because the first time it's called it will fail, this behavior is observed in Ubuntu Intrepid, but not Hardy):

```
 
./autogen.sh
autoheader
./autogen.sh
intltoolize --force
./configure --with-gksu=no

```

[*] gopenvpn installs a setuid executable "gopenvpnstart" which is used to start VPN connections without entering a password to gain administrator privileges. We need to use this executable for our setup. The documentation indicates that if a "#define USE_GKSU" statement exists in "gopenvpn.c" then "gopenvpnstart" will not be used.  However, this does not seem to be currently true. To get gopenvpn to use the "gopenvpnstart" executable you must go through the following procedure after executing the "/.configure" statement above. 

At the Terminal, execute:
```
gedit config.h
```

[*] This will open up a text editor, find the following line:

```

#define USE_GKSU 0

```

And delete it. A value of 0 is not good enough, it has to be completely undefined. 


[*] Save the changes (On the menu, File->Save) & Exit (File->Quit)

[/list]


**_Part 4 - Build/Install gopenvpn_**

[list]
[*] Execute the following commands:

```

make
sudo make install
```

[/list]


**_Running gopenvpn as root without password prompt_**

We need the gopenvpn executible itself to run as root so that the "resolvconf" package (that we'll be installing later) can properly execute when called via the "update-resolv-conf" script (which is called by the client .ovpn configuration up/down statements).
 
To get gopenvpn to run as root without a password prompt we'll be using the [Sudoers]("https://help.ubuntu.com/community/Sudoers") file. 

**_(Optional) Setting gedit as editor of the sudoers file_**

Personally I hate vim, for those that also hate VIM lets set gedit as the editor of the sudoers file.

[list=1]
[*] At the Terminal, execute: 
```
gedit ~/.bashrc
```

[*] Add to bottom of the file:

```

export EDITOR=gedit
alias visudo='sudo -E visudo'

```

[*] Save the changes (On the menu, File->Save) & Exit (File->Quit) 


[*] Exit and restart the Terminal for the changes to take effect.

[/list]

**_Configuring a user to run gopenvpn without password prompt via the sudoers file_**

[list=1]
[*] At the Terminal execute:
```
visudo
```

[*] Add to bottom the file, add the following:

```
[COLOR=Blue]username[/COLOR] ALL=NOPASSWD: /usr/local/bin/gopenvpn
```

In the above statement replace "username" with your log in name. The above sets the account specified, running under any hostname, to not need to provide a password when run under the root account (sudo/gksudo) for the /usr/local/bin/gopenvpn executible.


[*] Save the changes (On the menu, File->Save) & Exit (File->Quit)
[/list]


**_Setting gopenvpn to run at Gnome startup_**

**Note:** We use gksudo since gopenvpn is a graphical app that needs to run as root.

In Gnome go to the:
[list=1]
[*] **System->Preferences->"Sessions"** menu item.


[*] Go to **"Startup Programs"** tab and press the **"+Add"** button


[*] Set the following values:
	  
	  **Name:** gopenvpn
	  **Command:** gksudo /usr/local/bin/gopenvpn
	  **Comment:** OpenVPN Tray Client


[*] Press the **"OK"** button


[*] Press the **"Close"** button.
[/list]

**_DNS Suffix - The Key to Resolving VPN Hosts By Name_**

**Short Version:** Both sides of the connection should have unique DNS suffix assigned, and a querable DNS server aware of the suffix.

**Long version:**

Basic VPN logic dictates that both sides of the VPN connection should originate from different subnets. It would be problematic if a computer on both the remote and local networks had the same IP address. Lets say a local computer tried to access a remote computer (on the other side of the VPN) with an IP address of 192.168.1.3 and local computer existed with the same IP address, then, depending on how your connection is configured communication could only occur with either the remote or local computer, but not both. 

Similarly to gaurantee unique host names and the ability of the OpenVPN client to query the correct DNS server for the host being requested, both sides of the connection should have a unique DNS suffix assigned. This also allows us to have a computer with the name on both sides of the VPN connection since their full DNS names would be unique (eg computer1.apple.corp & computer1.microsoft.corp).

If your local network doesn't already have a DNS suffix configured, it's pretty easy to assign statically or via DHCP (If you're using DD-WRT v23 SP2 as your DHCP server it's the "LAN Domain" setting under the Administration->Services menu). Just pick a DNS suffix name out of the air, familyname.localhost, or companyname.corp are common choices, however don't choose [.local]("http://en.wikipedia.org/wiki/.local") to avoid possible problems.


**_Configuring the OpenVPN client configuration to automagically update your local DNS search order_**

At the bottom of your .conf/.ovpn client configuration file make sure you have the following two statements. 

```

up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

```

These statements call the update-resolv-conf script on client connection/disconnection. The update-resolv-conf script will then call resolvconf (we'll be installing this package later in the tutorial) to update the /etc/resolv.conf with the VPN server's search domains (DNS sufix). The script can handle multiple concurrent OpenVPN connections and will only add/remove the DNS suffixes for the connection going up/down.


**_Installing dnsmasq_**

dnsmasq is a DNS server package. We'll be installing and configuring dnsmasq by telling it which DNS servers to use for specific search domains.

To install dnsmasq, at the Terminal, execute the following:
```
sudo apt-get install dnsmasq
```

**_Configuring dnsmasq_**

[list=1]

[*] To edit the dnsmasq configuration file, at the Terminal, execute:

```
gedit /etc/dnsmasq.conf
```

[*] Find the section:
```
#server=/localnet/192.168.0.1
```

[*] Add entries for local and remote search domains/DNS Server IP addresses, for example:
```

server=/[COLOR=Blue]myhome.localnet[/COLOR]/[COLOR=Blue]192.168.1.1[/COLOR]
server=/[COLOR=Blue]mywork.corp[/COLOR]/[COLOR=Blue]10.51.1.2[/COLOR]

```
[/list]

**_Installing resolvconf_**

resolvconf will be called via the "/etc/openvpn/update-resolv-conf" script to update the client's search domain (DNS suffix) on client connection/disconnection.

To install this package, at the Terminal, execute the following:

```
sudo apt-get install resolvconf
```

A reboot will be required for this package to properly initialize, so I recommend rebooting the computer at this point.

[SIZE=3][COLOR=DarkSlateBlue]**You're done!**[/COLOR][/SIZE]

**_Tips/Tricks:_**

**Flusing the local DNS cache:**
[list]

[*]Install nscd by executing the following at the Terminal:
```
sudo aptitude install nscd
```

[*]Flush the DNS Cache by executing the following at the Terminal:
```
sudo /etc/init.d/nscd restart
```

[*]More info: [http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html](http://www.ubuntugeek.com/howto-clearflush-dns-cache-in-ubuntu.html)
[/list]

**Removing the OpenVPN client private key password when using a private key file/x509:**

If you would like to configure a client connection with no password prompts, or you would like to troubleshoot possible private key password issues then you may wish to remove the private key password from the private key file. To do this, at the terminal execute the following with values matching your client conifguration:

```
openssl [COLOR=Blue]rsa|dsa[/COLOR] -in [COLOR=Blue]private.key[/COLOR] -out [COLOR=Blue]privatekey-without-passphrase.key[/COLOR]
```

In the above command either specify rsa OR dsa, depending on the type of private key used.  

**Restarting the dnsmasq daemon**

This is usefull so that any configuration changes you make can take effect, at the Terminal execute: 
```
sudo /etc/init.d/dnsmasq restart
```

More info on dnsmasq can be found here:
[https://blueimp.net/linux/howto/dnsmasq.html](https://blueimp.net/linux/howto/dnsmasq.html)
[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

**Checking client search domains configuration after OpenVPN client connection/disconnection**

Execute the following at the Terminal:
```
cat /etc/resolv.conf
```

**Sample client .ovpn file**

.ovpn/.conf files should be placed in the "/etc/openvpn" directory.

```

client
dev tap
proto tcp
remote [COLOR=Blue]myhome.localnet 443[/COLOR]
resolv-retry infinite
nobind
persist-key
persist-tun
ca [COLOR=Blue]myhome/ca.crt[/COLOR]
cert [COLOR=Blue]myhome/logon_name.crt[/COLOR]
key [COLOR=Blue]myhome/logon_name.key[/COLOR]
ns-cert-type server
comp-lzo
verb 3
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

```


**_OpenVPN server running under DD-WRT considerations:_**

If your OpenVPN server is running under DD-WRT an issue I've encountered that the DHCP server running on DD-WRT doesn't properly pass the DHCP client configuration to the OpenVPN client. If you have control of the server the ideal solution is to modify the server configuration so that IP addresses, DNS suffix, and DNS server is provided by the OpenVPN server and not the DHCP server. For this to work properly make sure the OpenVPN server is configured to provide an IP range outside the DHCP server IP address range. I have provided a sample DD-WRT OpenVPN server configruation below to illustrate this configuration.

If you don't have control of the OpenVPN server you can either bring up the connection/client configuration manually (ifconfig) or via a custom script specified in the .ovpn client configuration file. 

Sample DD-WRT Firewall Script (I use port 443 since it's very rare for an outgoing firewall to block the https port):
```
/usr/sbin/iptables -I INPUT 1 -p tcp --dport 443 -j ACCEPT
```

Sample DD-WRT Startup Script:
```

echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
echo '600 1800 120 60 120 120 10 60 30 120' > /proc/sys/net/ipv4/ip_conntrack_tcp_timeouts


cd /tmp
openvpn --mktun --dev tap0
brctl addif br0 tap0
ifconfig tap0 0.0.0.0 promisc up

echo "
server-bridge [COLOR=Blue]Router LAN IP[/COLOR] [COLOR=Green](eg: 10.10.1.1)[/COLOR] [COLOR=Blue]Subnet Mask[/COLOR] [COLOR=Green](eg: 255.255.255.0)[/COLOR] [COLOR=Blue]First DHCP Address to give out[/COLOR] [COLOR=Green](eg: 10.10.1.151)[/COLOR] [COLOR=Blue]Last IP address to give out[/COLOR] [COLOR=Green](eg: 10.10.1.200)[/COLOR]
proto tcp-server
port 443
dev tap0
keepalive 15 60
daemon
verb 3
comp-lzo
client-to-client
push \"dhcp-option DNS [COLOR=Blue]DNS server[/COLOR] [COLOR=Green]If router is responsible for DNS then router's internal LAN IP (eg: 10.10.1.1) [/COLOR]\"
push \"dhcp-option DOMAIN [COLOR=Blue]DNS Suffix[/COLOR] [COLOR=Green](eg: myhome.localnet)[/COLOR] \"
tls-server
ca ca.crt
dh dh2048.pem
cert server.crt
key server.key
" > openvpn.conf

echo "
-----BEGIN CERTIFICATE-----
[COLOR=Green]--Replace with CA.CRT contents--[/COLOR]
-----END CERTIFICATE-----
" > ca.crt
echo "
-----BEGIN RSA PRIVATE KEY-----
[COLOR=Green]--Replace with SERVER.KEY contents--[/COLOR]
-----END RSA PRIVATE KEY-----
" > server.key
chmod 600 server.key
echo "
-----BEGIN CERTIFICATE-----
[COLOR=Green]--Replace with SERVER.CRT contents--[/COLOR]
-----END CERTIFICATE-----
" > server.crt
echo "
-----BEGIN DH PARAMETERS-----
[COLOR=Green]--Replace with dh2048.pem contents--[/COLOR]
-----END DH PARAMETERS-----
" > dh2048.pem

sleep 5
ln -s /usr/sbin/openvpn /tmp/myvpn
/tmp/myvpn --config openvpn.conf

```

---

### Post by Bill Day on 2009-01-06
I am working with your very interesting and thorough tutorial, and I have an observation and a question.

There is a small typo in Part 1 where it should say "sudo apt-get install subversion".

Also, I cannot seem to find .conf/.ovpn in my home directory or anywhere else.  Is there a particular place I should be looking, or do I need to create them, and if so where?  (I am assuming that .conf is a directory and .ovpn is a file.)

Thanks!

---

### Post by Bill Day on 2009-01-06
Oops, sorry.  With respect to point two, I figured out that you meant "/etc/openvpn/client.conf" on my system.  My bad.  I cannot really test things until I log on to a different subnet, but I will let you know how it goes.  So far, so good.

---

### Post by ryanmbruce on 2009-02-11
Yowza.  That's one thorough guide.  Thanks!

TalynOne, I don't suppose you would be interested in making a package for gopenvpn?  That would make this whole process much smoother.  I don't have much experience making packages, but I'd be willing to chip in some time to help, if you're interested.  You've already put this much work into it, so you may as well go one more step and make it widely available to everyone.

What do you think?

-Ryan

---

### Post by JeppeM on 2009-02-20
great guide, and i totally agree with ryanmbruce that a package for this would be great...

I did find a few problems though:

 * It should be sudo apt-get **install** subversion
 * You need to be root to edit /etc/dnsmasq.conf
 * Needs a litle bit information about what to do when you finish this guide :)

Other than those minor things, this guide made it happen for me... However, a package would be really helpfull

---

### Post by Xavier_To on 2009-02-20
Great tutorial, but i have issues connecting to my office's VPN... I lose my internet connection and lan connection whenever i launch gopenvpn connection.

Did anyone else experience this issue ?

---

### Post by tondop on 2009-03-20
I have a little problem. I successfully connects to the VPN server but I can't ping remote computer from LAN that have IP 192.168.252.xxx. My tun0 has IP 10.8.142.xxx

What is't wrong? Give me someone some advice?

---

### Post by bojo42 on 2009-03-25
hi there, i stumbled over this thread when looking for a solution to compile gopenvpn and so i should share with you that i made a deb package for it. so far the source package hasn't got a review by some packaging guru, but if you don't mind you can test it already.

regarding this howto i have included the script security patches, but i didn't comment gksu out. if some are still looking for that there is another solution at [http://tranceparance.wordpress.com/tag/vforvpn/](http://tranceparance.wordpress.com/tag/vforvpn/) without altering the source code.

for i386:
[https://launchpad.net/%7Ebojo42/+archive/ppa/+files/gopenvpn_0.0.svn20090325-0ubuntu1~ppa1_i386.deb](https://launchpad.net/%7Ebojo42/+archive/ppa/+files/gopenvpn_0.0.svn20090325-0ubuntu1~ppa1_i386.deb)

for amd64:
[https://launchpad.net/%7Ebojo42/+archive/ppa/+files/gopenvpn_0.0.svn20090325-0ubuntu1~ppa1_amd64.deb](https://launchpad.net/%7Ebojo42/+archive/ppa/+files/gopenvpn_0.0.svn20090325-0ubuntu1~ppa1_amd64.deb)

and i case you are willing to help to get this package in Ubuntu/Debian go to [https://bugs.launchpad.net/ubuntu/+bug/220362](https://bugs.launchpad.net/ubuntu/+bug/220362) 

best regards
bojo42

:guitar:

---

### Post by thePatric on 2009-04-26
Hi you guys,
I installed the program as described in the tutorial, but it won't open a connection, because my password is not accepted. I double and triple-checked it, and I typed it in absolutely correctly. What should I do?

And I found a bug: If I activate the "remember password"-option, the program crashes instantly.

Thanks for your advice :)

---

### Post by sefs on 2009-08-23
> **TalynOne said:**
> **_Last Updated:_** December 26th, 2008.

<snip>

**_Part 3 - Configure gopenvpn build_** 


[list=1]
[*] Execute the following commands ("./autogen.sh" needs to be called twice because the first time it's called it will fail, this behavior is observed in Ubuntu Intrepid, but not Hardy):

```
 
./autogen.sh
autoheader
./autogen.sh
intltoolize --force
./configure --with-gksu=no

```

[*] gopenvpn installs a setuid executable "gopenvpnstart" which is used to start VPN connections without entering a password to gain administrator privileges. We need to use this executable for our setup. The documentation indicates that if a "#define USE_GKSU" statement exists in "gopenvpn.c" then "gopenvpnstart" will not be used.  However, this does not seem to be currently true. To get gopenvpn to use the "gopenvpnstart" executable you must go through the following procedure after executing the "/.configure" statement above. 

At the Terminal, execute:
```
gedit config.h
```

[*] This will open up a text editor, find the following line:

```

#define USE_GKSU 0

```

And delete it. A value of 0 is not good enough, it has to be completely undefined. 


[*] Save the changes (On the menu, File->Save) & Exit (File->Quit)

<snip>



Hi, I would like to install it so that when I start it I have to enter my gsku password (which is similar to how you would run it from the command line anyway).  That is, with out this setuid thing.

What I can't understand is which method you are using above.

How can I configure to not use the gopenvpnstartup / setuid feature, but just run it as a normal app.

Thanks.

---

### Post by akavinski on 2009-08-25
Great tutorial !

I followed steps and there were no problems. But after restart I tried to connect to vpn I got this error "Error launching OpenVPN subprocess".
Can someone help me with this I have Ubuntu 9.04 x64 installed and openvpn 2.1 rc 11.

Thanks !

---

### Post by whlspacedude on 2009-09-10
Im having the exact same problem as akavinski.

---

### Post by akavinski on 2009-09-10
I solved problem with downgrading ubuntu 9.04 to 32bit version. And with Network Manager just follow wizard of OpenVPN connection and it works now like charm.

---

### Post by itismike on 2009-09-15
I too am seeing this error about the VPN service failing to start, yet I did not follow this guide.  It connects the first time, but after disconnecting I cannot reconnect without a reboot.  It has happened ever since I upgraded to Karmic Koala Alpha 5.  I found this while looking for a bug report.

---

### Post by clarkthehardy910mini on 2009-09-29
Please help.

Can anyone tell me how to undo all of this (I followed the instructions of the tutorial), but because I'm a total beginner, I did some guess work when it came to the Build and Subversion steps. 

So its not working properly: Even though I disabled gopenvpn from my startup services in Administration, now sometimes my network manager wont load at all and I cant get on the internet, unless I logout of ubuntu and log back in, sometimes I have to restart my computer.

I tried ~/gopenvpn/trunk/gopenvpn$ svn remove gopenvpn

but i get:

svn: Can't open file '.svn/lock': Permission denied

so i tried sudo svn remove gopenvpn

but it says: svn: 'gopenvpn' does not exist
 
Can someon please help me start from ground zero...so at least I dont have the bug of having to restart my computer to get my internet to work.

Thanks

---

