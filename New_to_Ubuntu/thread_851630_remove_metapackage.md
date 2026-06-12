---
title: "remove metapackage"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tdrusk on 2008-07-06
I installed ubuntu-mobile. I tried to remove it and it just removed the metapackage. I want all the programs associated with it removed. Why is this so complicated in Ubuntu? I used apt-get to install it. I tried to purge and nothig worked.

---

### Post by iaculallad on 2008-07-06
> **tdrusk said:**
> I installed ubuntu-mobile. I tried to remove it and it just removed the metapackage. I want all the programs associated with it removed. Why is this so complicated in Ubuntu? I used apt-get to install it. I tried to purge and nothig worked.

It's not that complicated. Had you used the command below to uninstall your ubuntu-mobile?

```
sudo apt-get remove ubuntu-mobile
```

and remove this file too:

```
sudo rm /usr/share/xsessions/hildon.desktop
```

---

### Post by bhadotia on 2008-07-06
Are you asking how to uninstall the dependencies ? Or are you just saying that this is very bad  that meta packages don't remove the dependencies along with them . 
If you are asking the first question then go into synaptic note down all the dependenncies from the dependencies tab in the properties windo of the metapackage and uninstall them all individually. You will have to check the 'show package properties' in preferences to see the dependencies tab - if you don't know about that.

---

