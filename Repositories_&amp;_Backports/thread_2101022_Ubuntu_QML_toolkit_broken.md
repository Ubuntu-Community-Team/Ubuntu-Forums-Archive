---
title: "Ubuntu QML toolkit broken?"
date: 2013-01-03
forum: Repositories &amp; Backports
---

### Post by digimyth on 2013-01-03
Hi all,

I'm using backbox linux (is based on ubuntu 12.04 and the only difference is that is using xfce4 instead of unity) and i tried to install QML toolkit by following the instructions here 
[https://developer.ubuntu.com/get-started/gomobile/#step-get-toolkit](https://developer.ubuntu.com/get-started/gomobile/#step-get-toolkit) but my problem is that can't find the following packages  (from step 2):
```

qt-components-ubuntu  qt-components-ubuntu-demos qt-components-ubuntu-examples  qt-components-ubuntu-doc notepad-qml                                                 

```
Actually i found this problem when i tried to create the "hello world" program (in this case called CurrencyConverter) because the QTCreator editor couldn't find the following package:
```

import Ubuntu.Components 0.1

```
What can i do?

thanks in advance

---

### Post by digimyth on 2013-01-03
I found the answer. Here is [http://askubuntu.com/questions/235440/how-do-i-install-the-qml-toolkit-on-12-04](http://askubuntu.com/questions/235440/how-do-i-install-the-qml-toolkit-on-12-04)

> 
The issue is they only have packages for Quantal and not Precise so   this fix works as well while still getting updates.
      Replace precise with your version of ubuntu.:
```

sudo add-apt-repository ppa:ui-toolkit/ppa
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list.d/ui-toolkit-ppa-precise.list
sudo apt-get update && sudo apt-get install qt-components-ubuntu qt-components-ubuntu-demos qt-components-ubuntu-examples qt-components-ubuntu-doc notepad-qml
```An other option is to download and install manually from here 
[https://launchpad.net/~ui-toolkit/+archive/ppa/+sourcepub/2907241/+listing-archive-extra](https://launchpad.net/~ui-toolkit/+archive/ppa/+sourcepub/2907241/+listing-archive-extra)

---

