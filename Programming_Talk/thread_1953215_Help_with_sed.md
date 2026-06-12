---
title: "Help with sed"
date: 2012-04-05
forum: Programming Talk
---

### Post by g320907aa on 2012-04-05
Hello guys, I am creating udev rule file using script. It contains sed statement which causing an error. Can you guys look into attachment to see what is wrong. Appreciate in advance.

---

### Post by Vaphell on 2012-04-05
sed doesn't like newlines inside its expressions

sed "s/...
.../.../"

care to explain what these atrociously complicated expressions are meant to achieve?

---

