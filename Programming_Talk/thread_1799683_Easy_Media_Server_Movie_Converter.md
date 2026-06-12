---
title: "Easy Media Server Movie Converter"
date: 2011-07-07
forum: Programming Talk
---

### Post by D0m1nat3 on 2011-07-07
Hi guys. I'm currently in the process of building a media server but want to avoid the hassle of ripping my dvd's to it all the time. Because half of my household only know how to open microsoft word, outlook and firefox they will always be coming to me to put their movies on the server.

So heres the plan. I'm going to create an application both server and client side that can effectivly rip a movie from any rom drive on the network to the server. I have already started on the server side (using c) and this part shouldn't be to hard. I'm using handbrake to convert videos to mkv format at the moment. I'll also be using mediatomb to serve out the movies. I'm also creating a drop zone in which any user can drop a movie into a shared folder on the network and the server will grab it and convert.

Now my windows programming is limited and I'm not quite sure what language etc to program it in. The program should only need to detect a movie in the rom drive, ask the server if the movie already exists in its database and if not ask the user to enter a name for the movie. Once this is done it notifies the server, the server should then access the shared rom and rip it.

Obviously I want to keep the project open source. I won't be able to work on it that much when uni comes back but over the next couple of weeks it can keep me from boredom . 

Any thoughts/suggestions/ideas?

**Problems to date:**

- Mounting a shared dvd-rom.
I thought running the following would do the trick:
```
mount -r //192.168.x.x/e /mnt/comp0 -o username=random,password=random
```
This mounts fine and i can list the files etc. The problem is when I use HandbrakeCLI and use /mnt/comp0 as the source HandbrakeCLI segFaults or only finds title1 which is 20 seconds long. Anyone know a solution?

Thanks
Ben
____

---

### Post by conundrumx on 2011-07-08
I think a better way to accomplish this would be to automate it on the server.  When someone inserts a DVD in the server, it would automagically rip it.

---

### Post by PaulM1985 on 2011-07-08
Or have it running on each client.  When the DVD goes in it rips it and copies it to the server.  That way you wouldn't have the remote mounting issues.

Paul

---

### Post by Aaron80 on 2011-07-22
Can you post your script and/or how-to for autoripping on your server? I'm sure many folks here would love that....myself included.

---

