---
title: "One launcher to launch multiple programs"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by jetersauce on 2008-09-18
How can I make a launcher that will run two programs? I tried to type this in the command line of the launcher

wine "/home/jason/.wine/drive_c/Games/Dynamix/Tribes/hudbot.exe" & wine "/home/jason/.wine/drive_c/Games/Dynamix/Tribes/Tribes.exe"

But I don't think I have it right.  I need the first one to launch THEN the second.

Then I tried making 

#!bin/bash
wine "/home/jason/.wine/drive_c/Games/Dynamix/Tribes/hudbot.exe"
wine "/home/jason/.wine/drive_c/Games/Dynamix/Tribes/Tribes.exe"

It would launch the 1st one but then wait for it to close before launching the second.  Plus it would ask if i wanted to run it every time.

Any help would be greatly appreciated :)

---

### Post by KIAaze on 2008-09-18
You're close. ;)

Try the following instead:

```
#!bin/bash
wine "/home/jason/.wine/drive_c/Games/Dynamix/Tribes/hudbot.exe" **&**
wine "/home/jason/.wine/drive_c/Games/Dynamix/Tribes/Tribes.exe"

```

"cmd1 **&&** cmd2": cmd2 is run only if cmd1 exits successfully. So it won't work for you since it will wait for hudbot to exit.

"cmd1 **&**": cmd1 is run and sent to the background, so you don't have to wait for it to finish.

And for your general *nix culture:
Another useful symbol: **|**
"cmd1 || cmd2": cmd2 is run only if cmd1 failed (exited unsuccessfully)
"cmd1 | cmd2": cmd2 uses output from cmd1 as input ("|" is called a "pipe")

---

