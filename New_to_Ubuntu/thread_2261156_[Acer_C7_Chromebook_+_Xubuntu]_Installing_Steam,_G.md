---
title: "[Acer C7 Chromebook + Xubuntu] Installing Steam, Gen6+ required [help!]"
date: 2015-01-16
forum: New to Ubuntu
---

### Post by Lewis_James_Davids on 2015-01-16
I'm currently trying to install steam on my Acer C7 chromebook with xubuntu installed. After installation and an attempt to open steam through terminal I get the following error.
```
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Gen6+ requires Kernel 3.6 or later.
steam: ../../../../src/mesa/main/context.c:1549: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-01-16 21:31:05] Startup - updater built Aug 26 2014 15:35:42
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20150116213105_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/lewisjd/.local/share/Steam/steam.sh: line 730: 15784 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
mv: cannot stat '/home/lewisjd/.steam/registry.vdf': No such file or directory
Installing bootstrap /home/lewisjd/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/lewisjd/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Gen6+ requires Kernel 3.6 or later.
steam: ../../../../src/mesa/main/context.c:1549: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2015-01-16 21:31:09] Startup - updater built Aug 26 2014 15:35:42
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20150116213109_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/lewisjd/.local/share/Steam/steam.sh: line 730: 15910 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"


```

I've googled the Gen6+ error as - taking a wild guess here - this is the main concern. All I get back is linux jargon which I'm not yet fluent. If someone could give me some tips and a push in the right direction on how to fix this, It would be much appreciated!

---

