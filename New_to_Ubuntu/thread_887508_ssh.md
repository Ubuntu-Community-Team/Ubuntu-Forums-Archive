---
title: "ssh"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ub007 on 2008-08-12
Hi,

I'm trying to run python programs on 5 nodes from a single head node.I thought this could be useful-The Cluster Command and Control (C3) tool suite-

[http://www.csm.ornl.gov/torc/C3/index.html](http://www.csm.ornl.gov/torc/C3/index.html)

It uses ssh,and when i give a command using the 'cexec' module in c3 suite,

$cexec mkdir /opt ( should create opt dir on all the 5 nodes)
instead i get permission denied.

I suspect this could be a problem with ssh.But ssh works fine when i attempt to connect using $ssh [email]david@node1.surr.ac.uk[/email](i have set up keys to avoid password login)

When i run cexec,it works find with the local head node,but on the other nodes-it tried to attempt connection and then says
permission denied(public key)

what am i missing here?Plz help.Thanks in advance....Or is there any way i could run batch commands on many machines rather than ssh-ing into each one manually...

Cheers
David

---

### Post by Cypher on 2008-08-12
Is "cexec" using your username to login to the other nodes? The SSH keys you setup are specific to your username..so if it was using something else, you would get an error..

---

### Post by ub007 on 2008-08-13
Yep,guess your right and thats the reason i'm getting the error...its pulling up the username of my localhost.i'm trying to tweak the code,but havent been successful so far.its a shame cz the tool looks brilliant,only if i could figure out a way to use it...lol

Cheers,thanks mate

---

