---
title: "Shortcut"
date: 2010-08-12
forum: Programming Talk
---

### Post by deejay_wonder on 2010-08-12
Hi,

I need a command for ctrl+w which Can be executed from a terminal - the command should close a tab in arora 

Thanks

---

### Post by deejay_wonder on 2010-08-12
Here is my simple script. The control+W should close the tab, but I do not know the exactly code for that which can be executed from a bash script. Killall is not what I want

```
#!/bin/bash
while true; do
firefox gmail.com	&
sleep	12
ctrl+w
done
```

---

