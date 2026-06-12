---
title: "Network interface controller not connecting"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by cybertron3000 on 2008-05-10
I recently bought a used Dell Optiplex desktop and installed Ubuntu.  Only catch is the network doesn't connect.  Network interface controller is a 3c59x driver, I believe.  

I don't know what is wrong, as my HP desktop with Ubuntu never had any problems.  

Help if you can, thanks.

---

### Post by klaasvanschelven on 2008-05-11
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=3c59x+network](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=3c59x+network)

What's the output from

```
$ sudo lshw
```

or 

```
$ sudo lspci 
```
And you may condider moving the thread to networking questions so the right people read it...

Klaas

---

