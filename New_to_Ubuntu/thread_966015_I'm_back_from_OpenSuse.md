---
title: "I'm back from OpenSuse"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-11-01
About an hour ago I installed Ubuntu8.10, after trying OpenSUSE and finding it to be incompatible with some of my hardware.  Specifically both my wired internet connection and my wireless didn't work.  I have the (somewhat dreaded, as I have come to understand) Atheros AR5007EG wireless network adapter.  I got it working last time, using madwifi (I think).  But I heard it was supposed to work "out of the box" for 8.10.  However, for some reason, my wired connection doesn't work.  It did work with 8.04 so I see no reason why it would suddenly become incompatible with 8.10.  I have an Acer Aspire7520-5168.  So, what can I do to get my wireless connection working without a wired connection.  Or if I have to get my wired connection going, how do I do that?  When I plug in the cord it says it is acquiring network address, and then it tells me it is disconnected.

---

### Post by talsemgeest on 2008-11-01
Have you tried manually initiating a connection using network manager?

---

### Post by SalsaShark on 2008-11-01
> **talsemgeest said:**
> Have you tried manually initiating a connection using network manager?

How do I go about finding the relevant information?

---

### Post by SalsaShark on 2008-11-02
Anyone?  I'm not sure how to find, or even what information I need to manually initiate a connection.

---

### Post by SalsaShark on 2008-11-03
Well for crap`s sake, all of a sudden the wired connection works.  I don`t understand why it works now, but it does.  Can anyone point me to where I can get the information to get my Atheros wireless working?

---

### Post by igknighted on 2008-11-03
Read the 8.10 release notes.  The module (ath5k i think?) for the drivers does not load.  There is a workaround listed in the errata.

[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

---

