---
title: "How do I get compiz?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Tex786 on 2008-11-27
Hi,

How do I get compiz in 8.10? I have been playing around with 8.10 and have always been able to get compiz. Now I am unsure how to get compiz..

Can anyone help??

---

### Post by theplastikjesus on 2008-11-27
> **Tex786 said:**
> Hi,

How do I get compiz in 8.10? I have been playing around with 8.10 and have always been able to get compiz. Now I am unsure how to get compiz..

Can anyone help?? I'm fairly new to 8.10 i think you can go to add new under applications and search for it in there.
Hope that helps.

---

### Post by jgoguen on 2008-11-27
Compiz is included by default in Ubuntu now.  If your video card can handle it, Compiz may already be turned on.  You can check by opening Appearance settings (System -> Preferences -> Appearance) and choosing the "Visual Effects" tab.  There are three options: None (no Compiz effects), Normal (some Compiz effects), and Extra (more Compiz effects).  Normally, Normal is chosen.  If you want more, try choosing Extra.  If None is selected, try choosing Normal to see if Compiz works well with your video card.

---

### Post by philinux on 2008-11-27
Check your vid card driver is enabled first.

System>admin>hardware drivers.

It would help if pc specs are posted including graphics card.

---

### Post by Michael.Godawski on 2008-11-27
Some more data please. Would be good to know the outputs of these terminal commands:

```
lspci
sudo lshw -C display
```

---

### Post by adult swim on 2008-11-27
if you run ```
sudo apt-get install compizconfig-settings-manager
``` from a terminal then you can go to system>preferences>compizconfig settings manager and set up compiz how you want it.

---

