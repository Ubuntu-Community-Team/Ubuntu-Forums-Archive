---
title: "How to free a port number"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by Tyler Lusk on 2012-09-10
13:51:51 [INFO] Starting Minecraft server on *:25565
13:51:51 [WARNING] **** FAILED TO BIND TO PORT!
13:51:51 [WARNING] The exception was: java.net.BindException: Address already in use
13:51:51 [WARNING] Perhaps a server is already running on that port?

Trying to get a server going for my grandson to teach him how to use linux but I keep getting this error trying to load server. Command I'm using is,    	 	 	 	 	 	   java -Xms1024M -Xmx1024M -jar craftbukkit.jar nogui


any suggestions?


Thanks, Tyler's Papa:confused::confused:

---

### Post by jerome1232 on 2012-09-10
That's not port 25, that's port 25565.

You can see what is using that port with

```
sudo netstat -tlp | grep 25565
```

Are you positive that there isn't already an instance of minecraft running?

---

### Post by Tyler Lusk on 2012-09-10
tcp6       0      0 [::]:25565              [::]:*                  LISTEN      3693/java     

Yea looks like java is using it how do I kill it? I'm learning along with my Grandson... Thx!

---

### Post by jerome1232 on 2012-09-10
Sounds like you already have a minecraft server running (Java is what would show up if minecraft was using that port)

Have you tried connecting to it from another computer?

---

### Post by coffeecat on 2012-09-10
Moved to own thread.

@Tyler Lusk, the thread you posted to had been dead for over 4 years. Please start your own threads. Thanks.

---

### Post by ubudog on 2012-09-10
Run & post the output of: 
```
ps ax | grep java
```

---

### Post by Tyler Lusk on 2012-09-10
I got it...I just rebooted the system and it's working now...Thank you. Now I need to learn how to install bukkit commands...Oh Boy! Any Minecraft fans out there? I hope somebody created a GUI for all this stuff...wish me luck!

Tyler's Papa

---

### Post by Tyler Lusk on 2012-09-10
> **coffeecat said:**
> Moved to own thread.

@Tyler Lusk, the thread you posted to had been dead for over 4 years. Please start your own threads. Thanks.


Ok sorry![IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]

---

