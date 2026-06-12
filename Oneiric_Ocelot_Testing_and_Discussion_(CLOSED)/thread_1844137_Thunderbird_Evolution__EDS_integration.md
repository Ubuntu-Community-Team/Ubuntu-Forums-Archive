---
title: "Thunderbird Evolution  EDS integration"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by svenole on 2011-09-14
After upgrading to Oneric, I've got into problems with thunderbird and addressbooks. The reason is that there has been developed some integration with Evolution addressbook setup and I am using Evolution. The problem is that I'm using Evolution for work email and thunderbird for private. Typically I am using thunderbird when at home where evolution does not connect to the Exchange / GAL. Now, thunderbird pops up error messages about this again and again. This would be find if I did know how to disable the whole thing, but I can not figure out how. When I delete the Global Address list from thunderbird, it tells me that I can not do this and it is back in there next time I start. Now, there might be a good reason for implementing this integration, but users that do not want it, should be able to disable it. I have not found a way to do that, I wonder if someone else has?

---

### Post by svenole on 2011-09-14
Now, obviously I was a bit fast here. The solution to this issue was to go into account settings and deactivate the use of global LDAP servers for each and every mailbox (I have several). Seems like thunderbird is picking up the Evolution setup by default thinking that the user wants these addressbooks to be shared. I'm not sure that this is a good idea. At least not until the same security mechanisms that exists in the MS world, are available (never?). There is no way I can get evolution connect to my mobile exchange account at this time and then this address book integration will not work when I am not connected to my work LAN.

---

### Post by afeder on 2011-09-16
It's right there under Tools > Add-ons > EDS Contact Integration.

[https://addons.mozilla.org/en-US/thunderbird/addon/eds-contact-integration/?src=api](https://addons.mozilla.org/en-US/thunderbird/addon/eds-contact-integration/?src=api)

---

