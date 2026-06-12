---
title: "Installing MoBlock"
date: 2015-01-20
forum: New to Ubuntu
---

### Post by Jonathon_Wisnoski on 2015-01-20
Been trying to follow: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) but it is far from clear which steps I am supposed to follow.

I think I have been following the right steps (skipping everything under the "Ubuntu 8.04 ("Hardy Heron") heading"), I get to installing the package, and it cannot find it. I try that "deb" step and not only am I unsure of my DIST (my code name is "trusty" apparently) but it says that it does not recognize the command "deb".

I am using some version of lubuntu:
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

---

### Post by mörgæs on 2015-01-20
On the page to which you link, did you read the top paragraph?

---

### Post by Jonathon_Wisnoski on 2015-01-20
No, good catch. So then, how do I undo
[LIST]
[*=left]sudo add-apt-repository ppa:jre-phoenix/ppa
[/LIST]

---

### Post by Jonathon_Wisnoski on 2015-01-20
No, good catch. So then, how do I undo: "sudo add-apt-repository ppa:jre-phoenix/ppa"? Or do I just leave it?

---

### Post by Holger_Gehrke on 2015-01-21
> **Jonathon_Wisnoski said:**
> ... how do I undo: "sudo add-apt-repository ppa:jre-phoenix/ppa"? 

From 'man add-apt-repository':
> 
-r, --remove Remove the specified repository

so it should be:
```

sudo add-apt-repository --remove ppa:jre-phoenix/ppa

```

It's a good idea to remove it. It may not cause any problem for a long time, so when it does some day, it would be hard to find the cause.

---

