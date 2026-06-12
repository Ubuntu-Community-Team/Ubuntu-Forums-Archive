---
title: "Best way to install .deb package"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-06-10
Hello all!

Can any of you guys or girls tell me what the most sensible way to install a deb package is?

Does the package manager track it if I install it using dpkg? or should I instead just download the source code and install it with checkinstall?

Also is it safe? I don't think it's a shady package but are there any hidden dangers? The program is FreeTube, an open source YouTube client and I would be getting the .deb from the official site (which I would link but I'm not sure that's allowed here) as it is not available through the main repo and there doesn't seem to be a PPA.

Thanks!

---

### Post by CatKiller on 2020-06-10
.deb packages, whether downloaded or built yourself, will be integrated into the normal package management. You can uninstall then, see what files are put where, and so on, but you won't get updates to them since they're not from a repository.

You can see what files are in a package with normal archive management tools, ark, file-roller, or whatever.

---

### Post by Holger_Gehrke on 2020-06-10
dpkg is basically the lower level of the package management infrastructure, so yes, the install will be seen by the rest of package management if you install with 'dpkg -i' . You could also use 'apt install' with a path to the package-file (basically there has to be at least one '/' in the argument for apt to understand you want it to install a local file). You could also double click the file in the file manager to open gnome-software to install the package. Or if you have gdebi installed that could also be used.

If you're worried about the program misbehaving then you could try using the flatpak. Flatpak is another implementation of sandboxed applications similar to snap and offering about the same level of protection (which is not all encompassing; it's better against faulty applications running amok than against intentional sabotage; there has been a well publicised case of a snap containing a crypto-miner in addition to the program the users wanted to install).

Installing from source only gives an additional level of security if you actually **read **and** understand** the source code** before** installing.

Holger

---

### Post by jcdenton1995 on 2020-06-11
Thanks for the info,

I chose to go install gdebi-core and use that as I understand that dpkg cant resolve dependencies, should there be any. I didn't realize apt can be used in the same way though. In terms of security I'm going to go ahead and trust the developer on this one as they are pretty active online in relevant forums etc. and they have open sourced it - even if I can't understand it myself I think it counts for something as, if there is some malicious code in there, somebody who can understand it would surely point it out.

> Installing from source only gives an additional level of security if you actually **read **and** understand** the source code** before** installing.

Great, I'm half way there then! :cool:

---

### Post by olduse78802 on 2020-06-11
I try to use gdebi whenever I can. It just works.

---

### Post by ActionParsnip on 2020-06-11
I use:
```

sudo dpkg -i filename.deb; sudo apt-get -f install

```

The first part installs the deb and the second part attempts to resolve deps using your available sources

---

### Post by jcdenton1995 on 2020-06-11
> **ActionParsnip said:**
> I use:
```

sudo dpkg -i filename.deb; sudo apt-get -f install

```

The first part installs the deb and the second part attempts to resolve deps using your available sources

Thanks, as someone who likes to know exactly what's going on, it makes me feel uncomfortable how many different ways there are to do things in Linux!

---

### Post by monkeybrain20122 on 2020-06-11
dpkg doesn't pull in dependencies. You can install a .deb by just right clicking it and the software store will install it and pull in the dependencies. But I prefer gdebi, it is faster than the software store. gdebi is in the repo (set gdebi as the default by opening .deb packages from properties > default applications, then next time when click a .deb gdebi check for dependencies, download them if needed and install it)

---

### Post by ActionParsnip on 2020-06-12
> **jcdenton1995 said:**
> Thanks, as someone who likes to know exactly what's going on, it makes me feel uncomfortable how many different ways there are to do things in Linux!

The first command installs the deb. If there are dependencies, you will see warnings and errors. If you already have the dependencies then it will simply install. If there are deps needed then the second command will pull them in for you. Using a GUI app like gdebi keeps you away from "what's going on" as it's all abstracted away from the user. The CLI way keeps you in control as you have to manually tell the system you want to satisfy package deps.

Obviously if the deps cannot be met then you'll see more warnings etc and you'll need to resolve those as part of the install of the initial deb.

HTH

---

### Post by jcdenton1995 on 2020-06-12
I always go the CLI route as I think the GUI's are self explanatory and if I ever had to use one I'd just work it out. However if my desktop envieroment stopped working or something like that then I think its important to at least be a bit comfy with the command line if you have to fix it via that route, and the best way to do that for me is just practice using it for 90% of what I try to do.

---

### Post by ajgreeny on 2020-06-12
I simply download the (trusted) deb I want to ~/Downloads, right click it in the file-manager and copy it, then in terminal run ***sudo apt install (right click to Paste)***

That simply removes the need for typing the full pathway ***/home/username/Downloads/filename*** though with autocompletion that is also very quickly accomplished even by a very bad typist (ie, me).

I can see no advantages to gdebi any more now that apt does the same job.

---

