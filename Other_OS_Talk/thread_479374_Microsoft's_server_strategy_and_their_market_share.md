---
title: "Microsoft's server strategy and their market share"
date: 2007-06-20
forum: Other OS Talk
---

### Post by cunawarit on 2007-06-20
I don't know if you guys have heard of it, but MS appears to have listened to a lot of criticism, and is planning to make its servers more attractive. How?

One thing key differentiating Windows 2003 Server and Linux servers is bloat and manageability. Bloats in terms terms of over reliance on GUI, no option to install a thiner version of the OS, and over reliance on the registry over setup files. 

To tackle this MS will release Server Core for Windows 2008 Server. Server core is a minimal installation, only a command line (that's right no GUI at all!), relying on setup files for services like IIS where possible. 

Is it a Linux server killer? No, it still has lots of disadvantages like:

* Server Core is not Debian, you can't start with a minimal server install and then add a package to do this and a package to do that. You get what you get and that's that.

* .NET will be supported in the future, till then you will not be serving ASP.NET pages with IIS, or managing your server with PowerShell. This is a MAYOR drawback! It is coming though... Personally I wouldn't even consider it till then. 

* Costs, needless to say it will not be gratis. But it may be cheaper!

* The registry is STILL there, and you'll have to either manage it with the command line or use regedit on a remote machine to manage the server's registry. 

* The silly name... Server Core will be Windows without windows! Maybe it should have been called MS DOS Server? 

What do you guys think? Do you think it'll convince some people to move across, or simply benefit those who already run Microsoft servers?

---

### Post by M$LOL on 2007-06-20
No, not MS-DOS Server, because it *is* the Windows NT platform, not the DOS one.

It still fails next to Linux though, because the Windows platform has so many holes in it, and even if you strip it down completely, it still sucks.

---

### Post by cunawarit on 2007-06-20
> **M$LOL said:**
> No, not MS-DOS Server, because it *is* the Windows NT platform, not the DOS one.

I know it is NT6 like Vista, but I was thinking of the name for marketing purposes. Anyway, you are right, it is Windows 2008 minimal install, it is still Windows even if it has no windows. 

> It still fails next to Linux
I'm of the same oppinion, Linux is much more flexible and that will ensure its number one status for the forseable future. 

> the Windows platform has so many holes in it
However, Server Core will greatly reduce the places where you can attack it from, I may be being hopeful, but maybe it will be much more solid from now on.

> even if you strip it down completely, it still sucks.
Agreed, it sucks in many places, and it isn't flexible. But it could be solid for certain tasks, and it may sway some, I am undecided on this... 

On the one hand Windows still falls short on many fronts, it comes with so little out of the box! Not even vital things for the modern world like an SSH server!

On the other, maybe its compact neatness will appear to users that don't require the flexibility Linux provides.

---

### Post by karellen on 2007-06-20
on server market I strongly doubt that microsoft could take over linux in the near future. Linux is simply better for what a server needs to do

---

### Post by smiggs on 2007-06-20
I assume by command line you actually mean powershell? I've only had limited use of the powershell so far on a xp desktop and it looks like it will be a real improvement over the dos prompt and scripting in previous incarnations. It's interesting that Microsoft are now confident enough in their command line that they will provide a command line only OS, it's been one of the main on desktop and server that has lead me to Linux and to find it on Windows is obviously going to be very useful there have been many times that a powerful command line utility may have allowed me to keep critical Windows servers up after the GUI has had a panic attack.

---

### Post by cunawarit on 2007-06-20
> **smiggs said:**
> I assume by command line you actually mean powershell? I've only had limited use of the powershell so far on a xp desktop and it looks like it will be a real improvement over the dos prompt and scripting in previous incarnations.

I've been using PowerShell a little bit and I've already come up with a couple of little scripts that would have taken much much MUCH longer to do in something like C#.

Sadly I am in no position to comment on how it compares to something like Bash. Because even though I know a little bit of Bash too, I don't know enough Bash, or PowerShell to give an informed opinion on how they compare. 

PS: Server Core will support Powershell. But not at first... The first release will not support .NET at all as I said above... I won't be too useful for me till it does.

---

### Post by smiggs on 2007-06-20
> **cunawarit said:**
> 
PS: Server Core will support Powershell. But not at first... The first release will not support .NET at all as I said above... I won't be too useful for me till it does.

hmmm seems a little pointless, I thought Powershell was one of the big selling point for this release. It's not as if I'll get anywhere near it until 2010 knowing my company's (entirely correct) policy on Windows releases so I'll be able to get over the pain of lacking powershell. 

The other features are going to be interesting though: 

The new terminal server features are somewhat reminiscant of Citrix but will surely come at a great cost in terms of CALS. It'll be good to see the back of Citrix though so long as the Linux clients for terminal services keep up with the Windows enhancements.

The Deployment Services again will be interesting if you can actually get it to work, it spells the end for the likes of Acronis and Norton Ghost. Which I guess we've got to be thankful for Norton's licensing is just a money making scheme and Acronis have forced my company to buy another copy of their product simply for a driver update.

---

### Post by kamaboko on 2007-06-20
Source: Linux-Watch.com

May 29, 2007

The server market is back, and Linux is helping, IDC reports. Linux servers posted their second consecutive quarter of double-digit growth and now represent 12.7 percent of the overall server market, or $1.6 billion for the first quarter of 2007.

The latest quarter was a good one for servers in general. Factory revenue in the worldwide server market grew 4.9 percent year-over-year, to $12.4 billion for the latest quarter. This is the fourth consecutive quarter of positive revenue growth and the highest Q1 server revenue since 2001, IDC said.

"The server market continues to experience solid growth as businesses of all types look to enhanced IT capabilities in order to help drive additional business efficiency, improved customer satisfaction, and accelerated revenue growth," said Matt Eastwood, IDC's program VP of enterprise platforms in a statement.

Microsoft's Server 2003 showed surprising strength. Microsoft Windows server revenue was $4.8 billion in Q1, showing 10.4 percent year-over-year growth and gaining 1.9 points of revenue market share over Q1 of 2006. According to IDC, this was the first quarter since IDC began tracking Linux server spending in 1998 that Windows server revenue has grown faster than Linux server revenue. Windows comprised 38.8 percent of all server revenue in Q1 of 2007.

That may be in part because the x86 architecture is continuing to accelerate. In the last quarter, it grew 8.7 percent year-over-year to $6.6 billion worldwide, its fastest growth rate in six quarters, IDC said.

Unit shipment growth also continued, with a moderate gain of 6.5 percent to 1.8 million servers as IT consolidation activities continue across the market, according to IDC. HP and Sun were the only top-five server vendors to outgrow the market in Q1 -- growing factory revenue 18.1 percent and 39.5 percent respectively -- and gaining x86 market share in the process. HP led the market with 35.3 percent x86 revenue share with Dell holding second place with 20.4 percent revenue share.

"For the third consecutive quarter x86 revenue growth rates increased while average selling prices have held steady," said Jed Scaramella, research analyst in IDC's Enterprise Computing group in a statement. "As customers continue to virtualize their IT environments, they require more richly configured server systems. While unit shipment growth rates continue to slow, the increased amounts of memory and I/O necessary for virtualization have driven revenue growth rates."

---

### Post by cunawarit on 2007-06-20
> **smiggs said:**
> The new terminal server features are somewhat reminiscant of Citrix but will surely come at a great cost in terms of CALS. It'll be good to see the back of Citrix though so long as the Linux clients for terminal services keep up with the Windows enhancements.

I have been thinking along the same lines, the prospect of running individual Windows applications on whatever machine I happen to be using is something I am quite looking forward to... rdesktop is very good right now, hopefully it won't fall too far behind for too long.

---

### Post by dca on 2007-06-21
They're only basing it on how many SLES coupons they've given out....  :D

---

### Post by Sunforge on 2007-06-22
I get the feeling that Microsoft is changing for the sake of change making us techs re-learn what we already know so that we can implement the same thing from a command line. No change there then. ;)

Exchange 2007 does similar things and introduces a host of server configurations that only apply to very large organisations.

---

### Post by smiggs on 2007-06-22
> **Sunforge said:**
> I get the feeling that Microsoft is changing for the sake of change making us techs re-learn what we already know so that we can implement the same thing from a command line. No change there then. ;)

Exchange 2007 does similar things and introduces a host of server configurations that only apply to very large organisations.

If they do it right they'll allow you access the GUI tools from your desktop, there's no reason for a server to run a GUI. You only really need to use a server direct from the console when it's going titsup and then I often find the GUI gets in the way, I can usually save my Linux and Unix servers from a reboot and therefore downtime if there's a memory leak in a application or some such but on Windows explorer can be pretty unresponsive if the server is in a spin.

---

