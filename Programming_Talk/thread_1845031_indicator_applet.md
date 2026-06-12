---
title: "indicator applet"
date: 2011-09-16
forum: Programming Talk
---

### Post by raja.genupula on 2011-09-16
how can i create indicator applet for my personal usage , i mean adding something to top panel in 11.04 . 

thanks in advance .

---

### Post by raja.genupula on 2011-09-17
please guys help me

---

### Post by SecretCode on 2011-09-17
[unity indicator - Google Search](http://www.google.com/search?client=ubuntu&channel=fs&q=unity+indicator&ie=utf-8&oe=utf-8&gl=za)

First result: [Application Indicators](http://unity.ubuntu.com/projects/appindicators/)

which contains link: "[Technical Overview](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators) with code samples"

---

### Post by raja.genupula on 2011-09-17
thanks for your reply .
thank you very much .

---

### Post by reda_ea on 2011-09-17
**EDIT**
...and a crappy webpage
[http://sites.google.com/site/redaea/cappind-py]("http://sites.google.com/site/redaea/cappind-py")
**/EDIT**

Here's a small python tool I made that creates a menu from standard input.
I posted about it in tips section but it still won't show up :/

anyway, it takes input in lines with the form "menu:submenu:..:element" and outputs back the chosen path

quick example, one i'm using right now for quick access to my ssh servers
```

cat $HOME/.ssh/config |
	grep "^[Hh]ost\b" |
	sed "s/^[Hh]ost\b\s*//g" |
	sed "s/\_/__/g" |
	./cappind.py -p |
	while read s; do
		gnome-terminal -x ssh "`echo $s | sed "s/\_\_/_/g"`"
	done

```

experiment with it and you'll see
```
./cappind/py -h
```

---

### Post by raja.genupula on 2011-09-17
> **reda_ea said:**
> Here's a small python tool I made that creates a menu from standard input.
I posted about it in tips section but it still won't show up :/

anyway, it takes input in lines with the form "menu:submenu:..:element" and outputs back the chosen path

quick example, one i'm using right now for quick access to my ssh servers
```

cat $HOME/.ssh/config |
    grep "^[Hh]ost\b" |
    sed "s/^[Hh]ost\b\s*//g" |
    sed "s/\_/__/g" |
    ./cappind.py -p |
    while read s; do
        gnome-terminal -x ssh "`echo $s | sed "s/\_\_/_/g"`"
    done

```experiment with it and you'll see
```
./cappind/py -h
```

great program , thanks for this man . 
i will try it when i get back to my system ,.

---

