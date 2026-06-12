---
title: "how to check if kernel driver exists with a bash script"
date: 2010-05-06
forum: Programming Talk
---

### Post by RocketRanger on 2010-05-06
Hi

Will the title pretty much says it all. I need to check with a shell script if a kernel driver exists and if it does remove it. The latter part is easy enough, it's the first I don't know how to do.

kenneth

---

### Post by dwhitney67 on 2010-05-06
```
modprobe -n <name of module>
```
or
```
modprobe -l <name of module>
```

Probably the -l option is best suited.

---

### Post by RocketRanger on 2010-05-06
Thanks! That partly did it.

I'm working on an embedded device and modproble -l gives me nothing at all while modprobe -n gives this error:
modprobe: cannot parse modules.dep

I'm using lsmod piped to grep which works but the modprobe seems to be a smarter solution.

Any ideas?

---

### Post by dwhitney67 on 2010-05-06
Where's the location of the driver that you expect to find?  AFAIK, modprobe only searches through /lib/modules/`uname -r`.

If you are merely attempting to ascertain if the file is present on your file system, then use the 'find' command to locate it.  If you know the full path, then just use the -f option with an if conditional:
```

if [ -f /path/to/my/kmod.ko ]
then
        # kmod exists
else
        # kmod does not exist
fi

```

P.S.  With the find command:
```

find /some/path -name kmod.ko -exec insmod {} \;

lsmod | grep kmod >& /dev/null

if [ $? -eq 0 ]
then
        # kmod has been loaded
else
        # kmod has NOT been loaded (or possibly not found)
fi

```

---

### Post by RocketRanger on 2010-05-08
I'm trying to automate a few setup routines and I want to determine if I had inserted a kernel module that I know will conflict with one I'm about to insert. 

Your answer cleared up something though. I seems that the system doesn't have a /lib/modules, it creates a file in /sys/module instead. So does that mean that if the file exists there that the driver is inserted in the kernel?

---

### Post by dwhitney67 on 2010-05-08
Honestly, I have no idea.  it appears that you are using a non-standard Linux distro, which obviously I am unfamiliar with it.

For that distro, read the documentation on **modprobe** and also **insmod**.  The former is supposedly more "intelligent", however it has its limitations.  If you need to load a specialized module that conflicts with another (that is supposedly already loaded), then perhaps you should look into developing a configuration file in **/etc/modprobe.d**.  Once again, though, maybe your non-standard Linux does not use this directory.

---

### Post by RocketRanger on 2010-05-08
After some poking around I think the distro it is running is BusyBox. The documentation on their website isn't particularly helpfull. It says insmod "Load the specified kernel modules into the kernel" and thats about it. There are no man, help or info commands so I feel like I'm just left guessing. Oh, and there's no modprobe.d in /etc.

Anyway I only ment to do this to make life a bit easier on me but this seems to be more difficult than just loading and unloading the modules by hand. I will go with your solution checking if the file exists in /sys/modules and keep my fingers crossed.

Thanks for your help. At least I now have a working solution.

---

### Post by dwhitney67 on 2010-05-08
BusyBox is a command utility set that is slimmed-down version of that provided by typical Linux systems.  It is not an OS (distro).  Typically BusyBox is used for small/embedded systems.  Here's some more info:  [http://www.busybox.net/about.html](http://www.busybox.net/about.html)

Anyhow, good luck with your endeavor.

---

