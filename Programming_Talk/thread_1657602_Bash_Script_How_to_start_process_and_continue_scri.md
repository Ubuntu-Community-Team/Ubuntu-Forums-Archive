---
title: "Bash Script: How to start process and continue script execution?"
date: 2011-01-01
forum: Programming Talk
---

### Post by Ek0nomik on 2011-01-01
I have a very simple bash script (which is going to be executed as a result of an HTTP request served up to Apache) which checks to see if a process is running, and if it's not I want to start the process and then continue on with the bash script so I can actually hand the user back an HTML response.

The issue is, when I execute the command which starts the process (it's starting up Java by calling up a .jar file), the bash script is hanging on that execution and not continuing with the script.  I believe it's just waiting for that execution to finish with an exit code so it can continue with the script, but I don't want it to.  I just want it to spawn the process and keep moving.

I haven't done much bash scripting, so help would be appreciated.

ek0nomik

---

### Post by johnl on 2011-01-01
You need to add **&** to the end of your command to tell bash to fork the process off in the background.


e.g.

```

#!/usr/bin/env bash

echo "starting..."
java -jar /my/file.jar &
echo "done"

```

---

