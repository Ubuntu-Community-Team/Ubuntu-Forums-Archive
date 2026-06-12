---
title: "Install and Configure Squid + Hamachi Proxy"
date: 2006-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Nomad64 on 2006-06-21
Since there is no good guide for installing and configuring Squid in Dapper, I wrote this guide for it.

This works for (K/X)Ubuntu 6.06 (Dapper Drake), and is untested in Ubuntu 5.10 (Breezy Badger) since I do not have a box to test it on. This guide walks you through setting up a Proxy server on a Ubuntu 6.06 box via Squid, then tunneling it through Hamachi. This enables you to use Hamachi to connect to the Ubuntu box, and then use it as a Proxy server...meaning it will be like surfing from that computers connection from anywhere. The benefits are obvious!

This walkthrough assumes that you have at least SSH access via PuTTY or another Linux terminal.

First, install Squid:```
sudo apt-get install squid
```
When Squid is installed, it will try to run and it will probably fail. Don't worry, there is still quite a bit to go over...So much for the easy part, now comes the configuration of Squid.

First, backup the default configuration file for Squid and make a new one. *Note: The default configuration file is a good file to at least glance through. If you want to do a more advanced configuration than this walkthrough does, you will want to read it.* ```
sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.backup
sudo rm /etc/squid/squid.conf
sudo vi /etc/squid/squid.conf
```

Below is a basic configuration file for Squid. I would suggest using this for the first time setup, so everything works and then playing with it later (be sure to read through the default configuration file before doing so). **Be sure to hit the "i" key on your keyboard while in vi before pasting this into the new file!**```
# # General Setup
# General options, these should all be left as-is (except the hostname) unless you know what you are doing.
http_port 3128
icp_port 3130
htcp_port 4827
visible_hostname server_hostname #Replace "server_hostname" with the hostname of your Ubuntu machine

cache_mem 16 MB
refresh_pattern . 0 20% 8640
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

# snews 563
# gopher 70
# wais 210

acl www_ports src 80 443
acl ftp_ports src 21
acl localhost src 127.0.0.1/32
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl CONNECT method CONNECT
acl PURGE method PURGE

http_access allow manager localhost
http_access deny manager
http_access allow PURGE localhost
http_access deny PURGE

# HTTP Access
# Allows access to HTTP(S) webpages. Comment these lines out if you don't want to allow access to HTTP(S) webpages.
acl wwwusers src 0.0.0.0/0.0.0.0
http_access allow all all

# FTP Access
# Allows FTP Access, comment these lines out if you don't want to allow FTP Access
ftp_user Squid@domain1.com
ftp_passive off
acl ftpusers src 0.0.0.0/0.0.0.0
http_access allow ftpusers ftp_ports

# Deny All Statements
# These are here mostly for reference, but you may want to use them depending on your setup.
# If you don't know what these are, leave them alone.
#never_direct allow all
#always_direct deny all
#http_access deny all
#icp_access allow all
#miss_access allow all 
```

Be sure to replace "server_hostname" with the hostname of your Ubuntu machine. If you don't know (or can't remember) just use the following command:```
hostname
```

After the information is entered in (you may want to double check), press the ESC key to exit insert mode, then type ":wq" (without the quotes) to write the file and quit vi.

Now you have to create the cache files for squid: ```
sudo squid -z
```
You may get some errors in this step, which are ok for now. Just be sure that there is line in there somewhere (probably the last) saying: ```
| Creating Swap Directories

```

Next, run squid in non-daemon mode, and with max debugging information on. This will allow you to run it, and test it, while getting some reasonable explination as to why it isn't working if you are having problems. ```
sudo squid -NCd10
```

At this point, Squid should be running. You will see a bunch of output appear on your screen, near the top should show something like this:```
| Accepting HTTP connections at 0.0.0.0, port 3128, FD 10.
| Accepting ICP messages at 0.0.0.0, port 3130, FD 11.
| Accepting HTCP messages on port 4827, FD 12.
| WCCP Disabled.
| Ready to serve requests.
```
This is good! Squid is saying that is ready to accept connections on those ports. *Note: Squid has to run as root in order to work properly.*

Now that the server is configured, time to configure your client-side applications to use it. Make sure you have Hamachi running, and that you are a part of the network with the proxy server. If you are running Linux, you may want to install [gHamachi](http://forums.hamachi.cc/viewtopic.php?t=2488) to make things easier.

Configure your client-side applications to use the server IP of your proxy server in Hamachi (5.xxx.xxx.xxx) and port 3128, unless you changed it in the configuration file. For example, in Firefox, open up the Preferences, click on the General Tab, then click on the "Connection Settings" button near the bottom. Select the "Manual Proxy configuration" radio button and add in the information to the "HTTP Proxy" and "SSL Proxy" boxes. If you are like me, you will also want to grab [this plugin](https://addons.mozilla.org/firefox/125/)

Once you are done configuring Squid, use ctrl+c to exit out of your "test session" (of squid) then type: ```
sudo /etc/init.d/squid start
```
This will launch the Squid daemon, which will run silently in the background of your Ubuntu machine, and automagically start when your computer is restarted. Just remember, you need to have Hamachi running on your server computer for the proxy to work properly. You may want to use the [Debian Startup Script](http://forums.hamachi.cc/viewtopic.php?t=5974).

You're Done!! Congratulations on setting up your proxy server.

Feel free to post recommendations, problems, etc that you have below

---

### Post by seismicmike on 2006-10-17
I have major problems dude. First, I've never heard of this hamachi. Can you tell me what it is and how to install it? Second, I haven't the foggiest clue what to tell Firefox my proxy server is. Should I say 127.0.0.1? If I do that it literally looks on my computer for every site I try to visit. That's not good. What about my hostname? I did that and got the same problem.

Thanks for your help

---

### Post by electricshoes on 2006-10-17
Quote from Hamachi.cc

 "  		Hamachi is a zero-configuration virtual private networking (VPN)  		application. 		

		In other words Hamachi is a program that allows you to 		arrange multiple computers into their own secure network  		just as if they were connected by a physical network cable."

There is a good Howto on setting Hamachi up.
[http://ubuntuforums.org/showthread.php?t=135036&highlight=hamachi](http://ubuntuforums.org/showthread.php?t=135036&highlight=hamachi)

---

### Post by crtvlynx on 2007-08-04
From my understanding this makes it all run off of your memory correct? seeing how there is no cache_dir only cache_mem

so my question is how do you set it up further to use the cache_dir..step by step including creating the directory creating the user/group and giving that user the correct permissions and adding the cache_effecctive_user and cache_effective_group.

thank you.

---

### Post by crtvlynx on 2007-08-06
no one respond to this anymore? hmm

---

### Post by Hashimi on 2007-08-09
Thanks for Nice share;

---

