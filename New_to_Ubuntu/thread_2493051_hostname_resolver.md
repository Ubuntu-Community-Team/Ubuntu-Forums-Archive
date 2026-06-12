---
title: "hostname resolver"
date: 2023-12-01
forum: New to Ubuntu
---

### Post by biojo on 2023-12-01
I have just installed ubuntu 22.04, normally in windows i can ping my NAS servers name, but in ubuntu i can only do the IP address, I presume i need to install or enable something?

---

### Post by TheFu on 2023-12-01
There are 3 different methods to handle name resolution.

a) /etc/hosts - it is a simple text file with the IPs and names for different systems.  This is how the internet started in the 1970s.

b) DNS - this is what the internet and nearly all corporate networks use. It scales to the entire world.  You can run a DNS inside your LAN, if you like. Some routers will do this and just need to be configured with a mapping between the hostname+domainname and the IP addresses for each system.  A pi-hole is a popular way to get both DNS ad-blocking AND have a local DNS on a LAN.

c) mDNS - this is relatively new.  It is also called ZeroConf. In Ubuntu (and most Linux desktops), it is provided by the "avahi" service.  Ubuntu desktops should have this pre-installed. Ubuntu servers do not.  Servers are expected to use DNS.  In avahi, the name is {hostname}.local .... so whatever the NAS hostname is, add ".local" and see if that works.  Home video streaming devices will often announce themselves through mDNS ... just add the .local to the end of the hostname.

The order that these things are checked is controlled by the /etc/nsswitch.conf file.  I've listed the order in the typical way with my a, b, c above.

Sometimes, in recent ubuntu, the name resolution provided by DNS goes through systemd-resolved, which is a local caching DNS for desktops.  There seem to be lots of issues with it, so many people will swap it out for some other tool or just directly point their desktops at normal DNS servers on their LAN or on the internet.  That's up to you.

---

### Post by biojo on 2023-12-02
my router does the DNS thats running OpenWRT, this runs adgaurd which also shows all the items on networks names

All my other systems on linux can ping host names and they run debian of some variety

So how do I get Ubuntu to use them?

---

### Post by TheFu on 2023-12-02
What's different between the working and non-working systems?  You'll need to look at the relevant config files and fix it.

Ubuntu should "just work", so something is wrong, somewhere.  What needs to be done, depends on how things are setup, which hasn't been answered.

There is a network troubleshooter script somewhere. It should gather all sorts of information and put it into a single file. Use that if you don't know what is needed.

---

### Post by biojo on 2023-12-03
the other systems are 

3 x OSMC, a kodi box that runs debian, again everything comes pre installed to watch, record tv etc

just checked the other system running ubuntu and that doesnt work either, ubuntu was installed on this last year, this system was installed this week

---

### Post by TheFu on 2023-12-03
Sorry, I'm not being clear.  There are config files that control DNS and how name resolution is performed. These are used by all Linux systems (nearly), so you should compare the working from the non-working setups.  My first post specified some exact filenames.  Compare those.

If you need help, you'll need to post those files here.  Put them inside forum 'code-tags' so we don't have to struggle to help you.

BTW, I use OSMC (have for about 5 yrs) and those systems have no problem with name resolution ... but OSMC isn't Ubuntu. It is a light debian with a non-standard network setup controlled by "conman".

---

### Post by biojo on 2023-12-03
I asked someone on the OSMC forum, turned out I changed a setting on router years ago so the old NAS could would with windows, so renabled that and its all working :)

---

### Post by TheFu on 2023-12-03
> **biojo said:**
> I asked someone on the OSMC forum, turned out I changed a setting on router years ago so the old NAS could would with windows, so renabled that and its all working :)

a) glad you figured it out.

b) please mark this thread as "SOLVED" using the thread tools button, to help the community - both those seeking answers and those looking to help. Time is precious, help others not waste it.

c) Actually post what the fix was so someone else can follow it.   Even a link to the forum post elsewhere would be helpful.  Right now, I'd have to guess that you enabled netbios-to-DNS translations (assuming that even exists).  Help others, please.

---

### Post by biojo on 2023-12-03
this fix was to have 

Local domain was set to blank "", so this was set to ".lan"

---

### Post by TheFu on 2023-12-04
.lan?  I like it, but if you set it to .local, then the default avahi settings will like it more.  You may need to find the avahid.conf file (if it has one) and set it to look at ".lan" TLDs.
Also, you might want to ensure the /etc/resolv.conf has a *search* of .lan and/or .local to help your sanity.  YMMV, of course.

I remove avahi from my systems and have a primary/secondary DNS on the LAN, so I use the search in the resolv.conf to specify my internal LAN TLD and my public WAN TLD. Definitely helps my sanity ... well, perhaps just a little.

---

