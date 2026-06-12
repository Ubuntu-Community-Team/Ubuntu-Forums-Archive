---
title: "Any dangers in apt-get clean, autoclean, autoremove?"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-11
I just started learning Linux and I am compiling a list of commands and its functions that optimize the system. I came across commands such as clean, autoclean, and autoremove. I have read that some of these commands may cause unintended consequences. From what I've read, however, I don't see how these commands are not safe in the sense that I can run them any time and expect them to optimize the system. 

apt-get clean flushes the cache of packages that are to be installed, right? So isn't the worst scenario that can happen is that I have to download the package again?
apt-get autoclean does the same thing as apt-get clean except it does not remove the cache of the latest version, so it's even "safer" than the worst case scenario of apt-get clean, right?

As for apt-get autoremove, it "removes orphaned packages that were installed as dependencies, *but are no longer*."&#8203; They may not be dependencies for the orphaned package, but what if they are dependencies for a package that I am using--will it delete it? If not, How could this command be "dangerous" or produce unintended consequences?

Thanks.

P.S. What other safe commands that optimize Linux should I be aware of? Anything from updating drivers to clearing cache of certain programs. I am not afraid to get dirty as long as there are clear instructions and I understand what I'm doing and the risks.

---

### Post by ian-weisser on 2014-09-11
I suppose it depends upon what you mean by 'optimize'. Packages on the system that you don't use don't get loaded or use RAM or CPU time. They use no resources at all except a bit of disk space.

Your understanding of clean and autoclean and autoremove is close enough. They are generally safe to use. There are always corner cases and exceptions.

---

### Post by garycheng12 on 2014-09-11
Actually, that's what I love about Linux. On Windows, leftover registries get accumulated and slow down the system. On Linux, the worst that can happen is you have a bunch of tiny files that take up a trivial amount of space. Still, understanding the unlikely scenarios could help me better understand Linux itself. Maybe I'll just keep feeling around and then I'll ask the questions again when I encounter them. Still, I'm not sure about whether or not autoremove deletes orphaned packages that, although are not needed for the deleted package it was intended for, are needed for other packages that I am using. Maybe an optimization application like Actually, that's what I love about Linux. On Windows, leftover registries get accumulated and slow down the system. On Linux, the worst that can happen is you have a bunch of tiny files that take up a trivial amount of space. Still, understanding the unlikely scenarios could help me better understand Linux itself. Maybe I'll just keep feeling around and then I'll ask the questions again when I encounter them. Still, I'm not sure about whether or not autoremove deletes orphaned packages that, although are not needed for the deleted package it was intended for, are needed for other packages that I am using. Maybe an application like BleachBit is the only thing needed?

---

### Post by mcduck on 2014-09-11
> **garycheng12 said:**
> 
apt-get clean flushes the cache of packages that are to be installed, right? So isn't the worst scenario that can happen is that I have to download the package again?
apt-get autoclean does the same thing as apt-get clean except it does not remove the cache of the latest version, so it's even "safer" than the worst case scenario of apt-get clean, right?
Yeah, with either one the worst-case scenario is that if you for some reason need to reinstall the package, it ahs to be downloaded again.

> **garycheng12 said:**
> 
As for apt-get autoremove, it "removes orphaned packages that were installed as dependencies, *but are no longer*."&#8203; They may not be dependencies for the orphaned package, but what if they are dependencies for a package that I am using--will it delete it? If not, How could this command be "dangerous" or produce unintended consequences?

autoremove won't remove a package as long as it's a dependency of *any* other installed package, or was installed manually by the user.

The only risks are that if you have a third-party software installed from source code or otherwise outside of the package management, and that software still needs the package. Or, if the package is not a dependency but instead provides optional extra features for some software. (for example the Archive Manager doesn't *depend* on rar/unrar, but is not able to work with .rar archives unless you have them installed. And Audacity doesn't *depend* on Lame, but you need it if you want to edit .mp3 files.)

In both these cases you would usually have installed those packages manually, so it would be pretty bad luck, although still possible, that they were already installed as a dependency for something else and you noticed that and didn't even try to install them yourself (which would have marked them as manually installed and thus protect them from autoremove).

So, my advice is that the first two are perfectly safe to use, unless you often end breaking installed packages and need to reinstall them & don't have regular access to Internet conenction. (in which case you proably should be more worried about why you need to reinstall stuff in the first place ;)). And for autoremove, I'd say it's pretty safe as well, but it's a good idea to glance through what packages it plans to uninstall in case you notice something you know you need.

What comes to optimizing stuff, running *apt-get clean* & *apt-get autoremove* a few times a year is pretty much everything I do to keep things clean. All the caches and other stuff are already usually managed by whatever app is keeping the cache in the first place so I don't see much point in using tools like BleachBit. I think they are only useful if you are really running out of disc space and need a quick, although just temporary, way of freeing a bit of space.

---

### Post by Bashing-om on 2014-09-11
garycheng12; Hello;

My 2 cent's worth.

IF you are running release 14.04 AND have not cleaned out the old kernels. To see "autoremove" in action:
In terminal do:
```

dpkg -l | grep linux-

```
to see a listing of the currently installed kernels.
OK, remove all those old no longer needed kernels, thus:
```

sudo apt-get autoremove

```
Now, compare:
```

dpkg -l | grep linux-

```

IF you are running release 12.04, "autoremove" does not have that capability.

The package manager always tells you what it is going to do, if you do not agree, one can always take an alternative action. It is wise to take notes on what the package manager intends, if for no other reason you keep abreast of your operating system.

[INDENT][INDENT]The care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vasa1 on 2014-09-11
> **garycheng12 said:**
> ... I have read that some of these commands may cause unintended consequences. ...
Would you **please** provide the specific links and quotes therefrom that gave you this impression?

---

### Post by ian-weisser on 2014-09-11
> **garycheng12 said:**
> understanding the unlikely scenarios could help me better understand 

Okay, let's say you install an application, Foo, and a dependency, libfoo, using the package manager.

```
sudo apt-get install foo
```
(you already know that you don't need to specify dependencies)

Having installed it, you choose to delete all the stored package files in the cache at /var/cache/apt/achives

```
sudo apt-get clean
```

Now you go offline, and decide to reinstall libfoo.

```
sudo apt-get install --reinstall libfoo
```

The reinstallation will, of course, fail: apt no longer has a package stored in the cache, and you're not online.

Next, let's install another application, Bar, from a tarball on some random website on the wild internet (Tip: DON'T do that). It also depends upon libfoo...but the package manager doesn't know that since you installed from a tarball instead of a package.

Let's uninstall Foo but keep libfoo. Bar still needs libfoo.
```
sudo apt-mark manual libfoo
sudo apt-get remove foo
```

libfoo is not an orphan because you explicitly told the package manager to keep it.

Let's change that.

```
sudo apt-mark auto libfoo
```

Now the package manager thinks libfoo is an orphan for three reasons:

1) Nothing else installed, according to the package manager database, depends upon libfoo.
2) Bar does depend upon libfoo, but it's not a package. So it's not in that database.
3) It's now marked as 'automatically installed', and eligible for autoremoval.

When you autoremove the 'orphan' libfoo at the next opportunity, you will unintentionally break Bar.

Finally, let's say you still have libfoo installed, and you install the shiny new foo-ee package, which happens to also depend upon libfoo. Libfoo is no longer an orphan, since the package manager database shows that foo-ee needs it. If libfoo is already installed, another won't be downloaded and installed over it. The package manager is smart about that.

That's really one of the glues that holds a distro together - it's a bunch of packages that share the _same_ dependencies. There's just one version of libfoo, and all the packages that need it rely upon the same one. Of course, there are exceptions to that, too.

See how it works? It's not easy to defeat the package manager and break your system, but it is also not difficult. It's a tool intended to protect you from mild negligence only. It's not magic or super-smart or intended to protect you from foolishness. If you tell it to uninstall your kernel and render your system unbootable...it will do that; you are it's master.

---

