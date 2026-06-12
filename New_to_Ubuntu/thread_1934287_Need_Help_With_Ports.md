---
title: "Need Help With Ports"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by Nikushimu on 2012-03-01
[SIZE=2]Hi Everyone, I'm new at using Ubuntu (on my laptop) i have 11:10 I think. Basically I am trying to set up a Minecraft Server for me && my close friends. My Question is: How do I check what's blocking the port & clear it? If it's not safe to clear it then how do I find an open port so that it will work?

_This is what it says when i try to run it:_
alex@Cacahuate:~/Desktop/server$ java -Xms1024M -Xmx1024M -jar CraftBukkit.jar nogui
174 recipes
27 achievements
19:59:02 [INFO] Starting minecraft server version 1.1
19:59:02 [INFO] Loading properties
19:59:02 [INFO] Starting Minecraft server on ***.***.**.**:25566
19:59:02 [WARNING] **** FAILED TO BIND TO PORT!
19:59:02 [WARNING] The exception was: java.net.BindException: Cannot assign requested address
19:59:02 [WARNING] Perhaps a server is already running on that port?[/SIZE]

---

### Post by cortman on 2012-03-01
I think Minecraft is supposed to be running on port 25565, not 25566, but that's a side note.
It looks like some other process is using the port. Run

```
sudo netstat -lpn | grep 25566
```

And post the output here. If it's not a crucial process, it could be as simple as killing the process and restarting Minecraft.

---

### Post by Nikushimu on 2012-03-01
Alright, I used that code && then tried to run the server again and it gave me the same error as it did at first. Sorry it took so long to reply.


Edit- I also switched it back to the original port that it was supposed to be on (i must have changed it on accident) && I ran it again with the 25565 && It gave the same results x.x

22:55:26 [WARNING] **** FAILED TO BIND TO PORT!
22:55:26 [WARNING] The exception was: java.net.BindException: Cannot assign requested address
22:55:26 [WARNING] Perhaps a server is already running on that port?

---

### Post by Nikushimu on 2012-03-02
I messed around with it a bit && it's finally working!! Thanks a lot for your help!!

---

