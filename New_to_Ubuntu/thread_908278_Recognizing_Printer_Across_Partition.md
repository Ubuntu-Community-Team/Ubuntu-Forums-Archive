---
title: "Recognizing Printer Across Partition"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by elvenwonder on 2008-09-02
I'm dual booting with vista and there's a printer on the network that I have installed (if that's the correct term), but I cannot get it to recognize on my ubuntu partition.  It's a big HP laserjet, so it should definitely be post-scripted.  How do I get it onto my linux partition?  (And, yes, I did go to System Administration Printing and looked for it on the list--it wasn't there.)  Thanks in advance.

---

### Post by dwanders on 2008-09-02
First thing to do is determine how the printer is accessed?

Is is networked (WiFi or Cable)?
Is it shared off another Computer (USB or Parallel) then shared through Windows?

Once you know how it is on your network, it will be pretty simple to set it up - if it is networked:

1) go into your Vista partition and get the settings for the Printer, you can use that information to connect to it from your Linux Partition. 
2) Or better yet, go to the printer and get the IP information from it (print out a test page - that should contain all the info you need IP Address, Subnet mask, and the model of printer)
If you cannot find a HP driver for it, and it is a plain BW laser jet, try HPLJ4 driver - it typically works without fail. 

If it is a shared printer from windows - ( and I realize this is silly but some folks might try and do it - it CAN NOT be shared from your Windows Partition it must be on a completely different computer) you will need to set up a Samba printer connection.  

Hope this helps

---

