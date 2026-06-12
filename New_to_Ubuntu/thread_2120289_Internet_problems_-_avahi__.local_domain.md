---
title: "Internet problems - avahi / .local domain"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by Gareth Edwards on 2013-02-26
Hello all,

Please help! I'm in at the deep end learning linux on my new system 76!

My internet kind of works - I can email and I downloaded GIMP, but when I try and download VLC player I get " Network service  discovery disabled - current network has a .local domain, which is not  recommended + incompatible with Avahi network" - the same also occurs when trying to get updates.

I gather this is an ISP thing, not a Ubuntu problem - but can some of you kind folk please give me some nice clear (absolute beginner remember ;)) instructions for a work-around?

Mega kudos to anyone who can help me get up and running and starting to play with new toy properly! 

Thanks for reading,

Gareth.

---

### Post by Locus Kiesselbachi on 2013-02-26
Hello!
What program gives you this message?

---

### Post by Sandertje on 2013-02-26
Do you only get the message or are you also actually unable to use the internet?

I've had that message myself before without it actually doing anything. Seems there are more people with that 'issue', see:
[http://ubuntuforums.org/showthread.php?t=1109941](http://ubuntuforums.org/showthread.php?t=1109941)

---

### Post by grahammechanical on 2013-02-26
That message will come up if you are connected to the router but the router is not connected to the ISP. If we power on the router and the computer at the same time we may get that message if Ubuntu loads before the router has established the connection to the ISP. This can happen because Ubuntu will start to make a network connection before we get to the login screen.

Does this prevent you from downloading? Does it stop the downloading of updates? The disabling of Avahi should not make any difference on a machine that is not connected through the router to other computers. It does not affect my single machine in any way.

> Avahi allows programs to publish and discover services and hosts running **on a local network** with no specific configuration. For example, a user can plug their computer into a network and Avahi automatically finds printers to print to, files to look at and people to talk to, as well as advertising the network services running on the machine.

[http://en.wikipedia.org/wiki/Avahi_(software)]("http://en.wikipedia.org/wiki/Avahi_(software)")

Regards.

---

### Post by Gareth Edwards on 2013-02-26
Thanks for the responses,

@Locus - I get this message when trying to download certain things on internet (so far noticed VLC & Updates)

@Sandertje - as mentioned in original post, internet kinda works (can email / youtube / I downloaded GIMP - but certain things (VLC / Updates) not possible and the "avahi / .local domain" message comes up - thanks for thread link, there's one (unconfirmed) work-around there I will try

@graham - it's a home set up - one router and 2 laptops (my wife's mac works fine) no network that I'm aware of.
yes - stops certain downloads (including updates)
disabling Avahi - sounds great - how do I do that? - I've tried searching with super key, but no dice....

Thanks for the input so far - please keep any information / instructions coming!

Cheers,

Gareth.

---

### Post by DuckHook on 2013-02-26
When posting, please provide more info. At least, what flavour and version of 'buntu you are using, what software recently loaded, if the problem occurred after an update, etc.

Avahi is not really that important. @grahammechanical is correct. In fact some consider it a form of software bloat and prefer to do without it. My only concern might be that its absence somehow upsets the Ubuntu ecosystem. Its absence will break some services that rely on it. For example, hplip will not successfully scan your local network for network attached printers if Avahi is nuked. No big deal because you can just point the setup program to a specific IP address, but some functionality is lost all the same. A bigger concern is that Avahi is not the problem but only a symptom of the real problem.

No network guru, I, but do:```
host -t SOA local
```as suggested by [this]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362") launchpad thread. It should return something like:```
Host local not found: 3(NXDOMAIN)
```If it returns something like```
local has SOA record...
```then your ISP is capturing Avahi's .local assignation, which the ISP should not be doing. If so, [this]("http://smallbusiness.chron.com/resolving-local-ubuntu-38861.html") thread contains a workaround, along with advice that your ISP should be contacted and asked to stop using .local as a unicast domain.

I don't understand why any of this would prevent you from downloading VLC, but you can at least try it to see if it fixes things.

Good luck!

---

### Post by Gareth Edwards on 2013-02-26
Thanks Duckhook!

Sorry (new to this game) shoulda mentioned using Ubuntu 12.10, only software loaded is GIMP, which seems to be working fine.

I will try the steps prescribed later (at work now) and let you know how I get on.

Thanks again,

Gareth.

---

### Post by DuckHook on 2013-02-26
Forgot to mention that you might also bypass the whole problem by using OpenDNS for all your DNS name resolution. You will have to go into your router and point *all* of your DNS server IP addresses to OpenDNS servers. I use OpenDNS and find them excellent. All sorts of little extra goodies too, like filtering out sketchy sites, etc. Great if you have kids you want to protect. For OpenDNS server addresses, setup, etc. go to their site [here]("https://www.opendns.com/").

---

### Post by bab1 on 2013-02-26
> **Gareth Edwards said:**
> ... please keep any information / instructions coming!

Cheers,

Gareth.
Avahi is the Linux implementation of Zeroconf.  The first paragraph [**[COLOR="Blue"]here[/COLOR]**]("http://zeroconf.sourceforge.net/") gives a concise description of Avahi.

In essence; in the ***absence*** of any network configuration (no dhcp or manual configuration) Avahi provides a local LAN IP address.  This address the has the first two octets as 169.254.  This address is never provided by dhcp and has nothing to do with your ISP.  

IMO, the first test would be to see what the IP address of your network card.  You can do that by posting the output of this command ```
 ifconfig|grep 'inet addr'

```...This provides the currently configured IP addresses.

When I do this I get the following```

         [COLOR="Red"]inet addr[/COLOR]:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
         [COLOR="Red"]inet addr[/COLOR]:127.0.0.1  Mask:255.0.0.0

```

---

### Post by Morbius1 on 2013-02-27
I have personally only come across this once and it was on someone else's network. I basically followed the diagnostic steps DuckHook posted:
> host -t SOA localAnd determined that in fact the users ISP was resolving .local names. Linux is designed to turn off avahi when that happens ( see the contents of /etc/network/if-up.d/avahi-daemon ). I am also somewhat puzzled why downloading one thing invokes this error and not others since the error should have been persistent from the start.

[COLOR=Blue]*BTW*[/COLOR], DuckHook's other post is the only way I have found to circumvent this problem if you live in a Linux / OSX environment both of which use Avahi / Bonjour by default. Pointing your system to OpenDNS name servers will bypass the ISP's name servers and the system will not disable avahi.

---

### Post by Gareth Edwards on 2013-02-28
Thank you for your help everyone!

All solved now - as it happens, moved apartment recently and the phone socket here gives no such problem! - we're not paying for internet here or last place (Korea's a bit funny like that) - so its  a case of so far so good!

Incidentally, you kind folks were much more helpful than the system76 support guy I was in contact with, so consider yourselves professional!

Cheers all,

Gareth.

---

### Post by b3n0 on 2013-12-23
Hey guys,
Sorry to bring this old thread back from the grave. However Gareth seems to be having the same issues that I'm having.
I'm running Ubuntu 13.10 on a Mid 2010 MacBook Pro. 

This pops us for then disappears after a few seconds. It's no biggie, but it's kinda annoying.
[IMG]http://fc08.deviantart.net/fs71/f/2013/357/5/2/screenshot_from_2013_12_24_11_10_40_by_b3n0-d6z4qw3.png[/IMG]
Any clues as to how I could fix it?

Merry Christmas

---

### Post by Morbius1 on 2013-12-24
Count yourself thankful that you didn't get the recommended notification:
> Avahi detected that your currently configured local DNS server serves
a domain .local. This is inherently incompatible with Avahi and thus
Avahi disabled itself. If you want to use Avahi in this network, please
contact your administrator and convince him to use a different DNS domain,
since .local should be used exclusively for Zeroconf technology.
It's unfortunate that Linux can't follow Apple's lead on this thing. OSX goes through a similar detection mechanism with Bonjour ( it's name for Avahi ) and does something intuitively simple: hostname.local is handled by Bonjour and server.domain.local is handled by the DNS server. Problem solved.

Anywho, the most often recommended solution is to go into /etc/default/avahi-daemon and change the "1" in "AVAHI_DAEMON_DETECT_LOCAL=1" to a "0". That will indeed remove the error message but the proponents of this method seen to ignore the very caution stated in the file itself in doing so:
> [COLOR=#0000cd]# [/COLOR][COLOR=#000000]1 = Try to detect unicast dns servers that serve .local and disable avahi in
# that case[/COLOR][COLOR=#0000cd], 0 = Don't try to detect .local unicast dns servers, can cause
# troubles on misconfigured networks[/COLOR]
AVAHI_DAEMON_DETECT_LOCAL=1

It's unfortunate in your case since you are a mac user and Avahi / Bonjour is a way for both these modern operating systems to find each other on the local network without a lot of fuss.

You can change your DNS server to OpenDNS as DuckHook suggested, change ".local" to ".alocal" so there is no interference with your ISP's DNS server ( I have no idea how to make that change in OSX since it's not an issue there ), disable the check in /etc/default/avahi-daemon, or live with the error message. The error message should only happen once on start up - right?

---

### Post by b3n0 on 2013-12-26
Hey,
Yep, just on start up or login. I followed that tutorial but it hasn't fixed it.

---

### Post by efflandt on 2013-12-27
Do you have anything in your /etc/hosts file that contains a .local domain, or does your router somehow use that for a LAN domain? I used to use .local as a LAN domain in /etc/hosts or local DNS, but many years ago SuSE strongly suggested not to use "local" as a domain due to conflict with something else (which I thought was multicasting, but maybe it was Apple zeroconfig).

Avahi can be handy for some things and is installed by default in Ubuntu. For example if I want to connect to another computer on my LAN with unknown dynamic IP (especially a Raspberry Pi with avahi-daemon installed) I can connect to it by its hostname.local, for example: ssh raspberry-pi.local or [http://raspberry-pi.local/](http://raspberry-pi.local/) if running apache.

Zeroconfig is a little flaky in Windows though, because if you install Apple Bonjour in Windows, I think PuTTY can find other computers by hostname.local, but Internet Explorer or Firefox need to have it settings modified to NOT to use a default DNS search domain, nor search the internet if it thinks a domain is missing, and only use the hostname without .local to find a LAN web server by zeroconfig/avahi.

---

### Post by InfiniteStudent on 2014-01-03
My computer and OS
Dell Vostro 1015
Ubuntu 12.04LTS
uname -a  Linux 3.2.0-57-generic #87-Ubuntu SMP

Four days ago I was informed that an update to this software was available and I
should run the update.

During the launching of the Update Manager I was aware of, but did not carefully
read, a warning of some kind regarding this software and updating my computer.

After updating Avahi my laptop will not connect to my wireless network.  It will
connect to other wireless networks but not the one I have at home.

When I attempt to connect using the Ubuntu connection icon I get the following message.

"Your current network has a .local domain which is not recommended and
incompatible with the Avahi network service discovery.  The service has
been disabled."

I can ping my router and DSL modem.  I can not connect with my
web browser or connect to my e-mail through Thunderbird

Following the advise on this thread I ran

ifconfig|grep 'inet addr'

and got  inet addr:  127.0.0.1  Mask:  255.0.0.0
            inet addr:  10.0.0.4 Bcast:  10.0.0.255  Mask:  255.255.255.0

host -t SOA local

return from this command

local has address 192.168.1.250

I have browsed through my hosts file and do not find any entry related to
'.local' or the IP 192.168.1.250.

How can I find out if my ISP is 'giving' me the .local?

Thanks.

---

