---
title: "kill command in simple bash-script"
date: 2012-10-23
forum: Programming Talk
---

### Post by zeezam on 2012-10-23
I'm trying to make a simple bash script that restarts firefox.

My script get stuck on the kill command and doesn't exit correct.

Any ideas?

```

#!/bin/bash
echo pid
PID=` ps -ef | grep firefox | grep -v grep | awk '{print $2}'`

`kill $PID`

done

```

---

### Post by Lars Noodén on 2012-10-23
You might use pgrep instead.

```

kill -HUP $(pgrep -x firefox)

```


Or come to think of it, you could use [pkill](http://manpages.ubuntu.com/manpages/precise/en/man1/pkill.1.html) directly.


```

pkill -x firefox

```

---

### Post by zeezam on 2012-10-23
> **Lars Noodén said:**
> You might use pgrep instead.

```

kill -HUP $(pgrep -x firefox)

```



Flawless! :)

---

### Post by Paddy Landau on 2012-10-23
I like pkill better, as it is simpler.

The problem with your first attempt is that there may be more than one process with "firefox". For example, the Flash plugin on my machine has a process that satisfies your query.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others.

---

