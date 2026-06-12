---
title: "Wireless help"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Wils on 2008-11-24
Hi 

Can anyone help me my wireless card an Netgear WG511 v2 work with Ubuntu 8.10. My laptop is an IBM Thinkpad T42

Thanks Wils

---

### Post by webdr on 2008-11-24
OUCH, NetGear... regardless of OS, NG products have never failed to disapoint me. Well, I'm sure you really didn't want my opinion, but there it is.

Onward to the problem at hand.
Can you post the results of lspci, iwconfig, and ifconfig?

That information will help a lot.
-Mark

---

### Post by jayfisher on 2008-11-24
Hey mate,
i think most hardwares are compatible with ubuntu nowadays, especially the big brands. Just to be sure though i did a Quick Search for u and it seems that ur card should work just fine :)

[http://www.ubuntuhcl.org/browse/product+netgear-netgear-wg511?id=10](http://www.ubuntuhcl.org/browse/product+netgear-netgear-wg511?id=10)

---

### Post by gychang on 2008-11-24
> **Wils said:**
> Hi 

Can anyone help me my wireless card an Netgear WG511 v2 work with Ubuntu 8.10. My laptop is an IBM Thinkpad T42

Thanks Wils

I have the same card "made in China", Taiwan is easy to set up as I understand.  I have not been able to get it working...  My laptop is Compaq Presario 2800T several yrs old...

Hopefully someone can help this newbie setup properly.

gychang

---

### Post by Wils on 2008-11-24
> **gychang said:**
> I have the same card "made in China", Taiwan is easy to set up as I understand.  I have not been able to get it working...  My laptop is Compaq Presario 2800T several yrs old...

Hopefully someone can help this newbie setup properly.

gychang

I have a"made in china" card not even aflashing light 

wils

---

### Post by bobnutfield on 2008-11-24
The new kernel in Intrepid (2.6.27) has a great deal of new modules to greatly improve wireless support.  However, I have not been able to find what module that card uses in the kernel.  It may be one that is still not natively supported.  However, it is KNOWN to work with Ndiswrapper.  This a program layer so that you can use Windows drivers in Linux.  It is not very complicated to install and use.  You must have you Windows drivers available on your Ubuntu system, which you can normally get from either Windows driver directories or from the CD that came with the card.

Here is a link to a tutorial for the card.  I don't know if it is Ubuntu specific, but I have read it and it will work with Ubuntu.

[http://declanmcgrath.wordpress.com/2007/05/12/installing-the-netgear-wg511v2-china-wireless-card-on-linux/]("http://declanmcgrath.wordpress.com/2007/05/12/installing-the-netgear-wg511v2-china-wireless-card-on-linux/")

---

### Post by seren6ipity on 2008-11-24
Wils, Have a look at the thread - [http://ubuntuforums.org/showthread.php?t=879766](http://ubuntuforums.org/showthread.php?t=879766)
It solved my problem with IBM Thinkpad T40. I blacklisted the problematic driver. 

Post by Chili has details how to do it.

Hope this helps!

---

### Post by gychang on 2008-11-24
> **bobnutfield said:**
>  However, it is KNOWN to work with Ndiswrapper.   You must have you Windows drivers available on your Ubuntu system, which you can normally get from either Windows driver directories or from the CD that came with the card.

Here is a link to a tutorial for the card.  I don't know if it is Ubuntu specific, but I have read it and it will work with Ubuntu.

[http://declanmcgrath.wordpress.com/2007/05/12/installing-the-netgear-wg511v2-china-wireless-card-on-linux/]("http://declanmcgrath.wordpress.com/2007/05/12/installing-the-netgear-wg511v2-china-wireless-card-on-linux/")

thanks for the helpful information, I have been unable to obtain ".inf" file, netgear only has .exe file that can not be extracted...  Some have found windows2000 driver works better but still not .inf file that I can locate.

any help out there?

gychang

---

