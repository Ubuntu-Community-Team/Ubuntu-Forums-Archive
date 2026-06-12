---
title: "How to uninstall java 9"
date: 2015-09-30
forum: New to Ubuntu
---

### Post by flex567 on 2015-09-30
I installed Java 9 this way([http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html](http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html))
```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java9-installer
```

 and I would like to remove it because it doesn't work with some applications. How can I completely remove it?

---

### Post by dino99 on 2015-09-30
install ppa-purge if it is not yet done; then from a terminal:

sudo ppa-purge ppa:webupd8team/java

---

### Post by slickymaster on 2015-09-30
Open a terminal window (Ctrl+Alt+T) and run the following```
sudo apt-get purge oracle-java9-installer
```Once that done, remove the PPA itself from your system, running```
sudo add-apt-repository --remove ppa:webupd8team/java
```

---

### Post by flex567 on 2015-09-30
> [COLOR=#000000]install ppa-purge if it is not yet done; then from a terminal:[/COLOR]

[COLOR=#000000]sudo ppa-purge ppa:webupd8team/java[/COLOR]

thanx

What is this ppa-purge ?

---

### Post by flex567 on 2015-09-30
I first used this method: 
> [COLOR=#000000]install ppa-purge if it is not yet done; then from a terminal:[/COLOR]

[COLOR=#000000]sudo ppa-purge ppa:webupd8team/java[/COLOR] 

and after that the second one: 
> [COLOR=#000000]Open a terminal window (Ctrl+Alt+T) and run the following[/COLOR][COLOR=#000000]Code:
sudo apt-get purge oracle-java9-installer[/COLOR]
[COLOR=#000000]Once that done, remove the PPA itself from your system, running[/COLOR][COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo add-apt-repository --remove ppa:webupd8team/java[/FONT][/COLOR]

It looks like the first method didn't remove it completely because the 2nd method did some work.

---

### Post by TokyoGhost on 2015-09-30
Isn't icedtea better alternative than java?

---

### Post by QIII on 2015-09-30
The topic is the removal of Oracle Java 9, not the comparative merits of Oracle Java and OpenJDK.

Please keep it to the OP's question, please.

---

