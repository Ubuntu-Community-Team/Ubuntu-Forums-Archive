---
title: "Ubuntu 12.04 not communicating with DHCP"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by digitalbeachbum on 2014-01-08
I installed Ubuntu 12.04 a few months ago and it was working fine from a base install. In fact, I got all the email, file browsing, internet browsing, every service I needed to work with no problems.

A week ago I had gone to do the updates and after it finished all my local network browsing stopped. I couldn't get an IP address either from the Windows DHCP server.

After some fustration I plugged the workstation in to a small Netgear router which I use for the wireless devices. This router has a different subnet and runs its own DHCP service.

When I connected with the Netgear box I could browse the web but the local DNS wasn't working and I couldn't see any of the local resources (including printers). I could ping them though. I wasn't surprised that the local stuff wasn't working properly because this wireless is setup just to let people browse the web from their phones or tablets.

When I plug the workstation back in to the wall jack, I don't get a new IP address. I can't browse the web. I can't do any thing. I've even tried to manually configure the network card and nothing works!! <-this really confuses me

I've tried all kinds of changes that I found on these forums and none of them have helped.

Any ideas? 

Thanks

Patrick

---

### Post by digitalbeachbum on 2014-01-08
Oh, one other thing. My IP phone and another test workstation all connected to the DHCP server through the wall jack and got a new IP, so it wasn't a problem with the wiring, the wall jack or the connection to the router in the phone room.

---

### Post by MrMichaelHill on 2014-01-09
Can you access your windows DHCP server?

---

### Post by MrMichaelHill on 2014-01-09
(Pressed post by accident)

If so, find your machine in DHCP, what ever the entry last used was and manually delete it, also if DNS runs on that server too then delete it out of DNS too. Reboot your machine and hopefully the server should pick it up as a new machine?

---

### Post by digitalbeachbum on 2014-01-09
> **MrMichaelHill said:**
> (Pressed post by accident)

If so, find your machine in DHCP, what ever the entry last used was and manually delete it, also if DNS runs on that server too then delete it out of DNS too. Reboot your machine and hopefully the server should pick it up as a new machine?

I will check on the DHCP/DNS server to see what the entries are... let me get back with you this item.

---

### Post by digitalbeachbum on 2014-01-09
> **MrMichaelHill said:**
> (Pressed post by accident)

If so, find your machine in DHCP, what ever the entry last used was and manually delete it, also if DNS runs on that server too then delete it out of DNS too. Reboot your machine and hopefully the server should pick it up as a new machine?

OK. I went to the DNS/DHCP server and deleted any references to the workstation.
I went back to the workstation and got the MAC address, then entered a reserved entry based on the MAC address.
I then went back to the workstation and couldn't get any thing to work.

I then went in to the Network Connections and noticed that my network choices were "wired connection 2".
On a hunch, based on my Windows experiences, I deleted the "wired connection 2" and then rebooted.

When the workstation came back up, I of course had no connect so I went back in to Network Connections and created a new entry with DHCP.
When I finished I had one entry for "wired connection 1" and low and behold, the IP address matched the entry I had put in to the DHCP previously.

I still have no clue what happened. It seems that some how the old "wired connection 1" was holding something which I needed but I couldn't see "wired connection 1".
Deleting every thing then rebooting seemed to reset all the network connections.

Thanks for the help!

---

### Post by Iowan on 2014-01-09
> **digitalbeachbum said:**
> ...
Deleting every thing then rebooting seemed to reset all the network connections.

Thanks for the help!
[[Solved]?]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by MrMichaelHill on 2014-01-09
I know from experience with network issues like that it is sometimes good to go back to the start (wiping all entries in DHCP etc) and starting fresh as such.

Good to hear your online :)

---

### Post by fishfin on 2014-01-09
*If so, find your machine in DHCP, what ever the entry last used was and  manually delete it, also if DNS runs on that server too then delete it  out of DNS too. Reboot your machine and hopefully the server should pick  it up as a new machine?*


Where do you look to find your machine in DHCP...and the DNS server listing in order to delete them,

SJF (newby)

---

### Post by MrMichaelHill on 2014-01-10
Hard to explain without being in front of a server.

Under DHCP, it should have Scopes (IP ranges), then under that should be address leases, look under there and you should see IP's and names, find and delete :)

In DNS have a look under Forward look up zones, I really can't remember the structure of the top of my head but flick through the various options under forward look up zones till you see a list of IP's and names, then find and delete the same :)

---

