---
title: "Triggering from terminal output"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by emnaki on 2011-09-28
Is there a terminal program that I could trigger from its text output to run certain commands depending on the text matched? For example everytime the the text 'core dumped' appears I can automatically run the command 'cp core* ~/core/'?

---

### Post by acrazyplayer on 2011-09-30
It seems like you want to make some sort of script that will run the commands you need, if it sees a certain output then it will run your desired commands. I am not good at scripts but maybe someone else can help you. Some more info will be required for them to help so try and explain as much as possible.

---

### Post by LinuxRocks713 on 2011-09-30
```

if [ "`cat logfile | grep "core dumped"`" != "" ]; then cp core* ~/core/; fi

```

---

