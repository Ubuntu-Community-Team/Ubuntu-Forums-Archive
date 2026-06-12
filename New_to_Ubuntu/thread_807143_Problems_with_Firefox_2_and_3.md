---
title: "Problems with Firefox 2 and 3"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-25
After reading the PC World article listed below, it answered a suspicion I had about Firefox 2. That it leaks memory. Wondered why my browsing got slower and slower over time. Article also said version 3  "can bring Linux systems to their knees". How would I fix the memory leak in version 2? Thanks.

Article:

[http://www.pcworld.com/article/id,146296/article.html](http://www.pcworld.com/article/id,146296/article.html)

---

### Post by sayakb on 2008-05-25
This is not a solution, but this is what I do. Add the Force quit applet to the panel. After prolonged usage (about an hour or so), force quit and restart firefox (or set FF3 to save existing pages when quitting). This way, the memory usage comes down, and you don't lost your work as well. You might also create a script with a launcher on the panel:
```
#!/bin/bash
killall firefox
firefox &
```

---

