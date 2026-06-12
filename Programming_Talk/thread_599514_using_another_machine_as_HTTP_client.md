---
title: "using another machine as HTTP client"
date: 2007-11-01
forum: Programming Talk
---

### Post by dijxtra on 2007-11-01
I wrote a python script which does some HTTP fetching and parsing. I can run only one instance of this script form one host (one IP address). I have then copied this script to machines A, B and C and I run that script from all of those.

But, it turned out that I don't have python on machine D, and I was supposed to run the script from there too. Now, is there a way to run the script only on machine A, and then tunnel the traffic to machine D so that to server it appears that the script is run on machine D?

I have a shell account on each of these machines and each has OpenSSH installed. I suppose I could do something with SSH port forwarding, but I'm not sure what. Few hints would be useful, so I can start googling for details.

Thanks in advance.

---

### Post by LaRoza on 2007-11-01
It would be easier to:

* Get Python for the other machines. If they are Windows, get ActivePython  [http://laroza.pbwiki.com/Windows](http://laroza.pbwiki.com/Windows)

* Use py2exe to make the python program a binary program. (For Windows)

* Use the equivalent of py2exe for any Python-less Linux setups. I think it is called "Freeze"

---

### Post by dijxtra on 2007-11-01
> **LaRoza said:**
> It would be easier to:

* Get Python for the other machines. If they are Windows, get ActivePython  [http://laroza.pbwiki.com/Windows](http://laroza.pbwiki.com/Windows)
Those are linux boxen and I'm not root.
> **LaRoza said:**
> * Use py2exe to make the python program a binary program. (For Windows)
See 1.
> **LaRoza said:**
> * Use the equivalent of py2exe for any Python-less Linux setups. I think it is called "Freeze"
Mmmmmmmmmm, this one's beautiful! :-) Yes, this one could be used. I'll use this one if I don't figure out how to do the tunnelling thing.

So, Freeze might solve my problem, but now I have spent quite some time reading ssh documentation and tunnelling tutorials, so I'd really like to know if it is possible to execute a python http client one one machine and make it look as if it was run on some other machine using ssh tunnelling. So, if anyone has an idea...

---

### Post by cwaldbieser on 2007-11-01
> **dijxtra said:**
> Those are linux boxen and I'm not root.

See 1.

Mmmmmmmmmm, this one's beautiful! :-) Yes, this one could be used. I'll use this one if I don't figure out how to do the tunnelling thing.

So, Freeze might solve my problem, but now I have spent quite some time reading ssh documentation and tunnelling tutorials, so I'd really like to know if it is possible to execute a python http client one one machine and make it look as if it was run on some other machine using ssh tunnelling. So, if anyone has an idea...

Without any more specific information about your problem, I believe that you must use dynamic port forwarding (also called SOCKS forwarding).  It would be something like:
```

$ ssh -D 1080 remote-machine

```
Your python program would have to use localhost:1080 as a proxy.  In theory this should work, though I have never tried this.

---

### Post by dijxtra on 2007-11-02
> **cwaldbieser said:**
> Without any more specific information about your problem, I believe that you must use dynamic port forwarding (also called SOCKS forwarding).  It would be something like:
```

$ ssh -D 1080 remote-machine

```
Your python program would have to use localhost:1080 as a proxy.  In theory this should work, though I have never tried this.
Oh, great. It works both in theory and in practice :-) It works for my browser, now I just have to set it up for my python http client. Thank you very much for this hint, that is just what I was looking for.

---

