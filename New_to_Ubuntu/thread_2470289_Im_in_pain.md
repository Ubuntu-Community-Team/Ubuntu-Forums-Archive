---
title: "Im in pain"
date: 2021-12-24
forum: New to Ubuntu
---

### Post by linuxhurts2 on 2021-12-24
Ubuntu cannot update chrome component, update itself, install apps, or upgrade itself without an error or a failed to download packages message.
Im using ubuntu cause my windows broke but ubuntu is completly incapable of doing anything i cant even watch netflix. I wish to genuinly understand what to do but using install commands and update commands dont work. I need help thank u.

---

### Post by howefield on 2021-12-24
What is the output of the following command..

```
sudo apt update && sudo apt upgrade
```

---

### Post by grahammechanical on 2021-12-24
Please tell us what version of Ubuntu you are using and the specification of your computer. It is possible that you have installed a version of Ubuntu that has reached End of Life support and therefore cannot be updated. Neither will you be able to install any software.

Regards

---

### Post by ActionParsnip on 2021-12-25
What is the output of
```

lsb_release -a; uname -a;apt-cache policy `dpkg -l | grep -i chrome | awk {'print $2'}`

```

---

