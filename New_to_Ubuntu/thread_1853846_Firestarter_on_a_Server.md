---
title: "Firestarter on a Server"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by RobDWaller on 2011-10-03
Hi,

I am new to running an ubuntu server -- or any server for that matter. I have been reading a lot about securing my server, with one obvious requirement being a firewall.

I also read that Firestarter was a good firewall manager and could be run on a server. 

So I installed it, however I have no idea how to manage it on my server. There seems to be very little documentation on this subject. For example,how do I manage it? Via terminal, or can I access the GUI via the web on my server?

I would really appreciate some advice on this topic, and any suggestions as to whether I should be running something else.

---

### Post by Paqman on 2011-10-03
Firestarter is an old obsolete package. It probably still works ok, but Ubuntu comes with a better system preinstalled these days. Check out [ufw]("https://help.ubuntu.com/community/UFW").

---

### Post by haqking on 2011-10-03
> **RobDWaller said:**
> Hi,

I am new to running an ubuntu server -- or any server for that matter. I have been reading a lot about securing my server, with one obvious requirement being a firewall.

I also read that Firestarter was a good firewall manager and could be run on a server. 

So I installed it, however I have no idea how to manage it on my server. There seems to be very little documentation on this subject. For example,how do I manage it? Via terminal, or can I access the GUI via the web on my server?

I would really appreciate some advice on this topic, and any suggestions as to whether I should be running something else.

IPTables/Netfilter is the built in firewall in the Linux Kernel, firestarter.UFW/GUFW etc are merely interfaces to manipulate it.

Firestarter itself as mentioned is out of date and alot of bugs reported on Launchpad.

If you are running a server then i suggest using IPTables CLI directly.

---

### Post by HermanAB on 2011-10-03
Actually, a firewall, is not an obvious requirement on a server...

On a server, you should only run the services you absolutely have to run and if that is the case, then a firewall will do nothing and is quite redundant.

On my servers, I run only one iptables rule, to rate limit new connections.  That protects against DOS and brute force attacks.

---

### Post by bodhi.zazen on 2011-10-03
> **RobDWaller said:**
> I also read that Firestarter was a good firewall manager and could be run on a server.

Then you read outdated and a poor source of information.

ufw is a command line tool and has been the default tool to manage your firewall for several years.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Or learn iptables directly

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

It is easy to manage a firewall if you understand basic networking and what it is you expect a firewall to do for you.

The problems with firestarter are:

1. It requires X, and IMO servers should not be running X.

2. It is no longer supported. Sure it is in the repos, but it no longer gets bug fixes, so if you have a problem you would need to write the code to patch it yourself. Not such a good option.

3. It conflicts with ufw.

4. It sounds as if you are installing it "because", without understanding servers or firewalls, always a bad choice when running a server.

---

### Post by Dangertux on 2011-10-03
> **HermanAB said:**
> Actually, a firewall, is not an obvious requirement on a server...


I agree with this, a firewall in most senses for a server is somewhat pointless, if you are doing your job in other security related areas a firewall should be pointless.

That being said, a 0 day will still own you, and a firewall can help mitigate the effects of this somewhat (stopping bind/reverse shells etc), as well so can things like Apparmor and SELinux.

I also agree with those who stated use iptables directly ; it's a good learning experience and makes it much easier to manage more complicated firewalls in my opinion because you have more control over exactly how packets are handled.

---

