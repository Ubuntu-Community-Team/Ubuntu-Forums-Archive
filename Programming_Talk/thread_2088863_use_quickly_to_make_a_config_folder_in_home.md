---
title: "use quickly to make a config folder in home"
date: 2012-11-27
forum: Programming Talk
---

### Post by condeGil on 2012-11-27
I need to make a ~/folder/configFile to use with my aplication. when the deb package is created by "quickly" should create this folder with this file. Someone can teach me to do it? 
By the way, can also tell me where should I put my axillary files ".py" in the project folders (like classes and stuff)?

---

### Post by Zugzwang on 2012-11-28
> **condeGil said:**
> I need to make a ~/folder/configFile to use with my aplication. when the deb package is created by "quickly" should create this folder with this file. Someone can teach me to do it? 


I'm not exactly sure if I understood you correctly, but you appear to want to get a file "~/folder/configFile" created automatically when someone installs the .deb package of your program?

This is not supported, as the "~" file is different for every user of the system, and thus this doesn't make sense on a multi-user system. Assume that you first install your program and then create a new user. This new user will surely not have the configuration file in place.

Here is an alternative: add some code to your program such that whenever the application is started and the configuration file is not present, some default configuration file is written to "~/folder/configFile".

---

