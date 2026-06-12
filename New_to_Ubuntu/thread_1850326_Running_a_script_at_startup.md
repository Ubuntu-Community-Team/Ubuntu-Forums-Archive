---
title: "Running a script at startup"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by 0PS on 2011-09-26
I'm having trouble running a shell script file. If I cd to the directory the file is in and then run, it works fine. However I can only run one command in "startup application prefrences". Below is in example of my problem.

The script is in /home/server/folder and is called script.sh

The script calls for another file in /folder called file.ext

If I run "/home/server/folder/script.sh" the script will run but I get an error saying "unable to access file.ext"

I think the script is trying to run from /home if I don't cd to the directory first but I can only use one command in startup preferences and I don't know how to get around this. I've read about putting a script in /etc/init.d instead but I have no idea how that works.

Thanks for any help.

---

### Post by collisionystm on 2011-09-26
When you run the script as yourself, are you running it as sudo?

---

### Post by 0PS on 2011-09-26
I'm not.

---

### Post by collisionystm on 2011-09-26
2 things.

1) Check your file permissions
2) Are you providing the entire path to the file inside your script?

---

### Post by 0PS on 2011-09-26
I'm pretty sure its not permissions. I have run the file fine, its just being able to do it in a single command.

Inside the script the file is called for like "file.ext". I've tried changing it to "/home/server/folder/file.ext" which works but then the file is run as though /home is its root and all its files are generated there instead of /folder.

---

### Post by anewguy on 2011-09-26
+1 on what collisionystm is saying about the path.  When you manually do it, you are in the appropriate folder to do so.  When the system runs it, it needs to know the full path to file.ext, otherwise it assumes it's in the current working directory for the system, which isn't going to be your folder.  So, just change your reference to file.ext to /home/server/folder/file.ext and it should work fine.

Dave ;)

---

### Post by anewguy on 2011-09-26
Okay, so your script is generating files?  What are the names and paths specified for them?

Dave ;)

---

### Post by 0PS on 2011-09-26
No the script just runs file.ext with some options. Its the file that is generating the files. :p

Theres no way of defining where the files are generated, I think they are generated in the root of where the file is run. Which is normally the root of the folder its in so no problems. But because I'm trying to run it in a single command and therefor outside its own folder, it thinks /home is its folder.

---

### Post by collisionystm on 2011-09-26
Maybe it would help to post the script and tell us exactly what you are trying to accomplish?

---

### Post by 0PS on 2011-09-26
Sorry, I thought making it generic would keep it short and simple. :p Heres the details..

I've setup ubuntu for running a minecraft server. I want to start this server at startup, so I can start the system and everything will be automatically running without further effort.

The files:
/home/server/minecraft/start.sh
```
java -Xmx1024M -jar craftbukkit.jar nogui
```/home/server/minecraft/craftbukkit.jar

So far this works perfectly:
```
cd /home/server/minecraft
./start.sh
```However the gui startup manager only allows you to enter one command and as noted before it doesn't work when you launch the file from /home/server/minecraft/start.sh.

---

### Post by anewguy on 2011-09-28
You may want to post this in the games and leisure (?) forum - someone there might be able to help you more with this game server startup.

Dave ;)

---

