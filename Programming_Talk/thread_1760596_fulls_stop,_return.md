---
title: "fulls stop, return"
date: 2011-05-17
forum: Programming Talk
---

### Post by scorpious on 2011-05-17
I want to create a programme that when run, will send a full stop then an enter over and over again as if I was typing it myself.

any idea's?

---

### Post by r-senior on 2011-05-17
man yes :D

---

### Post by CoffeeRain on 2011-05-17
As in a command? I could help you with just printing periods, but I don't know about using them as input to something. Could you explain a bit more?

---

### Post by roccivic on 2011-05-17
Open a terminal and execute this (use CTRC+C to quit):

```
while true; do echo -n "."; sleep 1; echo ""; sleep 1; done
```

or paste this into a text file, say "myscript.sh":

```
#!/bin/bash

while true; do
  echo -n ".";
  sleep 1;
  echo "";
  sleep 1;
done
```

then execute:

```
chmod +x /path/to/myscript.sh
/path/to/myscript.sh
```

---

### Post by scorpious on 2011-05-17
> **CoffeeRain said:**
> Could you explain a bit more?

Ok the other day i found that by repeatedly pressing any button followed by return, i could post multiple comments on someones Facebook profile. My friend set her account to send her a text message when someone comments so she suddenly got about a hundred messages from Facebook.

I figured I'd be much better of running some sort of script that would do this for me :popcorn:

---

### Post by r-senior on 2011-05-17
Wouldn't that constitute a denial of service attack?

---

### Post by scorpious on 2011-05-17
not sure. guess I'll find out

---

### Post by roccivic on 2011-05-17
What you want is the xsendkeycode command. You can install it with:
```
sudo apt-get install lineakd
```

Google for usage.

---

