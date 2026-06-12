---
title: "Need Help Moving From OPen JDK to Sun Java"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by vincej on 2011-11-24
Hi - Using  11.10 and I am running a Bukkit Minecraft server. In order to improve performance I need to move from Open JDK to Sun Java. I have Sun Java 6 successfully installed, however, I do not know the commands for pointing Bukkit Minecraft at the Sun version of Java. If it helps, I can tell you that in the start up script it reads: 

```
cat > minecraft.sh << EOF
#!/bin/sh
BINDIR="\$(dirname "\$(readlink -fn "\$0")")"
cd "\$BINDIR"
java -Xincgc -Xmx1G -jar craftbukkit-1.0.0-SNAPSHOT.jar
EOF
chmod +x minecraft.sh
```

Many Many Thanks !

---

### Post by Telengard C64 on 2011-11-24
I haven't setup a Minecraft server, so I can't help much, but this looks very, very relevant:

[http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Installing_Java](http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server#Installing_Java)

---

### Post by ptrakk on 2011-11-24
i just set one up yesterday. one moment and i will solve it.

---

### Post by ptrakk on 2011-11-24
try this: this is how i did it. change the server_location variable and dont put a / after it. you may also want to change the xmx settings to account for your ram. this code is designed for about a gig of ram installed. i have been playing this world for about a month and the server only takes up 21 Megs of ram. I would save this file as /usr/bin/minecraft.sh. then run 'chmod +x /usr/bin/minecraft.sh' once in terminal.
```

#!/bin/bash

################################################################################               minecraft.sh
## MAKE SURE THIS SCRIPT IS AVAILABLE IN YOUR $PATH.
################################################################################
# It's highly advisable to create a directory to hold all of your server files. 
# The jar will generate quite a few files upon first run and it would get pretty 
# messy if there are other files in the same directory.
################################################################################
## NEEDED INFORMATION
################################################################################
# This is the location for a Debian/Ubuntu java executable
javaexec=/usr/bin/java

# Set this to the directory containing the minecraft_server.jar
# Provide the full path from /
server_location=/root/Desktop/mcserver

################################################################################
## RUNNING THE SERVER
################################################################################
# By cd'ing to the server location
# All server files will be created in this directory.
cd $server_location

# Run the Server
`$javaexec -Xmx1024M -Xms512M -jar $server_location/craftbukkit-1.0.0-SNAPSHOT.jar`

# After killing off the server, you will be cd'ed back to the directory you were 
# at prior to running this script.
cd -

```

then to run it go to a terminal and type minecraft.sh. what i did was put minecraft.sh in my startup.

---

### Post by beew on 2011-11-24
Unless you need OpenJdk for some reasons you can just use sun java as your system default then you don't need to fool around with your program's start up script.

```
sudo update-java-alternatives -s java-6-sun
```

Now to check  which java you are using type
```
java -version
```

If you are using sun java you should see something like this

> java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)

---

