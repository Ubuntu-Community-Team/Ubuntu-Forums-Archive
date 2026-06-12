---
title: "Python urllib2 load only x number of lines"
date: 2009-05-09
forum: Programming Talk
---

### Post by Pyro.699 on 2009-05-09
Hey,

Using urllib2, how do you load just the first (as an example) 10 lines of a web page?

```

import urllib
load = urllib.urlopen('www.google.com') #Need to only load first 10 lines
html = load.read() #I know i could use load.read(bytes) but i just need lines

```

I need to use this cause the webpage I'm loading is around 3mb, and i only need the first few lines from it, but if i was to load the entire webpage it would eat bandwidth like crazzy.

Thanks
~Cody Woolaver

---

