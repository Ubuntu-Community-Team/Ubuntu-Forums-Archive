---
title: "Wireless USB cuts in and out"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-10-02
I have a laptop that I recently installed Xubuntu on.  It has a Compusa Wireless LAN USB Adapter.

It worked out of the box at first - then it started cutting out every now and then.  Now it's cutting out more often than it is connected.

It always says that it's connected, but nothing downloads.  It will download for a few seconds, and then just sit there for a while, and then download a little bit more.

---

### Post by stoogiebuncho on 2008-10-02
Some additional information:

lsusb lists the device as

Bus 002 Device 005: ID 148f:2573 Ralink Technology, Corp

A lot of what I have been finding online talks about installing ndiswrapper.  I am hesitant to do this because a) It looks like a very involved process and I'm not sure I could do it  b) Xubuntu IS seeing my wireless adapter and using it properly some of the time, it just cuts out intermittently.

Does anyone have any ideas?

---

### Post by stoogiebuncho on 2008-10-02
Would this relate to my problem?
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

It looks like it's for 7.04, and I'm running 8.04, but could that fix still work for me?  So far I still have not found anyone else who seems to have my problem of Xubuntu finding the USB Dongle and connecting, but not transferring data all the time.

There's a automatic script of the process here:
[http://ubuntuforums.org/showthread.php?t=757607](http://ubuntuforums.org/showthread.php?t=757607)

Would it be a good idea for me to try that?

---

### Post by stoogiebuncho on 2008-10-02
Hmmm, I'm not getting much luck with responses here.

From the research I've been doing, it looks like my best bet would be to install the serialmonkey drivers for rt73USB.  My hesitation is that this isn't a simple process, and if it doesn't work, I don't know if I would be able to reverse it.

Plus, everything I've read also says that this is supposed to work out of the box, so I'm starting to get frustrated. 

To take another tack - is there another cheap wireless network adapter I could buy that would work without all this hassle?

Thank you for your time.

---

### Post by stoogiebuncho on 2008-10-02
One more update.

I tried setting the bit rate to fixed and setting it to 11Mb, and that actually worked... until I unplugged the wireless adapter and plugged it back in.  

Now it apparently has a different driver.  In the connection information it USED to say rt73usb.  Now it just says usb.  It's still cutting in and out all the time, but I tried fixing the bit rate again and it didn't work this time.

---

### Post by stoogiebuncho on 2008-10-02
And now  it won't connect at all, and when I try to connect, it seems like it's disconnecting our cordless phone, which I really don't understand, but it's done it a couple of times now.

Is anyone out there?  I'm about to give up.

---

### Post by prem1er on 2008-10-02
Post this in another forum use the Wireless and Networking forum, you will probably get a better response.

---

