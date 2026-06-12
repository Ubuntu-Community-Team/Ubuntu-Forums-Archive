---
title: "How to get the Launcher back (production machine - no downtime allowed!)?"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by kramer65 on 2012-07-27
Hello!

I've got Ubuntu 12.04 running, but unfortunately, the launcher disappeared. It's not that I've got it on "auto hide mode", but the place where it used to be is simply empty, and shows my desktop background (see the attachment). I guess all could be solved by simply restarting my computer, but since I am running a very heavy program which cannot be interrupted (or 20 days of calculations would be gone), I cannot restart my computer as a whole.

Does anybody know how I can somehow get my launcher back without restarting my computer, or logging out. Is there a way to restart Unity without the need to quit all programs?

All tips are welcome!

---

### Post by Bufeu on 2012-07-27
Yes, just open a new terminal (or switch to text mode via CTRL + ALT  + F1) and run the following command:```
unity --reset
```[I]If you switched to text mode via CTRL + ALT + F1, press CTRL + ALT + F7 to bring back the GUI-version.
[/I]

---

### Post by kramer65 on 2012-07-27
> **Bufeu said:**
> Yes, just open a new terminal (or switch to text mode via CTRL + ALT  + F1) and run the following command:```
unity --reset
```[I]If you switched to text mode via CTRL + ALT + F1, press CTRL + ALT + F7 to bring back the GUI-version.
[/I]

Alright. I ran: unity --reset, and it seemed to reset. The launcher is still gone though. In the terminal, there is a large list of error messages:

```
kramer65@kramer65:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3000008

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3000003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3c00003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4600002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2c01a05

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4a00019

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x18057c3

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2d4680e

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x351f21f

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x351f22d

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x351f23b

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x351f249

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x351f257

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x184b140

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

(compiz:13158): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a2!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a5!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000a8!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000ab!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000ab!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000ae!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000b1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000b1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000b4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000b7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000ba!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000ba!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000bd!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000c0!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000c3!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000c6!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000c9!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xc000cc!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-07-27 11:06:25 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-27 11:06:26 unity.glib-gobject <unknown>:0 value "38327" of type `gint' is invalid or out of range for property `id' of type `gint'
WARN  2012-07-27 11:06:26 unity.glib-gobject <unknown>:0 value "38323" of type `gint' is invalid or out of range for property `id' of type `gint'
WARN  2012-07-27 11:06:26 unity.glib-gobject <unknown>:0 value "38325" of type `gint' is invalid or out of range for property `id' of type `gint'
ERROR 2012-07-27 11:06:26 unity.libdbusmenu-glib <unknown>:0 parse_layout_xml: assertion `id == dbusmenu_menuitem_get_id(item)' failed
ERROR 2012-07-27 11:06:26 unity.libdbusmenu-glib <unknown>:0 parse_layout_xml: assertion `id == dbusmenu_menuitem_get_id(item)' failed
ERROR 2012-07-27 11:06:26 unity.libdbusmenu-glib <unknown>:0 parse_layout_xml: assertion `id == dbusmenu_menuitem_get_id(item)' failed
WARN  2012-07-27 11:06:26 unity.glib-gobject <unknown>:0 value "38326" of type `gint' is invalid or out of range for property `id' of type `gint'
WARN  2012-07-27 11:06:26 unity.glib-gobject <unknown>:0 value "38322" of type `gint' is invalid or out of range for property `id' of type `gint'
WARN  2012-07-27 11:06:26 unity.glib-gobject <unknown>:0 value "38324" of type `gint' is invalid or out of range for property `id' of type `gint'
ERROR 2012-07-27 11:06:26 unity.libdbusmenu-glib <unknown>:0 parse_layout_xml: assertion `id == dbusmenu_menuitem_get_id(item)' failed
ERROR 2012-07-27 11:06:26 unity.libdbusmenu-glib <unknown>:0 parse_layout_xml: assertion `id == dbusmenu_menuitem_get_id(item)' failed
ERROR 2012-07-27 11:06:26 unity.libdbusmenu-glib <unknown>:0 parse_layout_xml: assertion `id == dbusmenu_menuitem_get_id(item)' failed
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
ERROR 2012-07-27 11:06:27 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x351f2e8

WARN  2012-07-27 11:07:09 unity.iconloader IconLoader.cpp:438 Unable to load icon . GThemedIcon application-vnd.android.package-archive gnome-mime-application-vnd.android.package-archive application-x-generic at size 64
```

Also, it doesn't end in another command line. It just seems to end with the last line and there is no option to insert new commands anymore.

Would you have any idea what could be wrong here?

---

### Post by Bufeu on 2012-07-27
[Re-install Unity]("http://askubuntu.com/a/131090").

---

### Post by kramer65 on 2012-07-27
> **Bufeu said:**
> [Re-install Unity]("http://askubuntu.com/a/131090").

And I can do that while all other programs are running?

---

### Post by Bufeu on 2012-07-27
> **kramer65 said:**
> And I can do that while all other programs are running?Yes, you can. If you can't open a terminal after uninstalling Unity, press CTRL + ALT +F1 to switch to text mode. CTRL + ALT +F7 will bring you back to the GUI-version.

---

### Post by kramer65 on 2012-07-27
Alright. I inserted all commands on the link you gave, but the result is still the same.

There were some errors however;
* It couldn't find the packages xserver-xgl and emerald
* the packages for git compiz-plugins-extra, compiz-plugins-extra, and unity where all already installed and didn't need to be upgraded.

Did I do something wrong, or did this simply not appear to be the solution? Is there anything else I can try?

---

### Post by NikTh on 2012-07-27
Hi , 
please open a terminal (ctrl+alt+t) and install ccsm 
```
sudo apt-get install compizconfig-settings-manager
``` when installation finish , call it for terminal ```
ccsm
``` and check if Unity Plugin is enabled. 

If not , then enable Unity Plugin , logout and login. 

Thanks

---

### Post by HiImTye on 2012-07-27
> **kramer65 said:**
> Also, it doesn't end in another command line. It just seems to end with the last line and there is no option to insert new commands anymore.
it doesn't allow you to enter new commands because it isn't forked to the background. next time end the command in & to fork it, like so:
```
unity --replace &
unity --reset &
```the first command will just re-launch unity. the second resets unity. I would go with the first option first.

..and if you forget to add the '&' you can hit Ctrl+Z and then type 'bg' to fork the last program run to the background. sort of like this:
```
tye@T:~$ gnome-shell --replace
    JS ERROR: !!!   WARNING: 'assignment to undeclared variable button_settings'
    JS ERROR: !!!   WARNING: file '/usr/share/gnome-shell/extensions/window_buttons@biox.github.com/extension.js' line 145 exception 0 number 156
Window manager warning: Log level 16: STACK_OP_REMOVE: window 0x15b not in stack

(gnome-shell:32589): folks-WARNING **: Failed to find primary PersonaStore with type ID 'eds' and ID 'system'.
Individuals will not be linked properly and creating new links between Personas will not work.
The configured primary PersonaStore's backend may not be installed. If you are unsure, check with your distribution.
^Z
[1]+  Stopped                 gnome-shell --replace
tye@T:~$ bg
[1]+ gnome-shell --replace &
tye@T:~$
```
(I run Gnome Shell so that's why I used that)

---

### Post by kramer65 on 2012-07-27
> **NikTh said:**
> Hi , 
please open a terminal (ctrl+alt+t) and install ccsm 
```
sudo apt-get install compizconfig-settings-manager
``` when installation finish , call it for terminal ```
ccsm
``` and check if Unity Plugin is enabled. 

If not , then enable Unity Plugin , logout and login. 

Thanks

Unfortunately, the Unity Plugin is already enabled. If I log out and log back in, will the programs that I am running be terminated, or will they run while I log out and back in?


> **HiImTye said:**
> it doesn't allow you to enter new commands because it isn't forked to the background. next time end the command in & to fork it, like so:
```
unity --replace &
unity --reset &
```the first command will just re-launch unity. the second resets unity. I would go with the first option first.


I tried both, but after it flickers a bit, nothing has changed with either of those two commands..

Any other tips maybe?:???:

---

### Post by yuvraj23 on 2012-07-27
Maybe you can logout and relogin using the Unity that isn't damage I mean if you have got your Unity 2d damaged then login using unity 3d and then re-install unity 2d


Thankx
Yuvraj

---

### Post by NikTh on 2012-07-27
> **kramer65 said:**
> Unfortunately, the Unity Plugin is already enabled. If I log out and log back in, will the programs that I am running be terminated, or will they run while I log out and back in?

Hi , 
if you log out programs will be terminated.

You can run ```
unity --reset
``` from VT (ctrl+alt+F2) wait 10 or more (maybe 15 minutes) to see if something fix the problem . 
Return to desktop environment with (ctrl+alt+F7). 

Sorry , no further ideas for now.

---

### Post by kramer65 on 2012-07-27
In that case I have to finish until my program ends (in a few days) before I restart my computer.

Thanks a lot for all the effort anyway! I really appreciate it!!

---

