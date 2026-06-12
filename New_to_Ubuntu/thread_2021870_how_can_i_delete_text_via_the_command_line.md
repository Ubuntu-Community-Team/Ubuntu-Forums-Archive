---
title: "how can i delete text via the command line"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-07-09
i use "iwlist wlan0 scan" to scan for wifi then i use "grep essid" to get the line with the essid which is "                    ESSID:"NETGEAR"". how can i delete the spaces and "ESSID:" so i only have "NETGEAR" left? is there a way with grep?

---

### Post by glennric on 2012-07-09
You can pipe the output to sed, awk, or cut and manipulate the text using those utilities.  For example
```
iwlist wlan0 scan | grep ESSID | sed 's/ESSID: //'
```
You may need to adjust that a bit for the precise format the text is returned from iwlist in.

---

### Post by steeldriver on 2012-07-10
although personally I'm more comfortable with sed, I think awk would be a more natural choice in this case - something like: 

```
iwlist wlan0 scan | awk 'BEGIN {FS=":"}{if ($1 ~ /[ \t]*ESSID/) print $2;}'
```

---

### Post by asmoore82 on 2012-07-10
Just to mix things up: **cut** !

```
iwlist wlan0 scan | grep ESSID | cut -d\" -f2
```

> **z3nhakr said:**
> is there a way **[COLOR="Purple"]with grep[/COLOR]**?
:P
```
iwlist wlan0 scan | grep ESSID | grep -oE '"[^"]+"' | grep -oE '[^"]+'
```

---

### Post by SlugSlug on 2012-07-10
> **asmoore82 said:**
> Just to mix things up: **cut** !

```
iwlist wlan0 scan | grep ESSID | cut -d\" -f2
```
:P
```
iwlist wlan0 scan | grep ESSID | grep -oE '"[^"]+"' | grep -oE '[^"]+'
```


I love this forum :popcorn:

---

