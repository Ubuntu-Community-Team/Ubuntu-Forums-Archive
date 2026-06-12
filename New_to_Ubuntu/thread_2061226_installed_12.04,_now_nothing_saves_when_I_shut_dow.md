---
title: "installed 12.04, now nothing saves when I shut down."
date: 2012-09-22
forum: New to Ubuntu
---

### Post by cmudd on 2012-09-22
I am very green with Ubuntu. I recently upgraded to 12.04. there was some kind of system error. now whenever I shut the computer down all bookmarks, saved passwords, history, commonly used sites are erased. the sound on videos is also choppy now. 

When I try to install updates now I get an error message as follows:

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.

This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu

                                    Partial Upgrade         Close

I am choosing to close at this time as I wish to clear up the current problems before moving forward

---

### Post by carl4926 on 2012-09-22
> I recently upgraded to 12.04From what?

> there was some kind of system errorHow random is that?

> now whenever I shut the computer down all bookmarks, saved passwords, history, commonly used sites are erased. Are you sure you are not just booting a Live CD?

---

### Post by hypnot0ad on 2012-09-22
Please be more specific. Help us help [you]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by cmudd on 2012-09-22
> **carl4926 said:**
> From what?

How random is that?

Are you sure you are not just booting a Live CD?

Not booting from a live CD. Some time ago my LINUX friend helped me install an earlier version of Ubuntu. I have been upgrading whenever a new version came available. I am pretty sure my last version was the 11.0?.

---

### Post by carl4926 on 2012-09-22
Sounds like time to backup and do a clean install

---

### Post by cmudd on 2012-09-22
> **carl4926 said:**
> Sounds like time to backup and do a clean install
ok. since this isn't giving the results I want that sounds good. how do I do this, and what do I need to back up?

---

### Post by cmudd on 2012-09-22
> **hypnot0ad said:**
> Please be more specific. Help us help [you]("http://ubuntuforums.org/showthread.php?t=1422475")
I am using Ubuntu so I don't have command lines. (maybe I should?)

---

### Post by hypnot0ad on 2012-09-22
Since it doesn't sound like you can run 12.04 (Im probably wrong) maybe you should think of installing something else. From what I understand if the machine can't run a live cd without much trouble you are probably not going to be able to install the real thing. 

Do you have anything on the computer that you would like to save before doing the install? Pictures, Docs, etc etc. Save them as they will be lost. No matter what version you choose the install steps will basically be similar and simple. I would think using the CD method over the USB will help you with your desired results.

Click on the how to install in my signature and save it somewhere. There you will learn what you need.

Have fun with your new ubuntu;)

---

### Post by carl4926 on 2012-09-22
> **cmudd said:**
> I am very green with Ubuntu. I recently upgraded to 12.04. there was some kind of system error. now whenever I shut the computer down all bookmarks, saved passwords, history, commonly used sites are erased. the sound on videos is also choppy now. 

When I try to install updates now I get an error message as follows:

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.

This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu

                                    Partial Upgrade         Close

I am choosing to close at this time as I wish to clear up the current problems before moving forward

Please let us see the result of

```
inxi -r
```

---

### Post by kostkon on 2012-09-23
Are you sure you aren't logging in as guest (ubuntu comes with a guest account by default)???

---

### Post by hypnot0ad on 2012-09-27
> **carl4926 said:**
> Please let us see the result of

```
inxi -r
```

What is?

```
inxi -r
```

---

### Post by carl4926 on 2012-09-28
inxi
is a systems information application
-r
should supply the repo info

---

### Post by hypnot0ad on 2012-09-28
If its something you need to install will it be useful to OP?

---

### Post by carl4926 on 2012-09-29
> **hypnot0ad said:**
> If its something you need to install will it be useful to OP?
It's usually installed
And it provides very useful Hardware info

---

