---
title: "Problems installing Ubuntu 14.04 dual boot with windows 8.1 UEFI"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by sdvf on 2014-04-19
Hi. I-m trying install the last version of Ubuntu, but when im going to install a boot repair to make a dual boot with Windows it gives me this error after "sudo apt-get update", E: Some index files failed to download. They have been ignored, or old ones used instead.



Because of that(i think), after enter "sudo apt-get install boot-repair" it gives me the message "E: Unable to locate package boot-repair".


What can i do?

---

### Post by sandyd on 2014-04-19
Hi, it seems that boot-repair has not been uploaded for 14.04 (Trusty) yet.

I have sent an email to the person providing the repository to ask them to build for 14.04.

---

### Post by robgraves on 2014-04-19
Hi, i got this to go through by issuing the following commands:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

---

