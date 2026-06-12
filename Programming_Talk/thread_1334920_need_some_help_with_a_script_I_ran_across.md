---
title: "need some help with a script I ran across"
date: 2009-11-22
forum: Programming Talk
---

### Post by OrangeCrush112 on 2009-11-22
I preface this by saying that I am in no way a 'programmer'; I only know the bare minimum, I'm sad and a bit embarrassed to say.

However, I ran across this and it interested me.

```
#!/bin/bash

echo "Starting up"

mpg123 /path/to/nice/music/* &

for (( i = 1; i <= 100; i++ )) do
    echo "Setting volume at $i"
    setmixer vol $i
    echo "Sleeping 10 seconds..."
    sleep 10s
done

```

along with an entry to your crontab, its an alarm clock that plays an mp3 of your choice.
However, even though I've gotten some of the kinks out on my own, I'm still having these problems:
1. What exactly is signified by 'mpg123,' the filename?
and 2. Bash does not recognize the command 'setmixer.' How can I fix that?

Please and thank you. :)

---

### Post by Barriehie on 2009-11-22
> **OrangeCrush112 said:**
> I preface this by saying that I am in no way a 'programmer'; I only know the bare minimum, I'm sad and a bit embarrassed to say.

However, I ran across this and it interested me.

```
#!/bin/bash

echo "Starting up"

mpg123 /path/to/nice/music/* &

for (( i = 1; i <= 100; i++ )) do
    echo "Setting volume at $i"
    setmixer vol $i
    echo "Sleeping 10 seconds..."
    sleep 10s
done

```

along with an entry to your crontab, its an alarm clock that plays an mp3 of your choice.
However, even though I've gotten some of the kinks out on my own, I'm still having these problems:
1. What exactly is signified by 'mpg123,' the filename?
and 2. Bash does not recognize the command 'setmixer.' How can I fix that?

Please and thank you. :)

1> mpg123 is an mpg music player

2> Google reveals that setmixer is a package in dapper

Barrie

---

