---
title: "Ubuntu 12.04 NFS Server Help"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by ncwalker2010 on 2013-07-04
Need some NFS Server help.  I am running Ubuntu 12.04

The goal is I have two directories off of /home and they are:

/home/homeserver/LocalRO that I wish to share as read only.
/home/homeserver/NetFree that I wish to share as read-write.

The computer is a desktop with a router connected to a cable modem.  And I wish to share this over the home WiFi network with two Linux laptops.  WPA2 Security is being used.

I am trying to follow this Wiki:

[https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Server](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Server)

And getting stuck.

I have nfs-kernel-server installed, dpkg -s on it yields (abbreviated):

```
Package: nfs-kernel-server
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 529
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: nfs-utils
Version: 1:1.2.5-3ubuntu3.1
Replaces: knfs, nfs-server
Provides: knfs, nfs-server
```

If I run an ls -l on a root directory /export I get:

```
drwxr-xr-x 7 root root 4096 Jul  4 18:58 LocalRO
drwsrwsrwx 4 root root 4096 Jul  4 16:34 NetFree
```

wiki reads like I am going to mount (connect) these folders in /export to the actual folders.  Makes sense.  Like a logical mapping.

Question 1:  Should the owners in /export be nobody:nogroup ? Or root:root?

Then I editted the file /etc/exports and added the following lines:

```
/export/LocalRO 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
/export/NetFree 192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)

```
I am at a total loss as to WHY the IPs should be 192.168.0.0/255.255.255.0 other than that is an inclusive statement for all IP addresses.

Question 2:  SHOULD they be those IPs?  I really no little about domains, IPs etc.  If I run ifconfig on the server computer I get:

```
eth0      Link encap:Ethernet  HWaddr f8:0f:41:05:c8:54  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::fa0f:41ff:fe05:c854/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1508914 (1.5 MB)  TX bytes:344384 (344.3 KB)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67667 (67.6 KB)  TX bytes:67667 (67.6 KB)
```

But I don't know what it means.

Question 2:  Is this safe?  If I understand things right, the eth0 IP numbers are coming from my router which is secure through the WPA2 key.  Is this right?

Then I added the following to /etc/fstab:

```
/home/homeserver/NetFree    /export/NetFree   none    bind  0  0
/home/homeserver/LocalRO    /export/LocalRO   none    bind  0  0
```

Because the Wiki said that would automatically mount them when I reboot.

Now, the Wiki talked about 3 more configuration files:

File 1 - /etc/default/nfs-kernel-server setting NEED_SVCGSSD=no, but no is default so I didn't change that.

File 2 - /etc/default/nfs-common setting NEED_IDMAPD=yes, but it says only for Ubuntu 11.10 and earlier.  I'm on 12.04 so I left that alone too.

File 3 - /etc/idmapd.conf should have

```
[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
```

and it does.  BUT ... the Wiki said **"In order for the ID names to be automatically mapped, both the client and server require the /etc/idmapd.conf file to have the same contents with the correct domain names."**

Question 3:  What does THAT mean?  How do I determine/set my domain name?  What should I set it to?

I didn't do anything with "Portmap Lockdown" and I don't know if I am using LDAP.

But, if I then issue the mount command like this:

```
mount -t nfs -o proto=tcp,port=2049 nfs-server:/ /mnt

```
Or like this:

```
mount -t nfs -o proto=tcp,port=2049 nfs-server:/NetFree /home/homeserver/NetFree

```
Or by rebooting (because I think I have fstab right)....

I should be able to check and see I have them mounted right with:

```
df -h

```
and I get zip.

Or are they mounted and I don't know it?

Thanks.

---

### Post by ncwalker2010 on 2013-07-04
Oh.  The wiki said I needed to export the shares by issuing

```

sudo exportfs -ra
```

And then restart the server.  For that I issued and got:

```
$ sudo service nfs-kernel-server restart
 * Stopping NFS kernel daemon                                           [ OK ] 
 * Unexporting directories for NFS kernel daemon...                     [ OK ] 
 * Exporting directories for NFS kernel daemon...                       [ OK ] 
 * Starting NFS kernel daemon                                           [ OK ] 

```

Then the mount command gives me:

```
$ sudo mount -t nfs -o proto=tcp,port=2049 nfs-server:/NetFree /home/homeserver/NetFree

mount.nfs: Failed to resolve server nfs-server: No address associated with hostname

```

---

### Post by SeijiSensei on 2013-07-05
> Failed to resolve server nfs-server

The name nfs-server does not point to an IP address.  Either replace it with the IP in the mount command, or edit /etc/hosts on each client machine to create an entry for the server like this:

```
192.168.1.100 nfs-server
```

NFS is a pretty complicated service for someone with no knowledge of how IP works.

The entries in /etc/exports are wrong as well.  If your network uses 192.168.1.0-255, then you need to have 

```
/export/LocalRO 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check)
```

The "netmask" 255.255.255.0 means that the associated network address spans all 256 values for the last "octet" in the address.  Your example with 192.168.0.0/255.255.255.0 would apply to addresses between 192.168.0.0 and 192.168.0.255.

Then there is the issue of permissions.  I recommend that both the server and the clients have the same /etc/passwd file, or at a minimum the same list of local users, ones whose user IDs start at 1000.   NFS enforces permissions the same way your client machine does.  So if user "joe" owns /export/LocalRO, user "jill" can only see those files if either the share has world-readable permissions, or jill and joe belong to a user group with those permissions.  If all this has flown over your head, start [here]("https://help.ubuntu.com/community/FilePermissions").

---

### Post by ncwalker2010 on 2013-07-05
Well, I know a lot more about IP now after some reading.

The gist is in my current system, I am automatically getting IP addresses from my router that only have validity inside the router's network.  And it's converting that to "channels" when multiple devices are talking to the net.  And from my understanding, if I ifconfig the server (kitchen) computer and get an IP address, it may not be the same if I power it down and power it back up.  So I don't understand how putting the IP address in the NFS config files will help unless I go to static IPs.

So I am leaning towards setting up my own domain (and reading about it) and going to static IPs.  My concern for that is while SOME of my household devices need to see this server, others (IPods, XBox, Nook, etc) do not.  And I have to beleive from the interface alone that dealing with static IPs on the Nook is a pain, if it is even possible.  (More research).  Further, if I make the Nook a static IP in my house, what happens if I go to Starbucks?  Do I have to go and switch it back?

A buddy of mine says it is possible in the router to make some of it static and some of it dynamic.  I am trying to entice him over for a Saturday with a six pack of craft beer to diddle with my network with me.

But my head is at: make an internal domain and static IPs for the computers, leave everything else alone.  And hey, worst case, another wireless router is cheap, relatively.

All this to get away from Samba.  Which I find slow and hard to understand.  (Hard to understand because it seems to work only when it wants to, I've found it inconsistent.)

But why Samba in the first place?  Well, some of the PCs that connect in my home are Windows.  :-(  Which leads to the question - if I make my own internal domain, am I going to be able to share files via an FTP and Internet Explorer to the Windows boxes?  I've failed miserably with Samba4 and just need something to work consistently.  Right now, that's flash drives and Sneakernet.  Which works, but I want sexy too....

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> Well, I know a lot more about IP now after some reading.

The gist is in my current system, I am automatically getting IP addresses from my router that only have validity inside the router's network.  And it's converting that to "channels" when multiple devices are talking to the net.  And from my understanding, if I ifconfig the server (kitchen) computer and get an IP address, it may not be the same if I power it down and power it back up.  So I don't understand how putting the IP address in the NFS config files will help unless I go to static IPs.

So I am leaning towards setting up my own domain (and reading about it) and going to static IPs.  My concern for that is while SOME of my household devices need to see this server, others (IPods, XBox, Nook, etc) do not.  And I have to beleive from the interface alone that dealing with static IPs on the Nook is a pain, if it is even possible.  (More research).  Further, if I make the Nook a static IP in my house, what happens if I go to Starbucks?  Do I have to go and switch it back?

A buddy of mine says it is possible in the router to make some of it static and some of it dynamic.  I am trying to entice him over for a Saturday with a six pack of craft beer to diddle with my network with me.

But my head is at: make an internal domain and static IPs for the computers, leave everything else alone.  And hey, worst case, another wireless router is cheap, relatively.

All this to get away from Samba.  Which I find slow and hard to understand.  (Hard to understand because it seems to work only when it wants to, I've found it inconsistent.)

But why Samba in the first place?  Well, some of the PCs that connect in my home are Windows.  :-(  Which leads to the question - if I make my own internal domain, am I going to be able to share files via an FTP and Internet Explorer to the Windows boxes?  I've failed miserably with Samba4 and just need something to work consistently.  Right now, that's flash drives and Sneakernet.  Which works, but I want sexy too....

You only need to set the server (NFS or SMB) to fixed addresses in a specific network. A network is nothing more than a defined range of IP addresses that can communicate with each other.  If the destination (e.g. the Internet) then the router passes the traffic to the public facing network upstream (your ISP).  All of this is to say that you already have a network setup with the router.  The entire IP network you are using should have some addresses that you can assign manually (not part of the pool).  There is a pool (a subset) of IP addresses that the router uses to hand out automatically.    You can set fixed IP addresses in this network  by reservation in the router or by a static configuration on the individual computer.  Either way will work for your situation.

You do not need to change your network or create a domain to achieve connectivity with all of your machines.  You don't need a domain to use an NFS or a Samba server.  Your existing automatic IP addressed (via DHCP) items like the nook do not need to be changed at all.

The NFS protocol will not work with windows machines by default and it is difficult to make it work.  Samba is what you want to use if you have windows computers in the network.  You should not have used Samba4.  You should use Samba3 for your network needs.  It is much simpler to set up.

[COLOR="#0000FF"]Edit:  If you provide the output of the following command I will tell you what your IP network is[/COLOR]```
ifconfig | grep inet
```

---

### Post by ncwalker2010 on 2013-07-05
redmk2 - You are echoing what my friend is telling me.  I have a router and a home network with WPA2 security.  He says there is a range of IP addresses that are handed out by my router from a DHCP service.  I can limit this range to a subset of the total.  Then I have a range of automatic ones (as long as there are more than devices) and some reserved to be static, that I can then use for the machines that I want to be static.  That sounds a lot better, by passing all the redirecting and mess to set up a domain (which I probably would not want to use).

Yes.  Samba3 works better.  But it still (for some reason) seems to work when it wants to.  It took forever to strip Samba4 back off, I have a pretty clean system at this point.  My Samba3 worked, but slow.  Which is why I am wanting to tackle NFS to see if it is faster.  It doesn't really matter, I am using this to learn.  And glad I don't make a living at it, because I'm slow at it.

Would I set the dynamic IP range on the router by logging in to it?  Or on the server (kitchen) computer?

---

### Post by dannyboy79 on 2013-07-05
first we should maybe understand your needs, and then we can go from there on whether to go with NFS or SAMBA etc etc.

So you currently have an Ubuntu 12.04 machine which has 2 folders that you want to be able to access from anywhere within your LAN correct?

Your router most likely has an area within it's settings where you can set certain MAC addresses to always get the same IP address. If you want your Ubuntu machine to always get an IP of 192.168.1.20 then set that up. BUT then also within the DHCP server section, change it's range from ALL IP's to only lease out 192.168.1.1 thru 192.168.1.19 so you never have a confliction. This is how I handle my home.

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> redmk2 - You are echoing what my friend is telling me.  I have a router and a home network with WPA2 security.  He says there is a range of IP addresses that are handed out by my router from a DHCP service.  I can limit this range to a subset of the total.  Then I have a range of automatic ones (as long as there are more than devices) and some reserved to be static, that I can then use for the machines that I want to be static.  That sounds a lot better, by passing all the redirecting and mess to set up a domain (which I probably would not want to use).

Yes.  Samba3 works better.  But it still (for some reason) seems to work when it wants to.  

It took forever to strip Samba4 back off, I have a pretty clean system at this point.  My Samba3 worked, but slow.  Which is why I am wanting to tackle NFS to see if it is faster.  It doesn't really matter, I am using this to learn.  And glad I don't make a living at it, because I'm slow at it.

Samba should be as fast as NFS.  The both use "userland virtual file systems" (external to the Linux kernel).
> 

Would I set the dynamic IP range on the router by logging in to it?  Or on the server (kitchen) computer?
You set the DHCP pool (range of IP addresses) in the router.  The router has the DHCP server in the device.

[COLOR="#0000FF"]Edit:  The router has an IP address that is in your network too.  Make sure you account for it when setting up the pool.  That number should NOT be in the pool.[/COLOR]

---

### Post by ncwalker2010 on 2013-07-05
Yes.  My needs are basically this ....

I have a PC in the kitchen that's (almost) always on.  Family members have some PCs too, and the goal is to have two directories.  One with read only files in it for pictures, things they need access to (files of different types) that I do NOT want them erroneously changing.  And also a directory they can create folders in and write to.  Thus they can share work, back up their systems, etc.

I then back up these two server directories onto a remote hard drive.

I've just about got everyone converted to Linux, but there are a few Windoze users too.  (which is why I originally used Samba).

That's basically it.  I DO have an entertainment center that is wireless for NetFlix access.  AND it's open source.  Would be cool if THAT could browse to this "server" as well.  But that would require some programming for that device.  (Maybe later).

So at the end of the day, that's it.  A couple of directories on the HD of the kitchen computer that other computers need to access.  Sounds like I reserve a few static IPs on my router and diddle with the configuration files and I'm there.

If NFS isn't any faster than Samba, maybe I better just start posting my Samba problems.  I don't know.  I'll get it working, then a few days later, it doesn't work anymore.  And I don't know why.

Last question - this isn't frequent access at all.  It's not like anyone works off these directories often.  It's an occasional movement of files.  Truth be told, flashdrives and sneakernet isn't THAT much of a hassle.  In reading about NFS, it's looking like automatically mounting these drives on the clients saps network resources.  I've also read up on FileZilla.  Given the needs, maybe I just need to spawn off a FileZilla service on the kitchen computer and do it THAT way....

The most interesting thing of all of this is learning about how many options there actually are out there.  :-)

---

### Post by ncwalker2010 on 2013-07-05
And let me add, there's lots of information here written by "you guys."  "You guys" being those who deal with this stuff on a regular basis.

To "us guys" who do NOT deal with this on a regular basis, it's greek and a little scary.  I haven't found one walkthrough yet written that is what I would call comprehensive for a new person.  So I can see why Linux is a turn off to the regular person.  You almost need a champion to help you the first year you use it.  I have to beleive a home network similar to what I want is something that MOST people would want.  And what would be cool would be a walkthrough on setting that up.  That would cover the enchilada....  What you do with your router.  How you allow people access to folders on the "server."  What folders you should back up.  What you do to protect your system from the outside.  But clear and concise.  The stuff I've found is good, but the background learning curve stuff isn't all connected well.  THEN you get a couple of people who aren't network type guys to test the walkthrough.

I can tell you this, I switched to Linux a few years ago because Windows seemed to CONSTANTLY require me to repair it.  The kids would browse the net, play their flash games, and inadvertently click things and "pollute the system" is the best way I can describe it.  If I made a Windows admin account and gave the kids the limited accounts, that sort of helped.  But then half the games they wanted to play couldn't connect to servers, or write their save files.  Like they weren't REALLY Windoze compliant.

So about every 3rd or 4th Saturday I spent cleaning up the old Windoze machine.  Hey, they can do without the games a bit, but what happened was they'd get it all hosed up THEN they couldn't do their homework.  A buddy said "try Linux...."  I never looked back.  Normally, I have to do some serious eat up my weekend admin time MAYBE about every 9 months.  VAST improvement over Windoze.

And NEW Windoze is worse.  I don't find it intuitive AT ALL where all these configuration settings go.

My beef with Linux really isn't all the command line stuff.  The beef is all the hunting around on the net you have to do.  I find I spend MOST of the time reading these guides and walkthroughs, having to learn the vocabulary, and the actual WORK part of it is like 15 minutes.  That's OK for me, I find it interesting.  None of my neighbors would.  They just bitch about Windoze.

Somebody puts a clear guide out there about how to set up a stable home network in Linux that a "normal" person could understand that was easy to follow, there'd be a LOT less Windoze users out there ...

THEN you'd want to revisit it with every distro release and rewrite it.  Heck.  It should just "unpack" and be in documents when the distribution is released.  It's the pointer trail that's a pain.  "This worked in Natty, but not needed in Lucid ..."  Or pieces of it here and there.

The home network is what people want that is lacking.  The rest of the stuff - that's handled pretty well through the Software center, which works like getting apps for a phone.

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> 
Yes. My needs are basically this ....

I have a PC in the kitchen that's (almost) always on. Family members have some PCs too, and the goal is to have two directories. One with read only files in it for pictures, things they need access to (files of different types) that I do NOT want them erroneously changing. And also a directory they can create folders in and write to. Thus they can share work, back up their systems, etc.

Easily done with both the basic Linux file system ownership and permissions.  Then Samba can provide the appropriate access.  Security has 2 parts;  authentication and access.> 

I then back up these two server directories onto a remote hard drive.

Again, very simple or if you like, not so simple.  The remote hard drive is what exactly?
> 
I've just about got everyone converted to Linux, but there are a few Windoze users too. (which is why I originally used Samba).

That's basically it. I DO have an entertainment center that is wireless for NetFlix access. AND it's open source. Would be cool if THAT could browse to this "server" as well. But that would require some programming for that device. (Maybe later).

So at the end of the day, that's it. A couple of directories on the HD of the kitchen computer that other computers need to access. Sounds like I reserve a few static IPs on my router and diddle with the configuration files and I'm there.

It sure sounds that way.  But the devil is in the details.> 

If NFS isn't any faster than Samba, maybe I better just start posting my Samba problems. I don't know. I'll get it working, then a few days later, it doesn't work anymore. And I don't know why.

We can handle the Samba problems right here in this thread.  You are the the OP so the direction we go in is entirely yours.  :D> 

Last question - this isn't frequent access at all. It's not like anyone works off these directories often. It's an occasional movement of files. Truth be told, flashdrives and sneakernet isn't THAT much of a hassle. 

In reading about NFS, it's looking like automatically mounting these drives on the clients saps network resources. I've also read up on FileZilla. Given the needs, maybe I just need to spawn off a FileZilla service on the kitchen computer and do it THAT way....

I don't know what “saps network resources” really means or what “spawn off a FileZilla service” means either.  I run both Samba and NFS on a couple of P3 Dells with 1GB of RAM each.  I have no problems at all.  The CPU is barely used.  The HDD efficiency (measured in I/O capacity) is what is important.

FileZilla is OpenSSH in a GUI package.  It uses OpenSSH SFTP and SSHFS do  what you want done.  You certainly can do that.  It's just a service like Samba and NFS.  All of these have their strengths and weaknesses.> 

The most interesting thing of all of this is learning about how many options there actually are out there.

And let me add, there's lots of information here written by "you guys." "You guys" being those who deal with this stuff on a regular basis.

To "us guys" who do NOT deal with this on a regular basis, it's greek and a little scary. I haven't found one walkthrough yet written that is what I would call comprehensive for a new person. So I can see why Linux is a turn off to the regular person. You almost need a champion to help you the first year you use it. I have to beleive a home network similar to what I want is something that MOST people would want. And what would be cool would be a walkthrough on setting that up. That would cover the enchilada.... What you do with your router. How you allow people access to folders on the "server." What folders you should back up. What you do to protect your system from the outside. But clear and concise. The stuff I've found is good, but the background learning curve stuff isn't all connected well. THEN you get a couple of people who aren't network type guys to test the walkthrough.

I can tell you this, I switched to Linux a few years ago because Windows seemed to CONSTANTLY require me to repair it. The kids would browse the net, play their flash games, and inadvertently click things and "pollute the system" is the best way I can describe it. If I made a Windows admin account and gave the kids the limited accounts, that sort of helped. But then half the games they wanted to play couldn't connect to servers, or write their save files. Like they weren't REALLY Windoze compliant.

So about every 3rd or 4th Saturday I spent cleaning up the old Windoze machine. Hey, they can do without the games a bit, but what happened was they'd get it all hosed up THEN they couldn't do their homework. A buddy said "try Linux...." I never looked back. Normally, I have to do some serious eat up my weekend admin time MAYBE about every 9 months. VAST improvement over Windoze.

And NEW Windoze is worse. I don't find it intuitive AT ALL where all these configuration settings go.

My beef with Linux really isn't all the command line stuff. The beef is all the hunting around on the net you have to do. I find I spend MOST of the time reading these guides and walkthroughs, having to learn the vocabulary, and the actual WORK part of it is like 15 minutes. That's OK for me, I find it interesting. None of my neighbors would. They just bitch about Windoze.

Somebody puts a clear guide out there about how to set up a stable home network in Linux that a "normal" person could understand that was easy to follow, there'd be a LOT less Windoze users out there ...

THEN you'd want to revisit it with every distro release and rewrite it. Heck. It should just "unpack" and be in documents when the distribution is released. It's the pointer trail that's a pain. "This worked in Natty, but not needed in Lucid ..." Or pieces of it here and there.

The home network is what people want that is lacking. The rest of the stuff - that's handled pretty well through the Software center, which works like getting apps for a phone.

I think you think that Linux should be like Windows.  Sorry but it's not going to happen.  In fact the desktop for a vast majority of installs is not even a concern.  I have used Linux and UNIX for the past 20+ years.  The desktop is a recent concern.  A nice one to be sure, but nowhere near the install base of non-GUI hosts for server use.

There is no way to get around the use of the proper terminology when describing a remedy for a problem.  There is a certain amount of basic knowledge needed to discuss anything.  You aren't expected to know how to build your car when talking it to the dealer for repair, but it helps if you  know how it works, even if it is just the basics. 

Linux and Unix put the complexity out there for you to configure as you wish.  Windows has the same complexity, they just hide it all.  Linux (and all Distros) have many developers (not paid), who do  not always see eye to eye on development.  Windows has divisions that are all managed by folks with a somewhat united front and all get paid by the same company.

My feeling is “it's either time or money” If you don't have the time to learn (which is okay by me) then you have to pay for the service.  Linux is still very much a developers and enthusiast OS.  Windows is as you mentioned, not worth the trouble.  That leaves Apple Mac OSX.  It's based on UNIX and has a slick GUI that works.  It cost money and you will have to install Samba on the latest version.  That should be easy to do.

All kidding aside Computer Science is a complex subject that you can really only know a piece of.  Even the subject of System Administration is multi layered and ever changing.  Samba or NFS technologies are a complete book all by themselves.  TCP/IP is a couple of books at least.  The Linux file system is a pretty long essay.  As you can see this is not a monolithic subject at all. 

Linux the “free OS” means more than: you didn't have to shell out and money.  The original ides was free to distribute and free of monetary costs.  In addition I guess we can add “free to ask questions”.

Most folks on this forum are happy to help you design and implement your network network needs.

Do you want to go back to trying Samba3.  Is the network configured to have a fixed address for the Samba server?  Can you ping this host by a hostname?  Describe what and how you want backups to happen?

---

### Post by ncwalker2010 on 2013-07-05
I think I am making progress with NFS.  And agreed.  You have to pay the price to get the terminology right.  It's not that as much as the shorthand.  I have expertise in different fields other than networking.  And when people watch me "do what I do" they think it's magic.  It's not.  I put time in to gain mastery.

And yes, I used to write software for a living (years ago, and not networking stuff, it was mathematical modelin.  My piece of it anyway.  Other guys did the networking and they might as well have been from Mars).  Point is - you DO get caught in the shorthand, which makes things you put a little cryptic for newbies.  Until the aren't newbies.

Anyway, I have been wrestling with the router trying to reserve an IP.  It lets me limit the masks it assigns automatically.  So I dropped the limit from .255 down to .200 and THEN assigned my kitchen PC to .222 in the router via the MAC address.  Thought I was pretty trick.  6 reboots later, I am STILL not getting .255 ....

DOH !!!  When I set the limit low, .222 was out of the range so the default was to say "Hey, I have an error so I'm going to give him an automatic one less than 200..."

I put the limit back to 254 (max) and set the kitchen pc to 222 (easy to remember) and I'm at .222 all day long ... :-)

Now to NFS ....

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> ...

Anyway, I have been wrestling with the router trying to reserve an IP.  It lets me limit the masks it assigns automatically.  So I dropped the limit from .255 down to .200 and THEN assigned my kitchen PC to .222 in the router via the MAC address.  Thought I was pretty trick.  6 reboots later, I am STILL not getting .255 ....

DOH !!!  When I set the limit low, .222 was out of the range so the default was to say "Hey, I have an error so I'm going to give him an automatic one less than 200..."

I put the limit back to 254 (max) and set the kitchen pc to 222 (easy to remember) and I'm at .222 all day long ... :-)

Now to NFS ....
What does all that mean?  The only mask I know in networking is the subnet mask.  The number 255 is not an ordinal number at all in a subnet mask.  If you router assigned an IP address it will re-lease that address to the original holder all day long.  The problem is when the host is off and that address is given up to some other host.

If you can reserve a leased address it will be by the MAC address as you have stated You will have to limit the DHCP pool of addresses.  THis has nothing to do with subnet masks or masks in general.  Look for the pool of automatically assigned IP addresses.

---

### Post by ncwalker2010 on 2013-07-05
[IMG]http://ubuntuforums.org/image/png;base64,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[/IMG]

Not sure if the picture will come through or not ....

Under the checkboxed heading "Use Router as DHCP Server" I set the Ending IP Address to 200 figuring it would reserve 2 through 200 as automatic IPs for the various devices.  (I have far less than 200).  THEN in the Address Reservation table just below, I set the Kitchen computer to .222

I hit apply and everything worked OK.  Turns out, that's not what the router wanted.  (And it didn't give me an error OR say it in the instructions to the left).

The router interpreted this combination as:
1) He only wants me to assign IPs up to .200
2) The big dummy set one of them to .222, which is outside of the range he wants so I'm going to assign it an automatic one IN the range he wants.
3) I'm not going to TELL him I'm doing this, I'm just going to laugh maniacally as he reboots and reboots until he figures it out.

So on MY router, the assigned IPs still have to be within the starting and ending IP addresses.  (Which in 20/20 hindsight makes total sense, because if I had 2 routers, I'd probably have to split the IPs between them.)

---

### Post by ncwalker2010 on 2013-07-05
Arggh.  The picture didn't come through of the router screen.

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> 

Not sure if the picture will come through or not ....

Under the checkboxed heading "Use Router as DHCP Server" I set the Ending IP Address to 200 figuring it would reserve 2 through 200 as automatic IPs for the various devices.  (I have far less than 200).  THEN in the Address Reservation table just below, I set the Kitchen computer to .222

I hit apply and everything worked OK.  Turns out, that's not what the router wanted.  (And it didn't give me an error OR say it in the instructions to the left).

The router interpreted this combination as:
1) He only wants me to assign IPs up to .200
2) The big dummy set one of them to .222, which is outside of the range he wants so I'm going to assign it an automatic one IN the range he wants.
3) I'm not going to TELL him I'm doing this, I'm just going to laugh maniacally as he reboots and reboots until he figures it out.

So on MY router, the assigned IPs still have to be within the starting and ending IP addresses.  (Which in 20/20 hindsight makes total sense, because if I had 2 routers, I'd probably have to split the IPs between them.)

[COLOR="#0000FF"]Edit: A reserved IP address is not the same as a static IP address.  Both are fixed,[/COLOR] but, yes the reserved is still handed out by DHCP.  The range can be what you like I have set mine to .50 to .75.  I don't want more than 25 hosts via DHCP anyway.  No two routers.  They would have to be on separate subnets.  You only need 1 dhcp router on a subnet active at any time.  IOW your sense is wrong.  :(   LOL

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> Arggh.  The picture didn't come through of the router screen.

No picture needed.  :)

So now we have a fixed IP address (via DHCP reservations).  Is Samba 3 still working?  What are the directories you wanted to share again?  You can mess with NFS as long as your sore head allows, but I think Samba for you is going to be easier.

---

### Post by ncwalker2010 on 2013-07-05
SUCCESS !!!!!

At least, I can see the server with the client and exchange files.  I'm going to play with it a bit and make sure the permissions are working like I expect.  Also, on the server, I made a directory /home/Client so I could easily find the mounts.  (I didn't want to go all the way back to root, harder to get there with Nautilus).  But the mounted drives show up as /home/Client/export/NetFee and I don't want the "export" in there.  But that should be easy to handle, I think.

And it is not automatically mounting via fstab.  So still a little playing around to do.  But the entire key that broke it lose for me was using the router to set the static IP address for the SERVER.  (Didn't do any of that with the client).  Then on the SERVER in the /etc/exports file I put:

```
/export/LocalRO 192.168.1.0/24(ro,sync,no_subtree_check)
/export/NetFree 192.168.1.0/24(rw,sync,no_subtree_check)

```

Where 192.168.1.0/24 represents the range of IPs my router allows.  For the Newbies, I figured this out with ifconfig.  But my reading showed there are only certain ranges for "subnets" which is what the network downstream of the router (in your home) is called.

Don't forget to issue:

```
$ sudo exportfs -ra
$ sudo service nfs-kernel-server restart

```

On the server when you change /etc/exports

Then on the client, I can mount it with the command line:

```
$ sudo mount -t nfs -o proto=tcp,port=2049 192.168.1.222:/ /home/Client

```

Where 192.168.1.222 is the static IP address I assigned to my _**server**_ machine via the routers assignment table so it always has the same IP.

It seems to be working fine now.  I can only read from LocalRO (though I haven't tried doing anything to it with a sudo on the client yet ...) and I can write to NetFree.

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> SUCCESS !!!!!

At least, I can see the server with the client and exchange files.  I'm going to play with it a bit and make sure the permissions are working like I expect.  Also, on the server, I made a directory /home/Client so I could easily find the mounts.  (I didn't want to go all the way back to root, harder to get there with Nautilus).  But the mounted drives show up as /home/Client/export/NetFee and I don't want the "export" in there.  But that should be easy to handle, I think.

And it is not automatically mounting via fstab.  So still a little playing around to do.  But the entire key that broke it lose for me was using the router to set the static IP address for the SERVER.  (Didn't do any of that with the client).  Then on the SERVER in the /etc/exports file I put:

```
/export/LocalRO 192.168.1.0/24(ro,sync,no_subtree_check)
/export/NetFree 192.168.1.0/24(rw,sync,no_subtree_check)

```

Where 192.168.1.0/24 represents the range of IPs my router allows.  For the Newbies, I figured this out with ifconfig.  But my reading showed there are only certain ranges for "subnets" which is what the network downstream of the router (in your home) is called.

Don't forget to issue:

```
$ sudo exportfs -ra
$ sudo service nfs-kernel-server restart

```

On the server when you change /etc/exports

Then on the client, I can mount it with the command line:

```
$ sudo mount -t nfs -o proto=tcp,port=2049 192.168.1.222:/ /home/Client

```

Where 192.168.1.222 is the static IP address I assigned to my _**server**_ machine via the routers assignment table so it always has the same IP.

It seems to be working fine now.  I can only read from LocalRO (though I haven't tried doing anything to it with a sudo on the client yet ...) and I can write to NetFree.

This is fine for all the Linux hosts.  They understand NFS.  What happened to " some of the PCs that connect in my home are Windows".  They will not understand NFS I believe unless they are Windows 7 Ultimate or I think Enterprise.  Windows 8 has no NFS by default I've been told.  You need to try your Windows hosts before you can declare success.

---

### Post by ncwalker2010 on 2013-07-05
Unless by brute force I MAKE everyone run Linux.  (I am the dad in the house, after all).

But yes, Windows compatibility via Samba is next.  I just wanted something reliable for my Linux side.  Again, for me, Samba crashes and crashes.

I'm going to play with NFS a bit and see what she'll do.  And, admittedly, I am happy because sharing files over the network is the LAST Windows hurdle I had to jump.  Microsoft could blow up tomorrow and I could effectively compute.

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> Unless by brute force I MAKE everyone run Linux.  (I am the dad in the house, after all).

But yes, Windows compatibility via Samba is next.  I just wanted something reliable for my Linux side.  Again, for me, Samba crashes and crashes.

I'm going to play with NFS a bit and see what she'll do.  And, admittedly, I am happy because sharing files over the network is the LAST Windows hurdle I had to jump.  Microsoft could blow up tomorrow and I could effectively compute.

Now that you have a fixed address Samba is a snap to set up.  Just ask and I will help you.

The advantave of Samba is you can browse for what you need.  With NFS you need to mount the shares explicitly via fstab or the mount command.

---

### Post by ncwalker2010 on 2013-07-05
SUCCESS !!!!

I was playing with Samba4 and it hosed everything.  So I went through and stripped it out.  (A little challeging).  And Saints on Bikes, but my smb.conf from Samba 3 days was on my backup.

So I just installed Samba3, copied my smb.conf to where she goes, restarted Samba, and now my two Windows 8 machines are seeing my server.  Read only and writeable, just like I wanted.

So ... let me look at that and see if I can enhance it using my shiny, new static IP.  And the NEXT task is to get the printer working.  :-)

---

### Post by ncwalker2010 on 2013-07-05
(It really isn't very hard, once you get used to it.)

---

### Post by redmk2 on 2013-07-05
> **ncwalker2010 said:**
> (It really isn't very hard, once you get used to it.)

You can breathe out now too.  It does all have a method to the madness.        LOL

Congratulations!

---

### Post by Zill on 2013-07-06
I appreciate that you are finding things frustrating when trying to do something you may regard as a common requirement.  However, all users are likely to regard their own specific requirement as important and, while this *may* be the case, every Linux system is configured in different ways.  This is because, unlike the corporate giants trying to force everyone to use their proprietary software in a specific way,  Ubuntu (and other Linux distributions) is based on choice and there are, inevitably, multiple ways to achieve an objective.

All Linux distributions are a co-operative effort and rely on the users, rather than some remote paid employees, to develop the software and associated support services.  As such, we should all assist in any way we can to improve our chosen OS.  You have, with some justification, highlighted that the documentation regarding home networking is inadequate.  On this basis, when you finally get your network working as you wish, it would really be useful if you would document what you have done and then submit this to the [Ubuntu Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam") for inclusion with the official documentation.

You may find the document entitled [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm") of interest as it shows the significant differences between proprietary software and Free and Open Source Software (FOSS) such as Ubuntu.

---

### Post by ncwalker2010 on 2013-07-06
Zill, don't take my comments the wrong way.  I have been, in general, extremely happy with Ubuntu.  And I don't mind diddling.  There are lots of great things that come out of the repository seamlessly.  Settung up share drives isn't one of them.

I would LOVE to help and have no problems writing down the steps that I took and can keep in perspective what matters to someone who is just dipping their toes in the pool.  I will take a look at your link and put something together.

---

### Post by ncwalker2010 on 2013-07-06
OK.  Phase 2:  I have my server putting out there the shared folders.  What's pretty cool is you do NOT have to mount them individually.  You can mount everything that the static IP is sharing to the network.  I decided that I didn't want to ALWAYS mount the client, but do so on command.  So I wrote a shell script.  That was fun (once I got going).  So the script actually tests to see if you have already mounted.  What I mean is, if you run it and you are not connected to the server, it mounts the directories.  And if you ARE connected to the server, it unmounts them.

But I went a bit further....  I also checked on the unmount to see if the connection was actually BUSY.  And it interrupts the unmount if it is and tells you the process.  To make it sexy, I sent all the user feedback through zenity.  So a little scipt in my local BIN folder, a double click, and we are easy-peasy.

```
#!/bin/bash
#
# This script checks to see if the NFS share to the homeserver is established.
# If it is established, then it will unmount it.
# If it is NOT established, it will attempt to connect to it.
#
# Check and see if the mount is in existence.  If the mount NOT present, the output
# of mount | grep /home/homeserver will be nothing.

MOUNTTERM=$(mount | grep /home/homeserver)

# Now check and see if MOUNTTERM is zero length.  If it is, we MOUNT the server.

if [ -z "$MOUNTTERM" ]

    then # There is no return from "mount", so mount the system.

    #sudo mount -t nfs -o proto=tcp,port=2049 192.168.1.222:/export/ /home/homeserver
    sudo /home/mark/bin/server.mount.nosu.sh    
    
    # notify user of success with a zenity popup.    
    zenity --info \
        --title="OesterTux Server" \
        --text="homeserver successfully mounted."

    else # The system is mounted, therefore, we want to unmount it.

    # Before we unmount it, we should probably check if it is busy....
    SYSBUSY=$(fuser -m -4 /home/homeserver) # if empty, nothing is using the mount

    if [ -z "$SYSBUSY" ]

        then
        #sudo umount.nfs4 192.168.1.222:/export/ -l
        sudo /home/mark/bin/server.unmount.nosu.sh

        # notify user of success with a zenity popup.
        zenity --info \
            --title="OesterTux Server" \
            --text="homeserver successfully UNmounted."

    else

        # Get the process information
        MYBADPRC=$(ps -p $SYSBUSY -j)
        MYNOTE="Cannot unmount homeserver. \n $MYBADPRC \n has it locked."
        # Notify User it cannot be unmounted with zenity
        zenity --warning \
            --title="OesterTux Server" \
            --text="$MYNOTE"

    fi

fi
```

I was EXTREMELY worried about putting SUDO commands in a script, and found this thread.  You have to do a few mods to get it to work. See the two calls to other shells?  server.mount.nosu.sh and server.unmount.nosu.sh?  Those just contain the mount and unmount commands.  One line scripts set to root:root as the owner and chmod to be executable.

You then edit a table and add them to a specific list of things that do NOT have to have sudo to run.  It's pretty slick.  It doesn't allow "mount" and "umount" (standard commands) to run without sudo.  Just these specific instances in the two sub-scripts, for wont of a better term.

Instructions for that are here:

[http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password](http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password)

And the steps are in the first answer.

---

