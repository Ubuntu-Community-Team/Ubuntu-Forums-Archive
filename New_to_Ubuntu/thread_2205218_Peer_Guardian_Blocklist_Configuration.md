---
title: "Peer Guardian Blocklist Configuration"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by mlnease on 2014-02-12
Hello,  I've been using Ipblock (for P2P security) for several years and have been perfectly happy with it.  Recently though, its lists have stopped loading and I've been unable to fix it.  So I've just installed Peerguardian Linux version 2.2.4 (from the PPA).   The installation went perfectly--but when 'on', PGL blocks all internet  access (as per the warning at [http://handytutorial.com/install-peerguardian-in-ubuntu-using-ppa/](http://handytutorial.com/install-peerguardian-in-ubuntu-using-ppa/)).    I assume this is because of the default blocklists loaded with the  installation but have no idea how to select blocklists that will protect  P2P without blocking internet access.    I hope this post isn't redundant.  I've Ixquicked this fairly  extensively and searched Ubuntu Forums but to no avail--any advice would  be greatly appreciated.    Thanks in advance.  

Edit:  I've had no responses to this post but I've found what I think is the solution (or may be the solutions) to my problem in the FAQs at [http://sourceforge.net/p/peerguardian/wiki/pgl-FAQ/](http://sourceforge.net/p/peerguardian/wiki/pgl-FAQ/).  

I've been adding and subtracting blocklists and opening and refreshing links I often use to make sure they still work.  Trial and error, hit or miss;  I think I've successfully whitelisted my IP address (essential, I *guess?*) and am, I hope on the way to having resolved this issue.  So--I really have no idea how safe I am from P2P snoops (then again, I was never really sure about Ipblock, either) but I guess I'll tentatively mark this thread SOLVED.  If anyone with similar issues has any advice, I'd be grateful if you'd contact me off-list--thanks.

Finally, thanks also to [bbergstrand]("http://sourceforge.net/u/bbergstrand/"),                                           [jre-phoenix]("http://sourceforge.net/u/jre-phoenix/"), and                                           [phrostbyte]("http://sourceforge.net/u/phrostbyte/") for this impressive *free*  software.

---

### Post by jre on 2014-05-20
Be careful with whitelisting your own IP. This may result in a complete whitelist of all traffic, because everything either starts (OUTPUT), ends (INPUT) or moves by (FORWARD) your IP address.

Just watch the logfile, if there are still blocks you at least haven't done it wrong completely ;)
Also try "pglcmd test" for a basic test if pgl works.
Of course with custom whitelistings I can't tell you if pgl still does what you want. Try to stick to a minimum.

General rules:
1. use only blocklists you want
2. in most cases only use *outgoing* IP whitelistings.

---

