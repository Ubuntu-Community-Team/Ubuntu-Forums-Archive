---
title: "Speeding up install/setup"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by jpdeaton on 2012-02-02
I do clean installs rather often. Is it possible to run some sort of script that will automatically install the packages I want and remove the ones I dont? Any other tips to speed things up?

---

### Post by uRock on 2012-02-02
You can create a command such as the following which will install with the install command and uninstall with the remove command, ```
sudo apt-get install name-of-package && sudo apt-get remove name-of-package
```Example;```
sudo apt-get install pidgin rhythmbox && sudo apt-get remove empathy banshee 
```

---

