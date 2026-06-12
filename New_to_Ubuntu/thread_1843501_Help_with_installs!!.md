---
title: "Help with installs!!"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Thiefot35 on 2011-09-13
I have just installed ubuntu and started having a nosy round it.I would like to use google chrome as my browser.how do i go about it.I am running ubunt 11.04.Please help.

---

### Post by sanderd17 on 2011-09-13
So everything is ok, exept that you want google chrome?

Just go to the software center and search for Chromium (the open source variant of google chrome, exactly the same code, but without google trademark).

---

### Post by mikewhatever on 2011-09-13
Just install Google Chrome.
[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by drmrgd on 2011-09-14
Here is the link to the repository containing Google Chrome.  Adding this to your repos list will allow you to easily update Chrome when they release a new version, which I think is handy.

[http://www.ubuntuupdates.org/ppas/8]("http://www.ubuntuupdates.org/ppas/8")

---

### Post by The Cog on 2011-09-14
The recommended way to install software on Ubuntu (or most Linux distros for that matter) is to use the distros software repositories. These are analogous to the app store on a smart phone. They provide software that is pre-built for your distro, including compiling for the right processor architecture, and creating all the required configuration files and startup scripts, putting launcher icons in the menus etc. For Ubuntu, this can be done from the "software center", or software can be installed from the command line. Some versions of Ubuntu also have an application called "Synaptic package manager".

I would suggest installing Chromium, the open-source variant of Chrome. This is one of the standard Ubuntu packages. You can probably find it in the software center. If you can't find it there, the package name is chromium-browser and I suggest that you open a terminal (command prompt) and enter the command
```
sudo apt-get install chromium-browser
```

---

