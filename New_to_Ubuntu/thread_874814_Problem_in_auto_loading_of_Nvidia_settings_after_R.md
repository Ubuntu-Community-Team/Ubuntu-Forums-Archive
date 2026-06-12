---
title: "Problem in auto loading of Nvidia settings after Reboot"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by SandyM on 2008-07-30
Hi I am a new ubuntu user . I am facing a very critical problem with regards to my nvidia settings. Although ubuntu do recognise these settings when I select them from menu but THESE SETTINGS ARE UNABLE TO SELF-RELOAD AFTER REBOOT . Everytime I have to manually apply these settings .
I alredy created an autoload entry in 'session' sub menu of'preference'. I recently reinstalled ubuntu due to certain other problem but then this autoload entry was working perfectly.
Please help !!!!!!!!!!!!!!!!!!!

---

### Post by Inxsible on 2008-07-30
You need to use the nvidia-settings program as root and make the necessary changes and once you are done, you need to click the Save to configuration file button. That will save the settings in xorg.conf and will still work on reboot

```
gksudo nvidia-settings
```

---

