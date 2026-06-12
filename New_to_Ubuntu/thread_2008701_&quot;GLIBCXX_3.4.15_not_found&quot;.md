---
title: "&quot;GLIBCXX_3.4.15 not found&quot;?"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by nevilshute on 2012-06-23
Hey there,

Been trying for a while now to get Magic the Gathering Online to run on my Linux machine. I'm a bit handicapped to this end though by being a bit of a Linux novice. 

I've installed gccg and followed the instructions I found here: [http://gccg.sourceforge.net/](http://gccg.sourceforge.net/). 

However, when I try to launch the game by typing ./Mtg I get the following message:
> 
/usr/lib/i386-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by ./ccg_client)I can't work out how to get `GLIBCXX_3.4.15' installed. Can anyone help? :)

Thanks

---

### Post by HiImTye on 2012-06-23
what version of Ubuntu are you using? it's part of libgcc 4.6+ which means that it should be included in libgcc1 for any version of Ubuntu since Oneiric
[http://packages.ubuntu.com/search?keywords=libgcc1](http://packages.ubuntu.com/search?keywords=libgcc1)

---

### Post by nevilshute on 2012-06-23
Thanks for replying. Umm, I'm using version 11.04 as far as I can tell. I'm afraid I'm not quite sure how to make sense of the link you posted :(

---

### Post by Robvdl on 2012-10-09
Having the same issue here with Ubuntu 11.04 also (32 bit), I used to build the same software on my Ubuntu 11.04 build VM and then run it on a set of target Ubuntu 11.04 machines and everything had been fine until now.

The target machine is now coming up with the following messages when I run our software:

```
/usr/lib/i386-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found
```

I have updated both machines, but still getting the same issue, I am still trying to figure out why this is happening, as I don't use any PPA's on these machines.

Both the build machine and target machine have the exact same version of libstdc++6 installed and libstdc++6-4.5-dev so this shouldn't be happening.

---

### Post by Robvdl on 2012-10-09
Sorry, it's working now and I don't really know what caused it, but I cleared out my build directory and checked out my source again and rebuilt the app, and everything was fine.

---

