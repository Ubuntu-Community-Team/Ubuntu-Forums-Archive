---
title: "script for mplayer to dump chapters"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by mimihu88 on 2011-12-14
a video dvd iso contains 15 chapters.
I want to separate each of them by a script to individual vob.
I've wrote a script:
```
for fl in *.iso
 do
   mplayer -chapter 1-1 -v -dumpstream -dumpfile ${fl}1.vob -dvd-device ${fl} dvd://1
 done
```
It can work out the 1st chapter of the iso.

How to wrote a better script so that it can separate all the 15 chapters to vobs accordingly in one time?:confused:

---

### Post by Vaphell on 2011-12-14
put another loop inside to parametrize chapter, for example
```

fl=FL
for chapter in {1..2}-{1..3}
do
  echo mplayer -chapter ${chapter} etc -dumpfile ${fl}_${chapter}.vob etc
done


mplayer -chapter 1-1 etc -dumpfile FL_1-1.vob etc
mplayer -chapter 1-2 etc -dumpfile FL_1-2.vob etc
mplayer -chapter 1-3 etc -dumpfile FL_1-3.vob etc
mplayer -chapter 2-1 etc -dumpfile FL_2-1.vob etc
mplayer -chapter 2-2 etc -dumpfile FL_2-2.vob etc
mplayer -chapter 2-3 etc -dumpfile FL_2-3.vob etc

```

---

### Post by mimihu88 on 2011-12-14
thank you for your reply!
i am totally newbie for linux and can't understand what you mean.

---

### Post by Vaphell on 2011-12-14
i mean: for each .iso file run additional nested loop that will enumerate chapter symbols to try one by one.

```
for [COLOR="Blue"]fl[/COLOR] in *.iso
do
  for [COLOR="DarkGreen"]chapter[/COLOR] in **{1..2}-{1..3}**
  do
    mplayer -chapter [COLOR="DarkGreen"]${chapter}[/COLOR] -v -dumpstream -dumpfile [COLOR="Blue"]${fl%.iso}[/COLOR]_[COLOR="DarkGreen"]${chapter}[/COLOR].vob -dvd-device [COLOR="Blue"]${fl}[/COLOR] dvd://1
  done
done
```

exact command is up to you, figure out what exactly changes in that mplayer line and what you need to nicely parametrize those chapters
{a..b} is a range from a to b,```
$ echo {1..3}
1 2 3
``` so if you want numbers in 1-15 range -> {1..15}.you can combine ranges together to produce all possible combinations of elements, like {a..b}{c..d}.
```
$ echo {1..2}:{3..4}
1:3 1:4 2:3 2:4
```
Define the range (in bold) according to your needs.
Also your dump file is some_name.iso1.vob. Consider dumping '.iso' part, for example with **${fl%.iso}**

Do yourself a favor and read about shell scripts a bit, you won't regret it.

---

### Post by mimihu88 on 2011-12-15
> **Vaphell said:**
> i mean: for each .iso file run additional nested loop that will enumerate chapter symbols to try one by one.

```
for [COLOR="Blue"]fl[/COLOR] in *.iso
do
  for [COLOR="DarkGreen"]chapter[/COLOR] in **{1..2}-{1..3}**
  do
    mplayer -chapter [COLOR="DarkGreen"]${chapter}[/COLOR] -v -dumpstream -dumpfile [COLOR="Blue"]${fl%.iso}[/COLOR]_[COLOR="DarkGreen"]${chapter}[/COLOR].vob -dvd-device [COLOR="Blue"]${fl}[/COLOR] dvd://1
  done
done
```

exact command is up to you, figure out what exactly changes in that mplayer line and what you need to nicely parametrize those chapters
{a..b} is a range from a to b,```
$ echo {1..3}
1 2 3
``` so if you want numbers in 1-15 range -> {1..15}.you can combine ranges together to produce all possible combinations of elements, like {a..b}{c..d}.
```
$ echo {1..2}:{3..4}
1:3 1:4 2:3 2:4
```
Define the range (in bold) according to your needs.
Also your dump file is some_name.iso1.vob. Consider dumping '.iso' part, for example with **${fl%.iso}**

Do yourself a favor and read about shell scripts a bit, you won't regret it.

What exactly I want is:
1:1 2:2 3:3 ...15:15 (15 chapters)
Among those combinations,how to rule out those unwanted?
Thanks very much for your help!
I'll read about shell scripts as much as possible.

---

### Post by Vaphell on 2011-12-15
define 'unwanted'
so general format is X:X? if that's the case then you go with simple range and use the variable twice
```
for chapter in {1..15}
do
  .... ${chapter}:${chapter} ...
done
```

---

### Post by mimihu88 on 2011-12-15
> **Vaphell said:**
> define 'unwanted'
so general format is X:X? if that's the case then you go with simple range and use the variable twice
```
for chapter in {1..15}
do
  .... ${chapter}:${chapter} ...
done
```

I made a little change as below and it's ok now!
> .... ${chapter}-${chapter} ...

Thanks a lot and I am very happy!:):):)

---

