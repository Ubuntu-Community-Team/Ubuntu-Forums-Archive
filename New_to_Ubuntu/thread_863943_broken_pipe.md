---
title: "broken pipe"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by solissydney on 2008-07-19
Hi. I am using XP and Ubuntu 8.04 and dual booting my PC and Laptop. On my PC I can't send emails using Evolution because of an broken pipe. Do I re-install?
I can't understand other replies to the same Q.
What is a tag? a keyword?

---

### Post by pavel989 on 2008-07-19
how do u know its a broken pipe. if theirs an error, google it, or post it here.

---

### Post by iaculallad on 2008-07-19
This should be the problem of missing MTA. Open your terminal and input the code below:

```
sudo apt-get install exim4
```

Then retry sending messages using Evolution.

---

