---
title: "Got some things from &quot;syslog&quot; and need to know what to do about it..."
date: 2013-04-29
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-29
*edit* This seemed to have been an actual bug. Got kernel updates today and so far, no freeze!

OK! I'm making some progress in tracking down what is going on when my system freezes but, I need help on what to do about what my syslog is telling me.

```
Apr 28 14:24:47 alan-Satellite-C855 kernel: [ 6194.343475] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Apr 28 14:24:47 alan-Satellite-C855 kernel: [ 6194.343480] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state

```

Where do I find that "/debug/dri/0/i915_error_state" file. I looked in the "home folder" with "ctrl+h" to show hidden files and folders but don't see that path. Do I have to use the terminal?

---

### Post by Cheesehead on 2013-04-29
Have you looked at the possible matching bugs on Launchpad?
I found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716) , which seems to match your description. If this is your bug, then the fix is in progress.

---

### Post by alhefner on 2013-04-29
> **Cheesehead said:**
> Have you looked at the possible matching bugs on Launchpad?
I found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716) , which seems to match your description. If this is your bug, then the fix is in progress.

That does seem to be the problem. I hesitated to call it an actual "bug". In one of the comments on that bug report, they do ask for the content of the "i915_error_state" file but apparently that has to be done via ssh access. Since I'm not networked with any other system (other than Internet access), I am unable to assist there...

---

### Post by tgalati4 on 2013-04-29
I presume you have a black or frozen display.  Log into the machine from another linux machine using* ssh*.  Then:

```
cd /debug/dri/0/
cat i915_error_state
```

If your graphics are working (say after a reboot) you would click on "File System" in Nautilus and then navigate to /debug.  It is not in your home directory.  Presumably there is some useful information in that file.

---

