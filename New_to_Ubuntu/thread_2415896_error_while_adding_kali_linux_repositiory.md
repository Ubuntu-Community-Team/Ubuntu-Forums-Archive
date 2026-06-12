---
title: "error while adding kali linux repositiory"
date: 2019-04-02
forum: New to Ubuntu
---

### Post by pratap73 on 2019-04-02
```

1) Add kali linux repositories
2) Update
3) Remove all kali linux repositories
4) View the contents of sources.list file

                    
What do you want to do ?> 1
Executing: /tmp/apt-key-gpghome.SOxyljXRGy/gpg.1.sh --keyserver pgp.mit.edu --recv-keys ED444FF07D8D0BF6
gpg: keyserver receive failed: No data


```

---

### Post by yancek on 2019-04-02
The link below has detailed instructions on this.  Have you read / done the steps shown?

 [https://www.ostechnix.com/install-kali-linux-tools-using-katoolin-linux/](https://www.ostechnix.com/install-kali-linux-tools-using-katoolin-linux/)

---

### Post by pratap73 on 2019-04-02
yes follow the same process still not able to add kali linux repository

---

### Post by #&amp;thj^% on 2019-04-02
I have seen this on other forums as well try:
```
wget -q -O - archive.kali.org/archive-key.asc | sudo apt-key add
sudo apt update
```
Let us know if this works.

---

