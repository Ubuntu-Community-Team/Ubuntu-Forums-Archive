---
title: "Workspace Problem"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by Gigabitten on 2012-09-03
Most programs open too big.  Sometimes, I can't resize them.  But recently, I discovered that these programs were spanning multiple workspaces.  It would seem that the opening of the program is being treated as if all of the workspaces are one...I don't use workspaces, so, if I need to disable their use to get this to work, I will.  Oh, and I'm using 11.04.  12.04 has some problems with Java, and once I got past those, Minecraft STILL had trouble.  But I'm a beginning Java programmer, and since this one comes with JDK, and I missed the 11.10 update(and so am not familiar with 11.10) I'm using 11.04.

---

### Post by jmate24 on 2012-09-03
this is what you need to install.  Ubuntu Tweak here are the instructions of how to add the repository and then install it.

Open a Terminal by searching for it in the Dash.

then once it opens up copy and paste this command into the terminal:

```
sudo add-apt-repository ppa:tualatrix/ppa && sudo apt-get update && sudo apt-get install ubuntu-tweak
```

If you have any problems then copy and paste this into the terminal:

```
sudo dpkg --configure -a && sudo apt-get install -f
```

give this a try and if it dosn't work pm me.

jmate24

---

