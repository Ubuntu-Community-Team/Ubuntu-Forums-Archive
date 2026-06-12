---
title: "Youtube videos do not work in Chromium"
date: 2016-06-14
forum: New to Ubuntu
---

### Post by Tom_Carr on 2016-06-14
I just switched from Chrome to Chromium to a 32 bit machine since Chrome is no longer supported.  Youtube videos work fine in Chrome and Firefox, but not in Chromium.  How do I fix this?

---

### Post by X-RED_Tech on 2016-06-14
Enable the Partners repository and

```
sudo apt-get update
sudo apt-get install adobe-flashplugin
```

---

### Post by Tom_Carr on 2016-06-14
Thanks.  How do I enable the partners repository?

---

### Post by deadflowr on 2016-06-14
> **Tom_Carr said:**
> Thanks.  How do I enable the partners repository?

Open the program Software and Updates, or run the command *software-properties-gtk*.
Then go to the section marked Other Software and click on the entry for Partners. (It'll ask for your password)
Then close. (It should ask if you want to close or reload the package listing. Reloading is as good as running apt-get update, so you can simply do that and then you only need to run the apt-get install command)

Hope it helps

---

### Post by Tom_Carr on 2016-06-14
Thanks

---

