---
title: "FreeNAS to Ubuntu"
date: 2018-11-27
forum: New to Ubuntu
---

### Post by chris230291 on 2018-11-27
Hi guys. Been running FreNAS for years and looking at switching to Ubuntu.

I have been playing with ZFS on Ubuntu and I have some questions. There is an option to have ZFS on root, do I want that? Whats the difference? I will want to be shareing it. I will also want docker containers to have access (a better docker, better driver/hardware support is the main reason I want to switch to Ubuntu).

I have tried setting up a samba share... Follwed a bunch of tutorials and tried GUI setup utilities. No matter what I try I am either able to share the dir completely open (dont want that), or I am not able to log in from windows (I am able to log into the share on the same Ubuntu machine I created the share on though). Anyone know why I am having problems? Maybe you can link me to instructions that should 100% work?

Thanks,
Chris

---

### Post by TheFu on 2018-11-28
ZFS is only supported for data LVs/partitions on Ubuntu. Don't use it for the OS.

CIFS is the protocol that Windows uses for file sharing. There are multiple versions of that protocol, so the version your Samba server needs to support will depend on the release of Windows being run.  Older CIFS protocols have some really bad authentication security, so using the newest version possible is best.

For Samba, forget the GUI tools.  They cause more problems then they solve.  That's a common thing with all Unix service management - forget the GUI. Stick with the config files and CLI commands.

Ubuntu makes help/how-to guides which cover non-trivial setups.  Always start with these.  If they are too complicated, which can easily happen, read through it and post the parts and the URL you don't understand.  The guides have to handle all sorts of situations that don't apply to you, so it comes down to learning what is and isn't important.  Only experience and time will fill in those gaps.

When searching for help on any topic related to ubuntu, prefer domains that end with ubuntu.com ... so help.ubuntu.com and wiki.ubuntu.com should be the main sources.  The problem with google is that you can't tell when you are new if the person posting a guide actually knows more than you or not.  People really new to Linux get excited and post solutions that worked for them, but there are lots and lots of other setups where those answers would do harm.  Reputable sources which target the release you are running are important.

When asking for help, we need facts. "It doesn't work" isn't exactly useful.  Trying to help someone shouldn't be like pulling teeth to get information.  But it is hard to know what information to provide when you are new.   Start with explaining your network setup, can the systems 'ping' each other by name?  Then posting the output from **testparm** on the samba server will show the real configuration.  Please use 'code tags' whenever posting commands and output. Thing line up better and are easier to read that way.  You'll get more eyes looking at the problem too.

We always need to know the release of Ubuntu.  Configuration of samba, network configuration methods and even how to start and stop daemons has changed over the different releases. Don't make anyone guess.  The /etc/lsb-release file has the answer. Tell us.

Using FreeNAS from the GUI-only is very different from using an Ubuntu Server setup. What's your skill level in a Liunx shell?

---

