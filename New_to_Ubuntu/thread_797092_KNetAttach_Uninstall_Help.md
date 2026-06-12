---
title: "KNetAttach Uninstall Help"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-16
When I try to uninstall KNetAttach in Add/Remove it says "one or more applications depend on kdebase-bin. To remove kdebase-bin and the dependent applications use the synaptic package manager" but when i go to synaptic package manager and look up "knet" (without the quotes) nothing shows up..the same with when i look up the full name KNetAttach..still nothing shows up! Is there a terminal code i can put in?

---

### Post by mevets on 2008-05-17
You should be searching for kdebase not knet. Removing this not only remove knetattach, but also kde. i Have gotten this problem since i decided to periodically check out kde4 on my gnome installation.

---

### Post by donniezazen on 2008-09-15
> **mevets said:**
> You should be searching for kdebase not knet. Removing this not only remove knetattach, but also kde. i Have gotten this problem since i decided to periodically check out kde4 on my gnome installation.

Thanks problem solved after i removed auto removal from Synaptic.

---

### Post by ericmwebe on 2008-09-26
uninstall knetattach from the console,
simply type sudo apt-get remove knetattach and hit the enter key and just follow what the console will give you.
After all that type sudo apt-get update and your good to go
Just that simple:)

---

### Post by khairi on 2009-06-01
> **soham_1207 said:**
> Thanks problem solved after i removed auto removal from Synaptic.
hi
how do you remove the auto remove option in synaptic?

---

### Post by wajdigary on 2009-12-21
> **mevets said:**
> You should be searching for kdebase not knet. Removing this not only remove knetattach, but also kde. i Have gotten this problem since i decided to periodically check out kde4 on my gnome installation.
hi... i already removed kdebase but.. still i see knetattach in my applications.. when i click it's still says: failed to execute child processes ( no such file or directory ).
help please?

i'm not an expert but i really love ubuntu.. i found many helpful solutions in this forum.. i hope someday i can be expert too.. so i join to help others too. 
thanks.

---

