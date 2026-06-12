---
title: "How do I create different operational settings per user?"
date: 2020-05-21
forum: New to Ubuntu
---

### Post by holiday1012 on 2020-05-21
I'm gaining experience with Linux distros and am also trying to introduce it to my friends. I know some families that are looking for a computer/OS for the whole household. I was wondering how one could set up a new user account that has various restrictions aside from admin privileges. Essentially full privilege/access to adult users and restrictions for children accounts on the computer. For example kids on their individual accounts cannot open certain files, run certain programs, cannot go to certain websites, etc. The restrictions would be tied to the account and customized. Is there a program that works as a nanny not just for web browsing but also able to do other system restrictions?

---

### Post by TheFu on 2020-05-21
Everything in Unix is permissions and group based.  Learn about those to get some ideas.  These are system-wide using normal file and directory permissions. Master those for controlling local access to stuff.

Admin stuff on Ubuntu is also controlled by a group, sudo.  Members of that group can administrate the system. Don't put the kids into the sudo group and they cannot admin the box.

There are system settings and user settings in Ubuntu, just like all Unix-like systems.  In general, system-wide settings are in /etc/.  All user specific settings are stored in the userid's HOME directory.

As for access to different network resources, what you've described is possible but non-trivial to setup on a single machine.  Normally the way I'd limit access by accounts would be to use a proxy server that performs the most restrictive filtering by default (for kids), then have the adults authenticate to the proxy server for additional access.  Depending on the ages involved, some simple methods may work well enough, like having whitelists and blocking all others.  The real issue is that almost all network configurations are system-wide, not per-user.  There are ways to have firewall rules per group. Those always seemed really ugly to me.

For small kids, you could just clear out the menu system and only put specific programs into it.  The other programs would still be on the box, but not in the menu.  A 10 yr old with interest would learn to launch those programs from a terminal, but most younger kids would not.  That may be all the restrictions needed.  IDK.

When I say using a different system, that could just be another system running inside a container or VM on the same machine.  For example, I'm running a pi-hole DNS server inside an LXD container on an Ubuntu system. It starts automatically when the main system starts. It is fairly lite.  I suspect running a squid proxy server in the same manner would easily be possible.

I don't really understand trying to restrict access to programs. Why?  After all, programs don't magically provide access to data files used by other users on the system.  Unix is multi-user from the ground up, since about 1970.  So is Linux.  Files owned by userA only have the access for userB, userC, userD that userA decides they should have.  Unix isn't Windows.

To learn more about users, groups, and managing them, here's a reference for most flavors of Linux: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  I've never been happy using any GUI programs to manage users. Always seemed too slow and didn't have all the capabilities needed.  Heck, most of the time, I'll just go edit the files directly on non-LDAP userid systems.  Takes just a few seconds that way and I don't need to look up commands or funky options to adduser/useradd, moduser/usermod, and group commands. Life can be easier when you understand the relationships of those files in /etc/.

---

### Post by holiday1012 on 2020-05-21
Hey thanks.

Perhaps it would be simpler to have a seperate computer for the kids with a particular linux distribution that is kid friendly. A little Raspberry Pi system. Also like the idea of another system running in a virtual machine.

---

### Post by TheFu on 2020-05-21
I don't understand kid-friendly.  All computers are kid-friendly. It is the adults that have troubles. ;)  The kids know that they can try anything and with normal user accounts, there isn't much damage they can do to the system.  It is only their files they can harm, not any other user's files.   

Different GUIs can be run based on the user's login.

Sure a R-pi v4 can be used for a low-end desktop, but if there's a family computer in the family room for everyone to share, I'm not sure I see the point.  

By about age 11-12, kids should have the same access to the internet as adults and in a family, both would want content-based filters like all libraries and schools use.  There's a proxy system ... Dan's Guardian ... I think that's the name. It can do content filtering.  

But squid proxy server can filter content too.  Put squid into an LXD container, setup the content filters and point all the desktops/tablets/phones to use that for a LAN-wide proxy.  It won't be point-n-click, but nothing is on Linux.

Between DNS and Squid, that's about all the filtering anyone needs.  For greater protection like enterprise companies use, block all devices except the squid proxy from internet access.  Setting up a transparent proxy makes that really easy for end users.

There are addons for some routers that do this too, but those routers usually aren't noob-friendly.  Something like pfSense, OPNsense supports having squid and content filtering on the router.  These require more expertise, however.  [https://docs.opnsense.org/manual/how-tos/proxywebfilter.html](https://docs.opnsense.org/manual/how-tos/proxywebfilter.html)
[https://docs.opnsense.org/manual/how-tos/proxytransparent.html](https://docs.opnsense.org/manual/how-tos/proxytransparent.html)
[https://openschoolsolutions.org/pfsense-web-filter-filter-https-squidguard/](https://openschoolsolutions.org/pfsense-web-filter-filter-https-squidguard/)

How deep is your network knowledge?  The less you have, the more important using an all-in-one device, separate from the computer is.

On my blog, there's an article from 2011 about a kid safety checklist. Quickly, that turned into internet filtering with some ideas in the comments.  [https://blog.jdpfu.com/2011/06/10/kid-safety-checklist](https://blog.jdpfu.com/2011/06/10/kid-safety-checklist)

---

### Post by CatKiller on 2020-05-21
> **TheFu said:**
> I don't understand kid-friendly.  All computers are kid-friendly. It is the adults that have troubles. ;) 

Exactly. My little one's been gaming (and drawing, and writing, and listening to music, and...) on Linux since he was 2. When he's old enough (he's 4 now) he'll get his own account on the computers in the house, with normal-user privileges, so that he can make his computing environment his own rather than his mum's. When he's older still he'll likely get his own computer, and older than that he can do his own admin. At some point he'll likely have learned enough and fiddled enough that he might manage to break something, in which case he'll be old enough to learn how to restore from backups.

Unix-like OSes, such as Linux, are multi-user from the start. Having some users being able to access/run things, and others not, just *is*.

---

### Post by holiday1012 on 2020-05-22
Well, perhaps I'm overthinking the situation. I was thinking for preteens. If anything something simple. I suppose some basic restrictions are easy enough to implement. 

Been looking at distros aimed at kids as well, like Sugar on a Stick.

---

