---
title: "Setting up a headless computer"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Stefanie on 2008-06-16
I have an old computer and I would like to use it as a headless computer/server to back up my data. I have never done something like this before so I need some advice on how to get started... Some links to good tutorials would be great, too. thanks!

---

### Post by miraceti52 on 2008-06-16
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Hope this helps :)

---

### Post by PriceChild on 2008-06-16
> **miraceti52 said:**
> [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

Hope this helps :)Reeeeeally old guide... wouldn't use it anymore, and ftp is insecure anyway.

I suggest you install using an alternate install cd, and get  it to install without any gui, cli only. (obviously you need a monitor and keyboard for this)

Then```
sudo apt-get install openssh-server
```
You'll then be able to ssh <address>, from any other machine on your network, where <address> is its ip, viewable from ipconfig.

---

### Post by Stefanie on 2008-06-16
ok, thans. is it really that easy? no pitfalls? will this work with a wireless connection? the network is using dynamic ip addresses for the moment, maybe i should setup a static ip or is this not necessary?

---

### Post by hyper_ch on 2008-06-16
if you don't setup static IP you'll have to figure out first on what ip the server runs...

And wifi runs if the card is directly supported... if not you'll have to see if you can find drivers/work arounds.

---

