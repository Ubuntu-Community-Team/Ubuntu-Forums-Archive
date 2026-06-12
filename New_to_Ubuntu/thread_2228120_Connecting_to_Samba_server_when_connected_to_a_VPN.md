---
title: "Connecting to Samba server when connected to a VPN"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by the-paul-84 on 2014-06-05
Hi!

I have an Ubuntu 12 server which I use as a samba file server to share videos to people on my network. 

Occasionally, I will download torrents on my Ubuntu 14 virtual machine. In order to protect my privacy, I use a VPN called BTGuard. 

My issue is that when I am connected to the VPN, I can not connect to my smb server. Is there a way I could edit the smb.conf to allow connection through the VPN? Thanks, and I look forward to hearing what to do.

---

### Post by scottbomb on 2014-07-07
I'm having the same problem. I have a Windows machine that samba can normally see but as soon as I connect it to a VPN service, samba  can no longer see if from my Ubuntu machine. I can still ping it via it's IP address so I would expect samba to see it as they are on the same network/subnet.

Any ideas?

---

### Post by scottbomb on 2014-07-08
And yet it worked today just fine. It's so unpredictable. Don't know whether to blame Samba or Dolphin. Will be testing this further with other distros (Xubuntu vs Mint) to see if I get different results.

---

