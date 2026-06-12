---
title: "[SOLVED]How can I sandbox epiphany-browser with firejail?"
date: 2020-06-01
forum: New to Ubuntu
---

### Post by peb-cak on 2020-06-01
Hi, 
I just installed **epiphany-browser** and I would like to use **firejail** to sandbox it but the browser will not start and I get error message in terminal:

```
/usr/bin/firejail /usr/bin/epiphany-browser

Reading profile /etc/firejail/default.profile
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-passwdmgr.inc
Reading profile /etc/firejail/disable-programs.inc
Warning: networking feature is disabled in Firejail configuration file


** Note: you can use --noprofile to disable default.profile **


Parent pid 51994, child pid 51995
Warning: cleaning all supplementary groups
Child process initialized in 75.19 ms


(epiphany:3): dconf-WARNING **: 19:40:41.961: Unable to open /home/pebcak/.local/share/flatpak/exports/share/dconf/profile/user: Permission denied


** (ephy-profile-migrator:7): WARNING **: 19:40:42.023: Failed to delete /home/pebcak/.config/epiphany/states.xml: Error removing file /home/pebcak/.config/epiphany/states.xml: Permission denied


(ephy-profile-migrator:7): dconf-WARNING **: 19:40:42.027: Unable to open /home/pebcak/.local/share/flatpak/exports/share/dconf/profile/user: Permission denied


** (ephy-profile-migrator:7): WARNING **: 19:40:42.027: Failed to create Gvdb table: Failed to open file “/home/pebcak/.config/epiphany/bookmarks.gvdb”: open() failed: Permission denied


** (ephy-profile-migrator:7): WARNING **: 19:40:42.029: Failed to enumerate files: Error opening directory '/home/pebcak/.config/epiphany': Permission denied


** (ephy-profile-migrator:7): WARNING **: 19:40:42.029: Cannot delete adblock directory /home/pebcak/.cache/epiphany/adblock: Error opening directory “/home/pebcak/.cache/epiphany/adblock”: Permission denied


** (ephy-profile-migrator:7): WARNING **: 19:40:42.030: Cannot delete adblock directory /home/pebcak/.cache/epiphany/adblock: Error opening directory “/home/pebcak/.cache/epiphany/adblock”: Permission denied
Failed to run the migrator process, Web will now abort.


Parent is shutting down, bye...
```

I don't know how to solve those permission problems. Without firejail the browser starts but I get a warning:

```
WARNING **: 19:44:02.587: Cannot fetch source for filter 1f353f7cdbb012b9fb1226455f1b3becba42070e1970c1524996fa3a871af406 from <https://easylist-downloads.adblockplus.org/easylist_min_content_blocker.json>: Unacceptable TLS certificate



```

I appreciate your help to solve this problem.


EDIT

:oops:

I apologize to forum! I should have looked at firejail's profile for epiphany browser before posting. It says:

```
Note: Epiphany use bwrap since 3.34 and can not be firejailed any more.
```

I feel silly. Not the best debut in the forum. I guess I live up to my user name

---

