---
title: "I screw up my TOTEM"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-21
Hello, i think i just screw up my TOTEM. I dont know what i click, but now I can not minimize TOTEM to it original size. One more thing, I accidentally defaulted my Color Balance and now the picture of my movie is very bad. How to reset TOTEM to default setting (as after install)

---

### Post by 1875 on 2008-05-21
Have you tried VLC instead of Totem ? Much better media player IMHO.

---

### Post by Maestro23 on 2008-05-21
> **wariskampar said:**
> Hello, i think i just screw up my TOTEM. I dont know what i click, but now I can not minimize TOTEM to it original size. One more thing, I accidentally defaulted my Color Balance and now the picture of my movie is very bad. How to reset TOTEM to default setting (as after install)

For you color issues: Edit>>Prefs>>Display

---

### Post by tdrusk on 2008-05-21
> **wariskampar said:**
> Hello, i think i just screw up my TOTEM. I dont know what i click, but now I can not minimize TOTEM to it original size. One more thing, I accidentally defaulted my Color Balance and now the picture of my movie is very bad. How to reset TOTEM to default setting (as after install)
The easiest way to fix this would be to open Synaptic and completely remove it. Then go into Home and View Hidden Files. Then find .totem ? This could be incorrect as I do not use Totem.

After that just reinstall.

---

### Post by neurostu on 2008-05-21
or you could just close totem and remove .totem directory. The next time you open totem it will create a new .totem dir, there isn't a need to unistall.

---

### Post by wariskampar on 2008-05-22
I have uninstall-reinstall TOTEM 3 times but the problem persist. Maybe the config file still exist therefore setting does not change. Where is the config file for TOTEM

---

### Post by RiceMonster on 2008-05-22
> **wariskampar said:**
> I have uninstall-reinstall TOTEM 3 times but the problem persist. Maybe the config file still exist therefore setting does not change. Where is the config file for TOTEM

```
rm -r ~/.config/totem
```

Then reopen it.

---

### Post by wariskampar on 2008-05-22
@RiceMonster; thank you very much. this solve my problem:)

When i look at TOTEM folder, i found at lot of other similar TOTEM folder(maybe duplicate copy due to re-install few times). How do I get a clean folder for TOTEM (as if new). Thanks

---

### Post by neurostu on 2008-05-22
just delete these extra folders, if you can't delete them then use sudo

---

### Post by wariskampar on 2008-05-22
I also think taht will do it. But how to know whether the folders are the right one. Any code to simply this task (delete safely w/o compromise current setting)

---

