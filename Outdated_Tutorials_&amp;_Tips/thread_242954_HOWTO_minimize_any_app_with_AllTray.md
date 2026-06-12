---
title: "HOWTO: minimize any app with AllTray"
date: 2006-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by k420 on 2006-08-24
First edit your apt sources list
```
sudo gedit /etc/apt/sources.list
```

add inside of this file he repo addresses
```
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
```

save and close your editor
then:
```
sudo apt-get update
```
```
sudo apt-get install alltray
```

after the install the applications will appear in accessories

---

