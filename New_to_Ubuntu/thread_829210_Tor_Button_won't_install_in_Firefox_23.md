---
title: "Tor Button won't install in Firefox 2/3"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2008-06-14
When I install TorButton either through the website or off my desktop, I get the following error:


> Firefox could not install the file at

file:///home/johngalt/Dektop/torbutton-current.xpi

because: Unexpected installation error
Review the Error Console log for more details.
-203



Error Console give the following output

> Line 3938
     var installLocation = this.getInstallLocation(item.id);


Can someone advise me to the solution please?

---

### Post by El Rogueo on 2008-06-14
I had that same problem a while ago, but it cleared up after in reinstalled Firefox. Maybe that'll work for you too?

---

### Post by Mega_Fauna on 2008-06-14
No, it didn't, but thanks for the response.

I have now discovered that this error appears in all my plugin installs.

Any ideas anyone?

---

### Post by it2007me on 2008-07-24
me too, i`m running on ubuntu 64bit..
hurmm..

i need the tor button (firefox addon..) :(

---

### Post by Austin_KW on 2008-07-24
Try foxyproxy. Can be used to setup multiple proxies.
Out-of-the-box support for Tor. Then just right click to enable/disable tor browsing.

---

