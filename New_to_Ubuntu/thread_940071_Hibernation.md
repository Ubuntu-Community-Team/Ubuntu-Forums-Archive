---
title: "Hibernation"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-06
I go command line and type 

```
sudo hibernate
```

but i can't hibernate... i get the following:

```
Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```

if i try and override it does nothing and i'm still at my desktop.

how do i sort out the ModulesUnloadBlacklist errors etc?

---

### Post by joey-elijah on 2008-10-08
*bump*

would love to get this sorted... any one help?!

---

### Post by Nxion on 2008-10-08
> **joey-elijah said:**
> I go command line and type 

```
sudo hibernate
```but i can't hibernate... i get the following:

```
Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```if i try and override it does nothing and i'm still at my desktop.

how do i sort out the ModulesUnloadBlacklist errors etc?


Is this on your desktop or laptop? If it is a laptop then what brand is it? Dell? HP? I was having the same issue with my laptop not wanting to sleep and it is a Dell.

---

### Post by joey-elijah on 2008-10-10
it's a desktop...

---

### Post by Nxion on 2008-10-14
Sorry it took me so long to reply

I found this and from what I read this should fix your issues. The title says it is for Gutsy but people have been using it for there Hardy machine without issue.

[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

Hope that helps.

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

