---
title: "Accidentally Installed Two Ubuntus"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by mezasemaster on 2014-06-21
Hello!

First of all, let me preface this by saying that I am absolutely inept when it comes to Linux-based OS, so please bear with me. I am installing Ubuntu on my Chromebook with Crouton so that I will have access to Steam and Steam titles on here, and so far everything has been smooth. However, I was using two installation guides at once to figure it out, one more general but clearer for a newbie like me and another for specifically installing it with Steam, and for the most part I was following the general guide over the Steam guide. So to install Ubuntu, I typed in the command "sudo sh -e ~/Downloads/crouton -t xfce." It worked and everything, but after I had installed it I noticed the Steam-specific guide told me to add "-r raring" to the end of the initial installation as it was supposedly "the best setup for gaming." I have no idea what difference it would make, so I went ahead and did that thinking it would overwrite the initial installation. To my surprise, it installed Ubuntu again all over, and by the time it finished I had three OSes to switch between, with the middle one being a sort of corrupted Ubuntu that had my web browser windows I had on it still open but nothing else and I was unable to do anything. Does anybody know how I go about uninstalling this one while keeping my most recent installation? Thank you!

---

### Post by mezasemaster on 2014-06-21
Okay, now it actually seems even worse than I thought. Whenever I return to Chrome, I can no longer switch to Linux again until I manually boot it up with "sudo start xfce4" in Crosh despite the fact there's a shortcut I could do it through before (and is how I get back to Chrome). Not only that, but whenever I do that it adds another "dead" Linux OS to switch through, so at first it had three OSes between Chrome, the first broken Linux, and the new second Linux, but now when I re-ran Linux after that it has four, with the third one being busted in the same vein as the second and the fourth one being the one that works, just adding a new one every time I relaunch. Also, when I go back to Chrome and the shortcut keys stop working, I get the following errors in Crosh:

```
setversion 1.4 failed
xfce4-session: No gpg or ssh authentication agent found


(polkit-gnome-authentication-agent-1:16458): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed


(polkit-gnome-authentication-agent-1:16458): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(Thunar:16411): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(xfce4-session:16276): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(xfwm4:16377): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(xfce4-panel:16398): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(xfdesktop:16433): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed


(wrapper:16636): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(wrapper:16641): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(xfdesktop:16433): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed


(xfdesktop:16433): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed


(xfdesktop:16433): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed


(xfsettingsd:16492): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(xfdesktop:16433): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) AIGLX: Suspending AIGLX clients for VT switch


(x-www-browser:17491): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(II) AIGLX: Suspending AIGLX clients for VT switch

```
Hopefully this will help, thanks.

---

### Post by oldfred on 2014-06-22
Added code tags. Please use code tags on any longer terminal type output.

Do not know chrome but know it has some unique requirements. But to understand what you have installed, see if this will run from either your install or a live installer.
Post link to BootInfo report that it gives (not report itself).

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

