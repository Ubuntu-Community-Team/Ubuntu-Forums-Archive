---
title: "Running a program from .sh file."
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Corvidae on 2013-02-10
Greetings. Completely rookie user here, just got 12.04 installed on the new laptop (Lenovo T530) for the first time and trying to get the hang of things. So far, only one issue:

One program I use often is Vassal ([www.vassalengine.org](www.vassalengine.org)). I downloaded and extracted the folder (as well as the JRE), and now I'm wanting to figure out an easy way to run it.

From the folder, if I run the .sh file, the program WILL start and works fine. However, it asks me every time if I want to run it, or if I want to display contents. Is there a way to have it not ask me this every time?

Secondly, I don't want to have to navigate to that folder every time I want to start it up. While it's running, I tried pinning its icon in the launcher, but that hasn't worked. When I close the program and try and restart it from that it just stared blankly at me and nothing happens.

Is there a n00b-friendly way that I can get easy access to starting this program, and not have to confirm every time I want to run it?

The contents, if that matters, of the .sh file are thus:

```
#!/bin/sh

#
# Execute this file to launch VASSAL on MacOS or Linux
#

# Find where VASSAL is installed, dereferencing symlinks
INSTALL_DIR=$(dirname $(readlink "$0" || echo "$0"))

# Launch VASSSAL
cd "$INSTALL_DIR" && java -classpath lib/Vengine.jar VASSAL.launch.ModuleManager "$@"
```

Thanks!

JB

---

### Post by Sealbhach on 2013-02-10
Hi, check [this]("http://handytutorial.com/manually-create-custom-application-launcher-in-ubuntu-12-10-unity/") out.

The shortcut for your launcher would be

sh /home/user/path/to/file/VASSAL.sh

Just point it to where your launcher script is/

.

---

### Post by Corvidae on 2013-02-10
Bingo!

That did it. Thank your for the prompt and helpful reply!

I'll get this all figured out eventually.

JB

---

