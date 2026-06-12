---
title: "compiz experimental plugins"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-17
Hello All, I'm running Ubuntu 12.4 and would like to install the latest version of the compiz experimental plugins for 12.4. Can you direct  me to the correct  text for the terminal or a download website to accomplice this task](*,)

---

### Post by deadflowr on 2012-10-17
You'll have to install them from git.

Read here: [compiz]("http://wiki.compiz.org/")

---

### Post by Frogs Hair on 2012-10-17
There are instructions under this video, just select show more. Use at your own risk.   
[http://www.youtube.com/watch?v=1ZEGJDpAZ3A](http://www.youtube.com/watch?v=1ZEGJDpAZ3A)

---

### Post by vegas89 on 2012-10-17
Went to the you tube video and did the script using copy and paste when the terminal got to the end it said there was an error on line 91 and the entire file had been ignored. Please advise:confused:            n XDG_DATA_DIRS, you need to add /home/vegas/.config/compiz-1/gsettings/schemas to your XDG_DATA_DIRS in order for GSettings schemas to be found!
-- Installing GSettings schemas to /home/vegas/.config/compiz-1/gsettings/schemas
-- Installing: /home/vegas/.config/compiz-1/gsettings/schemas/org.freedesktop.compiz.workspacenames.gschema.xml
-- Recompiling GSettings schemas in /home/vegas/.config/compiz-1/gsettings/schemas
/home/vegas/.config/compiz-1/gsettings/schemas/org.freedesktop.compiz.freewins.gschema.xml: Error on line 91 char 1: 0-1:unknown keyword.  This entire file has been ignored.
/home/vegas/.config/compiz-1/gsettings/schemas/org.freedesktop.compiz.ghost.gschema.xml: Error on line 31 char 1: 0-1:unknown keyword.  This entire file has been ignored.
running /usr/bin/gconftool-2 --install-schema-file=/home/vegas/src/compiz/plugins/workspacenames/build/generated/compiz-workspacenames.schemas > /dev/null  2>&1
-- Installing: /home/vegas/.gconf/schemas/compiz-workspacenames.schemas
-- Installing: /home/vegas/.compiz-1/plugins/libworkspacenames.so
Done.
Don't forget to restart compiz and ccsm after installing or removing any plugin. Enjoy! :-)
vegas@vegas-desktop:~/scripts$ nohup compiz --replace
nohup: ignoring input and appending output to `nohup.out'

---

