---
title: "Screen Resolution"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by HyperDriven on 2008-06-20
Well, ubuntu is up and running, and I'm loving it :) Thanks to those who helped me in my previous post - really appreciated ;) 

I am however experiencing a slight annoyance, not a problem. I have NO graphics card installed on this one machine (it melted horribly a month ago and haven't had the time or cash to replace it). The whole screen is very 'oversized' and everything seems zoomed in. Is there anyway to change the resolution of my TFT monitor? 

Thanks :)

---

### Post by ruffEdgz on 2008-06-20
When you go to System >> Screen Resolution does it let you change the resolution to a bigger size?

Just wondering :D

---

### Post by jimv on 2008-06-20
Well, we'd need to know what your graphics card/onboard graphics chip is.

To find out, type this in a console:

```
lspci | grep VGA
```

---

### Post by HyperDriven on 2008-06-20
> **ruffEdgz said:**
> When you go to System >> Screen Resolution does it let you change the resolution to a bigger size?

Just wondering :D
No it doesn't, the maximum is 800*600... 

@ jimv - it says it's a VGA compatible controller, UniChrome Pro IGP

---

### Post by WildOscar on 2008-06-20
If you have just installed a fresh copy of Hardy Heron, maybe this might help.

Goto. System>>preference>>main menu
and check box for Other>>Screen and Graphics
Now u can select ur display! ... install ur Driver
System>>Administrative>> Hardware drivers
Check on you graphisc card to download and use the restricted drivers.

Hope these steps help you sort it out. Faced a similar problem after reading the forums tried this, it worked!

---

### Post by Wobblybob on 2008-06-20
Do you need to instal a restriced driver for your [I assume] on board graphics card, try [System], [Admin..], [hardware Drivers] enable graphics driver if present, re boot then re check to make sure the driver is ticked as in use. You should be able to goto [System], [Preferences], [Screen Res...] to change the settings if they have not auto changed.

---

### Post by HyperDriven on 2008-06-20
Ok guys, will reboot and see what happens. I will have to end up getting a new graphics card soon anyway, but til then will try out what you have all suggested, and report back :) 

Cheers ;)

---

### Post by HyperDriven on 2008-06-21
Well guys, I got it working :) 

Wildoscar - probably the same probem as you mate :P 

Thanks again, everyone, for all your help :)

---

