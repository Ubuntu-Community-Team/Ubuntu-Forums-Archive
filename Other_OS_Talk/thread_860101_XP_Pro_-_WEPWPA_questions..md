---
title: "XP Pro - WEP/WPA questions."
date: 2008-07-15
forum: Other OS Talk
---

### Post by Roasted on 2008-07-15
I was at my dad's house last night, he told me he had some wireless trouble. Aside from the unusually slow laptop (hadn't ran adaware in a couple hundred days), I took a look at his network.

He had a 64 bit WEP encrypted network, along with default logins on the router. I changed the default logins.

Then, I changed him to WPA encryption. I went to his existing connection, hit the wireless networks tab, and saw his network listed in the order of preferred. I adjusted the settings in there from open/WEP to WPA, blah blah. 

But for the life of me I cannot connect to it when it's WPA. I set it back to the 64 bit WEP and it works now. I ended up leaving and I'm going back at the end of the day.

It dawned on me afterwards that maybe I should have deleted the entire connection and opened a new one, instead of trying to convert the settings from WEP to WPA...

When you set up WPA, is there anything in particular you should look out for, setting wise?

I just need WPA on, it to automatically connect when in range, and to save his WPA password so it's just... *computer boots up* BAM - Connected.

Thoughts?

---

### Post by dca on 2008-07-15
Generally that's a way to test if the WiFi NIC can even support WPA...  Intel 22xx & 39xx support it but I believe the 21xx doesn't support WPA.  Remove all wireless network connections from the manager.  Then click on that wireless network displayed.  It should prompt you for a WPA password, if it displays anything else there's a possibility that security is not supported w/ that NIC.  Same thing happened on my old Dell laptop.  Bought one of those new Belkin wireless dealies w/ the MIMO & 802.11n blah blah, set it to WPA and come to find out my laptop's too old to support it...

---

### Post by Roasted on 2008-07-15
Well, I doubt that the laptop doesn't support it. It's running XP Pro SP2, 2 gig of RAM, AMD Turion, etc... it's got pretty up-to-date specs. 

But, if it doesn't, I'll at least beef it up to 256bit encryption on WEP.

Thing is, I hate WEP. I truly do. It confuses me for some reason. :mad:

---

### Post by dca on 2008-07-15
See if this helps:
 
[http://www.mydigitallife.info/2008/07/07/unable-and-cannot-connect-to-wpa-and-wpa2-encrypted-wireless-wi-fi-network-in-windows-xp/](http://www.mydigitallife.info/2008/07/07/unable-and-cannot-connect-to-wpa-and-wpa2-encrypted-wireless-wi-fi-network-in-windows-xp/)

---

