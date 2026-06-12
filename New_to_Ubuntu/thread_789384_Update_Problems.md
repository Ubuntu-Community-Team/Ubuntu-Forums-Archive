---
title: "Update Problems"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by thunderwolf333 on 2008-05-10
I'm using the Update Manager and it's giving me a couple of problems.
it says it can only do a partial upgrade?
I think my AWN install somehow got messed up because that's the thing that's giving me problems really. AWN is fully functional for me now, except the weather app and it said I needed to update to fix it. so that's what im trying to do..

so i click partial upgrade and then it gives me the unable to authenticate error for libawn-bzr.

i read around and some people said to try sudo apt update. i tried that and it did fetch some data but i dont know if that did anything.

any help appreciated thanks! :D

---

### Post by macaholic on 2008-05-10
> **thunderwolf333 said:**
> 
i read around and some people said to try sudo apt update. i tried that and it did fetch some data but i dont know if that did anything.

any help appreciated thanks! :D
Well that's half the process, you have to do ```
sudo apt-get upgrade
```after update. Update fetches the changes, upgrade installs them.

---

