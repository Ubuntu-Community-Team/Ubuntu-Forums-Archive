---
title: "Ubuntu One"
date: 2011-06-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2011-06-21
I cant log into Ubuntu One. Any time I run the setup app, it claims I have no internet, yet my connection is fine. Anyone else having issue's ?

---

### Post by jbicha on 2011-06-21
Yes, it's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-sso-client/+bug/791548](https://bugs.launchpad.net/ubuntu/+source/ubuntu-sso-client/+bug/791548)

NetworkManager 0.9 changed its API so programs that check for network connectivity don't get the response they expected. Most apps have already been converted but Ubuntu One is lagging a bit.

---

