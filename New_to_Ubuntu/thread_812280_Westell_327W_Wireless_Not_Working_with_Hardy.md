---
title: "Westell 327W Wireless Not Working with Hardy"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bcc21k on 2008-05-29
I recently installed Hardy on an IBM T22 laptop with a Cisco Aironet 350 wireless card and I can not connect to the wireless network.  I do not see the wireless network in Network Manager screen. The Status and Activity lights on the wireless card do not flash on and off. I have a Westell Versalink Model 327W wireless modem.   Is this modem compatible with Hardy?  I read in the Network Manager documentation that the Aironet 350 is compatible with either unencrypted or WEP networks.    I am not sure what encryption is used by the modem. 
Thank you.

---

### Post by unutbu on 2008-05-29
> **bcc21k said:**
> I recently installed Hardy on an IBM T22 laptop with a Cisco Aironet 350 wireless card and I can not connect to the wireless network.  I do not see the wireless network in Network Manager screen. The Status and Activity lights on the wireless card do not flash on and off.

When the lights do not turn on on a wireless card, I think that means the operating system does not detect your card and/or does not load the proper driver to operate your card.

Unfortunately, it appears at least one other user is experiencing [difficulty with the aironet 350 under Hardy]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=776208"). On the other hand, an older post claims the ["350 works 'out of the box' on Ubuntu"]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=776208"). 

> 
I have a Westell Versalink Model 327W wireless modem.   Is this modem compatible with Hardy?
 Thankfully, modems speak the language of IP packets, which is an operating system agnostic protocol. (It doesn't matter what operating system you use; Hardy will be compatible with any modem.)

> 
I read in the Network Manager documentation that the Aironet 350 is compatible with either unencrypted or WEP networks.    I am not sure what encryption is used by the modem.
 
I believe the VersaLink Gateway Model 327W15 supports WEP. I'm not sure if this is exactly the same model as yours, but it should be close:

[http://www.westell.com/content/products/pdf/030_300444A.pdf]("Documentation on the Westell 327W15 from westell.com")

---

### Post by kerry_s on 2008-05-29
that's funny i thought i did this one. :confused:

please do not make more than 1 thread for the same subject. :mad:

mods, please merge/combine his 2 threads->
[http://ubuntuforums.org/showthread.php?t=812291](http://ubuntuforums.org/showthread.php?t=812291)

---

