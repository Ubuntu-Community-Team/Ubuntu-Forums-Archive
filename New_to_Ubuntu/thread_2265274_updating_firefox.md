---
title: "updating firefox"
date: 2015-02-13
forum: New to Ubuntu
---

### Post by trav9595 on 2015-02-13
how do you update Firefox to the latest solid version with minimal hassle and using the least data allowance ..using the terminal??

---

### Post by sandyd on 2015-02-13
> **trav9595 said:**
> how do you update Firefox to the latest solid version with minimal hassle and using the least data allowance ..using the terminal??

Hi, if you keep up with updates listed in the Update Manager, you should be at the following versions. They have been tested to be stable by the Ubuntu repository maintainers.

Utopic: 35.0.1
Trusty: 35.0.1
Precise: 35.0.1
Lucid: 20.0

If you want to update just firefox, run the below
```

sudo apt-get update
sudo apt-get install firefox
```

---

### Post by haplorrhine on 2015-02-14
Least data allowance?  I don't know, but the info page would have told you how to update it.

```
 info apt-get 
```

---

### Post by monkeybrain20122 on 2015-02-14
It is updated through xubuntu's normal update mechanism when a new version is available (software centre, synaptic or update manager etc) You don't need to do anything special.

---

