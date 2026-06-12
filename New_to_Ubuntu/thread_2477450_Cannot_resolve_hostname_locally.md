---
title: "Cannot resolve hostname locally"
date: 2022-07-25
forum: New to Ubuntu
---

### Post by unbuntunewbie02 on 2022-07-25
Hi,

Firstly i am a Windows System Administrator and wanted to build a monitoring dashboard using PHP and java on a Linux platform i am very new to Linux so thanks for your understanding.

I have a webserver (LAMP) on Ubuntu desktop, the build and webserver are working correctly.

But my device was on DHCP which worked correctly. On changing the IP to the IP i wanted outside of my DHCP scope.

I cannot ping any local PC name i can reach Google correctly in the network GUI it shows my internal DNS servers.

But I cannot ping anything internally via host name my /ect/resolv.conf nameserver points to 127.0.0.53

Does that require changing to my internal DNS server or am i missing something?

---

### Post by TheFu on 2022-07-25
> **unbuntunewbie02 said:**
>  
But I cannot ping anything internally via host name my /ect/resolv.conf nameserver points to 127.0.0.53

Does that require changing to my internal DNS server or am i missing something?

The localhost runs a caching DNS server. That's what is in the /etc/resolv.conf.  If you have a DNS on your LAN, you don't need that.  What I did was to stop, disable, mask, then purge the tool that Canonical decided to use for that local DNS caching - systemd-resolved.  You don't need it.

But, because sudo needs to perform hostname lookups (don't ask, but it is for good reasons), you'll want to have created the new /etc/resolv.conf file that points at your DNS already.

The trick is to swap in the new file quickly after removing the current symlink just after you've stopped the systemd-resolved daemon.

1) create a new /etc/resolv.conf.new with the settings you want inside.  Use 
```
sudoedit /etc/resolv.conf.new
```
2) run these commands, in order, relatively quickly:
```
sudo systemctl stop systemd-resolved
sudo rm /etc/resolv.conf
sudo mv /etc/resolv.conf.new /etc/resolv.conf
sudo chmod 644 /etc/resolv.conf
sudo systemctl disable systemd-resolved
sudo systemctl mask systemd-resolved
```

That's the minimal.  If you like, you can purge the systemd-resolved package or not.

If you have a LAN DNS, you may want to disable avahi and fix the /etc/nsswitch.conf to not look for mdns at all.  However, setting up network printers is nearly trivial (30 seconds) if they are driverless, support IPP and all the client machines have avahi running.  Besides that use, I have ZERO good use of Avahi (zeroconf and whatever Apple calls it), but for setting up network printers, I have to admit, it completely rocks.  

Avahi is the reason many of your LAN systems can be located using .local appended to the hostname.  For example:
```
$ ping regulus.local
```
That's mdns at work, if you leave the nsswitch.conf alone.  Your choice.  For a few years, avahi had major issues and would sometimes eat 100% of the CPU on a system from time to time. I've been purging avahi for over a decade from all my systems.  It is only part of desktop installs, not servers, so that is another consideration.  I have 10-20 "servers" and only 2 desktops, so DNS is mandatory for my needs.  Additionally, I don't use DHCP reservations for servers or desktops, only for laptops and devices like network TV tuners and IP cams where setting a static IP is next to impossible.  

Around here, only guest devices use DHCP on the guest network.  My wifi devices are all on an untrusted network and must use a VPN to gain access to the trusted network.  This network architecture started based on the FBI recommendations, but I discussed it with a number of infosec gurus to end up with 2 external networks (inside the ISPs router, but not inside my router) and 2 internal, wired-only, LANs.  Trusted desktops and servers, and for internet-facing servers.

---

### Post by SeijiSensei on 2022-07-25
Alternatively you can work within the systemd-resolved framework and make a couple of changes to /etc/systemd/resolved.conf. You'll need the IP of the server that provides local DNS resolution within your network. Presumably it's the one all the client machines are assigned during the DHCP handshake.

Let's suppose that your primary DNS server has IP 10.10.10.10, and that you have a backup DNS server at 10.10.10.11. Also I'll assume you have a domain name; let's call it "domain.name". Edit the resolver's configuration file, /etc/systemd/resolved.conf, using "sudo nano /etc/systemd/resolved.conf" like this. (Lines beginning with "#" are comments.)

```

[Resolve]
# point DNS to your primary
DNS=10.10.10.10

# make Cloudflare and Google the last resorts after 10.10.10.11
FallbackDNS=10.10.10.11 1.1.1.1 8.8.4.4

# search domains; include your organization's domain here plus any others
Domains=domain.name some.other.domain

```
Now restart the resolver with
```

sudo systemctl restart systemd.resolved

```
and test the result with
```

host -v somehost.domain.name

```
Do you get the right reply now? (You might also take a look at "sudo systemctl status systemd.resolved" if something goes wrong.)

---

### Post by unbuntunewbie02 on 2022-07-26
TheFu,

I have run through your steps with the same results and i cannot ping a hostname for example office-5 does not come back with a IP it should do instead Temporary failure in name resolution.

My new resolv.conf files has "nameserver 192.168.18.200" I don't think it should be this hard to change from DHCP to a static IP

Thanks James

---

### Post by TheFu on 2022-07-26
Can you ping 192.168.18.200?
Can the system resolve other IPs pointing at that nameserver?
```
$ dig @192.168.18.200  google.com
```
 
What, exactly, is inside /etc/resolv.conf?   Show the command with the results, please.  For example:

```
$ more /etc/resolv.conf
```

Also, ensure there is at least 1 extra empty line at the end of all text files.  EOL and EOF are sometimes seen differently, so a parser may not consider EOF to be the same as EOL.

You can check that reverse lookups are working correctly too.

And if you have a LAN domain, the DNS server may not be performing the lookup without the FQDN.  In the resolv.conf, we can use the 
```
search domain1 domain2 
```
so that lookups will try what we typed, say "comp5", then "comp54.domain1" then "comp54.domain2".

---

### Post by SeijiSensei on 2022-07-26
You need to leave resolv.conf alone. It's set up to use systemd-resolved. The nameserver should be 127.0.0.53.

---

### Post by TheFu on 2022-07-26
> **SeijiSensei said:**
> You need to leave resolv.conf alone. It's set up to use systemd-resolved. The nameserver should be 127.0.0.53.

If the OP did what I said, then systemd-resolved is disabled.  Since he is running a LAN DNS already, let that do the caching, not the local machine.

But, if he didn't follow those commands, and for a laptop I wouldn't either, then making systemd-resolved work makes better sense because we'd assume that a laptop would be taken to other networks. That isn't the situation for desktops or servers.

At least, that's my thought process.

---

### Post by unbuntunewbie02 on 2022-07-26
I have move the system back on to DHCP now to get my code working as it should do to monitor my critical systems.

But my Resolv.conf file now only has  nameserver 192.168.18.200

Do you want to drop the machine back on to a static and run the:

dig @192.168.18.200 google.com

As i know 100% i couldn't ping the FQDN of the devices i need to work with

---

### Post by SeijiSensei on 2022-07-26
On Ubuntu systems, the file /etc/resolv.conf is by default actually a "symbolic link" to /run/systemd/resolve/stub-resolv.conf. The /run directory is a temporary file space where applications can write information. See [https://unix.stackexchange.com/questions/13972/what-is-this-new-run-filesystem](https://unix.stackexchange.com/questions/13972/what-is-this-new-run-filesystem). /run is created anew at boot.

```
/etc/resolv.conf -> /run/systemd/resolve/stub-resolv.conf
```

In that file is the directive
```
nameserver 127.0.0.53
```
So your version of /etc/resolv.conf with 192.168.18.200 is either a static file that replaced the link, or you edited /etc/resolv.conf and in doing so edited /run/systemd/resolve/stub-resolv.conf.

Whatever the reason, you need to make the nameserver 127.0.0.53 for it to use systemd-resolved.

---

### Post by TheFu on 2022-07-26
Scotty:
The more they overthink the plumbing, the easier it is to stop up the drain.

If systemd-resolved was working perfect, the OP wouldn't have posted.


To the OP, just changing the files we've concentrated on in this thread isn't sufficient to make a system have a static IP.  Changing over to static IPs still needs to happen. That can be performed through the DHCP Server with a reservation outside the normal DHCP range (MAC-->IP)
or
by following the static configuration method for your specific desktop DE or server, if it is a server.  Most of the time, the "{DE} Desktop Guide" will have a section on setting a static IP address.  The entries required are (I didn't look at any GUI):
* IP
* netmask
* gateway
* DNS server(s)
* domain search order
I usually modify /etc/network/ or /etc/netplan/ files to have static IPs on my systems.
[https://help.ubuntu.com/stable/ubuntu-help/net-manual.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-manual.html.en)  Is for the Gnome DE.  Mate, LXQt, KDE, each will have a desktop guide for the latest LTS release and the prior LTS releases that are supported.

---

### Post by ActionParsnip on 2022-07-26
You set the IP to one outside of the DHCP scope but is it still inside the same subnet? You could always add a DHCP reservation using the MAC address of the interface so the system always gets the same IP but via DHCP

---

### Post by TheFu on 2022-07-26
> **ActionParsnip said:**
> You set the IP to one outside of the DHCP scope but is it still inside the same subnet? 
YES!  

> **ActionParsnip said:**
> You could always add a DHCP reservation using the MAC address of the interface so the system always gets the same IP but via DHCP
But the reserved IP still needs to be outside the DHCP range of IPs - even if the DHCP server is providing the reservation, but also if it isn't.

---

### Post by unbuntunewbie02 on 2022-07-27
The Static IP I gave to system was outside of my DHCP scope but was inside my range of the class c network.

The PC was configured to work on DHCP while everything was setup and once working i wanted the device off my DHCP range for PCS and onto a certain static IP within the same range.

On setting the IP by the GUI i could not ping the FQDN of the server that once provided the device with its DHCP IP. I could lookup external hostnames no problem for example google.com 

I have set the device back to DHCP which works correctly but i would like to move this device onto a static.

---

### Post by MAFoElffen on 2022-07-27
Sorry, but for this, I am agreeing with NOT disabling resolvd.

 Let me explain. It's not a resolv problem on the Linux machine, per-say. Setting it to static, outside his Windows DHCP server, it lost a connection (On the Windows side). Setting the nameserver in NetPlan to his internal Local DNS points that Linux Server machine to the Local Network DNS, but there is still a step missing to regain that connection on the Windows Server side... 

"Windows Server DNS", just like Linux Bind9, still needs it's "DNS Resource Records" added in the Forward & Reverse Lookup's to add that Linux Server information, because it now has a static address... (there is nothing broadcasting that hostname, tying it to an IP address), to be able to tie that static IP address to the Hostname. (I also do Windows Administration.) Different method of accomplishing that than Bind9, but logically the same.  DNS is DNS.

RE: [https://docs.microsoft.com/en-us/windows-server/networking/technologies/ipam/add-a-dns-resource-record](https://docs.microsoft.com/en-us/windows-server/networking/technologies/ipam/add-a-dns-resource-record)

That is why you have Local DNS servers on Local Networks. Right?

Beyond Windows Server DNS, Windows machines also have a "Host" file located at \Windows\System32\drivers\etc\host... That is very similar to format of and purpose of the host file in Linux machines.

---

### Post by unbuntunewbie02 on 2022-07-27
As I stated in my first post I am a Linux newbie and unsure what needs changing.

All I would like is my PC on a static and able to lookup the local domains host names either FQDN or single host name 

PC01 or [EMAIL="PC01@domain.local"]PC01.domain.local[/EMAIL] i know in Windows how to fix this but I am new to Linux i did have a static configured in the GUI but that didn't work at all.

---

### Post by MAFoElffen on 2022-07-27
The IPAM Windows Resource Records are the static records in IPAM. You said you "know in Windows how to fix this" and that you did "have a static configured in the GUI..." With the GUI in Windows IPAM?

Please attach a screen capture (Use the Windows 'Snip Tool') of the "GUI" record (In IPAM) of the Linux Server (with it's IP Address and Hostname) in Edit Mode... That is what you are referring to right?

---

### Post by SeijiSensei on 2022-07-27
Have you changed the nameserver setting in /etc/resolv.conf back to 127.0.0.53?

---

### Post by unbuntunewbie02 on 2022-07-27
I have resolved the issue, seems to be a stuck stale record on the Windows DNS side on removed and re-configured as static all ok.

But after doing what TheFuu advised:

[h=2][COLOR=#000000]Re: Cannot resolve hostname locally[/COLOR][/h][COLOR=#000000][INDENT][I][COLOR=#000000][IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **unbuntunewbie02** [/COLOR][[COLOR=#000000][IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/COLOR]]("https://ubuntuforums.org/showthread.php?p=14105595#post14105595")
[COLOR=#000000]But I cannot ping anything internally via host name my /ect/resolv.conf nameserver points to 127.0.0.53

Does that require changing to my internal DNS server or am i missing something?[/COLOR]

[/I]

[COLOR=#000000]The localhost runs a caching DNS server. That's what is in the /etc/resolv.conf. If you have a DNS on your LAN, you don't need that. What I did was to stop, disable, mask, then purge the tool that Canonical decided to use for that local DNS caching - systemd-resolved. You don't need it.

But, because sudo needs to perform hostname lookups (don't ask, but it is for good reasons), you'll want to have created the new /etc/resolv.conf file that points at your DNS already.

The trick is to swap in the new file quickly after removing the current symlink just after you've stopped the systemd-resolved daemon.

1) create a new /etc/resolv.conf.new with the settings you want inside. Use
[/COLOR][COLOR=#000000]Code:[/COLOR]
[COLOR=#000000]sudoedit /etc/resolv.conf.new[/COLOR]
[COLOR=#000000]2) run these commands, in order, relatively quickly:
[/COLOR][COLOR=#000000]Code:[/COLOR]
[COLOR=#000000]sudo systemctl stop systemd-resolved
sudo rm /etc/resolv.conf
sudo mv /etc/resolv.conf.new /etc/resolv.conf
sudo chmod 644 /etc/resolv.conf
sudo systemctl disable systemd-resolved
sudo systemctl mask systemd-resolved[/COLOR]
[COLOR=#000000]That's the minimal. If you like, you can purge the systemd-resolved package or not.

If you have a LAN DNS, you may want to disable avahi and fix the /etc/nsswitch.conf to not look for mdns at all. However, setting up network printers is nearly trivial (30 seconds) if they are driverless, support IPP and all the client machines have avahi running. Besides that use, I have ZERO good use of Avahi (zeroconf and whatever Apple calls it), but for setting up network printers, I have to admit, it completely rocks.

Avahi is the reason many of your LAN systems can be located using .local appended to the hostname. For example:
[/COLOR][COLOR=#000000]Code:[/COLOR]
[COLOR=#000000]$ ping regulus.local[/COLOR]
[COLOR=#000000]That's mdns at work, if you leave the nsswitch.conf alone. Your choice. For a few years, avahi had major issues and would sometimes eat 100% of the CPU on a system from time to time. I've been purging avahi for over a decade from all my systems. It is only part of desktop installs, not servers, so that is another consideration. I have 10-20 "servers" and only 2 desktops, so DNS is mandatory for my needs. Additionally, I don't use DHCP reservations for servers or desktops, only for laptops and devices like network TV tuners and IP cams where setting a static IP is next to impossible.

Around here, only guest devices use DHCP on the guest network. My wifi devices are all on an untrusted network and must use a VPN to gain access to the trusted network. This network architecture started based on the FBI recommendations, but I discussed it with a number of infosec gurus to end up with 2 external networks (inside the ISPs router, but not inside my router) and 2 internal, wired-only, LANs. Trusted desktops and servers, and for internet-facing servers.

[/COLOR]
[/INDENT]
[/COLOR]

Do i need to do anything to get my resolv.conf back to normal.

---

### Post by TheFu on 2022-07-27
> **unbuntunewbie02 said:**
> I have resolved the issue, seems to be a stuck stale record on the Windows DNS side on removed and re-configured as static all ok.

But after doing what TheFuu advised:

[h=2][COLOR=#000000]Re: Cannot resolve hostname locally[/COLOR][/h][COLOR=#000000][INDENT][I][COLOR=#000000][IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **unbuntunewbie02** [/COLOR][[COLOR=#000000][IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/COLOR]]("https://ubuntuforums.org/showthread.php?p=14105595#post14105595")
[COLOR=#000000]But I cannot ping anything internally via host name my /ect/resolv.conf nameserver points to 127.0.0.53

Does that require changing to my internal DNS server or am i missing something?[/COLOR]

[/I]


Excess stuff removed to keep the thread clean. Best to just reference the post # next time than to poorly quote the entire thing in a way that breaks prior formatting. 

> **unbuntunewbie02 said:**
> 
Do i need to do anything to get my resolv.conf back to normal.

Undo what I suggested, in reverse order. There are complementary commands for the ones I provided .... mask --> unmask, disable ---> enable ... you get the idea.  And put all the files back they way they were.  You do have backups, right?

I assumed the DNS was already solved and that a static IP had already been set inside the Linux system, since that wasn't mentioned.  It seemed like only a DNS issue and since you have a LAN DNS, there's little need for more bloated software running on every system like systemd-resolved, unless it is a laptop.

---

