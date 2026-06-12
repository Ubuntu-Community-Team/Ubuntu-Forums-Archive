---
title: "Uninstall Double Commander"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by GrindcoreVlad on 2012-02-05
I have installed double commander but since I cannot use the keyboard shortcuts (couldn't find the reason why...) i decided to remove it.

The problem is that I get the message 
> Virtual packages like 'doublecmd' can't be removed


Could you please advise me on what to do or maybe I have done something wrong in the first place. 

Thanks

---

### Post by Bodsda on 2012-02-05
Hi,

Welcome to the forums.

I can't find any info on this package in the ubuntu repositories so I'm gonna guess that you installed it from a ppa. Either way, a virtual package is just a package that defines a bunch of packages that need to be installed, it is not in itself any one package, so therefore cannot be removed. What you have to do is remove all of the actual packages that this meta/virtual package installed.

You'll be able to find this out by looking at the package in synaptic or somthing similar.

Hope this helps,
Bodsda

---

### Post by GrindcoreVlad on 2012-02-07
> **Bodsda said:**
> Hi,
You'll be able to find this out by looking at the package in synaptic or somthing similar.

Hope this helps,
Bodsda
I did it finally. I used Aptitude and found the package.

Thanks for pointing me in the right direction.

---

### Post by Karlchen on 2012-02-07
Just for those interested to learn what Double Commander is and where to find it: [**Double Commander - Download**]("http://doublecmd.sourceforge.net/site/eng/download.html")
There is a [Double Commander Ubuntu PPA](https://launchpad.net/%7Ealexx2000/+archive/doublecmd). So it can be installed and uninstalled using Synaptic.
Hence a piece of advice for free for all those users whose Ubuntu version does no longer bring along Synaptic: get Synaptic. Makes life a lot easier. :wink:

Karl

---

