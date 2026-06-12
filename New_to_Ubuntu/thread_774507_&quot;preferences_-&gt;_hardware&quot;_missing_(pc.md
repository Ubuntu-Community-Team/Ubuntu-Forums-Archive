---
title: "&quot;preferences -&gt; hardware&quot; missing? (pcmcia wifi card)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jackjones on 2008-04-29
Hello -
I would like to get a Wifi PCMCIA card working in Hardy Heron.
When I look at
Help -> Internet -> Wireless Networking -> Troubleshooting,
there's the following:
3.2.1  Check for device recognition
Open device manager
   System -> Preferences -> Hardware Information.

Hmmm, there is no "Hardware Information" option under System -> Preferences.  There was in the previous release (Gibbon?) but not Heron.  What should I do?

(BTW, the System -> Administration tab also lacks an analogue.)

---

### Post by mapes12 on 2008-04-29
Much depends on what model of card you are looking to install. Linux is not all that great at wifi networking. If you have a PCMCIA card that has native Linux drivers they will work out of the box. Checkout these guys out for help: 

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) 

Other than that you will need to configure a Windoze driver using the ndiswrapper (Google it) utlity which in my experience is OK but very problematic compared to native Linux driver supported cards.

Good luck!

---

### Post by jackjones on 2008-04-30
Well, the thing is, the **help instructions** don't match the **software**.
The **help instructions** refer to menu options that are non-existent.
Whatever card I get, I won't be able to follow the **help instructions** because they are wrong (apparently).
How should I file a bug report?

---

