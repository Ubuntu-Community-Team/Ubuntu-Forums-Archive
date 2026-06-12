---
title: "can't open google chrome"
date: 2020-02-10
forum: New to Ubuntu
---

### Post by andrew752 on 2020-02-10
Hello, I've installed google chrome and it is showing in 'ubuntu software' but when I try to run it, it won't open.  I'm new to ubuntu and linux, so not really sure whats wrong.

---

### Post by Frogs Hair on 2020-02-10
Hello and Welcome:

Please identify your Ubuntu version and try the following command in the terminal and report any errors. Copy/paste and enter your password. Also, did you download the package from the Chrome web site ?

```
google-chrome-stable

```

---

### Post by andrew752 on 2020-02-10
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic




:~$ google-chrome-stable
[18019:18036:0211/105240.380906:ERROR:cache_util.cc(135)] Unable to move cache folder /home/harps/.config/google-chrome/ShaderCache/GPUCache to /home/harps/.config/google-chrome/ShaderCache/old_GPUCache_000
[18019:18036:0211/105240.381117:ERROR:disk_cache.cc(184)] Unable to create cache
[18019:18036:0211/105240.381138:ERROR:shader_disk_cache.cc(606)] Shader Cache Creation failed: -2
[18019:18019:0211/105240.386192:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied (13)
[18019:18019:0211/105240.386281:ERROR:process_singleton_lock_posix.cc(19)] readlink(/home/harps/.config/google-chrome/SingletonLock) failed: Permission denied (13)
[18019:18019:0211/105240.386360:ERROR:process_singleton_posix.cc(256)] readlink(/home/harps/.config/google-chrome/SingletonLock) failed: Permission denied (13)
[18019:18019:0211/105240.386379:ERROR:process_singleton_posix.cc(280)] Failed to create /home/harps/.config/google-chrome/SingletonLock: Permission denied (13)
[18019:18019:0211/105240.386405:ERROR:process_singleton_posix.cc(404)] readlink failed: Permission denied (13)
[18019:18019:0211/105240.386424:ERROR:process_singleton_lock_posix.cc(19)] readlink(/home/harps/.config/google-chrome/SingletonLock) failed: Permission denied (13)
[18019:18019:0211/105240.386516:ERROR:chrome_browser_main.cc(1413)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

---

### Post by Frogs Hair on 2020-02-10
Use ctrl + H in the home folder to display hidden folders and follow the path  [COLOR=#000000] /home/harps/.config/google-chrome/. Delete the google-chrome folder and try starting Chrome with the icon again. A new folder will be created when restarting Chrome. [/COLOR]

---

### Post by andrew752 on 2020-02-10
> **Frogs Hair said:**
> Use ctrl + H in the home folder to display hidden folders and follow the path  [COLOR=#000000] /home/harps/.config/google-chrome/. Delete the google-chrome folder and try starting Chrome with the icon again. A new folder will be created when restarting Chrome. [/COLOR]

Frogs Hair, thank you very much.  That worked :)

---

### Post by Frogs Hair on 2020-02-11
You're Welcome !

---

