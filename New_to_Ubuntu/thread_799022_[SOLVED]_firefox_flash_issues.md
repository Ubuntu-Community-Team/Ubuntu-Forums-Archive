---
title: "[SOLVED] firefox flash issues"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by blampars on 2008-05-18
in either firefox 2 or firefox 3, i've tried uninstalling flashblock from synaptic but that didnt seem to do anything as far as getting all flash enabled. :(

also menus seem to expand under the flash item as to make them unusable because you cant get to them. example - [www.target.com](www.target.com) how do i fix that?\

thanks,
-b

---

### Post by shifty_powers on 2008-05-18
you need to install the adobe flash plugin.

assuming you're in hardy,

applications>add/remove and search for flash, then install the macromedia flash plugin ;)

---

### Post by blampars on 2008-05-18
i do have adobe macromedia flash installed, the problem is all flash is blocked and i have to click each item in order to get it to work. i just want it all enabled right off the bat. 

the other problem being drop down menus dropping 'under' the flash stuff and being hidden and inaccessable. i cant figure that one out :/

i've tried uninstalling and reinstalling but that hasnt fixed the issue(s)

---

### Post by Bakon Jarser on 2008-05-18
have you gone to Tools > Add Ons in Firefox and made sure flashblock is not there?  Are you running noscript?

---

### Post by blampars on 2008-06-17
removing the libswfdec-0.6-90 package through synaptic has solved my flash block problem.

problems with menus expanding under a flash object and being inaccessible is still an issue, but is a known bug i've found out.

---

