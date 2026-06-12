---
title: "NetworkManager.conf question"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2011-06-24
I have done a fresh install of Kubuntu 11.10 and I have noticed that if I use the KDE Network Management plasma widget, the Ethernet connection is unmanaged and fails to work because of a setting in the 
/etc/NetworkManager/NetworkManager.conf file:
```

[ifupdown]
managed=false
```

Which should be:
```

[ifupdown]
managed=true
```

in order for the Ethernet connection to work.

Is there any reason why the managed setting is set to false from a fresh install? Seems odd how it's set that way, or am I missing something obvious which means it has to be set that way..?

Thanks in advance.

---

### Post by seeker5528 on 2011-06-24
> **tghe-retford said:**
> Is there any reason why the managed setting is set to false from a fresh install? Seems odd how it's set that way, or am I missing something obvious which means it has to be set that way..?

When it's false network manager will not manage interfaces that are configured in '/etc/network/interfaces', interfaces not configured in '/etc/network/interfaces' should still be managed.

When it is set to true, network manager will manage the interface in spite of any configuration the interfaces may have in '/etc/network/interfaces'.

If this was a fresh install and there is configuration in '/etc/network/interfaces' for the interface in question, I would consider that a bug. 

If there is no configuration in '/etc/network/interfaces' for the interface in question and the KDE Network Management plasma widget fails to manage the interface because of ```
[ifupdown]
managed=false
``` in '/etc/NetworkManager/NetworkManager.conf', then I would consider that to be a bug in the KDE Network Management plasma widget since it is interpreting the setting differently than NetworkManager on it's own.

Later, Seeker

---

