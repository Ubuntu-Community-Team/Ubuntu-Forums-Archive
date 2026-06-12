---
title: "Ubuntu 13.4"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by rootytooty on 2013-10-24
I have Ubuntu 13.4 and I like it for the most part.  I knew that when I went from 12.4 or .10 to 13.4 I wouldn't have flash for videos and other things requiring flash.  I was told there is a way to go through the terminal to get flash installed.  I have tried several things that I was told to input but it never did bring in it for me in to install.  I would go back, if possible, to 12.10 so that I have the other capability.  

Any help would be greatly appreciated.

Thanks,
Bobby

---

### Post by mikewhatever on 2013-10-24
Flash is available through the Software Center - a point&click installation.

If you must use the terminal, run <sudo apt-get install flashplugin-installer>.

Internet connection is required in both cases. It shouldn't matter what version of Ubuntu you have.

---

### Post by rootytooty on 2013-10-25
That is great info, but the problem is, is that the software center doesn't bring anything up.  In my 12.4 it did and there is a lot of stuff there.  I have reinstalled 13.4 and it still doesn't bring it up.  When I click on it, you can see its working to find it, but nothing comes up and it never opens.

---

### Post by jerome1232 on 2013-10-25
What about the terminal command mikewhatever suggested

```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by bobbyr1 on 2013-10-29
I tried both suggestions on how to use sudo-apt-get but sometimes it will get some of the information needed and it will say continue and I click Y.  It then will say all the information didn't come in and something about line 56.  I don't want to keep asking you guys but I would like to get those things working.

Most all of the things I need work just fine but its flash or lack there of and my Software Center.  When I click on the Software Center it brings up the page with the menu and all the things on top.  But the curser just keeps on turning and the center doesn't come up.

I did the sudo apt-get thing on the software Center and it says the latest version is already installed.  But it just won't bring it up when its clicked on.

Any suggestions please///

Thanks,
Bobby

---

### Post by 3rdalbum on 2013-10-29
> **bobbyr1 said:**
> It then will say all the information didn't come in and something about line 56

All your problems stem from "line 56" - which indicates that you've made some modifications to the /etc/apt/sources.list file that are erroneous.

Go back into that file:

```
gksudo gedit /etc/apt/sources.list
```

and check what's on line 56. If it's obviously wrong, for instance it starts with something other than "deb" or a "#", you can delete it, save your changes and then run:

```
sudo apt-get update
```

and you'll probably find Software Center will work and you'll be able to install Flash Plugin.

If you can't figure out anything wrong with line 56, copy and paste the whole file into this thread and somebody will be able to look at it and figure out the problem.

In future, don't make direct modifications to the /etc/apt/sources.list file. Use the Software & Updates program for adding repositories instead.

---

### Post by newb85 on 2013-10-29
Instead of deleting line 56, you could also just add a # to the beginning.  Then apt-get will ignore the line.

---

