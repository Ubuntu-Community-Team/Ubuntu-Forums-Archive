---
title: "Trying the understand the GUI view of my Samba network"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by ar-jar on 2008-07-13
I have a Samba network set up at home. When browsing to Network Servers I get a window according to attached image network.png. If I then browse my way down the Windows Network I get a window according to image windowsnetwork.png.

Question #1: Why do I see the servers first on the same level as the icon for Windows Network (network.png) and then again in the folder for my Windows Network workgroup (windowsnetwork.png). I don't understand the GUI metaphor for this. It seems a bit like adding an icon representing your filesystem on your desktop and then having a folder representing your desktop somewhere in your file system (:-))

Question #2: How do I refresh the views of the network. When I fire up a new computer on the network, it takes several minutes for it to show up in the smb://home/ window (windowsnetwork2.png). Or is this just an idiosyncrasy of Windows Workgroups (don't right now remember how long this takes in Windows).

Question #3: The top level network view (network.png) doesn't get updated with the server that went on-line at all. The top level window still looks like that in network.png even though the new server shows in windowsnetwork2.png. This makes me wonder if I perhaps misconfigured something so that the server icons end up where they shouldn't? Also when waking up from Hibernation, the top-level server view never gets updated but shows computers that may have gone off-line and doesn't show computers that have come on-line.

I'm using smb.conf and regular Windows sharing to publish my shares. Heron and Satellite are Ubuntu machines, Solbacka and Verkstad are Windows machines.

Thanks!

Arto

---

### Post by fahadsadah on 2008-07-13
In Windows, commonly used folders appear in My Network Places, and also within the WORKGROUP folder. This is the same.

---

### Post by ar-jar on 2008-07-13
Thank you for your reply!

What you write is true but I have managed to construct a metaphor for My Network Places as a "cumulative and permanent list of links to network folders". They don't go away (for good or for bad) when I restart Windows. (Neither do they go away when servers go off-line.)

The network server list in Ubuntu on the other hand seems to be updated when I restart the computer to show what computers that are actually on-line at that point in time and thereafter becomes more inaccurate over time as it isn't updated.

It is therefore not a permanent list of links to all servers that have been on the network at one time or another (like My Network Places). Neither is it an updated list of servers that are on-line right now. It seems to be a list of servers that were on-line when I rebooted my computer the last time. And that is not awfully useful as all the computers on that list may have gone off-line and a bunch of new might have come on-line since then. And it is furthermore inconsistent with the list under Windows Network -> <Workgroup> that seems to continuously updated (albeit with a several minute delay).

I guess this is ok in an environment where servers stay on-line all the time but in the age of global warming I try to turn servers off when I can.

Arto

---

