---
title: "Unity doesn't start properly"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by zcacogp on 2012-08-29
Hello, 

I'm running 12.04 with Unity on my computer. And, for some reason, Unity now doesn't start as it should when you boot the computer; the windows don't have a menu bar at the top of them (the decoration is missing) and the Unity launcher doesn't appear (after logging in, the desktop icons appear but flicker for a second or so and nothing else happens.) 

Launching a terminal from a keyboard shortcut and typing "setsid unity" causes unity to re-load and all is fine from then on, but when you log out and in, the same problem occurs again. (I guess you could re-start unity by pressing Alt+F2 and typing 'unity', but Alt+F2 doesn't worh either.) 

I also have Gnome installed on the machine and this is unaffected. 

In my ignorance, I'd guess that I need to look at the command that is run at login to start Unity and see if this has changed in any way, but I don't know whether this is a correct approach to solving the problem. (Neither would I be able to spot a problem with it if there was one!) 

All help welcomed, thanks. 


Oli.

Edited to add: The machine has worked fine up until now. I used Gnome after upgrading to 12.04, and switched to using Unity a month or so ago ago, but it hasn't had a problem before now, and I haven't recently upgraded or changed anything.

---

### Post by zombifier25 on 2012-08-29
Run this command to reset Unity's config:
```
unity --reset
```
and see if it helps.

---

### Post by taras.kuzyo on 2012-08-29
I have the same problem with unity. But unity 2d is unaffected.

---

### Post by zcacogp on 2012-08-29
Zombifier, 

Thanks. I did as you suggested, and the terminal output looks like this: 

```

ogp@desktop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3c000b8

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2000219

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2000227

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:7730): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-08-29 10:51:44 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-08-29 10:51:44 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
ERROR 2012-08-29 10:51:45 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
ERROR 2012-08-29 10:51:45 unity.gtk <unknown>:0 gtk_icon_info_get_filename: assertion `icon_info != NULL' failed
ERROR 2012-08-29 10:51:45 unity.gtk <unknown>:0 gtk_icon_info_free: assertion `icon_info != NULL' failed
ERROR 2012-08-29 10:51:45 unity.gtk <unknown>:0 gtk_icon_info_load_icon: assertion `icon_info != NULL' failed
ERROR 2012-08-29 10:51:45 unity.gtk <unknown>:0 gtk_icon_info_free: assertion `icon_info != NULL' failed
WARN  2012-08-29 10:51:45 unity.launcher LauncherIcon.cpp:433 Unable to load 'workspace-switcher' from icon theme: 

```

... and it hasn't returned the command prompt (i.e. it looks like there is still a process running.) 

I can see that Unity is reset - the launcher has returned to all the default options. 

I'll try logging out and back in again ... back in a minute. Thanks for your help. 


Oli.

---

### Post by zcacogp on 2012-08-29
Zombifier, 

Great! I logged out and in again, and all was well. I shutdown and re-started and all seems well with that too! 

So, I think that's problem solved, many thanks for your help. Out of curiosity, what could have caused this? Is it likely to happen again? Should I be worried? 

Thanks again for your help. 


Oli.

---

### Post by zombifier25 on 2012-08-29
A corrupt Compiz profile caused this. unity --reset reseted all the settings to its original place.

---

### Post by zcacogp on 2012-08-29
Thanks zombifier. 


Oli.

---

### Post by zcacogp on 2012-08-29
OK, an update to this. Essentially, the problem is recurring; having reset unity (and seen it work fine for a couple of re-boots), it is now happening again. Running "setsid unity" re-starts unity and all is well from that point on, but clearly something is not as it should be. 

If this problem is from a corrupted Compiz profile, what is causing the corruption and how do I solve it? 

Thanks, again, for any help. 


Oli.

---

