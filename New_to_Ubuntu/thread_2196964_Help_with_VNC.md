---
title: "Help with VNC"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by nathankitsell on 2014-01-01
Ok, so I've got an old laptop that I've installed lubuntu on, and I want to be able to control it through VNC from my windows 8 laptop. I installed vino on the lubuntu system but must have done something wrong because I tried 3 different viewers on the windows laptop and couldnt connect. I've searched all over the internet for 3 days now and cannot find a solution. I've never used VNC before at all so could do with a very basic guide but I can't find one clear enough for me to understand as I really don't know ubuntu very well at all. It took me over an hour to figure out that when people say "do" blah blah that they meant type it into the terminal.

What I THINK is the problem is that the port isn't open on lubuntu - so it's not listening for incoming connections. Can anyone with experience with this give me a VERY CLEAR step by step guide on how to get this working? Thanks in advance!

---

### Post by steeldriver on 2014-01-01
I'm not sure how well vino-server integrates into the LXDE desktop - were you able to find the vino-preferences setup application in order to actually start the server? if not, try invoking it from a terminal

```
vino-preferences
```

You can also check that it's running using ps or pgrep

```

ps -ef | grep [v]ino-server

pgrep vino-server

```

If all checks out OK then the next step would be to check the listening port

```
sudo netstat -nlp | grep vino
```

(run on the server)

Are you tunneling the connection over SSH or using plain VNC? are the Windows laptop and the Lubuntu laptop on the same LAN?

---

### Post by nathankitsell on 2014-01-01
I was able to get into the preferences using that code, but i haven't tried the others. i'll give them a go, thank you :)
I'm not entirely sure what ssh is, but yes they're on the same LAN

---

