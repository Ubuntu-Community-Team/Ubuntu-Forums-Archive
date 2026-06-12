---
title: "Compiz not working"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by Skull Kid on 2011-12-07
Hey guys, I've recently installed 11.10 on my new laptop a few days ago and noticed the compiz effects were working on default, which I really liked. However after a day or two it seems those window effects are gone. I'm not sure what triggered it or caused it to happen, but even with the options checked in the config manager there's no animations at all. 

I've tried removing the nvidia-current package as suggested in another thread, but that doesn't work. Could anyone help me re-enable the effects? Thanks!

---

### Post by Skull Kid on 2011-12-07
Any ideas? For what it's worth, when I look up my display adapter it recognizes it as a GT555M, which is incorrect. It's actually a 540M. Could this be related, and how do I fix it? I'm currently using the recommended proprietary drivers from the 'Addtional Drivers' page. Thanks for any help.

---

### Post by BC59 on 2011-12-07
Try to reset Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

---

### Post by Skull Kid on 2011-12-07
Thanks for your help. That didn't seem to do much :( I'm following through the advice in [this]("http://ubuntuforums.org/showthread.php?t=1878130") thread and it seems I don't have Unity-3D enabled, even though it is selected at log-in. Something's making it fallback to 2D everytime and I'm not sure what.

---

