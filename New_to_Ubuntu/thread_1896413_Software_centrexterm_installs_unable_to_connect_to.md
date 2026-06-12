---
title: "Software centre/xterm installs unable to connect to internet"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by Zudotakuari on 2011-12-16
Hello there,

I have been running Ubuntu 11.10 for just over a month. Everything was working swimmingly until last week, when suddenly I have been unable to install/update anything from the software centre or manually. 

With regards to Software Centre, every time I try to install something it says 'failed to download package, check your internet connection'. My connection is fine, as I can still download images etc through firefox, browse the internet, yadda. When changing the server and selecting source (such as multiverse)  the process 'updating the cache' starts but doesn't ever do anything, no information is being received. 

When installing from terminal, sudo apt-get update or sudo apt-get install X the connection times out, every time. This is becoming increasingly frustrating! I've tried searching for this problem but the only solution I found was 'check your internet connection'. Which is fine. I also have plenty of space on my hard-drive.

Any suggestions would be really gratefully received!

---

### Post by bluexrider on 2011-12-16
> **Zudotakuari said:**
> Hello there,

I have been running Ubuntu 11.10 for just over a month. Everything was working swimmingly until last week, when suddenly I have been unable to install/update anything from the software centre or manually. 

With regards to Software Centre, every time I try to install something it says 'failed to download package, check your internet connection'. My connection is fine, as I can still download images etc through firefox, browse the internet, yadda. When changing the mirrors and selecting source (such as multiverse)  the process 'updating the cache' starts but doesn't ever do anything, no information is being received. 

When installing from terminal, sudo apt-get update or sudo apt-get install X the connection times out, every time. This is becoming increasingly frustrating! I've tried searching for this problem but the only solution I found was 'check your internet connection'. Which is fine. I also have plenty of space on my hard-drive and am running from root.

Any suggestions would be really gratefully received!

go to the "software sources" and change the server.

on the first tab choose "download from" click main server then choose other and then choose select best server.

then from terminal
```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ajgreeny on 2011-12-16
Are you really "running from root" as you said, or are you using sudo as normal?

---

### Post by Zudotakuari on 2011-12-17
> **bluexrider said:**
> go to the "software sources" and change the server.

on the first tab choose "download from" click main server then choose other and then choose select best server.

then from terminal
```

sudo apt-get update && sudo apt-get upgrade
```


Doesn't connect to any server and just throws the 'Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg 
  Unable to connect to 113.29.211.196:80:' on every line.


Ajgreeny, err, probably using sudo as normal then judging by your comment ha.

---

