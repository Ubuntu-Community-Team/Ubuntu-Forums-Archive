---
title: "gnome3  restarting?"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by duruttye on 2012-04-06
Hey there!

I'm on ubuntu 11.10 using gnome 3.

I noticed for a few days that google-chrome and chromium crashed a few times because of segmentation fault on Dell Vostro a860. But today I had a few gnome shell restarts also.

Running dmesg I get a few lines like this:
[HTML]gnome-shell[11834] general protection ip:4fbf22 sp:b5dff080 error:0 in libglib-2.0.so.0.3000.0[4b9000+f7000]
[/HTML] - exactly after everything dissapears from the desktop and it takes about 20-25 seconds for all apps opened to appear again.

I can also see:
[HTML]chrome[12025] general protection ip:b32416 sp:bf9b6fe0 error:0
[/HTML]

Maybe it's not related at all, but it's full of this, also:
[HTML]Inbound IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:00:11:6b:15:94:42:08:00 SRC=192.168.0.1 DST=239.255.255.250 LEN=326 TOS=0x00 PREC=0x00 TTL=4 ID=23181 PROTO=UDP SPT=1900 DPT=1900 LEN=306 
[/HTML]

Anybody else seeing this?

Thank you!

---

### Post by 2F4U on 2012-04-06
If Gnome crashes you should be able to find some hints in the file .xsession-errors in your home folder.

---

### Post by duruttye on 2012-04-06
well, I loooked at the .xsession-errors file, but I have no clue what those line mean :)

In the meanwhile I reverted to an older kernel (3.0.0-16-generic) and it didn't crash for an hour now. And I'm using google-chrome also, that didn't crash either. So, it's probably the new kernel.

Anyway, I insert the .xsession-errors here, maybe someone can see some errors there :)

[HTML]Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/domelaci/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-asYkN4
SSH_AUTH_SOCK=/tmp/keyring-asYkN4/ssh
GNOME_KEYRING_PID=1572
GNOME_KEYRING_CONTROL=/tmp/keyring-asYkN4
SSH_AUTH_SOCK=/tmp/keyring-asYkN4/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-asYkN4
SSH_AUTH_SOCK=/tmp/keyring-asYkN4/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-asYkN4
SSH_AUTH_SOCK=/tmp/keyring-asYkN4/ssh
GPG_AGENT_INFO=/tmp/keyring-asYkN4/gpg:0:1
chown: changing ownership of `/var/jupiter/available_resolutions': Operation not permitted
chown: changing ownership of `/var/jupiter/battery': Operation not permitted
chown: changing ownership of `/var/jupiter/cpu_mode': Operation not permitted
chown: changing ownership of `/var/jupiter/power': Operation not permitted
chown: changing ownership of `/var/jupiter/resolution_saved': Operation not permitted
chown: changing ownership of `/var/jupiter/rotation_saved': Operation not permitted
chown: changing ownership of `/var/jupiter/vga_saved': Operation not permitted
chmod: changing permissions of `/var/jupiter/available_resolutions': Operation not permitted
chmod: changing permissions of `/var/jupiter/battery': Operation not permitted
chmod: changing permissions of `/var/jupiter/cpu_mode': Operation not permitted
chmod: changing permissions of `/var/jupiter/power': Operation not permitted
chmod: changing permissions of `/var/jupiter/resolution_saved': Operation not permitted
chmod: changing permissions of `/var/jupiter/rotation_saved': Operation not permitted
chmod: changing permissions of `/var/jupiter/vga_saved': Operation not permitted
gnome-session[1476]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gnome-do" (No such file or directory)
gnome-session[1476]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "docky" (No such file or directory)
/usr/share/indicator-multiload/preferences.ui
** (nautilus:1705): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-dropbox 0.7.1
Initializing nautilus-image-converter extension
Initializing nautilus-gdu extension
Failed to play sound: File or data not found
Starting Dropbox...** Message: applet now removed from the notification area
Dropbox isn't running!
Done!
    JS ERROR: !!!   WARNING: 'assignment to undeclared variable button'
    JS ERROR: !!!   WARNING: file '/home/domelaci/.local/share/gnome-shell/extensions/show-desktop@l300lvl.tk/extension.js' line 80 exception 0 number 156
    JS ERROR: !!!   WARNING: 'assignment to undeclared variable type'
    JS ERROR: !!!   WARNING: file '/home/domelaci/.local/share/gnome-shell/extensions/temperature@xtranophilist/extension.js' line 213 exception 0 number 156
    JS ERROR: !!!   WARNING: 'assignment to undeclared variable r'
    JS ERROR: !!!   WARNING: file '/home/domelaci/.local/share/gnome-shell/extensions/temperature@xtranophilist/extension.js' line 325 exception 0 number 156

(gnome-shell:1684): Clutter-WARNING **: Attempting to add actor of type 'StLabel' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.
      JS LOG: GNOME Shell started at Fri Apr 06 2012 16:40:51 GMT+0300 (EEST)
** (process:2315): DEBUG: Telepathy Indicator started

** (gnome-screensaver:2316): WARNING **: screensaver already running in this session
failed to create drawable
** (nm-applet:1708): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1708): DEBUG: old state indicates that this was not a disconnect 0
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

(indicator-multiload:1714): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `window->update_and_descendants_freeze_count > 0' failed

(dropbox:1919): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(gnome-settings-daemon:1573): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `window->update_and_descendants_freeze_count > 0' failed
/usr/bin/jupiter:506: GtkWarning: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

failed to create drawable

(gnome-shell:1684): Clutter-CRITICAL **: clutter_text_get_editable: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1684): Clutter-CRITICAL **: clutter_text_get_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1684): Clutter-CRITICAL **: clutter_text_set_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1684): Clutter-CRITICAL **: clutter_text_get_editable: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1684): Clutter-CRITICAL **: clutter_text_get_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:1684): Clutter-CRITICAL **: clutter_text_set_text: assertion `CLUTTER_IS_TEXT (self)' failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1200004 (Desktop) with a timestamp of 0.  This shouldn't happen!

** (process:2393): WARNING **: recent-manager-provider.vala:125: Desktop file for contacts was not found
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (nautilus:1705): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x2e0004c specified for 0x2e00027 (Firestarte).

(gnome-shell:1684): Clutter-WARNING **: The actor 'uiGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(gnome-shell:1684): Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed
** (deja-dup-monitor:2764): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
Window manager warning: Log level 16: STACK_OP_RAISE_ABOVE: sibling window 0x3400001 not in stack

** (process:2393): WARNING **: recent-manager-provider.vala:125: Desktop file for contacts was not found
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(gnome-shell:1684): Clutter-WARNING **: The actor 'uiGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(gnome-shell:1684): Clutter-WARNING **: The actor 'uiGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

** (process:2393): WARNING **: recent-manager-provider.vala:125: Desktop file for contacts was not found
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(gnome-shell:1684): Clutter-CRITICAL **: clutter_actor_queue_relayout: assertion `CLUTTER_IS_ACTOR (self)' failed

** (process:2393): WARNING **: recent-manager-provider.vala:125: Desktop file for contacts was not found
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (gnome-commander:3877): CRITICAL **: GnomeCmdConFtp* gnome_cmd_con_ftp_new(const gchar*, const string&): assertion `uri != NULL' failed

** (gnome-commander:3877): CRITICAL **: GnomeCmdConFtp* gnome_cmd_con_ftp_new(const gchar*, const string&): assertion `uri != NULL' failed

(gnome-commander:3877): Gtk-CRITICAL **: IA__gtk_signal_connect_full: assertion `GTK_IS_OBJECT (object)' failed

** (gnome-commander:3877): CRITICAL **: GnomeCmdBookmarkGroup* gnome_cmd_con_get_bookmarks(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: GnomeCmdPixmap* gnome_cmd_con_get_go_pixmap(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: const gchar* gnome_cmd_con_get_go_text(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_closeable(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

** (gnome-commander:3877): CRITICAL **: gboolean gnome_cmd_con_is_open(GnomeCmdCon*): assertion `GNOME_CMD_IS_CON (con)' failed

(gnome-shell:1684): Clutter-WARNING **: The actor 'uiGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

** (process:2393): WARNING **: recent-manager-provider.vala:125: Desktop file for contacts was not found
** (process:2393): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events[/HTML]

---

### Post by MBybee on 2012-04-07
Same here, just since the new kernel.
Gnome Shell, ATI 5450, 64 bit.

---

### Post by MBybee on 2012-04-09
Not sure what video you're running - but for me, switching to the fglrx-devel fixed my crashes on the current kernel.

---

### Post by duruttye on 2012-04-11
I'm using: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

---

### Post by myandylai on 2012-05-03
I am also having the same issue at 11.10 64-bit and ATI 12.4 FGLRX from amd.com. It just randomly restart but it complete very fast like 2 sec. This especially will happen when I move the mouse pointer to the upper left of the screen to display the application tray.

I check the .xsession-error at ~, it was showing,

(gnome-shell:1855): Clutter-WARNING **: The actor 'uiGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
** Message: applet now removed from the notification area
gnome-shell-calendar-server[1916]: Got HUP on stdin - exiting
gnome-session[1769]: WARNING: Application 'gnome-shell.desktop' killed by signal
      JS LOG: GNOME Shell started at Fri May 04 2012 09:42:55 GMT+0800 (MYT)
** Message: applet now embedded in the notification area
** (process:2268): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

Using the fglrx from Ubuntu doesn't help as it break all the icon and text. Almost like a screen corruption. And the message above also mention that gnome-shell.desktop was killed by signal. Is this because Ubuntu doesn't like gnome and prefer unity so it killed gnome? It that's the case then I have no choice but switching it back to unity as it doesn't had any problem. Just I personally doesn't like unity at all. Not familiar with the interface. I prefer gnome.

Thanks.

---

