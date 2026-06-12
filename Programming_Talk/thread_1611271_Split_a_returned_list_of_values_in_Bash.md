---
title: "Split a returned list of values in Bash?"
date: 2010-11-01
forum: Programming Talk
---

### Post by fuzzyslippers on 2010-11-01
I have the code [PHP]#!/bin/sh
curl http://thepiratebay.org/top/all --silent -O temp1
TEMP="cat temp1"
URLLIST='$TEMP | grep "<div.*><a href=.*>.*</a>" | sed -e"s@<div.*><a@@g" | sed -e"s@</a></div>@@g" | grep ".*href=.*" | sed -e "s@href=@@g" -e "s@class=.*>@@g" -e "s@\" .*@@" -e "s@\"@@g" -e "s@.*/@http://thepiratebay.org/@g"'
OLD_IFS="$IFS"
IFS="\n"
for s in $URLLIST; do 
    echo $s
done[/PHP]
which I would like to index the top 100 torrents from The Pirate Bay, but when I run the script, it only returns the actual text from the variable, any suggestions?:confused:

---

### Post by spjackson on 2010-11-01
> **fuzzyslippers said:**
> [PHP]#!/bin/sh
curl http://thepiratebay.org/top/all --silent -O temp1
TEMP="cat temp1"
URLLIST='$TEMP | grep "<div.*><a href=.*>.*</a>" | sed -e"s@<div.*><a@@g" | sed -e"s@</a></div>@@g" | grep ".*href=.*" | sed -e "s@href=@@g" -e "s@class=.*>@@g" -e "s@\" .*@@" -e "s@\"@@g" -e "s@.*/@http://thepiratebay.org/@g"'
[/PHP]
I think you intended backticks here, not single-quotes, but $() is better, thus:
```

URLLIST=$($TEMP | grep "<div.*><a href=.*>.*</a>" | sed  -e"s@<div.*><a@@g" | sed -e"s@</a></div>@@g" |  grep ".*href=.*" | sed -e "s@href=@@g" -e "s@class=.*>@@g" -e "s@\"  .*@@" -e "s@\"@@g" -e "s@.*/@http://thepiratebay.org/@g")

```

---

### Post by fuzzyslippers on 2010-11-01
Thanks a lot, I feel dumb for not realizing that >.<

---

