---
title: "HOWTO: Setup an Apache Web Server For Free ($0)"
date: 2007-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by user1397 on 2007-12-05
So here's what I did to get an Apache Web Server running in my house.  I setup a very basic but totally cost-free server.  Note: This guide is not for setting up LAMP servers (Linux, Apache, MySQL, PHP/Perl/Python), as I didn't need to run a database or scripting for my small website, so all we're using here is Ubuntu Linux and Apache Server.

** 1.** Install the latest Ubuntu Server Edition on the computer you're setting up as a server. Make sure to **not select anything in the software selection screen** (where it asks if you want to install a LAMP server, an Email server, etc.), unless you know what you're doing.

**2.** Now go to [http://dyndns.com]("http://dyndns.com/") and make an account; I signed up for the Dynamic DNS service (because it's completely free) and made a hostname (my personal URL). Free hostnames cannot be top-level domains, such as yahoo.com, but you can make one like mydomain.dyndns.org

You may already have a hostname; in that case, you might want to sign up for the Custom DNS service, or also if you want to buy your own top-level domain (for example mydomain.com instead of a lower level domain such as mydomain.dyndns.org).  All the information you need to set up all the DynDNS stuff is at their website.

**3.** Log into your server, and install Apache and the DynDNS client: ```
sudo apt-get install apache2 ddclient
```If you don't know what to put for certain dialogs, **just go with defaults**.

Now you have to restart the ddclient: ```
sudo /etc/init.d/ddclient restart
```** 4.** Open a web browser on another computer, type your router's IP address into the address bar (usually 192.168.1.1 or something similar - look in your router's manual if not sure). You might need to give it a password to log in (the most common default is admin).

You will need to change a few settings, including port forwarding port 80 to the static IP address that you're going to give your server (**use the alternate ports 8080 or 8090 if you know that your ISP blocks port 80 by default**).

You also have to make sure that the DHCP address range of the router does not conflict with the future static IP address you'll assign your server. That means that if your DHCP hands out IP addresses starting at 192.168.1.100 till 192.168.1.110, then you'll want your static IP address of your server to be somewhere above that, like 192.168.1.125

If there is a DynDNS setting in your router (linksys has one, it calls it DDNS) then you should put your DynDNS account settings there.

** 5.** Now we'll set the server to have a static IP address (**assuming you went with 192.168.1.125 and that your router's IP address is 192.168.1.1**): ```
sudo nano /etc/network/interfaces
```and change
```
auto eth0
iface eth0 inet dhcp
```to
```
auto eth0
iface eth0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
```Then restart the network process: ```
sudo /etc/init.d/networking restart
```That's it! Now your server has a static IP address.

** 6.** If your ISP blocks port 80, then you have to change the default Apache config file: ```
sudo nano /etc/apache2/ports.conf
```**Change the ****80 to either 8080 or 8090**, depending on which port you forward to your static IP address in your router settings.  If you do this, you must restart Apache: ```
sudo /etc/init.d/apache2 restart
```**7.** If your ISP blocks port 80, and **if** you chose your alternate port to be **8080**, then your URL has to change accordingly; hence a sample host name you would make in dyndns.com could be name.home.dyndns.org:8080 (notice how you have to put a colon and the appropriate port number after the default URL).

In dyndns.com, you can use their "webhop" service (also free, just make another hostname) to redirect the host name you have (with the :8080) to a nicer looking one.  For example, you could tell people your URL is name.dyndns.org but it redirects to the one with the :8080.

You can also "cloak" your website so that when you redirect, say, name.dyndns.org to name.home.dyndns.org:8080, it still shows name.dyndns.org in the address bar; the only bad thing about this is that you'll be stuck with a DynDNS banner at the top of your website.

 **8.** Reboot, just to make sure everything is okay: ```
sudo reboot
``` and try going to your URL in a web browser, it should load instantly. 8) Also try checking if your website shows up on a computer outside you local network, to see if it is actually visible on the World Wide Web, and not just your LAN.  This can also be done by typing your URL in a proxy server, like this one: [http://www.freeproxyserver.net/](http://www.freeproxyserver.net/)

**9.** (optional) If you want to easily transfer files from your windows box to your ubuntu server, use this guide: (it worked for me) [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

This is great for updating your website files in /var/www.

Thanks to everyone who helped me with all of this, especially p_quarles, dfreer, and crashmaxx.

---

### Post by user1397 on 2007-12-13
tech9, rouge568, and alwiap you wanted me to tell you how everything went for me, and as you can see I got it all to work, so if you want to follow this guide but have any questions, let me know.

---

### Post by dfreer on 2007-12-13
Very nice guide ubuntuman001, and congrats on getting your webserver up and running!

> **ubuntuman001 said:**
> 
7) On the server, install the dyndns client: ```
sudo apt-get install ddclient
```and give it the information it asks for.

When I ran the automatic configuration for ddclient, it set several variables incorrectly (I may have just done it wrong :( ). Here's what I started with:
```
pid=/var/run/ddclient.pid
protocol=dyndns2
**use=if, if=eth0**
server=members.dyndns.org
login=*myusername*
password='*mypassword*'
*mydomainname.com*
```

The main thing I had to change here is the line highlighted in **bold**. If you set it to use the interface it will grab your LAN's IP address, which is most likely your private IP address. In most cases you'll want to change it to this:
```
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
```
This uses checkip.dyndns.com to grab your external IP address, and not your internal LAN IP.

Other useful things to add (see [http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html](http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html) for more details):
```
syslog=yes   ## logs information to /var/log/messages
mail-failure=*root*   ## you can replace this with your username if you wish
wildcard=YES  ## useful if you checked the "Use Wildcards" option, may not be available for the Free Dyndns service
custom=yes, *yourdomainname.com*  ## add the custom=yes option if you are using the "Custom DNS" service
```

> **ubuntuman001 said:**
> 
Then change the default apache config file: ```
sudo nano /etc/apache2/ports.conf
```and make it look like this after the Listen part (again, assuming you went with 192.168.1.125): ```
Listen 192.168.1.125:80
```if your ISP blocks port 80, then after the colon you would change that to either 8080 or 8090.

Unless you have a particular reason to bind apache to your static IP address, you don't need to specify your static LAN IP address in the ports.conf file. You can just do this:
```
Listen 8080
```
It's really not important, but it's one less thing you have to change if you for some reason change your static IP address. Plus, if you have multiple IP addresses on your server (two ethernet cards for example), it will respond to any incoming request for port 8080, and not just requests to 192.168.1.125:8080.

Just my two cents :D

---

### Post by tr333 on 2007-12-13
> **ubuntuman001 said:**
> 2) Once you have rebooted and you've logged in to your new install, you'll first want to omit the CD ROM repository from the sources.list file, to prevent apt from asking you for your server CD every time you want to install software: ```
sudo nano /etc/apt/sources.list
```Place an # in front of the CD repository (usually the first line, can't miss).

...

6) Now we'll set the server to have a static IP address (assuming you went with 192.168.1.125): ```
sudo nano /etc/network/interfaces
```

...

Then change the default apache config file: ```
sudo nano /etc/apache2/ports.conf
```

If you're editing config files with nano, you should use the '-w' option to disable wrapping of long lines.  This will prevent issues from arising if you have a long comment line in a config file and it gets wrapped onto the next line.

```
sudo nano -w /path/to/file
```

It would be even easier to set the EDITOR environment variable in ~/.bashrc to "nano -w".  This enables you to use the sudoedit command to edit files with nano.
```

# ~/.bashrc
export EDITOR="nano -w"

```
```
$ man sudoedit
$ sudoedit /path/to/file
```

---

### Post by tech9 on 2007-12-18
> **ubuntuman001 said:**
> tech9, rouge568, and alwiap you wanted me to tell you how everything went for me, and as you can see I got it all to work, so if you want to follow this guide but have any questions, let me know.

Wow! great job ubuntuman001! =D>

Thank you for taking the time to put this guide together! :)

I am going to  build a box/server special and dedicate it as an Apache Web Server ... powered by Ubuntu!\\:D/

---

### Post by user1397 on 2007-12-18
> **tech9 said:**
> Wow! great job ubuntuman001! =D>

Thank you for taking the time to put this guide together! :)

I am going to  build a box/server special and dedicate it as an Apache Web Server ... powered by Ubuntu!\\:D/Awesome! :guitar:

---

### Post by alwiap on 2007-12-18
I'm starting to do this right now, so I'll let ya know how it goes! :popcorn:

---

### Post by user1397 on 2007-12-23
> **alwiap said:**
> I'm starting to do this right now, so I'll let ya know how it goes! :popcorn:alright, let me know if you're having any issues...

---

### Post by p_quarles on 2007-12-25
All right, so just last night, my ISP decided to suddenly block my inbound port 80. Gah. Anyway, I remembered this tutorial, and followed the instructions for using webhop. Working nicely, thanks.

The problem: I seem to have to choose between two less-than-ideal options with this service. If I don't check the "cloak" box in the webhop setup options, the DNS server points to my site properly, but displays my IP address + port number rather than the URL. If I do check the "cloak" option, it displays the URL . . . as well as a banner advertising DynDNS's webhop service. 

Yeah, I know there's only so much you can expect from a free DNS, but does anyone happen to know a way around this?

---

### Post by user1397 on 2007-12-26
> **p_quarles said:**
> All right, so just last night, my ISP decided to suddenly block my inbound port 80. Gah. Anyway, I remembered this tutorial, and followed the instructions for using webhop. Working nicely, thanks.

The problem: I seem to have to choose between two less-than-ideal options with this service. If I don't check the "cloak" box in the webhop setup options, the DNS server points to my site properly, but displays my IP address + port number rather than the URL. If I do check the "cloak" option, it displays the URL . . . as well as a banner advertising DynDNS's webhop service. 

Yeah, I know there's only so much you can expect from a free DNS, but does anyone happen to know a way around this?yea that was the exact problem I was having, I couldn't find a way around it, so I decided that it showing my URL + port number was better than that banner at the top.
I know it looks sort of ugly, but it is the lesser of two evils, sotospeak (I think at least)

---

### Post by jan quark on 2008-01-02
Hi to all

I was fighting few days ago with the setting up of an apache server on my pc. 

with the help of the community I finally managed to bring a test web page online.

now after the fight I collected the scattered pieces of information from the post and wrote a tutorial.
[HTML]http://janquark.fatfreehost.com/tutorial2.html[/HTML]

can you please see it through for errors, only if you have time and its bad weather...

perhaps you can even test it?
just an idea

it worked for me

thanks in advance

PS
its my first howto so please zing and bash everything you find

---

### Post by sapperjanko on 2008-01-27
I must be a real n00b here, or I must be doing something wrong.

I just got ubuntu 7.10 Server up and running yesterday, I installed all the little things it asked in the install (MySQL, samba, LAMP, Mail server).

Now I have followed the tutorial, set the router to look at port 80 to 192.168.1.250 static on TCP (do i also need 2 set it to UDP), set up dyndns.org (sapper.mine.nu) but still having problems... 

The server is names ubuntu, and when i go [http://ubunta](http://ubunta) from another computer within the network it comes up with apache2-default directy, click that n a page loads up saying ITS WORKING....

But when i get a friend to try and connect to [http://sapper.mine.nu](http://sapper.mine.nu) it times out, they cant ping sapper.mine.nu:80 but yet they can ping sapper.mine.nu

What have i done wrong here.

Also with the ports.conf file should it look like this??
```
Listen 192.168.1.250:80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

---

### Post by user1397 on 2008-01-28
> **sapperjanko said:**
> I must be a real n00b here, or I must be doing something wrong.

I just got ubuntu 7.10 Server up and running yesterday, I installed all the little things it asked in the install (MySQL, samba, LAMP, Mail server).

Now I have followed the tutorial, set the router to look at port 80 to 192.168.1.250 static on TCP (do i also need 2 set it to UDP), set up dyndns.org (sapper.mine.nu) but still having problems... 

The server is names ubuntu, and when i go [http://ubunta](http://ubunta) from another computer within the network it comes up with apache2-default directy, click that n a page loads up saying ITS WORKING....

But when i get a friend to try and connect to [http://sapper.mine.nu](http://sapper.mine.nu) it times out, they cant ping sapper.mine.nu:80 but yet they can ping sapper.mine.nu

What have i done wrong here.

Also with the ports.conf file should it look like this??
```
Listen 192.168.1.250:80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```Hmm...for protocol I just used 'both' in my router settings, as in both UDP and TCP. (of course your router might be differnet than mine, but you get the idea)
 
your ports.conf looks fine; you don't really need the ip address though as one member mentioned in this thread, i.e. you can just make it 'Listen 80'

Your problem, if its not the protocol thingie, might just be that your ISP blocks port 80 by default; try what i said first about using both protocols, and if that doesn't work, then it is probably your ISP's fault that you're not seeing your page.  In my guide I also show you how to switch the port number.

---

### Post by mapltux on 2008-04-05
An informative post thanks ubuntuman001

---

### Post by shane2peru on 2008-04-07
First off, nice guide!  I too am rather new at this, and wondered if I could get any help.  I installed the Server and setup LAMP and well, I guess I check all those boxes for software install.  I'm running this as a test install, so if it flops, I will do it again, and get it right the 2nd or 3rd time. :)  Anyway, I changed the port to 8080 and both and when I go to [www.rices.homelinux.com:8080](www.rices.homelinux.com:8080)  I get, nothing!  From inside the Lan, I can access it on more than one computer.  Soooo?  What did I do wrong?  What would be my first step in troubleshooting this?  I do know that I have my dnydns account setup correctly and the ip address is correct.  I already have ddclient setup to work with OpenDNS and DNSOMATIC, and both of those are functional.  DNSOMATIC then in turn keeps my dnydns account up to date.  It is the long way around but it works.  Any help would be apprecaited.  Thanks!

Shane

---

### Post by dfreer on 2008-04-07
Best way to troubleshoot errors, I think, would be to start by going to [http://whatismyipaddress.com](http://whatismyipaddress.com), and write down the IP address it gives you.

Then, go to dyndns and make sure that the IP address for your host is the same as the IP you just wrote down. If it's not, then check your /etc/ddclient file for errors.

When testing to see if you can reach your website, start by specifying the external IP address in the browser, adding the port if needed (example [http://69.49.123.5:8080](http://69.49.123.5:8080)). Don't use the domain name until you know for sure the ports are not blocked, as it could be a DNS issue. Test from OUTSIDE the LAN, either by using a proxy server, getting online somewhere else, or by having a friend test for you. 

Then go to [http://www.canyouseeme.org](http://www.canyouseeme.org) from within your LAN (basically, just making sure that the IP it reports is the same as the one you wrote earlier), and check and see if the port is open.

If it's not, then you'll need to establish whether the problem lies with your ISP, your router, or your server's firewall. If you can access the site/port from within your LAN, then it's most likely not your server's firewall (if you have even messed with it at all).

To test if it's your ISP or your router, unplug the internet cable coming into your router and hook up a crossover cable between another computer and the internet port. Make the router use an external static IP address (like 192.168.1.5), then make your computer use a static IP address on the same subnet (like 192.168.1.1 while ensuring the subnet mask is set to 255.255.255.0).

From the computer hooked up to the router, and while your server is still plugged into the router, type the **router's** external IP address into your web browser, adding the port number if needed. For example, [http://192.168.1.5:8080](http://192.168.1.5:8080) If you can access your site, than the problem lies with your ISP blocking the port you are trying to use.

Hope this helps!

---

### Post by shane2peru on 2008-04-07
> **dfreer said:**
>  

Then go to [http://www.canyouseeme.org](http://www.canyouseeme.org) from within your LAN (basically, just making sure that the IP it reports is the same as the one you wrote earlier), and check and see if the port is open.

If it's not, then you'll need to establish whether the problem lies with your ISP, your router, or your server's firewall. If you can access the site/port from within your LAN, then it's most likely not your server's firewall (if you have even messed with it at all).

To test if it's your ISP or your router, unplug the internet cable coming into your router and hook up a crossover cable between another computer and the internet port. Make the router use an external static IP address (like 192.168.1.5), then make your computer use a static IP address on the same subnet (like 192.168.1.1 while ensuring the subnet mask is set to 255.255.255.0).

From the computer hooked up to the router, and while your server is still plugged into the router, type the **router's** external IP address into your web browser, adding the port number if needed. For example, [http://192.168.1.5:8080](http://192.168.1.5:8080) If you can access your site, than the problem lies with your ISP blocking the port you are trying to use.

Hope this helps!

Ok, this last part was most helpfull.  I'm sure my dnydns and ddclient are setup fine.  I ran them and checked all that.  Now when I go to that awesome web site you noted above, I find out that port 80, the connection was refused!  When I go to 8080 the connection times out.  Sooooo, I'm assuming that port 80 **is blocked**, and 8080 I'm missing a configuration somewhere to pass it along to my computer.  I did go in my router and setup the virtual server and forward 8080 to my machine.  I think I got this far before and had trouble setting up my modem?  Could my modem be a firewall too?  Thanks for the help!

Shane

---

### Post by mapltux on 2008-04-07
> **shane2peru said:**
> Now when I go to that awesome web site you noted above, I find out that port 80, the connection was refused!  When I go to 8080 the connection times out.  Sooooo, I'm assuming that port 80 **is blocked**, and 8080 I'm missing a configuration somewhere to pass it along to my computer.

Shane

8080 is blocked too for some ISPs perhaps you can search online what all ports are being blocked.

try choosing a random port like 83, 91 for testing purposes

---

### Post by shane2peru on 2008-04-07
well it was a thought, but I checked a bunch of misc ports 7575 4175, 8989, 15, etc.  and all of them were timed out.  I also out of curiosity checked 80 again, and it gives me the same response as any other port.  Does anyone know of another way to check the ports?  Perhaps another web site?  I live in Peru, and checking with my ISP is a little more of a pain than I want to mess with. :)  Their tech support is very sorry.

Shane

---

### Post by mapltux on 2008-04-07
> **shane2peru said:**
> well it was a thought, but I checked a bunch of misc ports 7575 4175, 8989, 15, etc.  and all of them were timed out.  I also out of curiosity checked 80 again, and it gives me the same response as any other port.  Does anyone know of another way to check the ports?  Perhaps another web site?  I live in Peru, and checking with my ISP is a little more of a pain than I want to mess with. :)  Their tech support is very sorry.

Shane

I am not sure how much of a help this is
[http://webtools.live2support.com/nt_cport.php](http://webtools.live2support.com/nt_cport.php)

and u update the ports.conf every time u forward ports?

then maybe a router firmware upgrade..perhaps someone with more experience would correct me

---

### Post by shane2peru on 2008-04-07
wow!  Got it thanks for the help!  I swapped out my modem for another one.  Wow, what a chore for setup etc.  Then I didn't have things at dyndns correct either! lol, you should have the wildcard box checked! Live and learn.  Glad it is done, thanks for the help.  

Shane

---

### Post by user1397 on 2008-06-29
Updated the guide to be more comprehensible and so that it would actually *work*.  It may have worked for some of you before, but a while back my ubuntu 7.10 server crashed so I reinstalled ubuntu but this time with 8.04, so I took the time to go through the whole process of setting it up again, and I noticed my guide didn't really work for me at first! :)

But all's well now, thanks for all the help on this everyone.

I think I'll also make an addition to the guide and add stuff about samba and transferring files from a computer to your server, but ahh....that's for another day :)

---

### Post by ssavelan on 2008-09-16
Man, this howto looked so juicy, just what I am trying to do.  Who knows, maybe it works... if it works will people be able to put mysite.dyndns.org into their browser and get "It Works!"?  From my machines here on the LAN mysite.dyndns.org sends them to the modem set-up/page/IP... seems like I am pretty close... been working on this for days though :(

Did your method through with the only errors throwing:

skylar@ABCtest:~$ sudo /etc/init.d/apache2 restart
[sudo] password for skylar: 
 * Restarting web server apache2                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                          [ OK ]
skylar@ABCtest:~$ telnet 127.0.1.1
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused

---

### Post by dfreer on 2008-09-16
> **ssavelan said:**
>                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


This error I'm pretty sure is the result of /etc/hosts or /etc/apache2/sites-enabled/* being incorrectly configured (the name of the file in /etc/apache2/sites-enabled/ could be www, default, or whatever you named it).

My /etc/hosts/ (the words in **bold** I replaced with generic names):
```
127.0.0.1       localhost.localdomain   localhost
10.1.10.101           **myservername.mydomain   myservername**
```

My /etc/apache2/sites-enabled/www:
```
NameVirtualHost *
<VirtualHost *>
        ServerName **myservername.mydomain.com**

        DocumentRoot /var/www/
```

Not sure if my example will help you, it would be helpful to post your /etc/hosts and /etc/apache3/sites-enabled/* files.

EDIT: Also, are you running telnet on your server? Why are you trying to telnet 127.0.1.1?

---

### Post by S0VERE1GN on 2008-09-23
very nooby question here, i began to setup the dns server settings in the file, and i typed them all in...

how do i save and exit? loL

I.E. this part:

Configuring Static ip address in Ubuntu server

Ubuntu installer has configured our system to get its network settings via DHCP, Now we will change that to a static IP address for this you need to edit Edit /etc/network/interfaces and enter your ip address details (in this example setup I will use the IP address 172.19.0.10):

sudo vi /etc/network/interfaces

**and enter the following save the file and exit**

# The primary network interface

auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1

---

### Post by S0VERE1GN on 2008-09-23
also, how do i get it to connect to the internet?
i can get any info to come in from my router

---

### Post by dfreer on 2008-09-23
> **S0VERE1GN said:**
> how do i save and exit? loL

I.E. this part:

sudo vi /etc/network/interfaces


vi is a bit complex for users not familiar with it. Instead of using vi, I would recommend you use nano, in which case you would type this commmand in instead:
```
sudo nano /etc/network/interfaces
```

Beyond that, in vi the command to save would be to press the ":" key, and then type "wq" (stands for **w**rite and **q**uit respectfully), then press <Enter>.

I always install the "vim" package when using vi, makes it easier to use because you can see the letters ":wq" at the bottom of the screen when you type them in. Try it if you prefer using vi:
```
sudo apt-get install vim
```


> **S0VERE1GN said:**
> sudo vi /etc/network/interfaces

**and enter the following save the file and exit**

# The primary network interface

auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1

> **S0VERE1GN said:**
> also, how do i get it to connect to the internet?
i can get any info to come in from my router

It really depends on how your home network is setup, I.E. how do you normally connect to the internet from your computer. If you use DHCP with a router, were you able to connect to the internet before you set up your static IP address? If you were, did you change your static IP address to be the same as the settings DHCP gave you before?

---

### Post by S0VERE1GN on 2008-09-23
The setup failed to conect to the internet via DHCP.  I usually conect wirelessly through a netgear wireless N router. I tried connecting directly through my cat 6 port, but nothing changed.  is there a specific code i can type in to get the net conection to configure?

---

### Post by S0VERE1GN on 2008-09-23
bump for an answer to the question

---

### Post by S0VERE1GN on 2008-09-24
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by dfreer on 2008-09-24
Sovereign, no need to bump a thread 3 times in 24 hour period :/

Wireless is going to be a problem with a web server, you are not going to want it. Beyond that, try connecting again via the ethernet port. Make sure it is set up to recieve an automatic address in /etc/network/interfaces, it should look like this assuming eth0 is your ethernet port:
```
auto eth0
iface eth0 inet dhcp
```

Then you can either reboot, or manually have it request an IP address with this command:
```
sudo dhclient eth0
```

You can check to see if you recieved an address with ifconfig, and test connectivity by either pinging a website or using lynx to browse the internet.

---

### Post by ounas on 2008-09-24
Thanks for the guide :):)

---

### Post by MicheleZ on 2008-09-29
Hello,

Thanks for the howto. I created a couple of pages and it works great.  
I have however a problem with wordpress.

My configuration is as follows:
My webserver is at 192.168.1.2

Router: DLink (web interface on 8081)
TCP IP redirected to 8080 (port 80 blocked by ISP)

created two profiles to use port 8080 as well as a directory in my /home instead of /var/www in /etc/apache2/sites-available and /etc/apache2/sites-enabled

My dyndns.org address is, say
abc.dyndns.org

Wordpress at the following address:
[http://192.168.1.2:8080/wp](http://192.168.1.2:8080/wp)
(both installation and blog address)

Now, on the intranet everything is great:
[http://192.168.1.2:8080/wp](http://192.168.1.2:8080/wp)
or 
[http://localhost:8080/wp](http://localhost:8080/wp)
get me to my wordpress page.

The problem is when I try to access from outside my intranet: when I try abc.dyndns.org:8080/wp I get a 504 gateway timeout error message.

I can connect to my index.html (and even to my abc.dyndns.org:8080/gallery2) without any problem. 

What am I doing wrong?

Cheers,

Michele

---

### Post by dfreer on 2008-09-29
> **MicheleZ said:**
> 
created two profiles to use port 8080 as well as a directory in my /home instead of /var/www in /etc/apache2/sites-available and /etc/apache2/sites-enabled


Hmmm... it might be helpful to see the contents of all files in /etc/apache2/sites-enabled/ (edit out/replace any data you think is sensitive). Also, try connecting to the site again and then post the relevent portion of your /var/log/apache2/ access and error logs during that time period, see if anything pops up.

Off the top of my head, I'm guessing it's a permission issue. Are all the folders in the website set to 755, or at least readable/executable by www-user? Are all the files 644 or at least readable by www-user?

Also, if you are accessing your website from within your LAN, but using the public address, try using a http proxy like [http://www.hidemyass.com](http://www.hidemyass.com)
Sometimes I've had issues with hitting the router which won't properly forward my request to the web server from inside the LAN.

---

### Post by MicheleZ on 2008-09-29
Hello Dfreer,

I kind of solved the problem as I was told that because of the way Wordpress (and similar applications) are designed, if you want to make it available on the internet you need to provide the public address where it is hosted so that the client can get other pages. 

Basically at present WP tells the client to get some information from an address consisting of [my private IP]/something which of course fails when the client is not on my intranet. 

I guess I will have to find a "real" host if I want to use WP :(

Cheers, 

Michele

---

### Post by dfreer on 2008-09-30
> **MicheleZ said:**
> Hello Dfreer,

I kind of solved the problem as I was told that because of the way Wordpress (and similar applications) are designed, if you want to make it available on the internet you need to provide the public address where it is hosted so that the client can get other pages. 

Basically at present WP tells the client to get some information from an address consisting of [my private IP]/something which of course fails when the client is not on my intranet. 

I guess I will have to find a "real" host if I want to use WP :(

Cheers, 

Michele

I can go over this in more detail later, but this shouldn't be a limitation. The basic solution is that you need to tell WP to give out your Public IP/free domain name instead of your private IP. It probably won't respond to requests from your LAN anymore, but that can be fixed too. 

But I don't think a 504 error message would result from this problem... it could. In my initial tests on my old wordpress installation, I got a "Redirect Loop" error, but that could be due to a different issue/unique way I set up my server.

Try poking around with wordpress again, and if I remember (feel free to remind me), sometime when it isn't 4:40 AM I will go through a clean installation of WP and help you out some more. I'm using Custom DynDNS, but it really shouldn't make any difference (I'm even using port 8080 too). 

I'm positive this should work for you.

---

### Post by spynappels on 2008-10-02
Hi guys,
   Sorry to hijack the thread, but could someone point me to a how-to on publishing a website from Dreamweaver to the resulting web server?  I've published web sites to hosted servers before, but want to host a small site on my own server to see if I can do it.

  Thanks for your help.

  Stef.

---

### Post by stevoo on 2008-10-02
Perhaps you can point me out what i am doing wrong.

I can view it normally over my intranet, but going public gives me problems

My apache file
```

<VirtualHost 192.168.10.6 213.207.183.3 >
	ServerAdmin stevoo82@gmail.com
	ServerName mafialand
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

```
My hosts file 
```

127.0.0.1 localhost
127.0.1.1 sTevooOnUbuntu
127.0.0.2 mafialand.dyndns.org mafialand

```

How can i push my site to go out public ? 

cheers

---

### Post by MicheleZ on 2008-10-02
Hello dfreer,

Been away a couple of days but willing to try to fix the issue of home-hosting WP. I will write a sort of tutorial if I get it to work.

> **dfreer said:**
> The basic solution is that you need to tell WP to give out your Public IP/free domain name instead of your private IP. It probably won't respond to requests from your LAN anymore, but that can be fixed too. 

Ok this is where I am now. If I configure WP to use my private IP address it works from the intranet, if instead I configure it to use abc.dyndns.org:8080 then it works from outside but not from the LAN.

> **dfreer said:**
> Try poking around with wordpress again, and if I remember (feel free to remind me), sometime when it isn't 4:40 AM I will go through a clean installation of WP and help you out some more. I'm using Custom DynDNS, but it really shouldn't make any difference (I'm even using port 8080 too). 

I'm positive this should work for you.

Here's where I am now:
WP is configured to use my_dyndns_domain:8080/wp both as directory where the files are and as URL of the blog. 
It works a treat from the intranet.
When I try to access my_dyndns_domain:8080/wp or 192.168.1.2/wp from the server itself, I get a connection refused message (from Firefox). I noticed that 192.168.1.2/wp was converted by firefox in my_dyndns_domain:8080/wp which of course on my machine does not mean much. Then I thought all I had to do was to modify the /etc/hosts file to tell my intranet computers that my_dyndns_domain/wp (where the blog is) is in reality my_intranet_IP. I added this line in the file /etc/hosts
192.168.1.2  my_dyndns_domain
but it did not really work.

Will keep scouring the wordpress forum and googleing of course!

Cheers,

Michele

---

### Post by user1397 on 2008-10-08
> **stevoo said:**
> Perhaps you can point me out what i am doing wrong.

I can view it normally over my intranet, but going public gives me problems

My apache file
```

<VirtualHost 192.168.10.6 213.207.183.3 >
    ServerAdmin stevoo82@gmail.com
    ServerName mafialand
    
    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>

```My hosts file 
```

127.0.0.1 localhost
127.0.1.1 sTevooOnUbuntu
127.0.0.2 mafialand.dyndns.org mafialand

```How can i push my site to go out public ? 

cheers
Are you sure your ISP isn't blocking port 80?  what port are you using?

---

### Post by user1397 on 2008-10-08
> **spynappels said:**
> Hi guys,
   Sorry to hijack the thread, but could someone point me to a how-to on publishing a website from Dreamweaver to the resulting web server?  I've published web sites to hosted servers before, but want to host a small site on my own server to see if I can do it.

  Thanks for your help.

  Stef.
well I don't use dreamweaver myself, so I don't know too much about it, but you can just save your html files somewhere on your windows desktop and then transfer them to your server by creating a network folder pointing to your server.

---

### Post by wifiwaves on 2010-01-31
Just a reminder that some home routers have a DMZ feature that can be used.
 
Use with caution...!

---

### Post by user1397 on 2010-02-02
> **wifiwaves said:**
> Just a reminder that some home routers have a DMZ feature that can be used.
 
Use with caution...!
Could you elaborate on that please?

---

### Post by dfreer on 2010-02-03
A typical home router will provide NAT (Network Address Translation); allowing multiple devices to access the internet using only one external IP address. It basically tracks outgoing connections from each computer and when a reply to that connection comes from the internet to the router, it checks it's internal table to see which computer to forward the message to.

The problem with this is that connections that originate from the outside (i.e. a request for a web page), the router has no idea which internal computer to route the message to. This is why port forwarding is needed, basically saying "All incoming messages on this specific port will always go to this machine".

Now DMZ (De-Militarized Zone) comes into play; for brevity I'm just going to explain why you would want to use it for a home server, as it has other more important uses, and I also don't quite understand how it work completely. Any DMZ'd device will be outside of the router's firewall, as in its ports will be completely exposed to the internet. Other devices will still be able to use NAT to access the internet, if I recall correctly it's just all incoming messages that are NOT a reply to an already established communication will be sent to the DMZ. 

So why use the DMZ? It's a lot easier to troublshoot connection issues when you know the computer is exposed to the internet completely, basically eliminating the troubleshooting step of whether port-forwarding was set up correctly (DMZ setup on home routers simply consist of checking a box enabling it, and inputing an internal IP address of the computer you want to use). The caution here is that the router's firewall will not protect the DMZ, removing one layer of security from your machine.

---

