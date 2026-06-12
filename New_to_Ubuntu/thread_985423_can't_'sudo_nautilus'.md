---
title: "can't 'sudo nautilus'"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by alwiap on 2008-11-17
I need to change a icon in /usr/share/pixmaps, so i was going to open nautilus using 'sudo nautilus', below is the output. I've also tried 'gksu nautilus', it displays the same message.  Any ideas?  Running Linux Mint 5.

```
alex@alex-desktop ~ $ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

(nautilus:9406): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:9406): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:9406): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:9406): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
```

---

### Post by phidia on 2008-11-17
Try > gksudo nautilus that's the preferred method I believe.

---

### Post by Joeb454 on 2008-11-17
> **phidia said:**
> Try  that's the preferred method I believe.

Indeed.

@OP - Using gksudo tells the system that you're wanting to launch a graphical application, whereas using "sudo" will just try to launch it as a CLI application.

*sometimes*, it doesn't matter if you use sudo, but as phidia said - it's preferred to use each appropriately :)

---

### Post by alwiap on 2008-11-17
i tried 'gksudo' nautilus, and i get the same result, after a restart as well.

---

### Post by jenkinbr on 2008-11-17
It appears to be generating segmentation faults, along with other critical errors.  ?Try sudo apt-get install nautilus to see if this cleans it up any?

At worst, it should only keep on doing the same thing.

---

### Post by alwiap on 2008-11-17
> It appears to be generating segmentation faults, along with other critical errors. ?Try sudo apt-get install nautilus to see if this cleans it up any?

At worst, it should only keep on doing the same thing. 

I just did that, still get the same error message.

---

### Post by phidia on 2008-11-17
> **alwiap said:**
> i tried 'gksudo' nautilus, and i get the same result, after a restart as well.

See if the thread [here]("http://ubuntuforums.org/showthread.php?t=963060") has any pertinence to your situation. 

Added: Do you have a blank cd or dvd in the optical drive?

---

### Post by PocketDog on 2008-11-17
Odd. I've had exactly the same issue all day. after reading this post I booted an earlier kernel (*-19) and, although it didn't show the usplash (an issue I fixed a fortnight ago) gksudo nautilus worked fine. I booted again into the 21 (Hardy latest) kernel I've been using and the nautilus in su mode appears to be magically fixed. No idea what that was all about

---

