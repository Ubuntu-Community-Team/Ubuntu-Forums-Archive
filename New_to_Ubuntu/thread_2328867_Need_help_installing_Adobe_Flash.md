---
title: "Need help installing Adobe Flash"
date: 2016-06-25
forum: New to Ubuntu
---

### Post by Jim_Robson on 2016-06-25
Hello, thanks for having this forum. This is a new installation. I like to stream music from SiriusXM, but the browsers (Firefox & Chrome) require the installation of Adobe Flash to stream music. I tried to insall Flash into my browsers, but I'm getting options that I don't understand and it wont install. Thanks for your help.

---

### Post by howefield on 2016-06-25
Chrome comes with flash out of the box, for firefox installing adobe-flashplugin should be enough.

```
sudo apt-get install adobe-flashplugin
```

Might help to outline what you have already done and what the exact "*options that I don't understand*" are ?

---

### Post by ajgreeny on 2016-06-25
You must enable the canonical-partner repositories in order to see adobe-flashplugin in the list of available packages.

Open software-sources from the menu or dash, depending on your Desktop, go to Other Software tab and at the top you will see the Partner Repositories; make sure they are enabled.

---

