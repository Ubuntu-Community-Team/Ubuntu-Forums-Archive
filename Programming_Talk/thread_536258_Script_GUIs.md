---
title: "Script GUIs?"
date: 2007-08-27
forum: Programming Talk
---

### Post by MattAd on 2007-08-27
Hello out there, everyone. I was wondering, is there a way of writing GUIs that can execute shell script commands? I wrote myself a nice bash script for setting up my wireless card, and was curious is I could create a frontend that looks a little nicer.

I don't know if this is possible (or even practical) or not, so it'd be much appreciated if someone told me, either way. Thanks!

---

### Post by Lord Illidan on 2007-08-27
Yep, quite possible. Automatix was made using this, as well as many other programs. Zenity can also be used to give a gui to your script.

---

### Post by vambo on 2007-08-27
zenity might be worth a look - see ```
man zenity
```

If not installed, it should be in Synaptic

Cheers

---

### Post by MattAd on 2007-08-27
> **vambo said:**
> zenity might be worth a look - see ```
man zenity
```

If not installed, it should be in Synaptic

Cheers

I probably sound like an idiot, but what is Synaptic? Is it a program, or a repository that I need to add? I've been assuming it's a program, but I have no idea.

I'll definitely check out Zenity, though. Thanks!

---

### Post by vambo on 2007-08-27
System -> Administration -> Synaptic Package Manger

---

### Post by pmasiar on 2007-08-27
Synaptic is GUI front-end for apt.

Python is good and flexible way to make GUIs. wxPython is you need tricky GUI, easyGUI if you want simplest basics. See wiki in my sig

---

