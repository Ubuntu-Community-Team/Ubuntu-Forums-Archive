---
title: "apt-get upgrade VS apt-get dist-upgrade"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by Majorix on 2012-04-08
Is it necessary or recommended to do
```
sudo apt-get upgrade
```
first or can I safely go ahead and directly run
```
sudo apt-get dist-upgrade
```
provided I
```
sudo apt-get update
``` first?

---

### Post by zandman on 2012-04-08
Based on previous experiences i would say that a direct distribution upgrade doesn't require to do the update first.
So all you need to do is to start "sudo apt-get dist-upgrade".

And if you run the update from command-line:
sudo apt-get update
sudo apt-get upgrade
is to get it completely done. But that's most likely what you meant by the "provided i Code.... first?"

---

### Post by jerrrys on 2012-04-09
[http://ubuntuforums.org/showthread.php?t=1952199](http://ubuntuforums.org/showthread.php?t=1952199)

---

