---
title: "How to manage update packages"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by HollywoodJumper on 2008-09-27
if i choose to use the package manager instead of the terminal is there any thing important i need to know about the repository indexes.  Is there a difference between the sudo apt-get install update and the update package manager? Other than the userfriendliness.  Do i need to check my synaptic package manager to make sure i am installing the updates i download. If anyone has some time to shed some light on these issues it would give me a warm and fuzzy.  
    p.s. Dont get pissed cause i am a noob](*,)[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by Xiong Chiamiov on 2008-09-27
The command is actually
```

sudo apt-get update
sudo apt-get upgrade

```
but that's a minor detail.  Both of them are front-ends to apt, so they do the same thing.  Whatever floats your boat.  Usually on the forums we tell you to install things with apt-get or aptitude because it's quite a bit easier to give instructions that way.

---

### Post by HollywoodJumper on 2008-09-28
So should i go through my synaptic package manager looking for stuff that was downloaded for an update but not installed?

---

### Post by Xiong Chiamiov on 2008-09-28
Unless you interrupt the update process, nothing should be downloaded and not installed.  And if it isn't installed, then it'll just show up in the updates again anyway.

---

