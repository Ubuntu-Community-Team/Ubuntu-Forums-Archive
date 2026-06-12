---
title: "WoW init script"
date: 2008-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by lavacano on 2008-09-19
```
#!/bin/sh

# Execute X on a high display port (modify if needed)
X :3 -ac -terminate &

# Make the process have more priority (-1 because CFS might barf if higher)
renice -1 -p `ps ax | grep "X :3 -ac -terminate" | grep -v grep | cut -c1-5`

# Change Directory to WoW installation
cd "/home/chadwick/.wine/drive_c/Program Files/World of Warcraft"

# Wait a little then execute wine (modify for your executable `which wine` could replace /usr/bin/wine)
sleep 2 && DISPLAY=:3 /usr/bin/wine Wow.exe -opengl &

# Wait a little then make the process have more priority (-1 because CFS might barf if higher)
sleep 2
renice -1 -p `ps ax | grep Wow.exe | grep -v grep | cut -c1-5`
renice -1 -p `ps ax | grep wineserver | grep -v grep | cut -c1-5`

```

most of it is adapted from gentoo's wiki but I added some process niceness.

you need to change 
# Change Directory to WoW installation
cd "/home/chadwick/.wine/drive_c/Program Files/World of Warcraft"

and might need to change 
# Wait a little then execute wine (modify for your executable `which wine` could replace /usr/bin/wine)
sleep 2 && DISPLAY=:3 /usr/bin/wine Wow.exe -opengl &

---

