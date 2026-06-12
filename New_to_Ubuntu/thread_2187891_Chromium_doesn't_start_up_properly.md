---
title: "Chromium doesn't start up properly"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by Delletje on 2013-11-14
Chromium only opens in new user profile status. My own user file seems to be corrupted. Starting via Terminal I get this thread. 
6192:6192:1114/164335:ERROR:process_singleton_linux.cc(238)] readlink(/home/kees/.config/chromium/SingletonLock) failed: Invalid argument
[6192:6192:1114/164335:ERROR:process_singleton_linux.cc(238)] readlink(/home/kees/.config/chromium/SingletonLock) failed: Invalid argument
[6192:6192:1114/164335:ERROR:process_singleton_linux.cc(262)] Failed to create /home/kees/.config/chromium/SingletonLock: File exists
[6192:6192:1114/164335:ERROR:process_singleton_linux.cc(238)] readlink(/home/kees/.config/chromium/SingletonLock) failed: Invalid argument
[6192:6192:1114/164335:ERROR:chrome_browser_main.cc(1228)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

also in my documents I can't seem to locate the specified .config file.
Anybody able to help?

---

### Post by jdeca57 on 2013-11-14
I just checked and .config/chromium does exist in my home directory. Of course, it's hidden. See [http://itsfoss.com/hide-folders-and-show-hidden-files-in-ubuntu-beginner-trick/](http://itsfoss.com/hide-folders-and-show-hidden-files-in-ubuntu-beginner-trick/) I'd suggest you simply delete the directory /home/kees/.config/chromium and then start chromium. It will create what it needs.

---

