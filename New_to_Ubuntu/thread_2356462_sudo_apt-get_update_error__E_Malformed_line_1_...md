---
title: "sudo apt-get update error : E: Malformed line 1 .."
date: 2017-03-23
forum: New to Ubuntu
---

### Post by nypep on 2017-03-23
I tried to install boot-repair but it failed
I typed in terminal:

1)  sudo add-apt-repository ppa:yannubuntu/boot-repair

Answer:
> 
Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpw8po4pz1/secring.gpg' created
gpg: keyring `/tmp/tmpw8po4pz1/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpw8po4pz1/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK





2)sudo apt-get update
Answer:

> E: Malformed line 1 in source list /etc/apt/sources.list.d/google-chrome.list (dist parse)
E: The list of sources could not be read.

Content of :
/etc/apt/sources.list.d/google-chrome.list is :
> 
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main


I searched but i couldn't find something similar to this.
What should I do?
Thanks anyways

---

### Post by deadflowr on 2017-03-23
Delete the first two deb lines in the google-chrome.list file.
And then move the stable a space over in the one that is left
Yours says
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/stable main
```
it should say
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```

hope it helps

---

### Post by nypep on 2017-03-23
Thank you very much ! It's fixed!

---

