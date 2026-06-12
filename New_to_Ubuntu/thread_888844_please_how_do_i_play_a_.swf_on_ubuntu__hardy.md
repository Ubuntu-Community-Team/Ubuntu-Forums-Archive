---
title: "please how do i play a .swf on ubuntu  hardy"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by nnamdi on 2008-08-13
hello friends i got an online tutorials in .swf format what do i install to play the file thanks

---

### Post by Thelasko on 2008-08-13
You need adobe's flashplayer to play those.  Open the terminal and type:
```
sudo apt-get install flashplugin-nonfree
```
That should get it to work.

---

### Post by nnamdi on 2008-08-13
hello thanks but it still did not work i got these error

```


GStreamer encountered a general supporting library error.

```

---

### Post by OutOfReach on 2008-08-13
Hmm, try this:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by reya276 on 2008-08-13
Try installing the 'ubuntu-restricted' package from synanptic. you can do this by going to System>Administration>Synaptic Package Manager. The once there do a search for Ubuntu Restricted and select that package(right-click mark) then click on apply.

---

