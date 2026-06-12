---
title: "Minecraft"
date: 2012-01-14
forum: Programming Talk
---

### Post by Fenlig on 2012-01-14
Hey Guys,

Im working on my minecraft sever and want to setup a personalised greeting when  a new player joins my server. But I'm a novice when it comes to  scripting and could do with some help.

So my script tails the server.log file to see when new players join and sends the message into another GNU screen where minecraft is running which is  a java application.
 
#!/bin/bash

user=`tail server.log |grep "logged in" | awk '{print $4}'`
screen -p 0 -S minecraft_public -X eval 'stuff "say Welcome to the server "$user" \015"'
echo "$user"

And all I see in game is Welcome to the server. I have tested this and  it echo's my user name in the terminal window which is "Fenlig" 

Anyone able to solve this?

Kind regards,
Fenlig.

---

### Post by trent.josephsen on 2012-01-14
$user is in a single-quoted string, so it doesn't get interpolated by the bash running the script, but instead by the eval run by screen.

You'll need to play with the nesting to get it to work right.  This might work:

```
screen -p 0 -S minecraft_public -X eval "stuff \"say Welcome to the server $user\"\015"
```

---

### Post by Fenlig on 2012-01-14
> **trent.josephsen said:**
> $user is in a single-quoted string, so it doesn't get interpolated by the bash running the script, but instead by the eval run by screen.

You'll need to play with the nesting to get it to work right.  This might work:

```
screen -p 0 -S minecraft_public -X eval "stuff \"say Welcome to the server $user\"\015"
```

That worked perfectly mate thanks.

Just have to work on making this constantly tail that log and react when it see somthing Login :)

---

### Post by Fenlig on 2012-01-14
Okay so when I put in the -f so the will tail it in real time the welcome message isnt being sent, but i can see the process running in the backround on the OS

user=`tail -n 1 server.log |grep "logged in" | awk '{print $4}'`
screen -p 0 -S minecraft_public -X eval "stuff \"say Welcome to the server $user\"\015"
echo "$user"

Is this cos it will just tail it and not do the rest of the commands?

---

### Post by trent.josephsen on 2012-01-14
In a word, yes.

I'm not sure how to tell you to fix this -- I used Perl and its File::Tail module to do my minecraft server magic.

---

