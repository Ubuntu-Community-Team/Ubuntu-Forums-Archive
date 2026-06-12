---
title: "Bash script for VBoxManage"
date: 2017-08-29
forum: Programming Talk
---

### Post by shakingtux on 2017-08-29
Hi all!
I want to create a bash script with my friends from university, which will help with creation and management virtualbox virtual machines from CLI. We want it to be interactive with user, but also work with parameters so if there is a need user can use it in other programs.  Do you have any advice how to work with this project? What options should be included when creating vm with CLI? When we will make something more, I will put here link to repository.

---

### Post by TheFu on 2017-08-29
Welcome to the forums.

Use vagrant - or better, use kvm (not virtualbox) and just script virt-install.

You can write a bash script if you like - just use multiple calls to vboxmanage, but I wouldn't.

But vagrant is the normal way software devs do this in the real world.  If they are server admins, they'd use something like kickstart or cobbler to load the base OS, followed by a devops tool like ansible, puppet, chef, cfengine, rexify, Salt-stack ... to configure everything going forward.

---

### Post by shakingtux on 2017-08-30
Thanks for reply ;)
I will read something about kvm and vagrant.It may help me in my work in the near future.
 I think we will do this script just for fun and bash practice :)
Maybe it will somehow help younger students on few linux subjects e.g. computer networks when we need to create one, and there isn't enough equipment so we work on virtual machines :)

---

### Post by TheFu on 2017-08-30
In the real world, using VMs is a way of life.  They are the solution deployed BY DEFAULT and it has been that way for over a decade. Deploying on physical systems is the exception.

---

