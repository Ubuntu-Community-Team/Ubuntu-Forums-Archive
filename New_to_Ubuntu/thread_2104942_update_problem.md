---
title: "update problem"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by shek092036 on 2013-01-14
I am having a problem updating my softwares and system updates..

it is showing the error
"Failed to download repository information
check your internet connection"

it is also showing errors that "cannot update because you have broken packages"

i have a 11.10 version of ubuntu.. pls help[SIZE=3][B]:p
[/B][/SIZE]

---

### Post by John_Swing on 2013-01-14
Hello,

To correct broken packages use the following command :

```
sudo apt-get -f install
```

For your internet error, try changing the repository in software-sources.

Regards.

John

PS: See this [thread]("http://ubuntuforums.org/showthread.php?t=947124") for more information on broken packages.

---

### Post by ibjsb4 on 2013-01-14
You can also try ..

[Opening a terminal and enter:]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

```
sudo apt-get update
```

Get any errors?  Please post using code tags.

[ATTACH]230072[/ATTACH]
[]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

---

