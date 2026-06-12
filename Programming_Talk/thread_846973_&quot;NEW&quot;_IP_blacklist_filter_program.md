---
title: "&quot;NEW&quot; IP blacklist filter program"
date: 2008-07-02
forum: Programming Talk
---

### Post by HunterThomson on 2008-07-02
So,

I'm planing on writting a little script this weekend to filter ip balacklists through iptables. What it will do is:

Download ipblacklists form bluetrack.co.uk

Cut everthing to the right of the : i.e. the ip range

Compare the iprange on the fist line to yesterdays ip range list if it dosn't mach any then input into $BlackIP and add to the bottom of the list.

iptables -I INPUT -m iprange --src-range $BlackIP -j DROP

Then go to the next line and so on until there is nothing on the next line.

The end result is that no mico$oft IP will ever get a packet back from my box.

MY question is.... WHY is there not a program like this alredy out and about? This seems simple enugh to me? Why do all the other programs use queue??? Why not just shut them down for good? Is this just a vary bad way to do it i.e. will it slow down my box or something... I don't see why?

---

