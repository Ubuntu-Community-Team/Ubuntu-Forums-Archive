---
title: "repository problem &lt;- please help"
date: 2006-07-27
forum: Repositories &amp; Backports
---

### Post by brotakul on 2006-07-27
i was trying to install "alien" via synaptic, but it didn't work because of fetching the file. i don't know why but i downloaded and manually installed all the dependencies and now i can't install/uninstall anything.
i tried an update, dist-upgrade, -f install, remove, nothing works. it sais:
```

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  alien: Depends: rpm (>= 2.4.4-2) but it is not installed
  libbeecrypt6: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.1-5) but 4.1.1-9 is installed
           Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
  libstdc++6: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
E: Unmet dependencies. Try using -f.

```
synaptic finds the 4 broken packages [alien, libbeecrypt6, libcc1, libstdc++6], but if i try to remove them, synaptic wants to remove a lot of software like ca amarok, gnome-panel[!!] and so on... :\ 
[ screenshot](http://img222.imageshack.us/img222/4126/screenshotyr0.png)
also, if i want to reload reops in sinaptic it sais:
```

http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

```
what can i do? if somebody knows the way to solve this, **please help**
thanks

---

### Post by izle on 2006-07-27
Hi,

manually installing packages can be quite a mess!!

I check on my system (dapper), there is no mention of a libc6-2.3.6-6 just the 2.3.6-0 version. But I search for alien and found it with synaptic. 

My guess is fix the repository problem with synaptic, and install alien via synaptic. You also may try to uninstall manually with dpkg -r  the package that are causing problem, but there is no waranty what I am telling won't break everything you worked so hard to build!!
 
for the "Could not connect to localhost:4001 (127.0.0.1)" part, check with ifconfig if your lo connection is activated.

finally you may check your source.list 

regards

---

### Post by brotakul on 2006-07-27
thanks for the tips izle, but it seemd that my system was a mess indeed. i had no choice but to make a fresh install. anyway, even if i lost a half of day to reconfigure it how i like, it's done now and it's working just fine. shame i couldn't fix the problems but since it was the first installing, it was surely a system going down with all my older mistakes i've done 'till now :P
but thank you anyway for the help and i'll try to be more carefull for the future :)

---

### Post by troy1of2 on 2006-08-28
I know you've already done a re-install and fixed your system by now but as a person who just went through the same thing I was curious. Did you happen to install anon-proxy?

Here's what happened to me:

I was going through the list of packages in Synaptic and came across this thing called anon-proxy which said it would allow you to surf the web anonymously which I thought, well that sounds nice, might keep some of the spammer, spyware, etc. types off my back so I installed it. While it was installing I remember it asking me if it could do something and I said 'Sure, why not!' BIG MISTAKE. It turns out it made changes to /etc/environment which  set an http proxy to localhost:4001. More details about that here:

[http://forums.debian.net/viewtopic.php?t=310&](http://forums.debian.net/viewtopic.php?t=310&)

So anyway, I didn't know all of that at first until I found that forum I linked to above. All I knew was I suddenly couldn't get into the forum on the GParted website to tell them how well the test version they just released worked for me. I couldn't connect to any of the repositories through Synaptic which at first I just thought was a temporary server outage or something and certain other things were not available. It took me  some googling to find out what the problem was which is how I found this message and the one I linked to. So if anyone is thinking of installing this anon-proxy BE CAREFUL. If it can work without setting that http proxy in the environment it might be safe to use, I don't know, I just removed it and went on with my life but hopefully this info will help someone else who runs into the same problem in the future.

---

### Post by brotakul on 2006-08-30
yes, i actually installed that anon-proxy :D [i guess it was anon-proxy, or maybe other proxy, i can't remember]

anyway, it seems now that i do not have any problems with my repos anymore. so i'm glad.

---

