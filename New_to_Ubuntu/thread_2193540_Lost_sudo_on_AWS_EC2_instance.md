---
title: "Lost sudo on AWS EC2 instance"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by brunodombidau on 2013-12-13
[COLOR=#000000][FONT=verdana]I have an AWS EC2 instance. I can login just fine, but neither "su" nor "sudo" work now (they worked fine previously).

[/FONT][/COLOR]> sudo su
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

It was my fault, I messed up while using *chown*, the problem is: I can't boot in recovery mode (or I don't know how to do this on AWS).

Tried different solutions I found on the forums and Google but nothing helped.

Any ideas on how to fix that?

---

### Post by Bashing-om on 2013-12-13
brunodombidau; Hi !

See if this tutorial is relevant to your issue.
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Habitual on 2013-12-13
or try ```
su - root
```

---

### Post by sandyd on 2013-12-13
> **brunodombidau said:**
> [COLOR=#000000][FONT=verdana]I have an AWS EC2 instance. I can login just fine, but neither "su" nor "sudo" work now (they worked fine previously).

[/FONT][/COLOR]

It was my fault, I messed up while using *chown*, the problem is: I can't boot in recovery mode (or I don't know how to do this on AWS).

Tried different solutions I found on the forums and Google but nothing helped.

Any ideas on how to fix that?

Shut down your current instance (make sure you are _NOT_ removing the instance, but shutting it down)
Create another instance, and detatch the EBS volume from the original instance. Attach that EBS volume to the new instance, and mount it.
Fix the permissions there, and shut down the new instance.
Attach the EBS volume back to the old instance, and you should be fine

---

