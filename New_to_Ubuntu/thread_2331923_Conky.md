---
title: "Conky"
date: 2016-07-26
forum: New to Ubuntu
---

### Post by nomadxp1 on 2016-07-26
Question fpr Conky users.. Can Conky be run on only _one_ desktop ?
Thanks for your help

---

### Post by QIII on 2016-07-26
I'm not at my machine to look, but I think you just need to add "sticky" to the window hints.

---

### Post by RobGoss on 2016-07-26
> **nomadxp1 said:**
> Question fpr Conky users.. Can Conky be run on only _one_ desktop ?
Thanks for your help

I'm not really sure what you mean on only one desktop, can you explain what it is you want to accomplish with Conky

---

### Post by yetimon_64 on 2016-07-26
> **nomadxp1 said:**
> Question fpr Conky users.. Can Conky be run on only _one_ desktop ?
Thanks for your help

I suspect you mean on every workspace (what you may be calling a "desktop"), if so then QIII gave the answer you need, that is you need to add the "sticky" hint under the "own_window_hints" line in the .conkyrc file.
For example the own_window_hints line from my ~/.conkyrc file reads ...
> ```
own_window_hints undecorated,below,**sticky,**skip_taskbar,skip_pager
```... the bolded word "sticky" above is what ensures the conky is on every workspace here. **Edit:** by contrast, if you mean you only want it on the one workspace and not all of them, remove the word "sticky" from the line and it will only appear on the first one the conky is opened on originally.

If you have multiple DEs (desktop environments or "desktops") installed on the one install of Ubuntu you can have the one conky show in each by adding a start up entry for each desktop environment. I have my conky show up whenever I boot into Unity or Xfce from the one ~/.conkyrc file. This is what I refer to as a "desktop", whereas if you only have one DE installed you are more likely to be referring to the "workspaces" on mate as "desktops". Hope that makes sense to you. Regards, yeti.

---

### Post by QIII on 2016-07-26
Ooooo!

I read that as "all" somehow!

---

