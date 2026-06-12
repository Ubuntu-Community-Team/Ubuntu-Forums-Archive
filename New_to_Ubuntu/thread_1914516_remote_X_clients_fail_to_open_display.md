---
title: "remote X clients fail to open display"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by bardov on 2012-01-24
I have a problem where when I ssh -X to remote machines,
some will set up the DISPLAY to something like localhost:15
but others fail to set up the DISPLAY.

Obviously those that fail to set up the DISPLAY fail to open x clients (xterm) back on my display.

If I try to set up DISPLAY=<my-ip-address>:0, I still fail to open remote clients. I have disabled the firewall (sudo ufw disable), and I did remember to enable remote clients with xhost +.

Using wireshark I see that the remote client is sending X11 [SYN], but it gets a reply of [RST, ACK].

Any ideas ?

Thanks,
Dan

---

