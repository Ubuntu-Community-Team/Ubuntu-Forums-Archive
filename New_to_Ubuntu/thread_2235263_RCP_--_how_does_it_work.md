---
title: "RCP -- how does it work?"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by Mk32 on 2014-07-19
I'm trying to figure out the requirements for rcp. Does it lean on telnet login? rlogin? rsh? Or is it a self-contained shell program? Is it a NFS client? 

I'm aware of the vulnerability of telnet, rlogin, rsh and rcp. It's that all the "man pages" for rcp don't say what it requires for it to work properly -- i.e. if it needs telnet port open. 

I do know that scp uses the SSH framework, but nobody says what rcp uses.

---

### Post by tgalati4 on 2014-07-19
You can't use rcp in Ubuntu because it points to scp:

> 
tgalati4@Mint14-Extensa ~ $ which scp
/usr/bin/scp
tgalati4@Mint14-Extensa ~ $ which rcp
/usr/bin/rcp
tgalati4@Mint14-Extensa ~ $ ls -la /usr/bin/rcp
lrwxrwxrwx 1 root root 21 Dec 28  2012 /usr/bin/rcp -> /etc/alternatives/rcp
tgalati4@Mint14-Extensa ~ $ ls -la /etc/alternatives/rcp
lrwxrwxrwx 1 root root 12 Dec 28  2012 /etc/alternatives/rcp -> /usr/bin/scp


I presume this redirection is done to keep old scripts working, but enforce a more secure framework.

In other/older linux distros, I believe rcp relied on the rlogin framework and port--it's been a really long time since I used it in Unix.  Here's a tidbit:

[http://linuxaria.com/howto/8-cool-ways-to-use-scp](http://linuxaria.com/howto/8-cool-ways-to-use-scp)

So without an RFC, *rcp* could be implemented in different ways by different distros.  You would have to read the source code of BSD's rcp to see what the comments say.

---

### Post by Mk32 on 2014-07-20
The first thing I found out in 9.10 was that it did as you said, rcp is just a symbolic link to scp. So it doesn't work. 

But the question still stands: does rcp use telnet login? rlogin method? ??? I think scp uses SSH for login, then the rest is handled without SSH. I'm just trying to find out what are the requirements to use it. Everywhere else on the net they all just assume it's already included.

---

### Post by tgalati4 on 2014-07-21
The answer depends on the operating system since there is no standard Request for Comments (RFC) for implementation of rcp.  Without a standard, different distros can use different frameworks to provide rcp functionality.  So the answer in Ubuntu is that rcp uses scp which uses ssh for authentication and encryption for transfers.

Final answer.

---

