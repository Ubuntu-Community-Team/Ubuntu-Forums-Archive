---
title: "Static IP with a DHCP port"
date: 2024-02-07
forum: New to Ubuntu
---

### Post by dabelort on 2024-02-07
Hello, 

Im completley new to this whole world, but i wanted to learn something new and here i am, i succesfuly installed ubuntu server no problems with that. Now i wish to make a static ip for future use of the server, sadly im stuck at the netplan edditing, because the router im using has 2 open ports, 1st and the 4th, 1st is used by my main desktop, the 4th till now was free. Now im using it for the server and turns out it runs under DHCP rules. Generally what ive found on the internet ive seen that shouldnt be an issue , but somehow i just dont get it. Tutorials who have DHCP still have the same subnet with the default gate way. Mine doesnt . Currently my 4th port runs on xx.xx.xxx.xx/19, default gate way is 192.168.1.254, with this im kind of stuck on what to do next, because if i follow guides nothing works and new errors that i have no clue what they mean show up. What should i do? 

Thanks in advance!

---

### Post by SeijiSensei on 2024-02-07
Is the server connected to a router? If so, it's likely the router is providing DHCP services to your network.

If you can access the administrative interface of the router, you should be able to modify its DHCP configuration so it gives out a particular IP address in response to a request from your server.

DHCP works by client machines broadcasting their hardware's Ethernet addresses. A DHCP server listens for these announcements and gives the requesting machine a valid IP address and usually some other information like the IP address of the client's domain-name server. These assignments are usually made at random from a specified range of IP addresses.

However, you should be able to override this random assignment for your server using administrative tools in your router. You should be able to see the list of address assignments made by the DHCP server in your router. You should then be able to modify the entry for your server and specify a fixed IP address.

Obviously you can also specify a static address on the server's side, but I've not done that with recent incarnations of things like NetworkManager so I'm going to let someone else chime in on that.

---

### Post by TheFu on 2024-02-07
If you want help with netplan, you'll need to post your netplan yaml file wrapped in forum code-tags to maintain spacing and columns.  YAML is extremely column dependent. It is very easy to screw that up and end with a non-working configuration.

For examples, see netplan.io.
Generally, there are 5 settings needed for a proper, simple, static IP configuration.
[LIST]
[*]IP address
[*]netmask
[*]default gateway
[*]2 nameservers - primary and backup
[/LIST]
That's it.  Of course, you'll need to correctly specify the interface device name. 20 yrs ago, that was almost always eth0.  These days, it can be based on the MAC or based on the driver/slot.  The **ip a** command should show all available ethernet adapters with working drivers in a computer. If DHCP is working, the netplan yaml file already has the correct device name. Use that following the examples.

Not all routers are created equal. Home/consumer routers don't have the the same capabilities that enterprise routers have - but we don't know what sort of router you have. Should we guess?  In general, ports in a consumer router won't impact DHCP or static IP assignments.  There can be exceptions, but normally, that isn't the situation.

There are other methods to accomplish static IPs, but they are outside Ubuntu, bring some issues, and if the router config isn't working, will end up causing any devices expecting to get their static IP assignment (also called DHCP reservation), to fail and not be provided any networking. That is bad.

---

### Post by MAFoElffen on 2024-02-08
The router feature that  SeijiSensei described is referred to as 'DHCP Reservation' or 'Static DHCP' which allows some routers to be configured to look at the MAC address of the devices making DHCP request, and if it has a specified MAC Address, t assign it with the IP Address that is configured within it's IP/Mask scope.

Unfortunately, not all consumer class routers support this feature. Built that is where you would look for and configure that.

Again, a static IP address is always an option, and a more widely accepted solution.

---

### Post by dabelort on 2024-02-08
Sadly my router doesn't support this feature , I might contact my ISP for clarification but that will be the last resort. but thank you for the reply

---

### Post by dabelort on 2024-02-08
> **TheFu said:**
> If you want help with netplan, you'll need to post your netplan yaml file wrapped in forum code-tags to maintain spacing and columns.  YAML is extremely column dependent. It is very easy to screw that up and end with a non-working configuration.

For examples, see netplan.io.
Generally, there are 5 settings needed for a proper, simple, static IP configuration.
[LIST]
[*]IP address
[*]netmask
[*]default gateway
[*]2 nameservers - primary and backup
[/LIST]
That's it.  Of course, you'll need to correctly specify the interface device name. 20 yrs ago, that was almost always eth0.  These days, it can be based on the MAC or based on the driver/slot.  The **ip a** command should show all available ethernet adapters with working drivers in a computer. If DHCP is working, the netplan yaml file already has the correct device name. Use that following the examples.

Not all routers are created equal. Home/consumer routers don't have the the same capabilities that enterprise routers have - but we don't know what sort of router you have. Should we guess?  In general, ports in a consumer router won't impact DHCP or static IP assignments.  There can be exceptions, but normally, that isn't the situation.

There are other methods to accomplish static IPs, but they are outside Ubuntu, bring some issues, and if the router config isn't working, will end up causing any devices expecting to get their static IP assignment (also called DHCP reservation), to fail and not be provided any networking. That is bad.

So currently my netplan file (00-installer-config.yaml) is holding its base set up :
```
network:
  version: 2
  ethernets:
     enp3s0:
         dhcp4: True
```

as this lets me use the server fine downloading packages and so on. But before this i tried this set up:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - xx.xx.xxx.xx/19
      routes:
        - to: 0.0.0.0/0
          via: 192.168.1.254
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
```

As i understand the gatway4 is deprecated , ubuntu server says it , so i used routes instead . hopes this inforamtion helps
Also i double checked with** ip a **and my ip has changed again (well duh) and now its zz.zzz.zzz.zz/19. (again dont know if this helps)
About the routers i assume myself i have a consumer router, it is fiber optic (dont know if this information matters) but as stated in the above i dont have access to change anything in the settings, either way would be nice to find out what should i do with the yaml file.

Thank you for your replys , and sorry for taking so long to give answers :)

---

### Post by SeijiSensei on 2024-02-08
I've always owned my own routers from companies like TP-Link and ASUS. They all permit DHCP reservations. I stopped using the ISP's router long ago since I didn't want to pay a monthly rental fee, and I wanted complete control over the device.

---

### Post by TheFu on 2024-02-09
Most residential routers would give out private IPs for the LAN and retain the public IP for the WAN/router to use.  This is a key aspect to NAT - Network Address Translation.  When you go back to the DHCP netplan, then generate and apply it, what, exactly, is the IP address you get?  I'd expect something like 192.168.x.x/24.   We need to know the IP range DHCP is using so we can be smart and pick a static IP for your LAN system.  If you have other devices connected through the same router, you can get their DHCP IPs.  

I usually setup my routers to split static IP ranges and DHCP IP ranges to prevent problems.  Typically, I'll have about 20 DHCP addresses on a /24 subnet and have all the others for static IP assignment or "DHCP reservations" for devices that don't allow locally controlled static IP setup.  For example, we use network TV tuners connected to antennas in the attic.  Those tuner boxes don't allow setting the static IP, so a router reserves specific static IPs for each tuner so that other devices on the same subnet can find them. It is easier if they are always at the same IP, right?  (hint, it is).  I haven't seen any consumer router made in the last 15 yrs that didn't support DHCP reservations.

Most computers wouldn't get the public IP, xx.xx.xxx.xx/19 and in no way do you have control over that.  Public IPs must be assigned through both your ISP and whatever the regional IP assignment group is - ARIN is an example.   Also, it would be really odd for a home connection to get a /19 subnet.  That's over 8000 IPs just for you.  **I'm 99.9999999% certain using zz.zz.zzz.zz/19 is wrong.**  Some ISPs do some odd things around the world.

Most residential setups get 1 IP.  I have a business connection and get a /29 (5 usable, public, static IPs) from my ISP - and it costs. If you didn't specifically ask for 8000 static IPs AND aren't paying - probably $500-$2000/month ... then you shouldn't reference those in your netplan.


Everything I've written above is for IPv4, not IPv6.  For IPv6, it is common to be given a /64 or a /56 by an ISP.  IPv6 addresses don't look anything like IPv4 addresses.

---

### Post by SeijiSensei on 2024-02-09
> **TheFu said:**
> Most residential setups get 1 IP.  I have a business connection and get a /29 (5 usable, public, static IPs) from my ISP - and it costs.
I had clients who got a /27 back in the early days when ISPs were handing them out to commercial clients like they were candy.

---

### Post by dabelort on 2024-02-09
I consulted with my ISP (they have made the routers basically unchangeable by the user and wont give me access to change anything myself) and seems like my best course of action is to get a new router  with which to try again, so for now i wait till i get the new router and will try again, but thank you for the advice and help!

---

### Post by aljames2 on 2024-02-09
Have you considered hanging a multiport dumb (unmanaged) switch off the port you want to use, you could have your desktop and server on the same subnet that way, if that is what you prefer.

As mentioned, you can set a static IP on the server using your nteplan .yaml file.  Some examples here: [https://netplan.readthedocs.io/en/stable/examples/](https://netplan.readthedocs.io/en/stable/examples/)

There are errors in your attempt as shown.  You cannot assign the same IP address to your server interface as the router interface on the subnet.  As TheFu said, 78.84.xxx.xx is wrong, not in the range of private IPv4 addresses, something wierd there.

Is your ISP provided router also your modem?  If so, and you wish to use your own router, you will likely need to put the ISP router/modem in bridge mode and then put your new router behind that.  If you have a separate modem already, then yeah, you can probably ditch the ISP router and use a new one.

---

### Post by TheFu on 2024-02-09
> **dabelort said:**
> I consulted with my ISP (they have made the routers basically unchangeable by the user and wont give me access to change anything myself) and seems like my best course of action is to get a new router  with which to try again, so for now i wait till i get the new router and will try again, but thank you for the advice and help!

I new router isn't needed and won't provide the necessary knowledge.  Just setup the correct static IP on the system.

If your understanding of IPv4 networking is weak, episode 25-29 (approx) of the *Security Now!* podcast will explain it.

---

### Post by CharlesA on 2024-02-09
Censored the public IPs after the OP asked.

Having a /19 is a bit odd for sure. I've got a /30 at home and a /29 at work.

What ISP do you have? Do you know the model of router did they provide? If you are trying to set up another device to act as a router, the other router should be set into passthrough mode if possible.

---

### Post by MAFoElffen on 2024-02-11
What is even more odd, is that you are trying to set the IP via DHCP. Did you not pick up on that? That is not what people usually do or are set on as a requirement. 

The more normal/accepted method is to set the IP as Static, from the machine itself.

---

### Post by TheFu on 2024-02-11
> **MAFoElffen said:**
> What is even more odd, is that you are trying to set the IP via DHCP. Did you not pick up on that? That is not what people usually do or are set on as a requirement. 

The more normal/accepted method is to set the IP as Static, from the machine itself.

Well, it is 50/50 - static assignment on the system or DHCP reservations.  I've seen both used in corporate environments.  I've also seen a corporate campus crashed because their redundant DHCP servers failed.  2000 systems and none worked.

Definitely best to set static IPs on each system, provided that system doesn't move.  For laptop, using DHCP reservations is probably smarter.
Back in 2011, I thought using DHCP reservations was a great idea for home. [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) even after seeing that massive failure around 2005 at a client.   

Then I messed up my DHCP settings at home and none of my system would get an IP. That's when I decided to add my caveat.
[LIST]
[*]Servers/Desktops - static IP configured on the device.
[*]Portable devices - DHCP Reserved IPs, configured in redundant DHCP servers.
[*]Devices that don't allow setting static IPs - DHCP Reserved IPs, configured in redundant DHCP servers. Mainly IoT stuff.
[/LIST]

---

