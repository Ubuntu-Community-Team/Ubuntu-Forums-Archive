---
title: "This requires installing packages from unauthenticated sources."
date: 2014-06-22
forum: New to Ubuntu
---

### Post by openation1 on 2014-06-22
hello everyone..........
                        Iam trying to install opera browser but it doesn't let me it says This requires installing packages from unauthenticated sources. Please help me. thank you

---

### Post by oldos2er on 2014-06-22
Get the gpg key for the Opera repository: ```
sudo apt-get install debian-archive-keyring

wget -qO - http://deb.opera.com/archive.key | sudo apt-key add -

sudo apt-get update

sudo apt-get install opera
```

---

