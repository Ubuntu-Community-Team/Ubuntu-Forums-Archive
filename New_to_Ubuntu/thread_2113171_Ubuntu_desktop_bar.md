---
title: "Ubuntu desktop bar"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by Don Martin on 2013-02-06
Is there a way to change the top bar on the Ubuntu 12.04 desktop.  I'd like to remove the word 'desktop' on the left side of the bar, and on the right side I'd like to have the option of removing the Evolution envelope icon or adding it later if I should start using twitter and such things.

Don

---

### Post by Frogs Hair on 2013-02-06
There are some options to remove or hide some items in the dconf Editor.
```
sudo apt-get install dconf-tools
```
The envelope can be removed along with everything in that menu.
```
sudo apt-get remove indicator-messages
```   
Log out and back in

---

