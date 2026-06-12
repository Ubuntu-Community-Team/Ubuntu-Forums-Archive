---
title: "How to find out unwanted dependencies?"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by Virajs on 2012-02-08
Hi, :)
Is there any way to find out unwanted dependencies in Ubuntu ? Because there might be dependencies for the software which I have installed earlier and I have uninstalled now.

---

### Post by dcsoldschool53 on 2012-02-09
Here is a web page that may help you find some of the unwanted files that you no long want or need.**_Warning!!!_** Read everything before you try to remove any files.

Cleaning up Ubuntu System
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

I hope this will help you.

---

### Post by mcduck on 2012-02-09
> **Virajs said:**
> Hi, :)
Is there any way to find out unwanted dependencies in Ubuntu ? Because there might be dependencies for the software which I have installed earlier and I have uninstalled now.

You can use "*sudo apt-get autoremove*" in a terminal to automatically uninstall all packages that were installed as a dependency for something, and the original package has now been removed.

And there's also the *deborphan* tool, which allows you to search for such orphaned packages. I think there is a GUI for it as well, but I recommend just setting up a filter for orphaned packages in Synaptic Package Manager instead.

---

### Post by Paqman on 2012-02-09
> **mcduck said:**
> I think there is a GUI for it as well, but I recommend just setting up a filter for orphaned packages in Synaptic Package Manager instead.

There is: [gtkorphan]("apt:gtkorphan"). But like you say you can just set it up as a filter in Synaptic, so if you've already got Synaptic then that's the way to go.

I don't bother with either, I just run autoremove once in a while.

---

### Post by mcduck on 2012-02-09
> **Paqman said:**
> There is: [gtkorphan]("apt:gtkorphan"). But like you say you can just set it up as a filter in Synaptic, so if you've already got Synaptic then that's the way to go.

I don't bother with either, I just run autoremove once in a while.

yeah, deborphan was much more useful before apt-get gained the autoremove ability, these days there really shouldn't be anything left for deborphan to find. But it still might be useful if you just want to check for possible orphaned packages instead of removing them, although apt-get's "-s" (simulate) option would do the same.

---

### Post by sadaruwan12 on 2012-02-09
What I use is the good old apt-get and the new ubuntu-tweak clean up function it does the job for me.

---

