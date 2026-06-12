---
title: "finding a file"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-11-05
okay just forgot how to do this. need to probably use a wild card. i need to find a file that ends with .mp4. tks

---

### Post by Lars Noodén on 2013-11-05
You could try [locate](http://linux.die.net/man/1/locate)

```

locate --regex '\.mp4$'

```

---

### Post by rburkartjo on 2013-11-05
lars tks that did the trick

---

### Post by Dennis N on 2013-11-05
If you want a GUI, Xubuntu comes with catfish (under accessories). Just put **mp4** in the search box. No wilds card needed. Your home folder is searched by default. You can change that by the selector. (Note: my comment relates to Xubuntu 12.10 - my current version - later releases may be different.)

---

