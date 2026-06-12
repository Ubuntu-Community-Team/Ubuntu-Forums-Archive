---
title: "Code::Blocks 10.5"
date: 2010-08-24
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-08-24
Will Ubuntu update code:blocks to the new version ?

---

### Post by X.Cyclop on 2010-08-25
Ubuntu only updates packages if there was found a bug in it, not when there's new features.:) So you can download the new version (10.5) from the [Official site]("http://www.codeblocks.org/downloads/26#linux").

---

### Post by sgtGarcia on 2010-08-25
Or You can add external repositories (now version 10.05svn6525 but it's updated nightly if I'm not wrong).

Code::Blocks
Add the following lines to your /etc/apt/sources.list :
```

deb http://apt.jenslody.de/ any main
deb-src http://apt.jenslody.de/ any main

```
& key
```

sudo apt-get update
sudo apt-get install jens-lody-debian-keyring

```

You are going to need new wx-widget
```

deb http://apt.wxwidgets.org/ lenny-wx main

```
& it's key
```

wget -q http://apt.wxwidgets.org/key.asc -O-  | sudo apt-key add -

```

---

