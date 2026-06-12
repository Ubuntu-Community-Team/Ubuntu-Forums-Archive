---
title: "How to restart a process or the program itself?"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by Tobias_Brodersen on 2014-01-14
Hey Peeps,
A few hours ago, i got a minecraft server running and going, able to connect it and stuff.
I made som changes on it though, but im not sure how to restart it, so that these changes step in.

I use Screen as console, but even after massive "googling" i can't find a answer how to restart the server, so that the changes will set in.

should I not be able to restart like my mumble server?
When i want to restart my mumble(murmur) server, i simply:
```
service mumble-server restart
```
But my minecraft server can't be found when i use the status command
```
service --status-all
```
I did find it, in the process list though
```
ps aux
```

Am i doing something terrible wrong? how do i restart my minecraft server :)
thanks in advance.

Toby - the ultimate ubuntu newbie

---

### Post by MG&amp;TL on 2014-01-14
If a service does not have the required configuration files to enable the *service* utility to work, you can stop the process by using *kill* (not as drastic as it sounds...). Find the process ID, then run

```
kill <PID>
```

replacing <PID> with the PID of the minecraft process. That should stop the program, and then you'll be able to start it again with the command you used to start it in the first place.

---

### Post by ian-weisser on 2014-01-14
You are running mine craft as a user application, not as a system or user *service*. Services have an Upstart configuration file in /etc/init or ~/.config/upstart. The "service" command only knows about applications that have an Upstart configuration file.

---

### Post by sandyd on 2014-01-14
> **Tobias_Brodersen said:**
> Hey Peeps,
A few hours ago, i got a minecraft server running and going, able to connect it and stuff.
I made som changes on it though, but im not sure how to restart it, so that these changes step in.

I use Screen as console, but even after massive "googling" i can't find a answer how to restart the server, so that the changes will set in.

should I not be able to restart like my mumble server?
When i want to restart my mumble(murmur) server, i simply:
```
service mumble-server restart
```
But my minecraft server can't be found when i use the status command
```
service --status-all
```
I did find it, in the process list though
```
ps aux
```

Am i doing something terrible wrong? how do i restart my minecraft server :)
thanks in advance.

Toby - the ultimate ubuntu newbie
You will want to attach to the screen console
```

screen -r
```
Then, stop the minecraft process by pressing Control+C

You can then start the minecraft process again once youve updated

---

