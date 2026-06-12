---
title: "Bash Expect - Cisco Devices"
date: 2014-12-19
forum: Programming Talk
---

### Post by Dominic--- on 2014-12-19
Hi all,

I am struggling with the following: I have a script which can login to to multiple switches and routers.
However, for a new development I need to login in some switches, and execute on all switches different commands (bases on each switch)

Is this relative easy to create? Cannot find any tutorials for such a thing and don't know how to program this with Expect.
Hope somone can point me in the right direction with some documentenation/tutorial.

Thanks

Grtz

---

### Post by TheFu on 2014-12-20
Most people are going with a DevOps tool to manage switches if they don't go commercial.  OTOH, expect has been around for a very long time - there are books written about it with thousands of examples.  Honestly, I haven't used expect since 1999, so I can't really help, but I can't imagine it being too hard.  I'd look at using Ansible first - that's a more current tool, but I can't say whether it will work for switches easily or not. Sorry.

Google found this: [http://www.jedelman.com/home/ansible-for-networking](http://www.jedelman.com/home/ansible-for-networking)

---

