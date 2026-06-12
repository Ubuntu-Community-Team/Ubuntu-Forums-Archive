---
title: "Nautilus Keeps Crashing - 12.04"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by Syndacate on 2012-07-18
As the title says, this started today, I got some updates but I don't remember all the libraries that were on there.  I haven't found anything that supports this problem.

I recently (couple days ago) tried Gnome3 (God it's awful).  I was able to undo everything - I think.  Though that's potentially related.  I had no problems up until today, when Nautilus randomly quit.

It opens back up, and quits in a couple seconds.  I kind of need this computer and don't have time for a format.

Doubt anybody can help, but it's worth a shot.

I logged an output of it, but seeing as there's obviously no debug symbols in the binary  provided, it's a pretty useless dump for tracking the exact problem, IMO.

Output below.  Any thoughts of attempts at fixing this issue?
```
syndacate@Syndacate:~$ gdb /usr/bin/nautilus
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /usr/bin/nautilus...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7fffeb24b700 (LWP 2801)]
[New Thread 0x7fffeaa4a700 (LWP 2802)]
[New Thread 0x7fffea249700 (LWP 2803)]
[New Thread 0x7fffe9840700 (LWP 2804)]
[New Thread 0x7fffc929b700 (LWP 2809)]
[New Thread 0x7fffc8a9a700 (LWP 2810)]
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

[Thread 0x7fffeaa4a700 (LWP 2802) exited]
[Thread 0x7fffc929b700 (LWP 2809) exited]
[Thread 0x7fffc8a9a700 (LWP 2810) exited]
[New Thread 0x7fffc8a9a700 (LWP 2814)]
[New Thread 0x7fffc929b700 (LWP 2815)]
[New Thread 0x7fffeaa4a700 (LWP 2816)]
[New Thread 0x7fffbbfff700 (LWP 2817)]
[New Thread 0x7fffbb7fe700 (LWP 2818)]
[New Thread 0x7fffbaffd700 (LWP 2819)]
[New Thread 0x7fffba7fc700 (LWP 2820)]
[New Thread 0x7fffb9ffb700 (LWP 2821)]
[New Thread 0x7fffb97fa700 (LWP 2822)]
[Thread 0x7fffc8a9a700 (LWP 2814) exited]
[Thread 0x7fffea249700 (LWP 2803) exited]
[Thread 0x7fffbb7fe700 (LWP 2818) exited]
[Thread 0x7fffbbfff700 (LWP 2817) exited]
[Thread 0x7fffbaffd700 (LWP 2819) exited]
[Thread 0x7fffb97fa700 (LWP 2822) exited]
[Thread 0x7fffeaa4a700 (LWP 2816) exited]
[Thread 0x7fffc929b700 (LWP 2815) exited]
[Thread 0x7fffba7fc700 (LWP 2820) exited]

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed

(nautilus:2798): GLib-GObject-CRITICAL **: g_object_add_weak_pointer: assertion `G_IS_OBJECT (object)' failed
[Thread 0x7fffb9ffb700 (LWP 2821) exited]
[New Thread 0x7fffb9ffb700 (LWP 2857)]

Program received signal SIGSEGV, Segmentation fault.
0x000000000048962e in ?? ()
(gdb) backtrace
#0  0x000000000048962e in ?? ()
#1  0x0000000000486773 in ?? ()
#2  0x00000000004760ba in ?? ()
#3  0x00000000004765cf in ?? ()
#4  0x00007ffff44d5393 in g_main_context_dispatch ()
   from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007ffff44d56e0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x00007ffff44d57a4 in g_main_context_iteration ()
   from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#7  0x00007ffff4aa21c4 in g_application_run ()
   from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#8  0x000000000042b8d9 in ?? ()
#9  0x00007ffff39bf76d in __libc_start_main ()
   from /lib/x86_64-linux-gnu/libc.so.6
#10 0x000000000042b925 in ?? ()
#11 0x00007fffffffe148 in ?? ()
#12 0x000000000000001c in ?? ()
#13 0x0000000000000001 in ?? ()
#14 0x00007fffffffe442 in ?? ()
#15 0x0000000000000000 in ?? ()
(gdb) quit
A debugging session is active.

	Inferior 1 [process 2798] will be killed.

Quit anyway? (y or n) y
syndacate@Syndacate:~$
```

Just a note, the assertion failures aren't always at 2798.  I'm not sure if that's a __LINE__ directive or not.

---

### Post by Syndacate on 2012-07-18
I googled the error it's spitting out before it dies, but I can't quite find any solid info about a 'why'.

---

### Post by Syndacate on 2012-07-18
I believe I found the root end-use cause.

The assertion seems to be tripped by closing a nautilus window.  The reason I see the issue at boot-up is b/c the first thing I do when Ubuntu finishes logging in is open nautilus to mount my externals (not set up in fstab, lol), then I **close** nautilus, creating the error.

I've did a bunch of blackbox tests and it seems whenever I close a nautilus window the assertion is tripped and nautilus seg faults.

Right now I'm 'testing' launching nautilus from a shell and just leaving the initial folder-view that launched and the terminal open.

So far, so good, no assertion output, nautilus hasn't died yet.  Though eventually I'm going to slip up and close a nautilus window...

---

### Post by Syndacate on 2012-07-18
> **dineseGe said:**
> I join. And I have faced it. We can communicate on this theme.

Not quite sure what you mean.  I think you mean to say you have seen this problem as well?

---

### Post by Syndacate on 2012-07-19
I believe the issue is related to installing Gnome3.

I installed it using this site as a source:
[http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/)

I removed it using:
sudo apt-get remove gnome-shell
sudo apt-get remove gnome-tweak-tool
sudo apt-get autoremove

PROBLEM:
I noticed just now that slider functionality has changed (random access is gone) and buttons are more square.  I'm guessing Gnome updated.  I am un-sure about how to revert this change, but I believe this is the root of the problem.  Any thoughts on making sure the default gnome packages are in place?  Some library is NOT compatible, it seems, and it's killing me :(

---

### Post by Syndacate on 2012-07-19
I fixed it. The problem is that none of the gnome3 tutorials have correct removal instructions. When installing Gnome3 it will update components of Gnome. These libraries will be newer versions than certain parts were designed to work with. Although they shouldn't hurt backwards compatibility - they do.

So all packages that are introduced into the system from external repos must be removed...but how?

Enter: PPA-Purge script, you can download it from the repos, it's in there by default, it removes packages added by 3rd party libraries if they have a newer version than what exists in the regular repos. READ the entire process before doing so.
To purge the repo, do:
```
sudo apt-get update
sudo apt-get install ppa-purge
# Make sure in your software sources, PPAs that you want to purge are enabled (their source code need-not be), otherwise the script doesn't work
sudo ppa-purge ppa:gnome3-team/gnome3
# Hit 'Y' when it prompts you for a solution, this takes a bit
sudo ppa-purge ppa:ricotz/testing
# Hit 'Y' when it prompts you for this solution, this takes a bit
```

Ignore update manager for now, if it opens, close it, wait until you've purged all the non-Ubuntu repos you wish to, then go into software sources, disable (and/or remove) those 3rd party repos, then update to fix dependencies

```
sudo apt-get autoremove # Remove unneeded dependencies
sudo apt-get clean      # Clean apt cache
sudo apt-get update     # Update
sudo apt-get fix        # Fix dependencies
sudo apt-get upgrade    # Update all packages to latest
```

Now this is kind of a fly with a bazooka approach. It'll hastily take deb packages installed from 3rd parties, such as Skype as 'unmet dependencies' and remove them. For me, since the only 3rd party thing I have that's not from a repo is Skype, I just re-installed Skype. Hope this helps if anybody has issues like me.

Removing all the newer libraries for Gnome3 fixed it. After this, everything ran as before, Nautilus no longer crashes.

EDIT:
Before I did this I also removed the base packages which caused my issues, so:
```
sudo apt-get remove gnome-shell
sudo apt-get remove gnome-tweak-tool
```

---

