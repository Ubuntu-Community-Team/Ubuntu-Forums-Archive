---
title: "Nice command for java process"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by androssofer on 2012-05-30
Here is what I would like to do:

I currently run a minecraft server. And after I run it I change its priority to -5 as it runs on a relatively low powered machine, so i like it having a bit more power to play with. However i'd like this to happen automatically.

so I have the following script to run the server:

```
java -Xmx2048M -Xms2048M -server -jar bin/minecraft_server.jar
```

and i thought of changing it to something like:

```
gksudo nice --5 java -Xmx2048M -Xms2048M -server -jar bin/minecraft_server.jar
```

which would ask for a password at start and then run as normal..

however that would mean that my minecraft server would be run as root, and as its public facing i'd rather it didnt. So can anyone suggest a better solution? perhaps one that starts minecraft with normal permissions, then changes its nice value automatically after its started execution?

---

### Post by linuxman94 on 2012-05-30
You can use the command "renice" to change the priority after the server has started.  A script like this should work:

```
#!/bin/bash
java -Xmx2048M -Xms2048M -server -jar bin/minecraft_server.jar &
pid=$!
sudo renice -n -5 $pid
```

The "pid=$!" part gets the process id of the server and then it uses that variable to change the priority.

---

### Post by androssofer on 2012-06-04
> **linuxman94 said:**
> You can use the command "renice" to change the priority after the server has started.  A script like this should work:

```
#!/bin/bash
java -Xmx2048M -Xms2048M -server -jar bin/minecraft_server.jar &
pid=$!
sudo renice -n -5 $pid
```

The "pid=$!" part gets the process id of the server and then it uses that variable to change the priority.

Didnt wanna work... :-(. is to do with permissions and sudo. 

so i tried 

```
gksudo
```

to get a prompt when I run the script. but nothing happened, so figured display might be off.. but alas, nothing.. this is my latest script:

```
#!/bin/bash
java -Xmx2048M -Xms2048M -server -jar bin/minecraft_server.jar &
pid=$!
DISPLAY=localhost:0.0 ; export DISPLAY
gksudo renice -n -5 -p $pid
```

any idea how to get it to prompt for a password?

---

### Post by linuxman94 on 2012-06-06
gksudo is for launching graphical programs as root, you don't need to use it with non-graphical programs.

As for the script, the following script would work but you would have to use rcon with the server.

```

#!/bin/bash 
gnome-terminal -x java -Xmx2048M -Xms2048M -server -jar bin/minecraft_server.jar
pid=$! 
sudo renice -n -5 $pid
```This will launch the server in its own terminal and run the renice command in the original terminal, which will close once the renice command has been completed.

---

