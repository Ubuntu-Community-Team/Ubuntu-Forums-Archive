---
title: "Reach Other Systems By Name?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by SamNSane on 2008-10-07
Small network with two WinXP SP3 systems and two Ubuntu 8.04.1 LTS systems. IPs are assigned via DHCP by a wireless router. When all of these systems were Windows systems the IP addresses didn't change. For some reason, however, they change on occasion now that there's a mix of operating systems as clients.

The Windows systems have no trouble at all finding each other by name, regardless of the IP addresses assigned them. Likewise, with smbfs installed on the Ubuntu systems, I can always reach the Windows systems by name and even browse to them by name via nautilus.

But finding or reaching an Ubuntu system by name isn't happening.

I've searched the forum and online documentation for information on how to fix this, but I'm not having any luck understanding just what the Dickens I need to do to simply reach an Ubuntu system by name on my LAN.

Obviously, I'm not looking for some sort of solution that involves using a static lookup table.

Please help me if you can.

---

### Post by cariboo on 2008-10-07
You need to have samba installed on your Ubuntu computers so that the windows computers can see them.

Jim

---

### Post by bodhi.zazen on 2008-10-07
You need to add your server to /etc/hosts

```
gksu gedit /etc/hosts
```

Add in your servers and LAN IP address , the format is 

ip_address  server_name

you can test this with a ping

ping server_name => you will see your LAN ip in the response.

---

### Post by SamNSane on 2008-10-07
> **cariboo907 said:**
> You need to have samba installed on your Ubuntu computers so that the windows computers can see them.

Jim

I looked at Samba, but it looks as though I'd have to run Samba on both Ubuntu systems, and that its records still wouldn't update automatically if the DHCP assigned IP addresses changed again. Is that right, or am I missing something?

As much bad-mouthing as I've seen pointed toward Windows' implementation of "network neighborhood browsing" (And I've seen more of it from Windows people than from people who use *nix.), it adapts automatically to changes in the IP assignments on the segment.

There's nothing along those lines for Ubuntu? If Samba is it, I guess I'm not understanding the documentation I've read. Samba seems to be more along the lines of a full SMB implementation for a domain.

Forgive me if I'm being dense. I'm new to Linux.

---

### Post by SamNSane on 2008-10-07
> **bodhi.zazen said:**
> You need to add your server to /etc/hosts

```
gksu gedit /etc/hosts
```

Add in your servers and LAN IP address , the format is 

ip_address  server_name

you can test this with a ping

ping server_name => you will see your LAN ip in the response.

Yes, I guess I should have mentioned specifically that I knew about this. But this is a static table, like using LMHOSTS. It's certainly better than nothing. But it means that I'll have to edit this file every time the IP addresses get reassigned by the router.

Thank you for the suggestion. Your instructions are precise and concise and just what someone new needs.

I'm hoping for a dynamically adaptable solution, but I'm beginning to think there isn't one for a small LAN setup like mine. Is that right?

---

### Post by bodhi.zazen on 2008-10-07
You can set up a local DNS server (bind9)

[http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm)

---

### Post by SamNSane on 2008-10-07
> **bodhi.zazen said:**
> You can set up a local DNS server (bind9)

[http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm)

This looks like a very good article. Thank you very much. It looks as though my choice will be to either do the text file edit you first suggested or BIND.

Shows you how new I am. I had a very wrong idea of what BIND is, which is why I wasn't reading about it.

Thank you very much.

---

### Post by Commander_Keen on 2008-10-07
> **SamNSane said:**
> Yes, I guess I should have mentioned specifically that I knew about this. But this is a static table, like using LMHOSTS. It's certainly better than nothing. But it means that I'll have to edit this file every time the IP addresses get reassigned by the router.

Thank you for the suggestion. Your instructions are precise and concise and just what someone new needs.

I'm hoping for a dynamically adaptable solution, but I'm beginning to think there isn't one for a small LAN setup like mine. Is that right?

You could also assign all pc with Static Ip address?
Also with DHCP, i believe that once the IP address are Assigned they are fixed with that PC until it leave the network, or until you release the IP address, but even if you release, it is still possible to get it back using ipconfig /r

---

### Post by rustutzman on 2008-10-07
> **Commander_Keen said:**
> You could also assign all pc with Static Ip address?
Also with DHCP, i believe that once the IP address are Assigned they are fixed with that PC until it leave the network, or until you release the IP address, but even if you release, it is still possible to get it back using ipconfig /r

Go into your router configuration and assign all by static IP and then edit the host file accordingly.

Russ

---

### Post by jerome1232 on 2008-10-07
> **bodhi.zazen said:**
> You can set up a local DNS server (bind9)

[http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm)

+1 

I use one on my lan, actually I use one in conjunction with a dhcp server (the dhcp server updates bind9 when ip addresses change and tries to assign their locally set hostname as the name)

It gives me much more control than my router did.

---

### Post by funky_D on 2008-10-07
hello everybody :)

i use static ip on my ubuntu, is there a way to register my hostname automatically on the DNS server (home router)?

thanks all :)
peace

---

### Post by SamNSane on 2008-10-07
> **Commander_Keen said:**
> You could also assign all pc with Static Ip address?
Also with DHCP, i believe that once the IP address are Assigned they are fixed with that PC until it leave the network, or until you release the IP address, but even if you release, it is still possible to get it back using ipconfig /r

This was actually my first choice, considering that this is a tiny 4-system LAN. The only problem I have with this is the way the dimwitted little network manager applet behaves when roaming is disabled.

I have a pretty easy setup now. My primary workstation is a laptop. Its only wireless connection is the LAN at home, on which I leave roaming enabled. I take it around to several other locations at which I connect on eth0 (wired) to networked via fixed IP address. That means that I have to save several network manager profiles, one for each of the fixed IP wired locations. When I come home I just connect via roaming, and all is pretty.

When I tried going fixed IP on the wireless connection (thereby disabling roaming) things got pretty ugly with the nm applet. Maybe I didn't persist long enough. But that is one pretty sad little applet, isn't it? Maybe I'm asking the wrong question and should just have focused on making that silly applet work with fixed IP addresses on both interfaces.

Thanks for your input. I may take a look at this again.

---

### Post by SamNSane on 2008-10-07
> **jerome1232 said:**
> +1 

I use one on my lan, actually I use one in conjunction with a dhcp server (the dhcp server updates bind9 when ip addresses change and tries to assign their locally set hostname as the name)

It gives me much more control than my router did.

This definitely looks doable, but may be more trouble than it's worth on a four-system LAN. Still, it might be worth it just for the learning experience. I might just decide to build a box for this purpose.

---

### Post by rustutzman on 2008-10-07
> **funky_D said:**
> hello everybody :)

i use static ip on my ubuntu, is there a way to register my hostname automatically on the DNS server (home router)?

thanks all :)
peace

```
127.0.0.1	localhost
127.0.1.1	machinename
192.168.10.155	mydomain.com
192.168.10.155	www.mydomain.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I set up a hosts file as above on my local machines that need to do name resolution. Create one file and copy it to the other machines. My network doesn't change very often so it's no big deal.


Russ

---

### Post by jerome1232 on 2008-10-07
> **SamNSane said:**
> This definitely looks doable, but may be more trouble than it's worth on a four-system LAN. Still, it might be worth it just for the learning experience. I might just decide to build a box for this purpose.

Don't worry that sad little applet actually improved quite a bit in intrepid, at least imho. (it can support multiple connections, it plays well with a static connections etc...)

---

### Post by SamNSane on 2008-10-08
> **jerome1232 said:**
> Don't worry that sad little applet actually improved quite a bit in intrepid, at least imho. (it can support multiple connections, it plays well with a static connections etc...)

If the changes in the applet's appearance are anything to go by, they really have improved it. Would you have heard whether or not they're going to backport that to Heron?

Aw, heck. I was going to be "responsible" and stick with the LTS version. I'm glad I put /home in its own partition, though I'm not sure it will actually save me that much trouble.

---

### Post by jerome1232 on 2008-10-08
> **SamNSane said:**
> If the changes in the applet's appearance are anything to go by, they really have improved it. Would you have heard whether or not they're going to backport that to Heron?

Aw, heck. I was going to be "responsible" and stick with the LTS version. I'm glad I put /home in its own partition, though I'm not sure it will actually save me that much trouble.

I doubt it, there were significant changes in intrepid regarding networking (files are kept in new places etc...) So I'm not sure installing the new version of the applet would even work right without significant tweaking.

For desktops I always go with the newest release, there are just to many goodies that come out to not upgrade. My little home server always sticks to the LTS version, a server doesn't need to go through massive possibly service breaking changes every 6 months, for no benefit.

---

### Post by funky_D on 2008-10-08
thanks rustutzman,
but i have laptops that use dynamic ip. so what i really need is to register my static ip machine on the DNS server (home router). my home router does not have ip reservations. i wanted the DNS to have all the names, so when somebody tries to reach other systems by name the DNS would have all information. I don't want create in each machine a hosts file. i would like a centralized database... if possible! :D
thanks all!
Dino

> **rustutzman said:**
> ```
127.0.0.1	localhost
127.0.1.1	machinename
192.168.10.155	mydomain.com
192.168.10.155	www.mydomain.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I set up a hosts file as above on my local machines that need to do name resolution. Create one file and copy it to the other machines. My network doesn't change very often so it's no big deal.


Russ

---

### Post by SamNSane on 2008-10-08
> **jerome1232 said:**
> I doubt it, there were significant changes in intrepid regarding networking (files are kept in new places etc...) So I'm not sure installing the new version of the applet would even work right without significant tweaking.

For desktops I always go with the newest release, there are just to many goodies that come out to not upgrade. My little home server always sticks to the LTS version, a server doesn't need to go through massive possibly service breaking changes every 6 months, for no benefit.

Yeah, you're right. Maybe I'll move on to Intrepid. I've only been on Linux a few weeks, having switched from Vista. I'm really enjoying it.

Is there a list somewhere of the application versions included in the Intrepid repository? Forgive me. I'm new at this and am just learning to find my way around. I want to know, in particular, whether or not they're using a later version of sunbird. I really vastly prefer 0.9 to the 0.7 that's in the HH repository. I got a DEB compiled for Linux Mint 5 (based on Hardy) and am a little shy about just assuming that I can blithely stick that into Intrepid.

---

### Post by Locke_99GS on 2008-10-08
> **SamNSane said:**
> Yeah, you're right. Maybe I'll move on to Intrepid. I've only been on Linux a few weeks, having switched from Vista. I'm really enjoying it.

Is there a list somewhere of the application versions included in the Intrepid repository? Forgive me. I'm new at this and am just learning to find my way around. I want to know, in particular, whether or not they're using a later version of sunbird. I really vastly prefer 0.9 to the 0.7 that's in the HH repository. I got a DEB compiled for Linux Mint 5 (based on Hardy) and am a little shy about just assuming that I can blithely stick that into Intrepid.

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by SamNSane on 2008-10-08
> **Locke_99GS said:**
> [http://packages.ubuntu.com](http://packages.ubuntu.com)

Dang! Ask and ye shall receive!

Thanks.

---

### Post by bodhi.zazen on 2008-10-08
Bah , try these :

[http://www.lucagasperini.com/blog/2006-ubuntu-search/](http://www.lucagasperini.com/blog/2006-ubuntu-search/)

They are search bars you may add to Firefox to replace "google".

---

### Post by Cato2 on 2008-10-08
> **SamNSane said:**
> 

The Windows systems have no trouble at all finding each other by name, regardless of the IP addresses assigned them. Likewise, with smbfs installed on the Ubuntu systems, I can always reach the Windows systems by name and even browse to them by name via nautilus.

...

Please help me if you can.

Here is a (relatively) easy way to do this.  It uses WINS, which is the naming system analogous to DNS that's used by Windows and Samba.  Basically you need to install 'winbind' as well as 'samba' on one of the Ubuntu PCs, and adjust /etc/nsswitch.conf, then you will find that you can reach all systems by name - not just when using Samba file sharing but when using any protocol.

See [http://ubuntuforums.org/showpost.php?p=3653772&postcount=13](http://ubuntuforums.org/showpost.php?p=3653772&postcount=13) for the details.  May be a bit easier than running a DNS server with dynamic updates.

---

### Post by SamNSane on 2008-10-08
> **Cato2 said:**
> Here is a (relatively) easy way to do this.  It uses WINS, which is the naming system analogous to DNS that's used by Windows and Samba.  Basically you need to install 'winbind' as well as 'samba' on one of the Ubuntu PCs, and adjust /etc/nsswitch.conf, then you will find that you can reach all systems by name - not just when using Samba file sharing but when using any protocol.

See [http://ubuntuforums.org/showpost.php?p=3653772&postcount=13](http://ubuntuforums.org/showpost.php?p=3653772&postcount=13) for the details.  May be a bit easier than running a DNS server with dynamic updates.

Well, there's certainly more than one way to skin a cat, isn't there? Thank you for this information, too.

It's interesting to me that, as varied as these approaches are, none of them matches up to the much-maligned Windows network neighborhood from the standpoint of ease-of-use and automatic adaptability.

The dynamically adaptable approaches would be outstanding for someone who had at least one static Linux box up and running at all times on his home network. That's not me. Both of my Ubuntu systems are laptops. They travel. Sometimes one of them is on the network, sometimes the other, and sometimes both.

The Windows systems are my wife's, and they are sometimes both present, and sometimes just one or the other.

Looks to me as though my choices are:
1. stick an always-on server on the network,
2. edit the /etc/hosts file (and then edit it again any time the dhcp leases change OR switch to fixed IP addresses and try to live with the shenanigans of the network manager applet when roaming is turned off on my wireless interfaces), or
3. just keep using IP addresses to designate the systems and accept the concomitant compromises in functionality on the network.

Can anyone tell me what happens if I edit /etc/hosts to associate my two laptops' names with IP addresses, and then take both of them to another network where they have different IP addresses? This happens, occasionally, and they have to share files with each other when I do it.

I guess I'd have to have a different hosts file for each network and copy the appropriate file into place for the appropriate network?

---

