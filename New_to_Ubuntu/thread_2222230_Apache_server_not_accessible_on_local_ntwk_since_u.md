---
title: "Apache server not accessible on local ntwk since upgrade to Ubuntu 14.04"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by stehelene on 2014-05-05
Hi all,

I modestly develop a small PHP / MySQL application called  Music_Portal for home usage i.e. only accessible from the machines of my  local home network.

To do so, I'm using XAMPP for Linux version  1.8.3-1 on my server, the name of the machine hosting this server is  Desktop-Ubuntu (not very original, I know [IMG]https://community.apachefriends.org/f/images/smilies/icon_wink.gif[/IMG]).
So  up to now, my client machines accessed the server and the application  with the following path / URL in the address bar of the client browser :
desktop-ubuntu/Music_Portal/
Important  to note that all my (home) clients work either under Linux / Ubuntu or  Windows using several browsers such as Firefox, IE or Chrome.
Well, in short, up to a very recent time, all that perfectly worked.

These  last days, I made several modifications in my application. I tested  them _locally_ on my server / host machine (Desktop-Ubuntu). In that case, I access the  application in the address bar of my browser using :  [http://localhost/Music_Portal](http://localhost/Music_Portal) ==> so far so good. Then I wanted to  perform a "real life" test on one of my clients under Windows + Firefox :  KO, the server is not responding anymore, Firefox displays (sorry in  french) "Le  delai d'attente est depasse" meaning "timeout expired".  Same result from another client running Ubuntu (14.04 too). Whereas my  local network seems to work properly since I succeed to ping the server  machine from any client machine.

Then, what changed since my last  "real life" tests ? Of course, I made some evolutions in my application  but at first glance, nothing to do with my issue. Nothing changed  either in my XAMPP configuration. But on the other hand, last week  (April 25th to be precise), I upgraded from Ubuntu 13.10 to Ubuntu  14.04. and last week end (last Friday), I installed the last updates available. So I'm  thinking this is where I have to investigate, compatibility issue  between XAMPP 1.8.3-1 and Ubuntu 14.04.

Could anyone more advised and competent than I am help to sort this out and fix this issue ?

Note : I posted also the same topic on the Apache friends forum but unsuccessfuly up to now. Apache friends distributing XAMPP.
Note 2 : I would have liked to attach my httpd.conf file but I do not succeed to attach it :-(

Thanks for your support

---

### Post by stehelene on 2014-05-06
Hi all,

Issue fixed !

The issue came from the fact that my host machine name, desktop-ubuntu, disappeared from my DNS table, I don't know really why, and not 100% sur this may be related to the 14.04 upgrade. I then updated my DNS table and everything is working fine now !

Thanks a lot ! :D

---

### Post by claracc on 2014-05-06
As you got fixed your problem please, mark the thread as solved with thread tools bitton un the top right part of the page.

Thanks

---

### Post by stehelene on 2014-05-06
OK, done, sorry, I missed that.

---

