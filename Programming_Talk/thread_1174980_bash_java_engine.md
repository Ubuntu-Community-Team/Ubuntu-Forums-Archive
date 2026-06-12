---
title: "bash java engine"
date: 2009-05-31
forum: Programming Talk
---

### Post by gishaust on 2009-05-31
Hi everyone

I have created a bash file to open my java program. I have the bash working fine except ubuntu brings up four options run in terminal, display, run, exit.

What I want to know is how do create an Icon for linux lovers that will do the following when you double click the icon it will

1. open a terminal.
2. run the program.
3. not bring up the other display box.

```

#!/bin/bash
java -jar timer.jar

```

---

### Post by SupaSonic on 2009-06-01
Copy the script to /usr/bin and then point the launcher to it by name, without a path maybe?

So if your script name is 'javalauncher', copy it to /usr/bin and then in launcer properties use command 'javalauncher'. Not sure that'll work though.

---

