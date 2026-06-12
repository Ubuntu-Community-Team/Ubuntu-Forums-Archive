---
title: "Start minecraft remotely"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by schneidaren on 2012-04-09
Greetings!

I wanted to control my ubuntu system remotely so I installed openssh-server and I use Putty to access from my win 7 system.
I want to start minecraft-server on the ubuntu system.
I can start minecraft-server with putty. But when I shut putty down the minecraft server stops. I want it to continue to run.

1. Please explain why and how to do it properly. 
2. If I start MC, and close putty, how to I reach the "MC interface" again once I reconnect?

Thanks

---

### Post by Cheesemill on 2012-04-09
You can use screen. First install it with:
```
sudo apt-get install screen
```
Then when you are using putty to connect to your server just type
```
screen
```
to open a new virtual terminal.
You can then start your minecraft server as usual. To detach from the virtual terminal hit CTRL+a and then d. This will detach the virtual terminal but keep all processes running in the background, you can then quit putty and Minecraft will keep running.

To recoonect simply open a new ssh session using putty and type:
```
screen -r
```
to reconnect to the virtual terminal session.

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

---

### Post by schneidaren on 2012-04-09
That worked, thanks

---

