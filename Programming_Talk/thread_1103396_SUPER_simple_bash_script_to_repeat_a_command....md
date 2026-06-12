---
title: "SUPER simple bash script to repeat a command..."
date: 2009-03-22
forum: Programming Talk
---

### Post by robfindlay on 2009-03-22
I need to repeat this command on a configurable interval:

igal -a -r -U -w 6

I tried this:
```

#!/bin/bash

igal -a -r -U -w 6

sleep 30

```

Just a guess that it MIGHT work.

Can anyone point me in the right direction?

-R

---

### Post by stroyan on 2009-03-22
```

#!/bin/bash

while sleep 30
do
  igal -a -r -U -w 6
done

```

---

### Post by robfindlay on 2009-03-22
> **stroyan said:**
> ```

#!/bin/bash

while sleep 30
do
  igal -a -r -U -w 6
done

```

THANK YOU! 

does the integer of 30 ALWAYS mean 30 seconds? 


-Rob

---

### Post by geirha on 2009-03-22
> **robfindlay said:**
> 
does the integer of 30 ALWAYS mean 30 seconds? 


Seconds is the default, yes.
```
man sleep
```

---

### Post by monkeyking on 2009-03-22
you should also be able to use 'watch' instead
like

[PHP]
watch igal -a -r -U -w 6
[/PHP]
or if you want the 30 sec interval

[PHP]
watch -n 30 igal -a -r -U -w 6
[/PHP]

---

