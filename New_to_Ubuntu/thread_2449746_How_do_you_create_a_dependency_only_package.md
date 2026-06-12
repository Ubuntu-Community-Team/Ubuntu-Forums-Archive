---
title: "How do you create a dependency only package?"
date: 2020-09-01
forum: New to Ubuntu
---

### Post by akangka on 2020-09-01
I want to install RemoteMouse. The problem is the program is shipped in .tar.gz but also contains a dependency. Instead of just installing the dependency and risk forgetting how to uninstall, I want to create a new empty package so that the dependency can be deleted by simply typing ```
sudo apt autoremove remotemouse
```

---

### Post by scorp123 on 2020-09-02
> **akangka said:**
> ... Instead of just installing the dependency and risk forgetting how to uninstall... 

I took a look at that tar.gz and it contains an "install.txt" file with detailed instructions. Not much to forget, you simply undo their install instructions:
```

sudo apt-get install -y mono-complete xdotool libappindicator0.1-cil-dev

If you are running it in Ubuntu 18, you may need the following command in addtional:

sudo apt-get install -y libcanberra-gtk-module

```

So you just replace "install" with "remove" in above commands and those dependencies will be removed again.


> **akangka said:**
> 
 ```
sudo apt autoremove remotemouse
```

You'd need to build your own Debian/Ubuntu "deb" package with the "dpkg-deb" tool (... Google can tell you more ...) and then enter the dependency information into the "control" file every "deb" package has at its core. But I feel this is "overkill". It would be a lot easier and more efficient to simply take the information from RemoteMouse's "install.txt" file and write your own quick "uninstall" script that will achieve the same thing and get rid of those dependencies if needed, there's no need to dive into "deb" package creation.

---

### Post by akangka on 2020-09-02
But, what if it turns out I installed another program, which turns out to also depends on the same dependency? (Especially if it's also not installed by `apt install` too.)

---

