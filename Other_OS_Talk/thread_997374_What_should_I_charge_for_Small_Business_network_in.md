---
title: "What should I charge for Small Business network install"
date: 2008-11-29
forum: Other OS Talk
---

### Post by rjs82vette on 2008-11-29
OK guys, I work for a medium size company and one of the previous employee's asked me to setup a network for his small business.

The problem is I haven't done any type of consulting work and really don't know what reasonable amount I should charge him.

This is in the Washington DC area.

What I did was install and configure the following

(1) 
 -Linux server for security, firewall, VPN, Anti-spam, Anti-virus, DHCP, DNS
 -windows 2003 SBS with exchange,users folders, shared folder, active Dir, print server, file server, created user account.
 -1 network color laser jet printer
 -5 desktops running windows XP, anti-virus, flash, java, office small business edition, defender, mapped user & shared folders, mapped printer to all user accounts.

(2) 
in the future he is going to want to have the ability for 50 remote employees to access folders and email(via pop).

(3) on-site and remote/phone support

what would the going rate be for initial installation and what would be a fair hourly rate for the support?

I don't want overcharge him but I really don't want to work for free either as I already have a full time job and this cuts into Miller Time.

Any suggestions would be appreciated

---

### Post by disturbed1 on 2008-11-30
Friend? $20/hour.

Not so much a friend? $40-$150/hour depending on your expertise in the area.

Some people charge flat rates for software install. OS Reload/Install with security $50-$120. Each additional app $10-$20.

7x$80 (OS/Security installs)
7x$25 (Additional software setups)
1x$25 (Networked Printer)
1x$100 (User credential and access rights management)
-----------
$860. Close to my first guesstimate of $900-$1000 for this job. Adjust to the going rate in your area. The easiest way to judge pricing, give the competition a call to see what they charge.

I've done similar jobs for local churches. 1 Linux server, 10 user desktops, 2 printers, remote access (User and Admin setups). Minus the cost of the hardware I provide, the installation cost clocks in around $800.

You can do support contracts (monthly, quarterly, bi-yearly, yearly) with discounts for more months. Or one time support costs. Remote should be cheaper than on site. **BE SURE TO INCLUDE HOURS OF OPERATION** I've forgotten that clause once or twice before. Nothing like having to do a support trip at 2 in the morning ;)

---

### Post by HermanAB on 2008-12-01
One thing I can recommend is to install a 'quadruple click' reverse VNC client on each machine for remote support.  Google for 'one click VNC' and 'Ultra VNC Single Click' - there are others too.  That will save you tons of petrol.

Cheers,

Herman

---

### Post by rjs82vette on 2008-12-01
Thanks for the info, I am going to look into the "one click vnc", looks good and open source... I love open source......

I'm looking around 150.00 an hr, here in the DC area.....

---

### Post by disturbed1 on 2008-12-02
VNC is OK, not the greatest though, many cases of screen redraw issues, running 5 or more seesions at a time falls flat. In all honesty, if they are XP-Pro installs, hard to beat RDP (RDP/TS client for Linux is available). For Linux support, ssh works best. Don't forget your firewall rules for what ever you choose.

My choice though, I use Go To Assist (not free, nor open source) inside a virtualized Windows environment. Being able to reboot into safe mode remotely is a life saver. I can not count how much time was wasted attempting to have someone boot into safe mode on their own. You'd be surprised just how ...um... just how some people are ;). I've ran 7 or more concurrent GTA sessions at a time without issues.

---

