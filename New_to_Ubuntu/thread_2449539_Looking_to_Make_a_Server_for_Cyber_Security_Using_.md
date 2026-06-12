---
title: "Looking to Make a Server for Cyber Security Using Ubuntu or Any Other Linux"
date: 2020-08-28
forum: New to Ubuntu
---

### Post by exstrad on 2020-08-28
I am very new to Linux and the different types that you can use and need some recommendations on what parts to get for a server that can be used for Cyber Security for my home. What is some advice I can get for setting and building a server and how to go about setting up the whole entire thing?

---

### Post by MartyBuntu on 2020-08-28
Why not try a server installation as a virtual machine? You can configure it and learn the ins and outs without worrying about breaking anything crucial.

---

### Post by TheFu on 2020-08-28
> **exstrad said:**
> I am very new to Linux and the different types that you can use and need some recommendations on what parts to get for a server that can be used for Cyber Security for my home. What is some advice I can get for setting and building a server and how to go about setting up the whole entire thing?

Maybe need to be much more specific to get good recommendations. "Cyber securty" is like saying I want to work with boats, but with no other information. Fishing? sailing? water sports? shipping? racing? white water rafting? Kayaking? lake or oceans? Just depends.

If you want a secure home, don't have servers.  Have well-maintained routers with strict firewall settings that block almost everything outbound and don't allow anything inbound.

If you are interested in becoming a data security or network security professional, seek out a local DefCon group (google that), attend the meetings, hang out with the people there, listen, ask questions, learn.  My preferred DefCon group has monthly virtual meetings since COVID, but there are 3 different groups in the metro area. That doesn't count the groups that different Universities have too.  A few months ago, one of the long-time security pros gave a show-and-tell about his "lab" setup.  He'd come into an old Dell R-server with 256GB of RAM, 32 Cores, and about 60 TB of disk.  

OTOH, most people either use a laptop or fairly modest desktop capable of running 5-20 VMs using Xen-NG or Proxmox or KVM or virtualbox or ESXi. These "lab" systems are on private, air-gapped, networks, since they play with viruses and attacks. Wouldn't be good to have your regular home networked hacked by accident. Many of the very experienced guys are fully trained networking gurus, so they will have some VMs internet facing and others on an internal network. To do this, good physical and logical network knowledge for all the OSes and network equipment is necessary.  Most run virtual routers as part of their virtual machine networks. It is common to have 4-6 physical NICs in the VM servers to support these advanced network configurations in a safe way.

My laptop for visiting client sites is a chromebook that boots a few different distros, depending on what I'm there to accomplish. What is needed depends completely on what I'm trying to accomplish.

Start small as you learn more, you'll see what is needed. Using virtual machines is pretty much mandatory to have many, many, different OSes, integrations, and practice systems for defend or attack.  Defending is much harder than attacking.

What, exactly, are your goals?

---

### Post by scorp123 on 2020-08-30
> **exstrad said:**
> ... a server that can be used for Cyber Security for my home ...

Sorry but what's that supposed to mean? What do you want to do exactly?

---

### Post by exstrad on 2020-09-02
Ok thank you for the help!

---

