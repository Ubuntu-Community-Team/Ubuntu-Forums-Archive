---
title: "Chromium will not allow webcam access"
date: 2019-01-04
forum: New to Ubuntu
---

### Post by spamanon on 2019-01-04
In my long adventure to use my webcam with facebook chat in Chromium, I have been trying to install flash player.  I am trying to follow the instructions on this page but they are not right. 

[https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en#canonical-partner](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en#canonical-partner)

When I open Ubuntu software there is NO "Other Software" tab.  There is only "All | Installed | Update" tabs.

How do I do this when the directions are wrong?  When I try to use chat a bubble pops up that tells me I need to allow camera access but there is nothing to click to do so.  I would show a screenshot but none of the image editors that came with ubuntu seem to allow pasting a print screen like paint did.  :-(

Thanks

---

### Post by spamanon on 2019-01-05
Any help at all?

---

### Post by Frogs Hair on 2019-01-05
The other software tab is found in software & updates. I think the author of the wiki was in error.

You can install flash with the following terminal command

```
sudo apt install adobe-flashplugin
```

---

### Post by spamanon on 2019-01-05
Something went wrong.  Any other suggestions?

[IMG]https://i.imgur.com/FpWfdea.png[/IMG]

---

### Post by Frogs Hair on 2019-01-06
Open software & updates > Other software and make sure the Canonical partners repository is enabled. Try the following which if successful will install flash and other codec packages for restricted formats .

```
sudo apt install ubuntu-restricted-extras 
```

---

