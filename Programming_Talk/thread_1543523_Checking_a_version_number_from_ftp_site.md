---
title: "Checking a version number from ftp site"
date: 2010-08-01
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-08-01
Well not really an ftp site but it was a space friendly definement (is that a word?).

So my 'task' is to get the latest version number from the 'VLC releases index site' automatically everytime a new one comes (currently 1.1.2):
[html]http://downloads.videolan.org/vlc/[/html]

All the suggestions of perl/bash/python/etc. are welcome but I'd appreciate a non-ugly & portable solution meaning that it's preferably short and/or wouldn't require the installation of any weird packages that nobody has. 

A good example would be to just wget the htm index file (since it's only 60kB) and do a grep/sed/awk/whatever.

Yeah, so thanks! Once again have some pop corn: :popcorn:. If you are on a slimming diet, give them back.

---

### Post by Bachstelze on 2010-08-01
It would make your life much easier if the latest/ link was actually updated to point to the latest version, as I guess it's supposed to be.  Right now, I gues it's safe to assume that the latest version is the one just before the "SuSE" entry, so you can get it with:

```
firas@tsukino ~ % wget http://downloads.videolan.org/vlc/ -qO - | grep -iC 1 suse | egrep -om 1 '[0-9]+\.[0-9]+\.[0-9]+'
1.1.2

```

wget fetches the page and outputs it to stdout
grep filters it to display only the "suse" line, plus the lines immediately above and below it
egrep filters it to display only the first chunk of text that is of the form <digits>.<digits>.<digits>, where <digits> can be any non-zero number of digits betwen 0 and 9

---

### Post by ghostdog74 on 2010-08-01
```

url='http://downloads.videolan.org/vlc/'
wget -O- -q "$url" | sed -e 's/^.*href="//;s/\/.*//' -ne '/^[0-9.]/p'|tail -1

```

Now, start reading up!

---

### Post by Intrepid Ibex on 2010-08-01
Thanks very much for both of you! Too bad the pop corn wasn't of any interest since it's still there.

> **Bachstelze said:**
> It would make your life much easier if the latest/ link was actually updated to point to the latest version, as I guess it's supposed to be.
Exactly, which is why I created this topic since it's (together with the "last" folder) about VLC 1.1.0 instead of 1.1.2.

Wonderful explanation about your 'script' by the way. You are being a big help to me.

> **ghostdog74 said:**
> Now, start reading up!
You mean like I should start reading up Bash tutorials or.. =P~

---

### Post by Intrepid Ibex on 2010-08-03
> **Bachstelze said:**
> ```
firas@tsukino ~ % wget http://downloads.videolan.org/vlc/ -qO - | grep -iC 1 suse | egrep -om 1 '[0-9]+\.[0-9]+\.[0-9]+'
1.1.2

```
Btw. just noticed that this outputs 1.1.2 twice because both the links name and the text itself is 1.1.2 in the htm file:
[html]<a href="1.1.2/">1.1.2</a>...[/html]

Thus the "[COLOR="Green"]| tail -1[/COLOR]" the scary ghost dog posted is also required.

---

### Post by Bachstelze on 2010-08-03
> **Intrepid Ibex said:**
> Btw. just noticed that this outputs 1.1.2 twice because both the links name and the text itself is 1.1.2 in the htm file:
[html]<a href="1.1.2/">1.1.2</a>...[/html]

Thus the "[COLOR="Green"]| tail -1[/COLOR]" the scary ghost dog posted is also required.

Yes indeed, it seems the -m parameter behaves differently in GNU grep and BSD grep... You can omit it, then.

---

### Post by Intrepid Ibex on 2010-08-03
I'm still waiting for the day when you are wrong :).

---

