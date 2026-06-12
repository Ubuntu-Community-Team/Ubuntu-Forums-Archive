---
title: "Bash rename file"
date: 2015-04-16
forum: Programming Talk
---

### Post by ayhankuru on 2015-04-16
rename problem :(

my script 

[https://gist.github.com/ayhankuru/ce1b366c0a43b8c0531d](https://gist.github.com/ayhankuru/ce1b366c0a43b8c0531d)
[https://gist.github.com/ayhankuru/ce91945d6ff95c94c6a7](https://gist.github.com/ayhankuru/ce91945d6ff95c94c6a7)
 output 
[https://gist.github.com/ayhankuru/8693934728979e5e9cb7](https://gist.github.com/ayhankuru/8693934728979e5e9cb7)

[https://github.com/ayhankuru/ytclear](https://github.com/ayhankuru/ytclear)

---

### Post by Vaphell on 2015-04-16
```
#!/bin/bash

function mp3name
{
    while read i; do
	name=$( ytclear <<< [COLOR="#0000FF"]"[/COLOR]$i[COLOR="#0000FF"]"[/COLOR] )
        mv [COLOR="#0000FF"]"[/COLOR]$i[COLOR="#0000FF"]"[/COLOR] [COLOR="#0000FF"]"[/COLOR]$name[COLOR="#0000FF"]"[/COLOR]
    done < <( find [COLOR="#0000FF"]"[/COLOR]$HOME/Müzik/$1[COLOR="#0000FF"]"[/COLOR] -type f -name '*.mp3' )
}
```

when you don't quote vars, they break into separate pieces if there is a whitespace. It's an unfortunate legacy of posix shells that causes orders of magnitude more problems than it solves.

check this out - here printf prints out each item it sees in [] on a separate line.
```
$ x='a b c d e f'
$ printf '[%s]\n' $x
[a]
[b]
[c]
[d]
[e]
[f]
$ printf '[%s]\n' "$x"
[a b c d e f]
```

as you can see shell split $x on every space and printf got to see 6 separate params instead of 1. "$x" preserves the value in one chunk.
TL;DR: always put your vars in ""

---

