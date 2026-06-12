---
title: "Real Time Programming"
date: 2006-09-04
forum: Programming Talk
---

### Post by Dsypher on 2006-09-04
I need to code in Real Time Java for a university project. I have kubuntu 6.06 installed; is it possible to convert it to a real time linux?

Any sorta help would be appreciated.

---

### Post by amo-ej1 on 2006-09-04
I haven't tried with it, but apt seems to contain some rtai packages. These could be a nice starting point.

```

root@lap# apt-cache search rtai | grep ^rtai
rtai - real time application interface
rtai-doc - real time application interface (documentation)
rtai-source - real time application interface (module source)

```

---

