---
title: "newbie realtek r8168 problem"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by swedski on 2008-08-15
Hello,
Totally new to Ubuntu.  Bought a book and am trying to figure things out.  I have a strange problem, so here it is:
My internet connection works great on all my computer UNTIL I start my Ubuntu connection and try to download something with Transmission.  Suddenly my 24MB down 1 up connection slows to 0.05 down 0.025 up.  I have definitely narrowed it down to my Ubuntu machine once Transmission bittorrent starts.  What do I do??

SYS stats ASrock ALiveNF5-eSATA2+ R3.0
4gb memory
500gb hd
meaning I have a realtek r8111b pci express gigabit network card which according to all forums I have read (and my Device manager)running on the r8169.ko drivers which cause a bug.( I have other ??? marks in my device manager but that is for another thread)  


I am not positive this is the cause like I said I turn transmission on and Bang!!! my entire internet connection slows down, shut it off and speed picks up.
June I had a Linksys wrt54g with dd-wrt firmware network was fine. Installed Ubuntu in July network slowed but didn't put 2 + 2 together.  Got a Netgear wrn854t hade similar problem but because its refurbished couldn't get support so went and got a D-Link Dir-655 (my cable company wants you to use D-Link)  Point being all three routers had the exact same problem.  


I need help 
1) removing the old drivers 
2) installing the new correct ones.
every time I try I get errors

I am also so new that I do not have a good grip on the various commands, root, bash, etc.  I have a book but...

Is there anyone who can talk me through this???
I am interested in seeing if this is the problem and learn how to update drivers etc.

---

### Post by Bachstelze on 2008-08-15
You mean your connection speed is normal in Ubuntu until you start Transmission? Have you tried another BitTorrent client?

---

### Post by swedski on 2008-08-16
I was thinking of that but then I saw the bug and realtek.
I will try a new one today.
Thanx

---

### Post by swedski on 2008-08-16
Gezz what an idiot I am.  Put Ktorrent in and my system seems fine.
I'll give it as day but no instant slowdown.

Still would be nice to know how to get the right drivers for the netcard but I will take a working system anytime
Thanx Mark

---

