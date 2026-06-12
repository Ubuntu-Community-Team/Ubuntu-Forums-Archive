---
title: "[SOLVED] Laptop with External Monitor: Saving Settings to X Configuration File"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by SilverDragon on 2008-11-27
I'm trying to set up my external Samsung SyncMaster 226BW with my laptop with specs which are in my signature. To accomplish this I went to System > Administration > NVIDIA X Server Settings.Then I went to X Server Display Configuration and set everything up the way I want it.

The problem is when I click on "Save to X Configuration File" I get an error which I took a screen shot of and attached to this post.

I think I have to save my changes with "Save to X Configuration File" because when I log out/shut off/restart I have to set up the external monitor again.

---

### Post by Elfy on 2008-11-27
Run the command form terminal as root

```
gksudo nvidia-settings
```

---

### Post by marshall.robert on 2008-11-27
you will need to run it as root, press alt+f2 to get the run dialog up and then type ```
 gksudo nvidia-settings 
```

---

### Post by SilverDragon on 2008-11-27
Well that was a simple fix #-o

It worked but I am just wondering why gksudo is used instead of sudo?

---

### Post by Elfy on 2008-11-27
You should use gksudo for all gui apps and sudo for not - information is available here 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

It can cause problems - I think it did cause me problems, but not completely sure :)


I edited my entry in the admin menu so it starts with root rights.

---

