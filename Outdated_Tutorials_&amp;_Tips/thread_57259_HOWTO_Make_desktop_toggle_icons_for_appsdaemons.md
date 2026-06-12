---
title: "HOWTO: Make desktop toggle icons for apps/daemons"
date: 2005-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2005-08-15
This is a quick way to make your desktop (or other) icons act like on/off switches for certain applications or daemons. Once double clicked, the icon will check whether the app/daemon is running, and if it's not running it will run it; if it's running it will terminate it.

1) Create an empty script file "e.g. tgscript1.sh". 

2) Make the file executable with "chmod +x". Create a launcher that points to it.

3) Insert the following into the script. replace [app] with the name of your app.

```

#!/bin/bash
ps -e | grep [app]
x=$?;
if [ $x -eq 1 ]; then
        [app]
 
else
        killall [app]  

fi

```

The above works good for toggling frequently used apps, since you don't need an indicator to tell you whether the app is running or not, but for daemons you may also want to know whether they're running or not at a given time. The version below replaces your launcher icon according to the state the app/daemon is in, but to actually see the effect you need to click your desktop and press ctrl+r to refresh it. It would be nice if there were a command that makes Nautilus refresh the desktop but i haven't found one; please give me a shout if you know of such a thing. In the code below, replace [icon] with your original icon path that you use with your launcher, [on icon] with the path to an icon that you'd like to see when the app/daemon is on and [off icon] with one that will correspond to the off state.

```
#!/bin/bash
ps -e | grep [app]
x=$?;
if [ $x -eq 1 ]; then
cp  [on icon] [icon]
        [app]
 
else
cp [off icon] [icon]
        killall [app] 

fi

```

ps. thanks to [tread](http://ubuntuforums.org/member.php?userid=15773) for hinting me to this one.

---

