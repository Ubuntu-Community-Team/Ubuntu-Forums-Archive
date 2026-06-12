---
title: "WIFI Driver Selection"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by johnhouk on 2008-11-16
How can I find out what wifi driver im looking for? All i know is that the onboard wireless-b, in my gateway laptop, is an Orionoco.

---

### Post by bumanie on 2008-11-16
In terminal > lspciThis will give you all the information needed - note it is a long list, but as long as your wifi card is recognised, it will be in the list. It should show the model number of the card. Have you looked in hardware drivers, to see if it is recognised?  System --> Administration --> Hardware Drivers.

---

