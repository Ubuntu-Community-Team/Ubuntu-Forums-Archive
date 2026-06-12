---
title: "It seems like my Ubuntu hardrive is always running"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by videocheez on 2008-04-26
I just upgraded to the latest version of Ubuntu and my hardrive seems to always be running.  It sound like data is constantly being read and written to.  I have a dual boot comp with Windows on two SATA raid drives and ubuntu is on a dedicated eSATA drive.  I'm not sure what is going on but would like to know how i could diagnose why my hardrive is always making lots of noise even when I'm not doing anything.  Any suggestions will be appreciated.

VC

---

### Post by SnakeHips on 2008-04-26
in terminal

```
top
```

this should give you some clues...

---

### Post by mister_pink on 2008-04-26
How long has it been doing it for? I suspect its the search program creating its index, it should only do it for a while then stop.

---

### Post by insane_alien on 2008-04-26
sounds like the indexer. 

tracker took a few days to compile an index on my computer though mine was a bit of an extreme case. and i bumped its priority down as low as it could go.

---

### Post by videocheez on 2008-04-26
> **SnakeHips said:**
> in terminal

```
top
```

this should give you some clues...

Thanks man.  I never knew about this top command.  It was very clear that mythtv which I installed a while back but never properly configured it was trying to do something.  I uninstalled it and the hardrive finally "chilled out"

Thanks again,

VC

---

