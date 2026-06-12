---
title: "What's the meaning of out/input in IpBlock"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by rbjscv on 2008-08-11
I'm a little confused about the meaning if output vs input in IpBlock.

Also I notice that my log is almost entirely ouput - sometimes completely. 
Why is there little or no input entries?  Is this the norm?

I'm behind a router with 1 port open for kTorrent.  Same port is open in Firestarter to everyone, and kTorrent is set to use the same port.

Hope that's enough to describe my situation. Thanks all.

---

### Post by ukripper on 2008-08-11
> **rbjscv said:**
> I'm a little confused about the meaning if output vs input in IpBlock.

Also I notice that my log is almost entirely ouput - sometimes completely. 
Why is there little or no input entries?  Is this the norm?

I'm behind a router with 1 port open for kTorrent.  Same port is open in Firestarter to everyone, and kTorrent is set to use the same port.

Hope that's enough to describe my situation. Thanks all.

Out means outgoing traffic from your machine and in means incoming traffic to your machine from outside of your machine.

You have blocked most of your incoming ports therefore  you have less incoming traffic logs than outgoing. if you are uploading something outgoing traffic will increase drastically.

---

### Post by rbjscv on 2008-08-11
Thanks.  At least I was correct on my definitions.

As far as incoming open ports, I've opened one port on my router, the same # in firestarter, and same in kTorrent.  Seems like that should mean incoming blocks, right?  

If there are no incoming hits, then I'd assume there is no downloading data either - in spite of the incoming open ports.

Is this reasonable?  Or do I need more coffee and wait for the sun to shine.

---

### Post by ukripper on 2008-08-11
> **rbjscv said:**
> Thanks.  At least I was correct on my definitions.

As far as incoming open ports, I've opened one port on my router, the same # in firestarter, and same in kTorrent.  Seems like that should mean incoming blocks, right?  

If there are no incoming hits, then I'd assume there is no downloading data either - in spite of the incoming open ports.

Is this reasonable?  Or do I need more coffee and wait for the sun to shine.

You have blocked your all incoming ports on firewall except ktorrent ports and incoming traffic is getting churned via ipblock. ip addresses you are blocking on ipblock should only be coming through the ports you have filtered in your firewall. So theoratically, you shouldn't have anything else available to outside world except ktorrent but make sure you have opened corect ktorrent ports on router as well otherwise there will be no downloading. I believe ktorrent uses different ports for upload and download you should make sure you got them righ on firewall and router.

---

### Post by rbjscv on 2008-08-11
Thank You.  I thought I was on the right trail.  Just wanted a guide to make sure I had the right map AND the right trail.

---

### Post by ukripper on 2008-08-13
> **rbjscv said:**
> Thank You.  I thought I was on the right trail.  Just wanted a guide to make sure I had the right map AND the right trail.

You are welcome! Have fun.

---

