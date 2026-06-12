---
title: "Keep external disk from pausing"
date: 2010-08-21
forum: Programming Talk
---

### Post by Nonno Bassotto on 2010-08-21
I have an external disk without a on/off switch. This means that it turns itself off after X minutes of inactivity.

This is a bit annoying, for two reasons. First, it is sometimes off when I need to access some files on it. Second, it is sometimes off when I do NOT need to access anything, but the OS thinks otherwise. So it happens that I am opening a file on the internal disk, or even just browsing the internet, and everything hangs until the disk is started, which takes several seconds.

I'd like to find a way to prevent it from switching off, unless I want to. A simple way would be something like
```

while [ 1 ]
  do touch SOMEFILEONTHEDISK
  sleep 100
done

```
but this is still not perfect. I'd like to actually switch it off sometimes.

So I'd need to continously poll it when it is mounted, and have it unmounted otherwise. Hence I need the script to detect whether the disk is mounted, and touch the file only in this case. How should I modify it?

And moreover, is there a less hackish solution to my problem?

---

### Post by Nonno Bassotto on 2010-08-21
Nevermind, this should work
```

#!/bin/bash

DIRECTORY=/media/disk/Backup/

while [ 1 ]
	do if [ -d "$DIRECTORY" ]
		then touch "$DIRECTORY"poll
	fi
	sleep 100
done

```

---

