---
title: "Access Samba shares from Windows 8?"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by squakie on 2013-04-24
** PLEASE NOTE:  I'VE MARKED THIS AS SOLVED BUT THERE IS NO SOLUTION HERE - I'VE JUST GIVEN UP ON THE ENTIRE THING **



I seem to be having a problem I don't understand.  I have xubuntu running on an old laptop.  I loaded Samba and configured my workgroup name, turned on user security and added a share.

On the xubuntu laptop I can see the network, see the workgroup, see the server and log into the share.  Right now I don't have ufw enabled, but assume I should.  I don't know how to set it up to allow Samba shares (ports??).

On my good laptop I have Windows 8 with ZoneAlarm installed and running  Trend Micro antivirus.  If I open file manager and click on network, sometimes the server shows, sometimes it doesn't.  Clicking on it always results in the same message - it can't find the network path.

On Windows 8 I tried the registry addition of the lanman "level"  as per Windows 7 - but Windows 8 doesn't have both control001 and control002 as per Windows 7.  Still can't get to the server.

Besides the old crappy laptop running xubuntu and Samba, there are 3 other laptops here - Windows XP Pro, Windows 7 and Windows 8.  Mine is the Windows 8 one.  I want to be able to run backups by user to their share in Samba, and also set up shares for common pictures, etc..  I thought xubuntu running Samba was the way I was supposed to accomplish this.

Has ANYONE been able to see Linux Samba shares from Windows 8??  I've left the sb.conf pretty much default.  I don't know a thing about making Samba the master browser, domain controller, etc., and was *hoping* I wouldn't have to learn that part of things.  Firewall settings?  Something in the Samba server conf file? 

ANY help would be greatly appreciated!!

---

### Post by squakie on 2013-04-26
Bump.  The only thing I have even seen mentioned is turning off user lever security in Samba and letting all shares be seen and available to all Samba users, including guest.  I haven't tried it since right now I am trying to load XP on the old laptop to see if all these different versions of Windows can do simple sharing or not.  If so, that buys me just as much as trying to get Samba user-level security working with Windows 8.  I'd really like to keep this all Linux based if possible.

---

### Post by squakie on 2013-04-27
I found another older post on the internet for this.  It has a registry update for Windows 8 so that it can access Samba shares, but it also seems to require that the computers in question all be part of a domain.  In addition, I found another thread that suggested the Samba box should be made the domain server to avoid excess net traffic from computers trying to discover the domain server.  With enough playing around, I'm sure I could manage that, but I'm afraid I've been away from these things long enough that I have what may be the dumbest question in the world:

I am not a business running my own domains.  I'm just a guy who has cable, which feeds the cable router/phone adapter/tv adapter/wireless box.  All of the PC's here connect to the internet via the wireless connection.  DNS is via the net.  So how could I set up a domain that is local to the wireless side and still let the computers use the internet and DNS there?  2 of these laptops are also taken "on the road" and used at other private and public wireless access points to access the internet.  I'm quite confused here (I bet THAT didn't show, eh? ;) ;) ) and really need some help trying to understand how this would work before I just go setting up the Samba box to also be a domain server.

---

### Post by redmk2 on 2013-04-27
> **squakie said:**
> I found another older post on the internet for this.  It has a registry update for Windows 8 so that it can access Samba shares, but it also seems to require that the computers in question all be part of a domain.  In addition, I found another thread that suggested the Samba box should be made the domain server to avoid excess net traffic from computers trying to discover the domain server.  With enough playing around, I'm sure I could manage that, but I'm afraid I've been away from these things long enough that I have what may be the dumbest question in the world:

I am not a business running my own domains.  I'm just a guy who has cable, which feeds the cable router/phone adapter/tv adapter/wireless box.  All of the PC's here connect to the internet via the wireless connection.  DNS is via the net.  So how could I set up a domain that is local to the wireless side and still let the computers use the internet and DNS there?  2 of these laptops are also taken "on the road" and used at other private and public wireless access points to access the internet.  I'm quite confused here (I bet THAT didn't show, eh? ;) ;) ) and really need some help trying to understand how this would work before I just go setting up the Samba box to also be a domain server.

I think it's important to define what you mean by "domain".  For the most part a "domain server" is a centralized server that holds the centralized login accounts and security settings for a particular "domain".  It is a security thing.  Samba can do that but it is not absolutely needed.  It has nothing really to do with file sharing per se.  It is important to the conversation to know what version of Samba are you using.  I use Samba 3.6 for all my file shares.  I do not administer my 6 hosts centrally at all.  This is typically thought of as a workgroup situation, but it's all semantics as you don't even need to be in the same workgroup for it all to work.  There are so many variations to both domain PDC (NT style) or DC (AD (LDAP) style) or workgroup (Ad Hoc) that it is best to decide first what it is you are attempting to do.  I believe you would just need a workgroup situation.  

If you want all of this to work correctly you need to have the basic networking connectivity pieces working first.  The basic Samba install using Ubuntu debs (Synaptic or some such) expects that you have done this.  To me this means you need to configure your local network name resolution (LAN side DNS) .  This is specific only to your LAN.  The Internet DNS is not part of this configuration.  You could think of this as your domain.  I have all of my desktop/server hosts configured with a static IP address (via /etc/network/interfaces).  My laptops have a consistent IP address (unchanging) too.  Once the IP addresses are consistent, you can set the hostnames via the /etc/hosts file.  When resolving DNS the hosts will first check the *hosts * file first before consulting a DNS server.  This is also how Windows and Apple OSX work also.

Why is this important?  Because ***Samba by default***, checks the *hosts *file as part of this DNS local lookup and if successful, the hostname is converted to a NETBIOS name that Samba can use.  With out this you have to resort to a non-default configuration.  It's okay to do that, but if you don't understand you might not get it all correct and then be frustrated with inconsistent results.  I believe that all the configuration and registry hacks are unnecessary for successful local single segment LAN operation of Samba 3.6.

I would start with a simple default smb.conf file and correctly setup IP networking and build out from there.  One server and a single Windows host.  Then use debugging (-d3 or so) to pinpoint what, if any, problems you are experiencing.  As it stands now it appears you have too may variables to contend with (yes I have read your other posts).

In short Samba should be able to share files in a simple home LAN without too much fuss.   The correctly configured TCP/IP infrastructure is very important to successful operation of Samba.  I have used the same setup from Win2000 to Windows7 and never had to resort to any modification of the Windows clients registry at all.  It's helpful to understand that Samba 3.6 has 3 aspects of operation -- PDC (NT style Domains) -- File sharing (mapping a drive) and Network Browsing.  I don't see that you need the first and you may not need the last either, but it will make Samba more enjoyable.
To start with, are you using Samba 3.6 or Samba4 ?

---

### Post by squakie on 2013-04-27
I'm not at the system at this moment, but I believe it's 3.6 - I seem to remember samba4 being mentioned in synaptic as still experimental and not to use it for a production environment.  Since I think backups fall into the production environment are, I stuck with what I believe is samba 3.6. 

You are very correct in my wanting to keep this as simple as possible.  All I really want to do:

- all three laptops should have their own unique shares that the other PC's can't see
- all three laptops should be able to access 1 or more common shares (say for pictures, common documents, etc.) where things are in a single place.  I started with just a workgroup XXXX just to test, and I turned deleted the text that was in that other choice (I can't find the thing right now, but it had a name instead of being in a workgroup).  I just simply want to be able to assign a logical drive in Windows to the corresponding Samba share
- I just want the 3 flavors of Windows to be able to access the shares (Win XP Pro, Win 7 and Win 8)
- I'd like to keep all the shares on the external usb drive (perhaps more than 1).  I think as far as sharing the drives it should be a non-issue
- I would like to start with a single laptop - my Windows 8 one - and get it all working with Samba
- in that regard, I'd like the xubuntu old laptop with Samba to have a fixed IP address (I tried this but it was late at night and I obviously didn't follow the instructions ;) ). My understanding is that all of that goes in the interfaces.conf (sp?) file.  The 3 laptops that I want to be able to use the Samba shares I would like to keep at dynamic addresses if possible - I don't know if that's a practical idea or not - I just thought it would minimize changes to each laptop. 
- I don't have a clue anymore on what, if anything, I need to change in /etc/hosts
- I'm also not sure about what you mean by the TCP/IP infrastructure - everything is IPv4.  On the Windows 8 laptop I do have the file and printer sharing enabled in the tcp/ip configuration.  Beyond that I don't understand enough anymore to know what the heck to do - I hope you don't mind that and would be willing to work with me.

If you don't mind helping me, perhaps when this is all done and working we can collaborate (or maybe you'd just like to do it since you know this stuff ;) ) on a simple how-to for this simple type of sharing.

Thank you so much for your response and help.  As I'm sure is obvious, I am more than a little lost, and I think the things I've seen on the net for Windows 8 being able to access Samba shares is just confusing things.

I'm going to start by completely reloading xubuntu and then samba on the old  laptop and take the default Samba config and see what happens.  I'll also assign am IP address to it.

Thank you so very much again!  I think what I want to do is really simple and doesn't require the other things I have found - and I don't understand any of that anyway! ;)

---

### Post by squakie on 2013-04-27
Here's another dumb question - I really hope you don't mind.  Without Samba installed, is there something I can do to be sure that the networking parts themselves are working - like seeing the xubuntu machine from the Windows 8 laptop and vice versa?  Maybe there's something I'm missing at a very basic level there as well.  I just thought I had to have Samba so I could have a workgroup name so I could match it to Windows and be able to see each other.

---

### Post by redmk2 on 2013-04-27
> **squakie said:**
> Here's another dumb question - I really hope you don't mind.  Without Samba installed, is there something I can do to be sure that the networking parts themselves are working - like seeing the xubuntu machine from the Windows 8 laptop and vice versa?  Maybe there's something I'm missing at a very basic level there as well.  I just thought I had to have Samba so I could have a workgroup name so I could match it to Windows and be able to see each other.

With your default install of Xubuntu we can start by confirming that it uses the proper hostname.  

I like to use the CLI fo all my configuration, so we will use that.  Open a terminal and use this command```
hostname
```...what do you get?

What is returned when you use this command```
cat /etc/hosts
```

Can you explain basically how you setup your TCP/IP networking on this host?  I'm curious and I have never used Xubuntu.  I have a really old Pentium 3 Dell that I use as a Samba server to do backups with.  It is Ubuntu server 12.04 with no GUI at all.  Do you intend on using this Xubuntu host for anything other than the Samba server?

---

### Post by squakie on 2013-04-28
As far as I know, xubuntu is just ubuntu but with the xfce desktop manager instead of unity - it makes it lighter.  So, the installation automatically set up networking.  By default, it adds the name of the user being set up to the front of what it finds for the computer "description", which usually ends up being a long string.  I didn't take the default and instead entered "dwesamba".  So, the outputs you wanted are as follows:
```
dwesamba@dwesamba:~$ hostname
dwesamba
dwesamba@dwesamba:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    dwesamba

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
dwesamba@dwesamba:~$ 

```

I only plan on using this old laptop just for Samba, so perhaps I would be better off with just the server edition?

I did follow a couple of threads in the forum for setting up a static IP address - tried it first via network manager/edit, but all I got was a network that I couldn't do anything with on the net.  Pings to a name came back as unable to resolve the name. I had looked at the network information (it's wireless) prior to the editing, so everything go entered the same except for the IP address - I changed it to 10.0.0.250 (I have a printer at 252, and there's another printer - my brother in-laws' - that's wireless also but he installed it when I wasn't home so I don't know what it assigned for IP - I think 10.0.0.50).  Btw, my net is showing at 10.x.x.x since the cable box/telephone adapter/net access point has a built-in router (only a few ports) so it grabs the higher IP so I get it's subnet for the wireless.

I tried doing what was in another thread, with instructions from chili555, to set a static IP address in 12.04 (i'm at 12.10) but that also resulted not only in a network that wouldn't work - the system wouldn't boot up all the way - got stuck on waiting for network configuration and then it completely hung.  Tried the old power button off, then power back on and let it boot, but with the same result.  This was both trying network manager and also by just making changes to /etc/network/interfaces.  That last one caused a lock up - perhaps I was supposed to shut-down or remove nm before putting the changes in interfaces.

So, I reinstalled xubuntu 12.10 from scratch again, did the updates again, then let it do the upgrade to 13.04.  Things didn't work any better and I couldn't get my network back.  So....I reinstalled xubuntu 12.10 again and did the updates.  Now I'm just using the default auto-configuration for wlan0 instead of specifying anything so I at least have an internet connection again!  But alas - no static IP address!

It's a completely green install right now - I've done nothing with it.  If you think I'd be better off just installing the server version just let me know.  I was just leary of it because I didn't know what any of the defaults were - like does it automatically enabled http, php, etc., access, when all I want is Samba.  If just the server version I won't need to use xubuntu - I just did that since t doesn't use unity and therefore actually runs on this old laptop.  And I'm not afraid of the command line.  Although.....in the mess I got into I tried going in via root terminal recovery mode only to find the only editor that I knew of that it would run was vi - and I hadn't used vi since 1993 so any knowledge I had on that is gone! ;)  I also don't remember how to start the dhclient from the command line but I'm sure I could figure that out.  I think I'll go ahead and download the server version and burn a disc so I'm ready in case you think I should just go that way.

EDIT:  btw, when I've tried to set a static ip via network manager, in the ipv4 settings I had to change it to manual so I could specify anything.  After stopping and restarting networking, it would connect, and it showed the same under information as it did when I used just the whatever it defaults to - the only differences were "manual" instead of "automatic" and the IP address - "10.0.0.250" versus "10.0.0.7" <- what it seems it's always getting assigned anyway.

---

### Post by squakie on 2013-04-28
Well, an update.  I downloaded Ubuntu server 12.04 32-bit and installed it, selecting only samba and my wireless as the network.  When it booted my network let me ping [www.yahoo.com]("http://www.yahoo.com").  Hosts shows "Ubuntu" now instead of "samba", as I just took the default.  With that in mind, the hosts file now also show "Ubuntu" instead of "samba".

I tried following [this]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html")  I tried to temporarily give wlan0 a static IP address via:

sudo ifconfig eth0 10.0.0.100 netmask 255.255.255.0


An ifconfig then showed the IP address I specified and the mask I specified.  I tried to ping [www.yahoo.com](www.yahoo.com) again, and it failed with hostname not found.  I thought this must be a DNS error, yet /etc/resolv.conf shows the correct IP address for the dns servers and a line for Comcast's things.  So, just changing the IP address seems to stop me from being able to use DNS.  Perhaps this is a router issue, and to be honest I don't want to mess with the router set up as the last time I did my brother inlaw had problems with the net (was actually problem when he tried to access Juno) and of course since I made changes - well, you know.

So at any rate, I'm going to try leaving the interface as dhcp and see if things get any further.

My next step is to edit the smb.conf file and just change the workgroup name to GWSTJS0001 to match the workgroup name I put in Windows 8.  I'll see if anything shows on the Windows 8 computer after doing so.

So far I'm just leaving the USB drive unplugged since it appears to be a non-issue in this entire thing.

---

### Post by squakie on 2013-04-28
Okay, now I'm really confused.  I still don't see anything in Windows 8.  On the server I tried pinging my printer at 10.0.0.253 and it replies back, so the default network configuration does let me see something on the net.  From the server I can also successfully ping the Windows 8 computer by IP address.

So, after all that, using the default network configuration and the default smb.conf file (except for the workgroup name), I'm still back to where I started from - Windows 8 doesn't see the workgroup or the server.  I am really confused right now as it means things in the server must be configured right, yet Windows 8 doesn't see the server.

---

### Post by squakie on 2013-04-28
I tried [this]("http://blog.gambliser.com/2012/03/how-to-join-windows-8-to-samba-domain/") registry update for Windows 8 (so Windows 8 can join a Samba domain) but not - obviously I don't have any Samba domain.

---

### Post by squakie on 2013-04-28
I copied a very short smb.conf file shown in a thread on the forums that supposedly worked with Windows 8.  I restarted smbd, tried to restart nmbd but it apparently wasn't started so I had start it.  I go back over to the Windows 8 PC - no server again.  I don't know if this has anything to do with being wireless or what, but I think I'm going to can this whole thing, by a used 64-bit machine and put Windows Home Server 2011 on it.  I've seen reports about WHS 2011 not wanting to work with uefi drives, but I suspect that if run the Dell backups I can probably direct the output there (as I want to with Linux and Samba).  I don't know if it will work with wireless either, but I just can't connect this to the router - there isn't physical room there.

I suppose this could also be something with dynamic versus a static IP address on the server, but I followed several threads on the net for doing this (they all say to do the same things) and it just doesn't work.  As soon as I change dhcp to static and add an IP address it won't boot - gets into that "waiting for network configuration" loop and eventually freezes the system.

Very frustrating for something that should be SO easy. 

I'm just going to mark this as solved and give up on Samba on Ubuntu.

---

### Post by prodigy_ on 2013-04-28
Rather then trying unrelated registry "tweaks", you should have used the common tools for Windows/Samba diagnostics: **ping**, **telnet**, **net view**, etc.

Editing smb.conf is generally the way to go if there's an authentication issue. If there's a name resolution issue, you need a WINS server or a zeroconf solution.

P.S. Just tried to access my Samba shares from a clean Win8 installation (VM, no registry changes or anything). Works like a charm. Relevant portions of smb.conf:
```

[global]

...

local master = yes
preferred master = yes
ntlm auth = no
lanman auth = no
client ntlmv2 auth = yes

...

[Filesystem]
        comment = Root filesystem
        browsable = yes
        read only = no
        path = /
        guest ok = no
        create mask = 0644
        directory mask = 755

```

---

### Post by redmk2 on 2013-04-28
> **squakie said:**
> Okay, now I'm really confused.  I still don't see anything in Windows 8.  On the server I tried pinging my printer at 10.0.0.253 and it replies back, so the default network configuration does let me see something on the net.  From the server I can also successfully ping the Windows 8 computer by IP address.

So, after all that, using the default network configuration and the default smb.conf file (except for the workgroup name), I'm still back to where I started from - Windows 8 doesn't see the workgroup or the server.  I am really confused right now as it means things in the server must be configured right, yet Windows 8 doesn't see the server.

Why did you do that?  I only mentioned using the server edition in passing.  If you are going to wander around installing this or modifying that without guidance, we cant move forward. How would we have a coherent conversation or diagnose anything if the installed OS keeps changing?   I've been administering UNIX/Linux networks for 20+ years now, so I know what I'm doing.  I have no appetite for chasing after you.  If you don't know what you're doing, then you have to wait for answers from those folks that you ask for help from.

---

### Post by squakie on 2013-04-28
I'll go back to step 1 and wait.  Bare xubuntu, host things showing as they did before.  The things I've been doing are either straight out of Ubuntu wiki's, from forum threads that worked, or from the book Ubuntu Unleashed.  Seems like this should be extremely simple.  I suspect it's because I'm using wireless as the other threads I've read, the Ubuntu wiki's I've read and Ubuntu Unleashed, everyone is using ethx, not wlanx.  The simple bit of changing my ip address to static should have worked just fine, but for some reason it doesn't.

You'll have to excuse, I hope, my impatience.  I used to be a systems programmer and systems administrator on big iron, minis and micros.  We had Unix on a couple of those boxes.  I've done the networking bit then also.  It's just been so many dang years and the late 60's and 70's recreational activities are catching up with my memory and reasoning.  It's extremely frustrating to me when I *used* to know this, and now feel like a complete idiot every time I try even what should be extremely simple.

---

### Post by redmk2 on 2013-04-28
> **squakie said:**
> I'll go back to step 1 and wait.  Bare xubuntu, host things showing as they did before.  
Great!  I don't mean to be ugly, but when I spend time analyzing what is best for you and deciphering your posts, I get a little testy when it is all in vain.  > 

The things I've been doing are either straight out of Ubuntu wiki's, from forum threads that worked, or from the book Ubuntu Unleashed.  
I'm not so sure all that info is accurate or current.  I don't take any of that at face value.> 
Seems like this should be extremely simple.  I suspect it's because I'm using wireless as the other threads I've read, the Ubuntu wiki's I've read and Ubuntu Unleashed, everyone is using ethx, not wlanx.  The simple bit of changing my ip address to static should have worked just fine, but for some reason it doesn't.
And that is one of my questions, so I'll ask now;  WHAT DID YOU DO in your attempt to provide a static IP address for this host previously? > 

You'll have to excuse, I hope, my impatience.  
Sure thing.  We've all been there at one time or another.> 
I used to be a systems programmer and systems administrator on big iron, minis and micros.  We had Unix on a couple of those boxes.  I've done the networking bit then also.  
No JCL here.  NO Token ring either.  Only straight up TCP/IP and DNS with a touch of NETBIOS.> 
It's just been so many dang years and the late 60's and 70's recreational activities are catching up with my memory and reasoning.  It's extremely frustrating to me when I *used* to know this, and now feel like a complete idiot every time I try even what should be extremely simple.
I don't mine explaining every step we take.  Most folks are bored with that.  They just want it to work.

Confirm for me:  We have a laptop running Xubuntu with  a wireless interface that is configured dynamically via DHCP from your router.  I assume this configuration can be viewed using Network Manager.  Last night I looked at the configuration on my laptop which uses Network Manager.  I have a statically configured IP address on that host.  So I know it can be done.  

What is the IP address, subnet mask and gateway IP address for the laptop.  I assume the host name is  still *dwesamba*.  Is that correct?  Is the laptop able to connect to hosts on the internet (i.e. Google or Yahoo, etc.)  I assume so.  Post me the output of ```
ifconfig -a 
``` ...and the contents of ```
/etc/resolv.conf 
``` 
I will also need the output of ```
cat /etc/hosts
```...as I assume you have re-installed Xubuntu again. 

By way of explanation the IP address etc. and the output of the 3 commands will tell me what IP subnet, gateway, hosts file and DNS server you are using.  I know you have provided that, but I want only the raw data.  Then I will know for sure what we have and can advise you on what to do to set a static IP address.

---

### Post by squakie on 2013-04-28
The output of ifconfig -a:

```
dwesamba@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0e:7f:7a:5f:a7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88519 (88.5 KB)  TX bytes:88519 (88.5 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c3:63:73  
          inet addr:10.0.0.7  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec3:6373/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218313498 (218.3 MB)  TX bytes:7494268 (7.4 MB)

dwesamba@laptop:~$ 

```

Contents of /etc/resolv.conf.  Please note I edited the search line as it includes things specific to comcast that I don't think are supposed to be for posting in a public place.  If you need it, I can PM it to you.

```
dwesamba@laptop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search xxxxx.xx.xxxxxx.net
dwesamba@laptop:~$ 

```

An the contents of the /etc/hosts file:

```
dwesamba@laptop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Note that I changed the system name to "laptop" so the word "samba" isn't in there to mislead anything.

---

### Post by redmk2 on 2013-04-28
>  WHAT DID YOU DO in your attempt to provide a static IP address for this host previously? 

I would like to know the answer to the above.  Did you use Network Manager to view or alter the settiings?

---

### Post by squakie on 2013-04-28
Sorry - I missed that one.

On the current setup I haven't touched it.

When I attempted before I tried going through nm and editing the connection, defining the ip address (I believe to do that you have to change it from "automatic" to "manual", then defined the route, dns servers, etc., from what it showed for the active connection before finishing the changes in nm.  When I got done, the dns server ip's where in nm as well as in resolv.conf, but the "search" that is there for the comcast stuff wasn't anywhere - and I assume that's why it couldn't resolve a name to an IP.

When that didn't work, I reset the connection in nm back to it's automatic defaults, then put the information in the interfaces file.  But again, the "search" that is there for the comcast stuff wasn't anywhere - and again I assume that's why it couldn't resolve a name to an IP.  When that didn't work I reset interfaces back to it's original contents.

But again, that was before - right now I haven't touched it.  The computer name is "laptop", and all of the xubuntu updates have been applied.  I haven't installed anything - no synaptics manager, nothing.  I also reset the Windows 8 laptop so the workgroup there is WORKGROUP so when the time comes to install Samba and try it's default conf file I won't need to change anything in it just to start.

I hope that's what you wanted to know - if not, just let me know.

EDIT: I just tried something on a hunch - I edited in nm again, under ipv4, changing automatic manual, my ip address as 10.0.0.250, netmask at 255.255.255.0, and gateway to 10.0.0.1 .  I put the string that showed in resolv.conf for comcast in the "additional search domains" - didn't put anything in the dns servers.  When I disconnected from my wireless via nm, then connect again via nm, the "Information" in nm showed the updated information - the requested IP address, etc, - but opening a browser it still can't resolve the name to an IP address. I then deleted the connection via "edit" in nm, then reconnected so it's all back to the defaults again.

---

### Post by redmk2 on 2013-04-28
Is NM installed by default on Xubuntu?  I'm interested in what your experience was before.  This is so I better understand what's going on at your end,  The search name isn't that important to resolving internet based names (Google or Yahoo type things).

What other machines are there in this LAN.  Can you tell me their addresses.

I'm working up a plan here.  :D

---

### Post by squakie on 2013-04-29
NM is installed by default in xubuntu.  The other computers are 3 laptops - 1 Win XP Pro, dynamic address; 1 Windows 7, dynamic address and 1 Windows 8, with dynamic address.  I was really hoping I wouldn't need to change those laptops to static addresses. EDIT:  I should add that the 1st 2 laptops belong to my sister and my brother in-law.  While I set things up for them to be able to access the net, even completely reloaded both OS's thanks to viruses they managed to aquire, they do really prefer I not mess with theirs.  They do, however, want to be able to backup to what I'm trying to set up.  So, I wanted to get this working with my Windows 8 laptop before going back and assigning network shares to them and getting backups set up for them.  But that's down the road.......right now, since I started from scratch, I think we're concentrating on getting a static IP for my cheapy laptop with bare xubuntu, right?  Least wise, I thought it seemed like a good idea to just get the static IP working on the xubuntu box, including access to internet domains, and then moving on to what - Samba, or something simpler yet so Windows 8 can see the xuuntu box?

If you need more information on the experience I had before just let me know and I'll try to find my notes (but I think I threw them away last night - I could always try again).

EDIT:  and if helps any, the Windows 8 computer shows a NetBIOS name of DAVE-R15.

---

### Post by redmk2 on 2013-04-29
> I just tried something on a hunch - I edited in nm again, under ipv4, changing automatic manual, my ip address as 10.0.0.250, netmask at 255.255.255.0, and gateway to 10.0.0.1 . I put the string that showed in resolv.conf for comcast in the "additional search domains" - didn't put anything in the dns servers. When I disconnected from my wireless via nm, then connect again via nm, the "Information" in nm showed the updated information - the requested IP address, etc, - but opening a browser it still can't resolve the name to an IP address. I then deleted the connection via "edit" in nm, then reconnected so it's all back to the defaults again. 

Remember that when you edit a thread on this forum that there is no notification.  I just happened to see this.  I guess you just can't leave it alone.  ;-)

In this case -- no harm, no foul.  But you mess around at your own risk.  In fact you are close.  Before you do anything else a quick review is i order.  This might help you understand what all these settings mean.

**IP address** = The network address of the individual interface.  Each host that is connected to a network has at least 2 interfaces.  Your laptop has 3.

**Network mask** = The filter that determines which part of an IP address is the network address and which part is the individual host address.  The net mask 255.255.255.0 means the first 24 bits (255.255.255 (3 octets)) are the network address and the last 8 bits are the individual host.  Your the wlan0 interface is: 10.0.0 = network and the .250 is the host address.  You can represent the network like this 1.0.0.0/24.

**Gateway** = LAN side IP address of the router.  This is needed for any traffic that is not local.  It is the address that all traffic is sent to when there is no known route to the remote host.  

**Search** = The  search  list is normally determined from the local domain name; by default, it  contains only the local domain name.  In your case you have no local domain name, nor do you need one.  The search name allows you to enter only the hostname while the search name is appended to the DNS lookup.  If you created a **[COLOR="#FF0000"]local[/COLOR]** DNS domain (say squakie.net) and you didn't want to type that out each time you used ping (e.g ping laptop.squakie.net) you would add *squakie.net* to the search parameter.  Then you could just type *ping laptop  *and it would lookup *laptop.squakie.net*.  In fact I do this very thing.  I live at the beach so I created a domain named **beaches** (no .net or .com or .local).  My laptop's host name is maui.  When I ping it as *ping maui* it returns *maui.beaches*  ISP's do strange things for their own convenience, not for your benefit and not always as prescribed in the TCP/IP protocol.  You don't need a search parameter at all.
[B]
DNS server[/B] = In your case this is the DNS server that resolves **[COLOR="#2200FF"]WAN[/COLOR]** side DNS lookups only.  This is only because you have not configured any local DNS lookups.  I don't recommend you do that.  It is a needless complication.

**/etc/hosts **This is the file that is the original DNS primitive.  Originally all hostname lookups were handled by /etc/hosts files, but this quickly became unworkable for something as vast as the Internet and Web.  To this day Ubuntu (all Debian distros) first try and resolve hostname requests via /etc/hosts before trying DNS servers.  So when you ping a local host by name the OS first checks the /etc/hosts file.  This is an important concept for what we are attempting.

**Interfaces **Earlier I said that you have 3 interfaces on the laptop.  They are the loopback (lo) Ethernet (eth) and Wireless (wlan).  This means if we needed to connect to your network via a wired connection we could do that.  I'm sure the router accepts Ethernet connections.  There are advantages to Ethernet.  Speed and ease of configuration come to mind.

As you want to use Wireless we will attempt that.  It should work for now.  

Lastly there is the loopback adapter.  This is a virtual interface.  No physical device at all.  Originally used for testing the hosts IP stack.  The host can only talk to itself on this interface.  Another important concept to understand.

The first thing I want you to do is *configure the **wireless** interface*.  You are correct that that we need set these settings in the NM config window.  We should use the following parameters.

[SIZE=2]Using the ***IPv4 Settings ***tab, we configure the following:[/SIZE]
Method = Manual (this is the static setting)
Address = IP address of your choice in the network 10.0.0.0 /24 (i.e. 10.0.0.250 or some such).
Netmask = 255.255.255.0 (the 24 bit network mask)
DNS servers = 127.0.0.1 (this is DNS sever that this host uses for Internet (WAN side) DNS resolution) 
Gateway = 10.0.0.1 ( the LAN Side IP address of the router)
Search Domains =  (Leave it blank for now.  Nothing is needed here)

Check the box for available to all users.

Reboot the system.

At this point we should have TCP/IP connectivity both locally and to the Internet.  But we will not have hostname resolution to for local lookups yet.  You should be able to ping the laptop with its static IP address ```
ping -c 4 10.0.0.250
```...or whatever IP address you assign to the laptop.  Is this so?  can you ping an Internet address by DNS name?  Like this ```
ping -c 4 ubuntu.com
```

If this works I would reboot the host a couple of times to insure that the static address is consistent. 

What do you get now from these commands```
ifconfig -a

cat /etc/resolv.conf
```

Hopefully this works and we can move on to the next phase.

---

### Post by squakie on 2013-04-29
Well, it "sort of" works. Maybe this is was you were looking for.  I started by disconnecting my active connection, then editing it (HOME-93B8) to set up as suggested.  The attachment net5.png shows the information from network manager for the connection after I rebooted.

I could ping the address from the local machine:

```
PING 10.0.0.250 (10.0.0.250) 56(84) bytes of data.
64 bytes from 10.0.0.250: icmp_req=1 ttl=64 time=0.075 ms
64 bytes from 10.0.0.250: icmp_req=2 ttl=64 time=0.062 ms
64 bytes from 10.0.0.250: icmp_req=3 ttl=64 time=0.062 ms
64 bytes from 10.0.0.250: icmp_req=4 ttl=64 time=0.089 ms

--- 10.0.0.250 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.062/0.072/0.089/0.011 ms

```

However - and I don't know if you wanted this or not but it seems important - trying the same ping on my Windows 8 laptop comes back Destination host unreachable.


Trying the ping by domain name failed on the local box failed.



Results of ifconfig -a :
```
eth0      Link encap:Ethernet  HWaddr 00:0e:7f:7a:5f:a7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12103 (12.1 KB)  TX bytes:12103 (12.1 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c3:63:73  
          inet addr:10.0.0.250  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec3:6373/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3390 (3.3 KB)  TX bytes:7427 (7.4 KB)


```


These are the contents of the /etc/resolv.conf file:
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1




Perhaps some of this will make sense to you.  I've been confused since the first time I tried this - it has always shown as connect and with the static ip address, I could ping out by ip address, couldn't resolve a domain name and couldn't ping "in" - just as now.  I hope you can solve that pretty easily.

BTW - I forgot to thank you for your work so far and for the definitions - I actually did know this at one time but I haven't touched any of it since 1993.  I just can't remember what stuff is anymore.  Thanks also for your patience.

---

### Post by squakie on 2013-04-29
Oh, I should tell you I reset things in network manager again back to the defaults so I could post this back here.

---

### Post by redmk2 on 2013-04-29
> **squakie said:**
> Well, it "sort of" works. Maybe this is was you were looking for.  I started by disconnecting my active connection, then editing it (HOME-93B8) to set up as suggested.  The attachment net5.png shows the information from network manager for the connection after I rebooted.
The JPG shows everything as expected.  The connection is correctly configured.> 


I could ping the address from the local machine:

```
PING 10.0.0.250 (10.0.0.250) 56(84) bytes of data.
64 bytes from 10.0.0.250: icmp_req=1 ttl=64 time=0.075 ms
64 bytes from 10.0.0.250: icmp_req=2 ttl=64 time=0.062 ms
64 bytes from 10.0.0.250: icmp_req=3 ttl=64 time=0.062 ms
64 bytes from 10.0.0.250: icmp_req=4 ttl=64 time=0.089 ms

--- 10.0.0.250 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.062/0.072/0.089/0.011 ms

```

So far so good.  This shows that the laptop's entire IP stack is working.  The ICMP packets appear at the wlan0 interface and are responded to. > 

However - and I don't know if you wanted this or not but it seems important - trying the same ping on my Windows 8 laptop comes back Destination host unreachable.

This might be the configuration of the Windows 8 host.  What are the IP settings on the Windows 8 host?> 


Trying the ping by domain name failed on the local box failed.

 I assume you mean you could not ping *ubuntu.com*.  Is this correct?

> 



Results of ifconfig -a :
```
...

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
 ...

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c3:63:73  
          inet addr:10.0.0.250  Bcast:10.0.0.255  Mask:255.255.255.0
 ...

```...This is all good.> 


These are the contents of the /etc/resolv.conf file:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```...this also looks correct.
> 
Perhaps some of this will make sense to you.  I've been confused since the first time I tried this - it has always shown as connect and with the static ip address, I could ping out by ip address, couldn't resolve a domain name and couldn't ping "in" - just as now.  I hope you can solve that pretty easily.

So far this is as expected.  Right now we have outbound IP connectivity with no DNS name resolution.  With some more testing I'll bet that we will find that the Windows 8 machine will be the culprit to this problem, but we shall see.

> Oh, I should tell you I reset things in network manager again back to the defaults so I could post this back here. 
Are you telling me that you can't use the Windows 8 host to connect to this forum?  How will we ever progress diagnosing the problems if we have to start over each time?

We need to try pinging the following from the laptop (in the static configured state) ```
ping -c 4 91.189.94.156
```
Post the output of these 2 commands```
ping -b -c 2 10.0.0.255

arp -a 
```

What do you get when you try and ping the Windows 8 host from the laptop?

I suggest you leave the laptop in the configuration we set it to and use another host (Win8) to post you response to these questions.  But it's up to you.  If you want to be constantly be reconfiguring each time then be accurate with the settings. We don't need to add to the problem.

[COLOR="#0000FF"]**Edit:** do you know how (and what) to revert on the Win8 host registry to return to the default settings.  This is something you need to do at some time.[/COLOR]

---

### Post by squakie on 2013-04-29
As far as resetting - I just did that so I could post the screen outputs to you.  Long story short:  until I find a different place for the xubuntu clunky old laptop I can only access 1 USB port - and the wireless adapter is in it.

I did put everything back in - every screen output, etc., looks just the same.

I may have misspoken in my previous reply:  I can ping by address the xubuntu machine, but I can't actually ping out of the 10.0.0.xxx subnet.

I rebooted the Windows 8 laptop - it picked up 10.0.0.9, and I am able to ping it by address from the xubuntu laptop.  I guess that's a step in the right direction?

Ping of Ubuntu.com takes quite a while then returns with "unknown host".

I'm posting the pings, etc., first, then I'll post the details on the Windows 8 networking setup:
[LIST]
[*]ping of 91.184.94.156: 4 packets transmitted, 0 recevied, 100% packet loss, time 3023ms
[*]ping of 10.0.0.255: 2 packets transmitted, 0 received, 100% packet loss, time 1007ms
[*]
[/LIST]
arp -a returns:[LIST]
[*]?(10.0.0.1) at <adapter MAC address was here> [ether] on wlan0
[*]?(10.0.0.9) at <adapter MAC address was here> [ether] on wlan0
[*]
[/LIST]

The following is from the Windows 8 laptop Network Connection details.  I do have all the configuration details for the adapter itself written down if you need those as well:

[LIST]
[*]Connection-specific DNS Suffix <the comcast string goes here>
[*]Description  Intel(R) Centrino(R) Wireless-N 2230
[*]Physical Address <my adapters MAC address here>
[*]DHCP enabled yes
[*]IPv4 Address 10.0.0.9
[*]IPv4 Subnet Mask 255.255.255.0
[*]Lease Obtained <a date and time>
[*]Lease Expires <a date and time>
[*]IPv4 Default Gateway  10.0.0.1
[*]IPv4 DHCP server  10.0.0.1
[*]IPv4 DNS server -2 sets of address (I'm keeping private unless there is some reason to know them publicly)
[*]IPv4 WINS server - no value
[*]NetBIOS over tcp/ip enabled  YES
[*]Then the information for IPv6, but since I'm using IPv4 I don't see a need to type it all in.
[*]
[/LIST]

I hope that's what you needed.  I also have a question regarding not being able to ping out to the internet:  I seem to remember, and I'm probably wrong, that the .0 address - in this case 10.0.0.0 - was used for internet traffic - do we need to specify it somewhere?  I ask because the intranet traffic (10.0.0.xxx subnet?) seems to be working tcp/ip wise, but nothing to the internet is working.

---

### Post by squakie on 2013-04-29
I just decided to try something else that I didn't know if it mattered at this point or not.  On the Windows 8 laptop I tried pinging the xubuntu laptop (10.0.0.250) and after a short time I got a host unreachable message.  From that Windows 8 laptop I could still ping my wireless printer and I could ping sites on the web.  So, I can ping the Windows 8 laptop from the xubuntu laptop, but I can't ping the xubuntu laptop from the Windows laptop.  Don't know if that matters at this point or not.

---

### Post by squakie on 2013-04-29
I thought I'd also post back the registry changes that were merged in on the Windows 8 laptop.  I don't see how they could be making any difference but what the heck:

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanManWorkstation\Parameters]

&#8220;DNSNameResolutionRequired&#8221;=dword:00000000

&#8220;DomainCompatibilityMode&#8221;=dword:00000001

Supposedly this to give Windows 8 backwards compatibility to older domains.  This was one of the things returned in my many searches of the internet for Windows 8 not seeing a Samba share.

---

### Post by redmk2 on 2013-04-30
> **squakie said:**
> As far as resetting - I just did that so I could post the screen outputs to you.  Long story short:  until I find a different place for the xubuntu clunky old laptop I can only access 1 USB port - and the wireless adapter is in it.

I did put everything back in - every screen output, etc., looks just the same.
I understand.> 
I may have misspoken in my previous reply:  I can ping by address the xubuntu machine, but I can't actually ping out of the 10.0.0.xxx subnet.

I rebooted the Windows 8 laptop - it picked up 10.0.0.9, and I am able to ping it by address from the xubuntu laptop.  I guess that's a step in the right direction?

Ping of Ubuntu.com takes quite a while then returns with "unknown host".

I'm posting the pings, etc., first, then I'll post the details on the Windows 8 networking setup:
[LIST]
[*]ping of 91.184.94.156: 4 packets transmitted, 0 recevied, 100% packet loss, time 3023ms
[*]ping of 10.0.0.255: 2 packets transmitted, 0 received, 100% packet loss, time 1007ms
[*]
[/LIST]
arp -a returns:[LIST]
[*]?(10.0.0.1) at <adapter MAC address was here> [ether] on wlan0
[*]?(10.0.0.9) at <adapter MAC address was here> [ether] on wlan0
[*]
[/LIST]

The following is from the Windows 8 laptop Network Connection details.  I do have all the configuration details for the adapter itself written down if you need those as well:

[LIST]
[*]Connection-specific DNS Suffix <the comcast string goes here>
[*]Description  Intel(R) Centrino(R) Wireless-N 2230
[*]Physical Address <my adapters MAC address here>
[*]DHCP enabled yes
[*]IPv4 Address 10.0.0.9
[*]IPv4 Subnet Mask 255.255.255.0
[*]Lease Obtained <a date and time>
[*]Lease Expires <a date and time>
[*]IPv4 Default Gateway  10.0.0.1
[*]IPv4 DHCP server  10.0.0.1
[*]IPv4 DNS server -2 sets of address (I'm keeping private unless there is some reason to know them publicly)
[*]IPv4 WINS server - no value
[*]NetBIOS over tcp/ip enabled  YES
[*]Then the information for IPv6, but since I'm using IPv4 I don't see a need to type it all in.
[*]
[/LIST]

I hope that's what you needed...

Sort of what I needed.  Not always in the same order I asked the question or even from the current last post.  :-(    This makes it somewhat difficult for me to try something and then get a direct response.  If I ask something in one post, I expect you'd answer it in the next reply.  I need you to answer all of the questions I ask in pretty much the order I asked them.  I wouldn't ask them If I didn't need the info.

I think we need to set some more ground rules.  If I ask you for the output of some command please post the **[B]*entire output***[/B] as it appears on the screen.  The output is best for me if you post it using the ```
 blocks that the forum editor provides.  Please don't edit the output.  I don't necessarily explain all that I'm looking for in the output I request.  You might delete the very part I'm looking for.  When I am diagnosing the problem I make an hypothesis for a result from a command  and look at the results to confirm my thoughts.  Sometimes an answer of failure is *almost* as important as getting to success.   

Your reluctance to show me the mac addresses and DNS settings are really misguided security.  The MAC addresses are only relevant to your LAN.  The MAC address/IP pair is not even seen outside of your LAN. as everything is behind NAT provided your router.  You have NO PUBLIC FACING IP addresses that you control.  The DNS server settings that you use are for Internet facing DNS servers I assume.  DNS servers are by nature public services.  You are just one of many users for any particular Comcast DNS server.  All that being said If you want to PM me with what you feel is sensitive data then do that rather than not supply it at all.
>  I also have a question regarding not being able to ping out to the internet:  I seem to remember, and I'm probably wrong, that the .0 address - in this case 10.0.0.0 - was used for internet traffic - do we need to specify it somewhere?  I ask because the intranet traffic (10.0.0.xxx subnet?) seems to be working tcp/ip wise, but nothing to the internet is working.

The IP address 10.0.0.0 is **[COLOR="#0000FF"]not a valid host address[/COLOR]** as stated in the protocol.  It is the **[COLOR="#008000"]Network ID[/COLOR]** as defined by the netmask 255.255.255.0.  In all IP networks, the Network ID and Broadcast address should *never be assigned to a host in the network*.  We don't need to state the network ID.  All that is needed is the Netmask and the Broadcast address to determine the Network ID
> I just decided to try something else that I didn't know if it mattered at this point or not. On the Windows 8 laptop I tried pinging the xubuntu laptop (10.0.0.250) and after a short time I got a host unreachable message. From that Windows 8 laptop I could still ping my wireless printer and I could ping sites on the web. So, I can ping the Windows 8 laptop from the xubuntu laptop, but I can't ping the xubuntu laptop from the Windows laptop. Don't know if that matters at this point or not.
This sounds like a firewall problem.  **Do you use host based firewalls? ** The only firewall I have is at the edge of the network (in the router).  There are no firewalls between my LAN hosts.  Think of it like your house.  If you have a lock on the front and back door, you don't need a lock on the interior doors to keep the bad guys out.  I would turn off any firewalls you have configured in the laptop and Win8  
> I thought I'd also post back the registry changes that were merged in on the Windows 8 laptop. I don't see how they could be making any difference but what the heck:

[CODE][HKEY_LOCAL_MACHINE\System\CurrentControlSet\Servic es\LanManWorkstation\Parameters]

&#8220;DNSNameResolutionRequired&#8221;=dword:00000000

&#8220;DomainCompatibilityMode&#8221;=dword:00000001
```

Supposedly this to give Windows 8 backwards compatibility to older domains. This was one of the things returned in my many searches of the internet for Windows 8 not seeing a Samba share. I don't speak MS so this is all Greek to me.  I do know that no registry hacks are needed for Samba simple LAN sharing.  You can do as you wish here.  However, I don't diagnose Windows OS based sharing problems past the basic user settings.  Right now we are just trying to get TCP/IP connectivity sorted.

What we have now is a situation where you can't do 2 things with TCP/IP connectivity.  No Internet (default gateway) and no Ubuntu response to ping requests from Win8.  Both of these sound like a firewall configuration problem or a Router MAC address for the laptop problem.  In fact, as you have stated, the *laptop TCP/IP *works fine on the local network.  Can you ping the router from the laptop.  Post the entire output from this```
ping 10.0.0.1
```

PM me this Comcast info: "IPv4 DNS server -2 sets of address (I'm keeping private unless there is some reason to know them publicly)"

---

### Post by squakie on 2013-04-30
I just spent the last 3 hours trying to get screen prints of everything you asked for so you can see I didn't omit anything pertinent, though you obviously doubt that.  I've also done my best to answer/reply with everything you've asked for.  If Windows 8 is going to be the problem, and you don't do Windows, this is all rather pointless.  I'm not disabling firewalls - I've had several notifications from outside my local net attempting to make inbound connections from places that look quite suspicious.  I'm not providing some of the DNS id's and the Comcast search prefix since those things, as far as I know, are not public knowledge.  I'm not providing local MAC addresses as I have been advised against that, and others have advised others against that, on these forums.

So, we're at an impasse - you apparently think I'm not providing information that is pertinent to the problem.  A search of the internet finds  "a lot" (I can't count past 10) people having problems trying to "tie" Windows 8 and Linux together - be it by Samba shares or other - such as the pinging of the pertinent IP addresses.

You don't do Windows - if it's going to be a Windows problem then none of this is of use to me.

I appreciate your attempts at help, I really do.  But this should be EASY,  *REAL* easy.  Almost everything you have put here are things I tried before I posted.  I don't need difficult at this point in my life, and sure don't need to be left with the networking working but still having no access to/from Windows 8.

I'm just going to save my pennies, buy a cheap 64-bit box so I can put Windows Home Server on it - problem solved.

---

### Post by redmk2 on 2013-04-30
> **squakie said:**
> I just spent the last 3 hours trying to get screen prints of everything you asked for so you can see I didn't omit anything pertinent, though you obviously doubt that.  I've also done my best to answer/reply with everything you've asked for.  If Windows 8 is going to be the problem, and you don't do Windows, this is all rather pointless.  I'm not disabling firewalls - I've had several notifications from outside my local net attempting to make inbound connections from places that look quite suspicious.  I'm not providing some of the DNS id's and the Comcast search prefix since those things, as far as I know, are not public knowledge.  I'm not providing local MAC addresses as I have been advised against that, and others have advised others against that, on these forums.

So, we're at an impasse - you apparently think I'm not providing information that is pertinent to the problem.  A search of the internet finds  "a lot" (I can't count past 10) people having problems trying to "tie" Windows 8 and Linux together - be it by Samba shares or other - such as the pinging of the pertinent IP addresses.

You don't do Windows - if it's going to be a Windows problem then none of this is of use to me.

I appreciate your attempts at help, I really do.  But this should be EASY,  *REAL* easy.  Almost everything you have put here are things I tried before I posted.  I don't need difficult at this point in my life, and sure don't need to be left with the networking working but still having no access to/from Windows 8.

I'm just going to save my pennies, buy a cheap 64-bit box so I can put Windows Home Server on it - problem solved.

Fine by me.  I don't administer any Windows products but that doesn't mean I don't know the SMB/CIFS protocol and have Windows 7 laptops as part of my working network.  As I said before, the default registry settings are fine.  If you are paranoid about security then nothing I can say is of any value.  This effort has been for you not me.  My network has multiple Samba servers interacting with Windows, Apple and Linux OS's.  So I'm happy happy with my network.

---

### Post by Zill on 2013-04-30
redmk2:  You have obviously put considerable effort into your replies to this thread and I must say that your questions seemed perfectly reasonable to me.  Unfortunately, the OP seems to have his own ideas which will prohibit resolution of the problem.  Sometimes we have to accept that some users should just stick to Windows. :-(

---

### Post by steelered on 2013-04-30
ACK! I was following along to get to your resolution redmk2. However, my time is limited to an hour or two in the evenings.
If that strings this out too long for you I understand. Ugh, jury duty in 2hrs. Cheers

EDIT: I can't access shares from 8. I also can't access my media files on 8 from any other devices (xbox360 or BR players), since the samba and openSSH install on the lappy. I fiddled with it and got a message in win8 or ubuntu that system or network time was out of sync and did i want to fix it. I said yes and it worked until a server reboot..the lappy.


hostname
TurleyClan


cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       TurleyClan.gateway.2wire.net    TurleyClan


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters




resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.254


ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:1c:23:b2:f7:f1
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feb2:f7f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30496 errors:0 dropped:484 overruns:0 frame:0
          TX packets:5226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1344 txqueuelen:1000
          RX bytes:8597649 (8.5 MB)  TX bytes:489256 (489.2 KB)
          Interrupt:10


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)






Gateway/Router (ip static - created the ip from within the router web utility)
PING -c 4 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=255 time=2.62 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=255 time=0.763 ms
64 bytes from 192.168.1.254: icmp_req=3 ttl=255 time=0.740 ms
64 bytes from 192.168.1.254: icmp_req=4 ttl=255 time=0.746 ms


Desktop(win8pro ip static - created the ip from within the router web utility)
 ping -c 4 91.189.94.156
PING 91.189.94.156 (91.189.94.156) 56(84) bytes of data.
64 bytes from 91.189.94.156: icmp_req=1 ttl=42 time=165 ms
64 bytes from 91.189.94.156: icmp_req=2 ttl=42 time=162 ms
64 bytes from 91.189.94.156: icmp_req=3 ttl=42 time=162 ms
64 bytes from 91.189.94.156: icmp_req=4 ttl=42 time=162 ms






Samba v.? on a Dell vostro1500 (ip static - altered by editing eth0 and it stuck in the router)
192.168.1.128

---

### Post by redmk2 on 2013-04-30
> **Zill said:**
> redmk2:  You have obviously put considerable effort into your replies to this thread and I must say that your questions seemed perfectly reasonable to me.  Unfortunately, the OP seems to have his own ideas which will prohibit resolution of the problem.  Sometimes we have to accept that some users should just stick to Windows. :-(

@ Zill -- I agree.  But I had to try even though I saw the train wreck in front of me.  :D

@ steelered -- I'll look at the data later in the day and give you my ideas.

---

### Post by steelered on 2013-04-30
Thank You [COLOR=#000000]redmk2![/COLOR]

---

### Post by redmk2 on 2013-04-30
> **steelered said:**
> ACK! I was following along to get to your resolution redmk2. However, my time is limited to an hour or two in the evenings.  If that strings this out too long for you I understand. Ugh, jury duty in 2hrs. Cheers
Not at all.  We can take as much time as we need.  I'm about due for jury duty myself.> 

EDIT: I can't access shares from 8. I also can't access my media files on 8 from any other devies (xbox360 or BR players), since the samba and openSSH install on the lappy. I fiddled with it and got a message in win8 or ubuntu that system or network time was out of sync and did i want to fix it. I said yes and it worked until a server reboot..the lappy.
Checking the time difference is a security check for SSH for sure.  The concept is the network should all be using the same network server.  Therefore we might have an intruder if the times are not the same for both hosts.  It has to be off by some amount in minutes, not just a few seconds.  What was the time differential?  You might want to set up network time protocol (NTP).  That way all the hosts on you LAN will have the same time.

The settings below are for TCP/IP and DNS.  A couple of pointers.  It's easier to read and comment on if you wrap the data in ```
 blocks.  In the advanced editor used on this forum, the **[SIZE=3]#[/SIZE]** icon at the top to the right on the middle row of icons will wrap the output in these [code] blocks.  I will do this for this post.  See my comments in red.> 

[CODE]
hostname 
  TurleyClan  [COLOR="#FF0000"]<-- this is good.  Never more than 15 characters long[/COLOR]

```

```
cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       TurleyClan.gateway.2wire.net    TurleyClan  [COLOR="#FF0000"]<--  This should be mapped to the real interface[/COLOR] 

```
As I said before:   This is a virtual interface. No physical device at all. Originally used for testing the hosts IP stack. The host can only talk to itself on this interface.  This should be mapped to your LAN network IP address (e.g 192.168.1.128 I believe).  There is an interesting story as to why Debian (and therefore Ubuntu) configure the loopback address with the hostname. > 

```
resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.254 [COLOR="#FF0000"]<-- How did you configure this?  Via NM or ...[/COLOR] 
```


ifconfig -a


```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:b2:f7:f1
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feb2:f7f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30496 errors:0 dropped:484 overruns:0 frame:0
          TX packets:5226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1344 txqueuelen:1000
          RX bytes:8597649 (8.5 MB)  TX bytes:489256 (489.2 KB)
          Interrupt:10


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)

[COLOR="#FF0000"]It's all good here[/COLOR]


```


Gateway/Router (ip static - created the ip from within the router web utility)
```
PING -c 4 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=255 time=2.62 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=255 time=0.763 ms
64 bytes from 192.168.1.254: icmp_req=3 ttl=255 time=0.740 ms
64 bytes from 192.168.1.254: icmp_req=4 ttl=255 time=0.746 ms
[COLOR="#FF0000"]It's all good here too.[/COLOR] 
```

Desktop(win8pro ip static - created the ip from within the router web utility)
```
 ping -c 4 91.189.94.156
PING 91.189.94.156 (91.189.94.156) 56(84) bytes of data.
64 bytes from 91.189.94.156: icmp_req=1 ttl=42 time=165 ms
64 bytes from 91.189.94.156: icmp_req=2 ttl=42 time=162 ms
64 bytes from 91.189.94.156: icmp_req=3 ttl=42 time=162 ms
64 bytes from 91.189.94.156: icmp_req=4 ttl=42 time=162 ms [COLOR="#FF0000"]<-- This can't be the Win* IP address.  
What is the IP address of the Win8 host?[/COLOR] 

```

Samba v.? on a Dell vostro1500 (ip static - altered by editing eth0 and it stuck in the router)
192.168.1.128
You can see the version number of Samba with this command```
smbd -V
```...What version of Samba does it show?

All of this is preliminary to configuring Samba.  It's just confirming the TCP/IP networking and DNS name services.  Before we go any further you need to have consistent network time across all hosts in your network.  In the mean time we can test some things with the following:

Post the output of this command from the host TurleyClan ```
ping -c4 TurkeyClan
[COLOR="#FF0000"]# TurleyClan pinging itself[/COLOR] 
```
Post the output of TurleyClan pinging Win8 (by hostname)

Post the output from this command from the Win8 host ```
ping TurkeyClan
[COLOR="#FF0000"]Win8 pinging TurkeyClan[/COLOR]
```

Maybe it's best for you to list the IP address/hostname (OS type) so I can ID them when posting to you.

At the top of this you said this all worked it you reset the time.  Is that so?  Do you really need anymore help?  I'm willing, but I'm not really sure what more you need.  maybe it would help for you to restate your problem.  I know you were in a hurry this morning.

-Red

---

### Post by squakie on 2013-05-01
If someone would like to point where I DIDN'T provide the information that was asked for please point it out.  I answered everything as best I could.  I refuse to turn off a firewall because the first time I take my Windows 8 laptop away from home to a public network guess what?  You may not believe it, but I HAVE had warnings on my Windows 8 laptop from ZoneAlarm informing me that someone was attempting inbound connections.  And, just for kicks, I turned off the firewall and tested - guess what?  It STILL didn't work.  You may think me a fool, but I'm not.  You may think me dumb, but I'm not.  I don't have time to set one lousy setting and not see results.  Samba shares are simple to set up and normally work.  Networking is easy to set up.  I have followed all kinds of tutorials and the Ubuntu Unleased book, and they have all shown the same things.  I extremely doubt that the book is wrong.  With Windows 8 there are problems - look on the net or no further than the post just behind here.

But whatever, the thing is this thread is done.  Any of you with additional problems please open your own threads.

---

### Post by lisati on 2013-05-01
Closed by request of OP

---

