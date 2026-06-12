---
title: "/usr/bin/ld: cannot find -lX11"
date: 2015-11-14
forum: New to Ubuntu
---

### Post by dallasabartlett on 2015-11-14
I am super green at this, but I need help getting some packages set up on my computer. This message has popped up while attempting to install. How might this be resolved?

/usr/bin/ld: cannot find -lX11

---

### Post by steeldriver on 2015-11-14
Hello and welcome to the forums

It might be resolved by installing the libx11-dev package from the repositories

We may be able to give a more complete answer if you tell us what you are trying to install

Since you're new, I'd also point out that building software from source should generally be a last resort - when you absolutely can't use one of the pre-built binary packages from the repositories or find a properly maintained "PPA"

---

### Post by dallasabartlett on 2015-11-14
Thanks for the tip. I tried it, and nothing seems to have changed.

I am attempting to install Speech Recognition software called HTK.

Thanks for the tip on it being a last resort option, but unfortunately, I think it is my only option for this particular code. Any other thoughts?

---

### Post by sandyd on 2015-11-14
Try installing 32bit libs as well
```

sudo apt-get install libx11-dev:i386
```

---

### Post by grahammechanical on 2015-11-14
You might be better off doing this

> 
[LIST=1]
[*]Search the archives of the [htk-users mailing list]("http://htk.eng.cam.ac.uk/cgi-bin/search.cgi?q=installation&ps=20&o=0&m=all&ul=%2Fpipermail%2Fhtk-users")
[*]If you don't find what you're looking for in the search, [EMAIL="htk-users-request@eng.cam.ac.uk?Subject=subscribe&Body=subscribe"]subscribe to the htk-users list[/EMAIL] and post your question there.
[/LIST]


[http://htk.eng.cam.ac.uk/docs/inst-nix.shtml](http://htk.eng.cam.ac.uk/docs/inst-nix.shtml)

Regards

---

### Post by dallasabartlett on 2015-11-14
You were right. I didn't realize it was a 32 Bit program, or that I needed to install separate libraries. Thanks for the help, I really appreciate it!

---

