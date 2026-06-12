---
title: "c-programming missing lib files"
date: 2006-04-14
forum: Programming Talk
---

### Post by monkeyking on 2006-04-14
Hey,
I wanted to do some c-programming.
But ubuntu didn't have make og gcc installed.
So I did a quick app-get.
And now I can compile, but it seems like it doesnt know where to look up
the h files like

#include<stdlib.h>

thanks.

By the way I installed gcc 4.0

---

### Post by xenmax on 2006-04-14
Try ```
sudo apt-get install build-essential
```

---

### Post by monkeyking on 2006-04-14
That did it, I guess.

Thanks mate.

---

