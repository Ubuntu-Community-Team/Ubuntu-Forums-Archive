---
title: "Bash script OR condition"
date: 2007-03-02
forum: Programming Talk
---

### Post by hollebolle on 2007-03-02
Hi all, probably a simple question.
The following script set my background to a random jpg from the specified folder.

```
#!/bin/bash
NIMGS=`find /media/commondrive/Pictures/wallpapers -iname '*.jpg' | tr -d ' '`
IMGS=`find /media/commondrive/Pictures/wallpapers -iname '*.jpg' -printf "%p#"`
N=`echo $NIMGS | wc -w`
((N=RANDOM%N))
BGNAME=`echo $IMGS | cut -d '#' -f $N`
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$BGNAME"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"

```

The probem is that I want to include png's too. Logically that would mean that it should look for *.jpg OR .*png. But how to do that.
Tried ('*.jpg' || '*.png') and '*.jpg' || '*.png' but no luck.
What am I missing?

Thx

---

### Post by ghostdog74 on 2007-03-02
try this
```

find . \( -name "*jpg" -o -name "*png" \) -print

```

---

### Post by hollebolle on 2007-03-02
Sweet, thats perfect...
Thx a bunch

---

