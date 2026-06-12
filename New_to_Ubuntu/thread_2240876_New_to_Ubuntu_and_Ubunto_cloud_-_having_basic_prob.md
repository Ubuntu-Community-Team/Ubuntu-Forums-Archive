---
title: "New to Ubuntu and Ubunto cloud - having basic problems accessing new VMs"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by serge8 on 2014-08-22
Hi guys, 

I am brand new to Ubuntu and everything that comes with it, my apologies if this question sounds a bit simple. 

After installing Ubuntu Desktop 14.04, I followed the guidelines of the post below to install a single machine openstack cloud:
[http://astokes.org/ubuntu-openstack-installer/](http://astokes.org/ubuntu-openstack-installer/)

with the stuff mentioned there, I was able to run cloud-install without any trouble. 

I see that it has created several virtual machines functioning as different OpenStack nodes (controller, compute, Neutron, etc).

My problem is as follows - when trying to create a new VM through the Horizon browser interface, I get an error saying the following:

**Error: **       Failed to launch instance "i1": Please try again later [Error: No valid host was found. ].

I googled around and learned that this error is commonly associated with lack of resources, but that is simply not the case here.


I wanted to see the feedback from the openstack services themselves but I am not able to ssh into the VMs that cloud-install created that are running these services. 


How do I get to these VMs?
I tried SSH ing with no responce, I tried ssh-copy-id to get my public key there, but got a permission denied error. 

I can ping the VMs fine, they are responding. 


So, how do I get into these VMs running the openstack services?
The forum rules said that since this is my first post, I should post here.

Thanks in advance

---

### Post by TheFu on 2014-08-23
Not too many folks here use openstack.  Posting in the "Server" forum might be slightly better, but ... I don't recall any openstack questions there recently either.

You'll get better help on the openstack forums, IRC or email list.  They will assume that you've read everyone on the openstack website and have reviewed all the log files.

For a first post here, openstack is an extremely advanced tool.  I hope you have significant UNIX/Linux experience and are just new to Ubuntu. Otherwise, be prepared for an extreme hill-climb to understanding.  Debian?

---

