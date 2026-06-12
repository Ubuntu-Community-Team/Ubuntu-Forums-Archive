---
title: "[Bash] Return to Prompt After Executing GUI"
date: 2011-11-25
forum: Programming Talk
---

### Post by dodle on 2011-11-25
I have a bash script that launches a GUI, but when I execute it from a terminal I have to wait until the GUI closes to get back to the prompt. How can I tell the script to finish executing after I launch the GUI? I know that Firefox does this. Windows does this with the *start* command.

**--- EDIT ---**
Never mind, just found the answer here: [http://ubuntuforums.org/showthread.php?p=4329301&highlight=bash+return+prompt#post4329301](http://ubuntuforums.org/showthread.php?p=4329301&highlight=bash+return+prompt#post4329301)

```
#! /bin/bash

/program/to/execute &
```

---

