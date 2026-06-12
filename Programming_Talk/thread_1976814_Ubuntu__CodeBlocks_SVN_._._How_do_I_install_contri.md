---
title: "Ubuntu / Code::Blocks SVN . . How do I install contrib-plugins? (Pasgui PPA)"
date: 2012-05-09
forum: Programming Talk
---

### Post by Jynks on 2012-05-09
I decided to use the PPA offered by Pasgui but the contrib plugins did not install and I do not know how to install them...

[https://launchpad.net/~pasgui/+archive/ppa/](https://launchpad.net/~pasgui/+archive/ppa/)


```
sudo add-apt-repository ppa:pasgui/ppa
sudo apt-get update
sudo apt-get install codeblocks

```

The above sets the ppa and installs his build of code::blocks fine (I think it was 3 days old) I do not know the command to install the contrib-plugins ... any ideas?

---

### Post by Vaphell on 2012-05-09
that ppa doesn't provide the package according to its list of packages

```
apt-cache search contrib | grep codeblocks
```
or something like that to check if they are available in your currently enabled repos

---

