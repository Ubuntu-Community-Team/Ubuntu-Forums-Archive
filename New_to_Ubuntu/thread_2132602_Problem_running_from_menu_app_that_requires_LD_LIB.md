---
title: "Problem running from menu app that requires LD_LIBRARY_PATH"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by GreatBunzinni on 2013-04-05
I need to run an application which only runs properly if LD_LIBRARY_PATH contains a specific path.  When I run that app from the command line, after I export LD_LIBRARY_PATH, the app runs properly.  

I've added the export line to /etc/bash.bashrc, and it appears that all terminals I open do have the LD_LIBRARY_PATH properly set.  With this, it became possible to run the app from any terminal without having to set the LD_LIBRARY_PATH first.

Unfortunately, in spite of the environment variable being set in each terminal, running the app by clicking an icon from the menu doesn't work, as the app throws an error message telling the user to properly set LD_LIBRARY_PATH.

So, my question is: does anyone know how to set LD_LIBRARY_PATH so that it's possible to run apps from the menu?

---

### Post by The Cog on 2013-04-05
I'm not sure it's a good idea to make this LD_LIBRARY_PATH global to your desktop, even if you can.
I would suggest that you try one of the following:
Change the command line configured in the launcher from "programname" to "LD_LIBRARY_PATH=whatever programname", which will set the path just for that command. If you can't do that, create a small script like:
```
#!/bin/sh
export LD_LIBRARY_PATH=whatever
programname
```and then launch the script instead of launching the program directly.

---

### Post by GreatBunzinni on 2013-04-05
Thanks for the help.  I've followed your suggestion and, although it's a bit hack-ish, it works.  Basically, I've did both: created a small script that includes the export LD_LIBRARY_PATH and added a new launcher which calls the script instead of the app.  And it works.

Again, thanks for the help.

---

