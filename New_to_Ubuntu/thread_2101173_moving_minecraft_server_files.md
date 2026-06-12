---
title: "moving minecraft server files"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by KG4UJD on 2013-01-03
I have a minecraft server running on Ubuntu 12.04 I want to move the server files out of my home dir into a folder named minecraft_server how do I do this? Do I need to change the file path? If so how I do this?

---

### Post by I8NY on 2013-01-04
There are a couple things you need to consider before moving the minecraft world and server.   Always make a backup of the minecraft server before you try any.  The main files needed to move for the minecraft server is the "world" folder.  It could be called something else if you changed the world name under the server.properties.  Besides that, you then must have the minecraft_server.jar in you new folder that you want with "world" folder present too.  Now if you have been launching the server by just clicking on the minecraft_server.jar, that is not going to work.  Launching application like that will make them run in the home folder and not the folder that they are present in.  You will have to launch it from the terminal by "cd /directory/location/" then "java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui" for it to run in the correct folder.  You could also edit a shellscript that I use to make running it easier.
```
#!/bin/bash
#memory amount minecraft can use
MEMALOC=1024
cd /home/user/Games/minecraft_server/
screen -m -d -S minecraft java -Xincgc -Xmx${MEMALOC}M -jar minecraft_server.jar nogui
```  With this you can just stop the server in-game or by typing in the terminal "screen -r" that will show you the standard server screen.  That should get everything working for you.  Reply back if you need anymore help.

---

