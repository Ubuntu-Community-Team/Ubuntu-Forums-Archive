---
title: "Gconf modifications during package install"
date: 2011-10-05
forum: Programming Talk
---

### Post by maddis on 2011-10-05
I have multiple modifications I've done in gconf and I'm planning on to make a package that I can install and it would make those same changes to that system. 

I tried using gconftool, but it seems that using it in preinst or postinst scripts aren't good idea. Also I cannot(I think) use schemas since I'm not creating new keys, just editing existing ones.

What's the right way to do that? Or is there (easy) way to backup selected keys with values and not all keys? Package solution would be better. That way I could keep up with the versions easier.

---

### Post by nvteighen on 2011-10-05
GConf stuff is located at the user's directory, so doing this at install-stage would set those keys as owned by root... making them impossible to customize for the user. IIRC, what packages do with GConf is to set schemas, but I'm not sure.

---

