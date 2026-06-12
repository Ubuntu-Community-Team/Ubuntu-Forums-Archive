---
title: "New to Ubuntu with some questions..."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Toxic Thrasher on 2008-05-05
First off, hello everyone.

Well, I finally got around to installing Ubuntu, and I love it, but I'm having a small problem.

The problem is that some embedded videos on sites are not working (I'm guessing they are flash). Its only some videos it seems, and the ones that do work sometimes lag quite a bit. Is there something I am missing to make all of them work? 

And one question I have is about viruses and spyware. When I use windows, I always do a virus/spyware scan before ordering anything online. With Ubuntu, do I need to worry about viruses or spyware?

Thanks everyone!

---

### Post by Tatty on 2008-05-05
In short, no need to worry about viruses or spyware as there are currently no linux viruses which exist in the wild and function on a modern linux kernel.  There have only been a handful ever to exist, most only in a computer lab, and they have all now been patched out of existance.

Thats not to say that there will never be another one in the future, but for now its nothing to worry about.  The best advice is to simply keep up to date with the linux community, as if anything like that appears then word of it will spread very quickly, probably followed rapidly by a fix.


For the flash issue, which flash player have you installed?  Currently the open source flash players lack somewhat, although this should be fixed as Adobe has recently announced plans to open the specifications for flash.

You should install the proprietry flash player to make all the flash videos work.

---

### Post by superbenny on 2008-05-05
sudo aptitude install flashplugin-nonfree

---

### Post by linfidel on 2008-05-05
> **Toxic Thrasher said:**
> First off, hello everyone.

Well, I finally got around to installing Ubuntu, and I love it, but I'm having a small problem.

The problem is that some embedded videos on sites are not working (I'm guessing they are flash). Its only some videos it seems, and the ones that do work sometimes lag quite a bit. Is there something I am missing to make all of them work? 

And one question I have is about viruses and spyware. When I use windows, I always do a virus/spyware scan before ordering anything online. With Ubuntu, do I need to worry about viruses or spyware?

Thanks everyone!I assume you are not running as root; this is the equivalent of running Windows as administrator.  If people didn't run as administrator, the amount of viruses or spyware would go down drastically, because these programs would not have the authority to install themselves.  That is one of the big reasons that linux or unix is safer - users rarely run as root, and there's really no need to - you just use sudo.

I think Vista is trying to do something similar, but I think it's able to be bypassed, so it probably will be.  Windows users, for the most part, don't want to think about it.

I don't use any antivirus software or antispyware on my Ubuntu system, and don't plan to.

---

### Post by Sef on 2008-05-05
> sudo aptitude install flashplugin-nonfree

First type this code:

```
sudo apt-get update
```

then type

```
sudo aptitude install flashplugin-nonfree
```

---

### Post by superbenny on 2008-05-05
Sorry, there was a database error and I submitted it twice...and now I can't delete this post...

---

### Post by rburkartjo on 2008-05-05
toxic, try this to fix fash player if it still isnt working. it worked for me your need to open the spm to do this
[http://blog.eirikhoem.net/index.php/2008/04/30/firefox-java-problem-with-ubuntu-804-solved/](http://blog.eirikhoem.net/index.php/2008/04/30/firefox-java-problem-with-ubuntu-804-solved/)
cheesemaker

---

