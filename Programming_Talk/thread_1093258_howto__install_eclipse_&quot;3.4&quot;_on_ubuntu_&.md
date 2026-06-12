---
title: "howto : install eclipse &quot;3.4&quot; on ubuntu &quot;8.10&quot;, linking to /usr/bin"
date: 2009-03-11
forum: Programming Talk
---

### Post by crazy ivan on 2009-03-11
Just had a bit of frustration I want to spare you.. 
Since the packaged Eclipse 3.2 is not supported any more by a lot of plugins, I downloaded the 3.4 binaries from the ([ official website]("http://www.eclipse.org")). Everything went straightforward.. Unpacking to /opt/eclipse launching ./eclipse in that folder.
Now i thought I'd link it up by ```
sudo ln -f /usr/bin/eclipse /opt/eclipse
```. But this yields the error "The Eclipse executable auncher was unable to locate its companion shared library." Tweaking the eclipse.ini to the proper path changed nothing (thats what actually frustrated me), but changing it to wrong paths brought ./eclipse to produce the same error. 

Long story, short workaround:
here is my new /usr/bin/eclipse

```

#! /bin/bash
cd /opt/eclipse
./eclipse

```

Don't forget to make it executable ```
 sudo chmod 755 /usr/bin/eclipse 
``` after editing it.

In case you want some further customization (Desktop icons.. ) check out the [ubuntu wiki article]("https://help.ubuntu.com/community/EclipseIDE")

---

### Post by dmizer on 2009-03-16
Moved to Programming talk. :)

---

