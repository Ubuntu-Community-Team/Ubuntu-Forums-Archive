---
title: "Can't get Steam to run"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by Horbo on 2012-12-20
I hope this is the correct forum for this?

I've downloaded the open beta deb for Steam, installed it, "run" it once (which causes Steam to download 112 MB of stuff to complete the installation) but now running it does nothing.

If I double click the desktop icon I get no response.

If I type "steam" in a terminal I get this:
```
$ steam
Installing breakpad exception handler for appid(steam)/version(1355957371_client)
Xlib:  extension "GLX" missing on display ":0.0".
Looks like steam didn't shutdown cleanly, scheduling immediate update check
Installing breakpad exception handler for appid(steam)/version(1355957371_client)
Installing breakpad exception handler for appid(steam)/version(1355957371_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 32090 with name 0eBlobRegistryMutex_811A2F9B76A0A146D7C4296DCBC02BF8
removing stale semaphore last operated on by process 32090 with name 0eBlobRegistrySignal_811A2F9B76A0A146D7C4296DCBC02BF8
removing stale semaphore last operated on by process 32090 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 32090 with name 0eSteamEngineLock
Xlib:  extension "GLX" missing on display ":0.0".

```

My best guess is that it won't run because there is something wrong with my display drivers.  Correct?

I have a GT 240, and the drivers definitely don't seem to be working: although the drivers tab in Software Sources says I'm using the current nvidia drivers I can't change my resolution to anything above 800x600.
If I open the nvidia server settings it says I'm not using the nvidia x server, and to run "nvidia-xconfig" and restart x - I have done both those but the message doesn't change.

This is how I installed the nvidia drivers:
```

sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current
Then rebooted.

```

I have since tried changing the drivers in Software Sources > Additional Drivers, but it makes no difference.

Have I done something wrong?
Are the drivers the reason steam won't run?
Why aren't the drivers working?

---

### Post by arpanaut on 2012-12-20
Take a look here:
[http://ubuntuforums.org/showthread.php?t=2081405](http://ubuntuforums.org/showthread.php?t=2081405)

---

### Post by Horbo on 2012-12-20
Hooray!

Thanks arpa.

I followed the links in the first post, which pointed me at this script to fix my nvidia drivers, and it worked!
[http://ubuntuxtreme.com/howto/nvidia-drivers-installer-script/](http://ubuntuxtreme.com/howto/nvidia-drivers-installer-script/)

What a horrible mess things were up until that point.  In 12.04 I installed my nvidia drivers fine wit just 2 clicks, but was a nightmare here in my new 12.10 install.

---

