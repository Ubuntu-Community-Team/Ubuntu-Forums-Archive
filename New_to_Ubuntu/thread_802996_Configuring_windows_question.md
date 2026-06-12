---
title: "Configuring windows question"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-21
I'm running Ubuntu 7.10 on an old AMD Duron white box and although I've upped the graphics card and RAM, I still get the "fun house mirrors" effect every time I move a window. In Kubuntu there was a setting to just move the window without it's contents showing. Does Ubuntu have a similar feature? Thanks.

---

### Post by Bakon Jarser on 2008-05-21
if it's anywhere it will be in the compiz manager which isn't installed by default for some reason.

```
sudo apt-get install compizconfig-settings-manager
```

Then go to System > Preferences > Advanced Desktop Effects Settings

The first thing I'd do if I were you is try turning off wobbly windows and see if that helps.

---

### Post by jacatone on 2008-05-22
And where is this wobbly windows settings?

---

### Post by Bakon Jarser on 2008-05-22
It's in advanced desktop settings under the effects section.

---

