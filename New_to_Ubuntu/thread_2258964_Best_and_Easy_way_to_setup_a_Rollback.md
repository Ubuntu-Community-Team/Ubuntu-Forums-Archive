---
title: "Best and Easy way to setup a Rollback"
date: 2014-12-31
forum: New to Ubuntu
---

### Post by amb1s12 on 2014-12-31
I'm trying for the last few months to move to linux from MAC OS and in few times I had to reinstall unbuntu because of something that I did wrong. I would like to know if there an easy way to do that a system backup that if I mess up the OS, I can easly go back and type few commands and I'm good. I don't want to reinstall the OS again, I would rather just have like either an internal extra HD or external HD handling this. Thanks in advance.

---

### Post by raja.genupula on 2015-01-01
if we dont know whats wrong you did and stuck we can't help you lad.

---

### Post by MrSteve on 2015-01-01
you should have daja dup backup installed 
its very similar to time machine on OSX just not as pretty ...

also it maybe worth while next time setting a separate  / (root) partition of about 20GB 
then a /swap partition then rest of the HDD can then be used for the /home partition

this way if you have to re-install you only have to format the / (root) partition leaving the /swap and /home partitions intact (do not format) so all data on the home partition is available after the re-install
just make sure that when doing this you insert the same details such as user name and password at set up as you did the previous time ...

---

### Post by grahammechanical on 2015-01-01
> [COLOR=#000000]I can easly go back and type few commands and I'm good.[/COLOR]

We all want that! :)

But it is never that easy or simple. There are file systems in Linux such as the B-Tree file system (BTRFS) that will let us take a "snapshot" of the system and then revert back to the way the OS was when the snapshot was taken. But btrfs is still under development and during my experiments with it I could not find a utility with a graphical user interface (GUI) that made the management of snapshots (creating, deleting and rolling back) easy. Everything has to be done through the command line. 

Ubuntu has a recovery option that we access through the Advance Options for Ubuntu sub-menu. If we have installed Ubuntu on btrfs and created a snapshot of the system, then the Recovery menu will present us with an additional option. That of "apt-snapshots - Revert to old snapshot and reboot."

It works. And if we know what we are doing we can even revert an upgrade to a newer version of Ubuntu back to the previous installed version. I would not attempt to explain how to work with btrfs to an experienced user let alone a new user. It is something we learn through our own experience of making mistakes.

Regards.

---

