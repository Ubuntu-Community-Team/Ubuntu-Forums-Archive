---
title: "[SOLVED] Install frostline"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Stargazer777 on 2008-05-30
I am trying to install frostline from the website frostline.com. When the download was complete, an icon appeared under applications>internet>frostwire. Every time I clicked on the icon though, nothing would happen. I also tried Applications>Accessories>Terminal: Sudo apt-get install frostwire, and frostwire was not found in Applications>Add/Remove.

---

### Post by /usr/bin/hacked? on 2008-05-30
Try running it in the terminal, and paste the error message you get. If you get ```
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```
(or similar) it is likely just a java error, try installing 1.4 or 1.5 and then try re-installing. 

or you could compile from source ;)

---

