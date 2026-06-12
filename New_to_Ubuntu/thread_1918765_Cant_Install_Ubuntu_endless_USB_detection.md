---
title: "Cant Install Ubuntu endless USB detection"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by ntrautner on 2012-02-01
I tried to instal ubuntu. I downloaded a .iso for  64 bit ubuntu. Burned image to a disk the proper way. Set my bios to boot from CD ROM. It detects the disk and starts to run. It shows the purple screen for a bit then it starts detecting USB devices...

ON IN TO INFINITI.

Thats right. It just starts to show lines of messages detecting USB devices or showing ones that arent connected to anything.

Once the number hit 100 I just labeled it ridiculous and hard rebooted.

Now explain this to me. I am able to load it as a virtual box on my computer. But If I try the wubi installer, or installing form a disk it does this thing where instead of loading the nice purple configuration screen its nasty ugly lines of code just telling me its detecting a seemingly un ending number of USB devices on my computer. Is instalation really supposed to run like that? It cant be. I got an old laptop from work replaced its busted hard drive gave it more memory, put ubuntu on it and it ran like a dream. Instillation was easy worked very fast and my Wife is now a proud and happy linux user. How could this be so hard for my computer wich is brand spankin new. Im lost...

Please help.

---

### Post by wolfen69 on 2012-02-01
> **ntrautner said:**
> How could this be so hard for my computer wich is **brand spankin new**. Im lost...


That's probably part of the problem. New hardware can be the *most* problematic of all computers. The developers need time to write drivers for newer hardware, because most companies don't release drivers for linux.

Let's take a look though, post the output of 
```
lspci
```

---

