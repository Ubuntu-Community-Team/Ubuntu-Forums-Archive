---
title: "network manager"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Mr.Pickels on 2008-10-21
When I shutdown the system I get the following errors:

Network Manager <WARN> nm_signal_handler(): Caught signal 15, shutting down
                 normally

Network Manager <INFO> Caught termination signal

Network Manager <DEBUG> [1224644010.763255]nm_print-open-socks(): Open
                 Sockets List:

Network Manager <DEBUG> [1224644010.763255]nm_print-open-socks(): Open
                 Sockets List Done.

Network Manager <WARN> nm_hal_deinit(): libhal shutdown failed - Did not 
                 receive a reply.  Possible caused include: the remote 
                 application did not send a reply, the message bus reply 
                 timeout expired, or the network connection was broken.

---

### Post by Xiong Chiamiov on 2008-10-26
Does it shutdown successfully?  When I used NM I got that just because it doesn't like that way I shut down the computer, or somesuch.

---

### Post by crashcoredump on 2008-10-26
I see that with regularity upon shutdown from the console. I had some problems with NM in Fedora 8 as well. At one point everytime I updated software I had to uncheck NM to successfully run the updates.
I think Network Manager is just a bit buggy.

---

