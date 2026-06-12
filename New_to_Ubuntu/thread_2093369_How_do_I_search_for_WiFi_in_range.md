---
title: "How do I search for WiFi in range?"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by Carl50 on 2012-12-10
What do I use to search for wireless networks in range?  The "Network connections" thing in the "Preferences" menu doesn't seem to give me the option of searching for wireless networks.

---

### Post by haqking on 2012-12-10
> **Carl50 said:**
> What do I use to search for wireless networks in range?  The "Network connections" thing in the "Preferences" menu doesn't seem to give me the option of searching for wireless networks.

```
iwlist <interface> scan
```

---

### Post by Carl50 on 2012-12-10
It can only be done in the terminal?  There's no utility that does it?

---

### Post by haqking on 2012-12-10
There are many ways to do it but I have no idea what you are running or what desktop environment you have.

The above works regardless.

---

### Post by arpanaut on 2012-12-10
If I click on my wireless icon on the right of the top panel it shows me all available networks in range. Or is it something else you are looking for?

---

### Post by AstroLlama on 2012-12-10
if the wifi is running it should constantly be scanning and updating every few seconds in the network connections dialog. is there a network you know is present but isn't being detected?

---

### Post by Carl50 on 2012-12-10
> **arpanaut said:**
> If I click on my wireless icon on the right of the top panel it shows me all available networks in range. Or is it something else you are looking for?
It does that fine when I'm in the ubuntu, but there is no similar feature in lubuntu.  It isn't seeing all the other networks I have around me.

---

### Post by haqking on 2012-12-10
> **Carl50 said:**
> It does that fine when I'm in the ubuntu, but there is no similar feature in lubuntu.  It isn't seeing all the other networks I have around me.

That is the first time you have mentioned what you are running though tagged with lubuntu, but we need more information in the post

When posting for support please mention hardware, operating system and version and applicable screenshots.

Cheers.

---

### Post by agxryt on 2012-12-10
I'm also eager to hear more about this.

Running Lubuntu 12.04. I'm just a little confused as to why features are missing from the same package depending on the DE.

---

