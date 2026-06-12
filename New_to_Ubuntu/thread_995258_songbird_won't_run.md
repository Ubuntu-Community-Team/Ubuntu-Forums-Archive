---
title: "songbird won't run"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by esedizzle on 2008-11-27
Whenever I start songbird it says that my music library is corrupt and it won't start.  When I click on continue anyway it doesn't and when I click on delete library and restart it doesn't do that either.  How do I scan my music library for corruption or get songbird to run anyway

---

### Post by ahmadz1991 on 2009-03-13
Same problem.. :( :(

---

### Post by LowSky on 2009-03-13
way to bring a post back form the dead... the OP is from November 2008

first off how did you install songbird? repo? deb file? source?

try deleting your songbird profile it should be in your home folder

/home/user_name/.songbird

to make it easier just delete the .songbird folder... it will rebuild on the next time you start songbird

---

### Post by ahmadz1991 on 2009-03-13
.deb
and i have no .songbird folder, but only a folder called\; .songbird2
and no matter how many times i delete it ,, it doesn't help.. :(

---

### Post by sparcxl on 2009-09-20
```
sudo apt-get remove libvisual-0.4-plugins

```
That was keeping me from running it. Found the above @ [http://linuxhub.net/2009/08/songbird-1-2-wont-start-on-ubuntu-9-04-fix/](http://linuxhub.net/2009/08/songbird-1-2-wont-start-on-ubuntu-9-04-fix/)

Sorry for bringing up an old post, but this just happened on 9.04, with the Songbird 1.2 .deb from getdeb

---

### Post by greggannicott on 2009-10-04
> **sparcxl said:**
> ```
sudo apt-get remove libvisual-0.4-plugins

```That was keeping me from running it. Found the above @ [http://linuxhub.net/2009/08/songbird-1-2-wont-start-on-ubuntu-9-04-fix/](http://linuxhub.net/2009/08/songbird-1-2-wont-start-on-ubuntu-9-04-fix/)

Sorry for bringing up an old post, but this just happened on 9.04, with the Songbird 1.2 .deb from getdeb

Thanks! I was having issues where I'd start Songbird, an entry for it would appear in the taskbar and then go - and that would be it.

The above fixed that for me.

Cheers.

---

### Post by oooh on 2010-01-19
Same problem here, my folder is .songbird2. IT HAS BEEN WORKING FOR MONTHS, AND SUDDENLY IT STOPPED WORKING.

I tried both:
- uninstall libvisual plugin. I have no such library so i can not uninstall
- delete content of .songbird2. Does not work. It regenerates the folder when i try to run songbird

In any case, songbird does not start at all. At terminal is says it can not find application.ini. I also restored it from the repository, so now I get:

(songbird-bin:3894): GLib-WARNING **: g_set_prgname() called multiple times
Bus error

Any idea?

Just found this : [http://getsatisfaction.com/songbird/topics/songbird_fails_to_start_on_fedora_11_with_undefined_symbol_in_libgstdeinterlace_so](http://getsatisfaction.com/songbird/topics/songbird_fails_to_start_on_fedora_11_with_undefined_symbol_in_libgstdeinterlace_so)

I will give it a try ...

---

