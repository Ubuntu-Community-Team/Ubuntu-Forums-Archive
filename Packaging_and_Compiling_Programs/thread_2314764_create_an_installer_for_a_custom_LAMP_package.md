---
title: "create an installer for a custom LAMP package"
date: 2016-02-23
forum: Packaging and Compiling Programs
---

### Post by alain.roger on 2016-02-23
Hi,

i would like to create my own LAMP package that should be able to install itself.
I was thinking to use an installer for that.

is there something like that ?
i'm looking for something that propose a GUI with some fields and button to allow end use to interact with package.

Any suggestion would be appreciated.

thx

---

### Post by ian-weisser on 2016-02-23
Which part do you need help with: The GUI? The packages? The dbus interface to aptdaemon?

Design question: Why does a user need a different GUI beyond the existing Software Center and debconf? Are your users likely to be installing LAMP stacks frequently with different choices?

---

### Post by alain.roger on 2016-02-24
in fact with everything, i'm trying to learn to do something nice and interactive for future users.

Basically i'm not satisfied by those LAMP stacks available AMPPS, XAMP, Bitnami...there are still some missing "bricks" and i would like to build one installer for eveyrthing where i would be able to select what to install and especially how to update it without losing any previous setting. 

As i have this need, i guess several other people have such need too.

Moreover it should allow people to easily synchronize their LAMP stack among computers... so they could shift from laptop to desktop just synchronizing it... so it should avoid on each computer to reinstall and manually setup each computer on the same level...

---

### Post by ian-weisser on 2016-02-24
Perhaps you could expand on those 'missing bricks' and setup issues that you want to overcome.
I'm not a big, regular LAMP user...but the times I have set up a stack, I don't recall it being terribly difficult or confusing. So more detail may help us understand.

Be aware that LAMP stacks generally don't require displays, and often run headless. Are you sure you need a GUI?
Users who frequently spin up duplicate LAMP stacks (and other software) are encouraged to look into JuJu and similar tools.
Users need precise duplication and snapshotting of a system, for migration or testing or other reasons, are encouraged to look into LXC Containers or Virtual Machines. 

You already know that you will need to use shell to pass commands to apt (or dbus to pass instructions to aptdaemon), so you might create a VM to safely play with those and figure out which of their features you want to use for your project.

---

