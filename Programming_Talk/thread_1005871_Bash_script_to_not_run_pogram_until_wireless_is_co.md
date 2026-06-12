---
title: "Bash script to not run pogram until wireless is connected and working"
date: 2008-12-08
forum: Programming Talk
---

### Post by justinjstark on 2008-12-08
When I log in, I have programs to open that I do not want to open until the wireless is connected.  Most of the time I have to manually authenticate my sessions so I can't simply wait for 10 seconds or something before I load the programs.  I also can't just wait for the wireless interface to be up (like [http://bbs.archlinux.org/viewtopic.php?id=51716](http://bbs.archlinux.org/viewtopic.php?id=51716)).  Just because the interface is up doesn't mean http is working.

So I figured I would just ping google every ten seconds until it worked and then load the program.  Like so:

```
#!/bin/bash

ping -c 1 -W 10 google.com &>/dev/null
until [ $? -eq 0 ]; do
	sleep 10
	ping -c 1 -W 10 google.com &>/dev/null
done

exec $1&
```

Unfortunately, some of the networks I use must block pings.  So I need another method to tell if the network is connected (and authenticated) and then to load a program.

Please help.  I don't know how else to test other than ping and I'm not good with bash scripting.

---

### Post by Catalyst2Death on 2008-12-08
you could do something like:
```

result=ifconfig | grep "inet addr" | grep 255.255.255.0

if[result!=""]
#i'm connected!
else
#i'm not :(

```

syntax is probably not completely right, but I hope the idea is clear

---

### Post by justinjstark on 2008-12-08
> **Catalyst2Death said:**
> you could do something like:
```

result=ifconfig | grep "inet addr" | grep 255.255.255.0

if[result!=""]
#i'm connected!
else
#i'm not :(

```

syntax is probably not completely right, but I hope the idea is clear

The problem with that is that the network assigns me an inet addr before I am authenticated (I still can't use http).  Basically, once I am on the network and try to go to a website, it redirects me to a page asking for credentials.

I did find a way that will work: wget google.com and then search for the string Lucky (from I'm Feeling Lucky).  If I'm authenticated, it will find it.  If not, the wget page will be the login page for the network.

```
#!/bin/bash

wget google.com -O /tmp/google &>/dev/null
grep Lucky /tmp/google &>/dev/null
until [ $? -eq 0 ]; do
	sleep 10
	wget google.com -O /tmp/google &>/dev/null
	grep Lucky /tmp/google &>/dev/null
done

exec $1&
```

It's not great but it does the trick.  I'm going to use it until somebody has a better suggestion.

---

### Post by geirha on 2008-12-09
It looks like a good solution to me. The only problem is that if you happen to be in a non-english speaking country, google might consider giving you a page translated to the local language, in which case Lucky might not match. 

When you are authenticated, what happens when you go to the authentication page? If it gives you a "You are already authenticated" kindof string, then that would probably be a better thing to match for.

Your current script can be made a bit shorter btw:
```
#!/bin/bash

while ! wget http://google.com -O- 2>/dev/null | grep -q Lucky; do
    sleep 10
done

exec $1

```

The return value of the last command in the pipe is the one that gets evaluated by while.

---

### Post by justinjstark on 2008-12-09
> **geirha said:**
> It looks like a good solution to me. The only problem is that if you happen to be in a non-english speaking country, google might consider giving you a page translated to the local language, in which case Lucky might not match. 

When you are authenticated, what happens when you go to the authentication page? If it gives you a "You are already authenticated" kindof string, then that would probably be a better thing to match for.

Your current script can be made a bit shorter btw:
```
#!/bin/bash

while ! wget http://google.com -O- 2>/dev/null | grep -q Lucky; do
    sleep 10
done

exec $1

```

The return value of the last command in the pipe is the one that gets evaluated by while.

It is more likely that I will be on a different network with a different authentication page than be in a non-english country.  So searching for a common string in Google would be best.  I didn't just want to search for Google either since it is possible that that the authenication page will have some kind of redirect string in it that includes google, etc.

I was looking at making it shorter.  Piping straight from wget is definitely better.  But I think you have a few typos.  Here's what I did:

```
#!/bin/bash

until wget -q -O - http://www.google.com | grep Lucky > /dev/null; do
	sleep 10
done

exec $1&
```

---

### Post by Lockheed on 2009-06-04
Correct me if I'm wrong, but this way screenlets won't load unless I am online, right?

I use it also for other widgets than google calendar and it would not be very productive.

Can you write a script that restarts screenlets once the connection is established?

---

