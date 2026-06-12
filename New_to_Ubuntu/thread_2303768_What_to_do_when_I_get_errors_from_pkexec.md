---
title: "What to do when I get errors from pkexec?"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by lambdafox on 2015-11-21
I am running Xubuntu 15.10, but this is not a distribution specific question.  I only mention it, because gksu is not installed with Xubuntu.

Example number 1:

```
 pkexec system-config-samba
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/share/system-config-samba/mainWindow.py:62: Warning: invalid (NULL) pointer instance
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: Warning: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: Warning: g_object_get: assertion 'G_IS_OBJECT (object)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gdk_pango_context_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_context_set_font_description: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_context_set_base_dir: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_context_set_language: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_new: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_set_attributes: assertion 'layout != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_set_text: assertion 'layout != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_get_unknown_glyphs_count: assertion 'PANGO_IS_LAYOUT (layout)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: Warning: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
Segmentation fault (core dumped)

```

Example 2:
```
~$ pkexec medit

(medit:4926): Gtk-WARNING **: cannot open display: 
~$ 

```

```
pkexec catfish
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(catfish.py:4964): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
/usr/bin/catfish: line 2:  4964 Segmentation fault      (core dumped) python3 /usr/share/catfish/bin/catfish.py "$@"
```

I see many recommendations not to run such apps with sudo.  They seem, however, to run fine when I do. :confused:

Here are my real questions, though:

Should I report an error on the policykit package, and / or
On the specific application, and / or
Do I change some setting(s) / configuration(s) on my system?

---

### Post by grahammechanical on 2015-11-21
I have a limited understanding of pkexec or polikit (PolicyKit) and it is my understanding that set policy statements are used to force user authentication to an action. If we use

```
pkexec prgram
```

then the program will run as root. But there must be a policy statement regarding that program. This is my understanding. We can find the default installed policy statements in /usr/share/polkit-1/actions/. Is there a policy statement for system-config-samba?

I also made the error of seeing pkexec as a simple replacement for gksu but I was wrong. Each application we try to run using pkexec requires a matching policy statement. That is how the method works, as far as I understand things.

[https://wiki.ubuntu.com/DesktopTeam/Specs/PolicyKitIntegration](https://wiki.ubuntu.com/DesktopTeam/Specs/PolicyKitIntegration)

Regards

---

### Post by Lars Noodén on 2015-11-21
> **lambdafox said:**
> 
I see many recommendations not to run such apps with sudo.  They seem, however, to run fine when I do. :confused:

I'd ignore pkexec and use sudo.  If you are running a graphical program then you want the -H option so that root does not drop files in your home directory.  That might not happen the second time you run a graphical program but will almost certainly happen the first time you do.  

And if you are going to edit a file, I'd recommend sudoedit instead of other ways.  By default, on the Ubuntus, sudoedit gives you nano, but if you want another you can specify that with the $EDITOR environment variable.  

```

export EDITOR=/usr/bin/gedit 
sudoedit /path/to/some/file

```

---

### Post by lambdafox on 2015-11-22
> **grahammechanical said:**
> ...

```
pkexec prgram
```

... there must be a policy statement regarding that program ... in /usr/share/polkit-1/actions/....

None of the three programs has a .policy file in the /usr/share/polkit-1/actions folder.

For medit, I found a suggested one for gedit with a google search and simply replaced gedit with medit in the file contents and the file name.

file name: org.freedesktop.policykit.pkexec.medit.policy

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>
    <vendor>medit</vendor>
    <vendor_url>http://mooedit.sourceforge.net/</vendor_url>
    <action id="org.freedesktop.policykit.pkexec.medit">
    <description>Run medit program</description>
    <message>Authentication is required to run the medit</message>
    <icon_name>accessories-text-editor</icon_name>
    <defaults>
        <allow_any>auth_admin</allow_any>
        <allow_inactive>auth_admin</allow_inactive>
        <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/medit</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
    </action>
</policyconfig>
```

This works great.  

I wonder, is there a public place where .policy files are shared for different applications?  I am thinking of something like xfcelooks.org for themes...

---

### Post by lambdafox on 2015-11-22
I created org.freedesktop.policykit.pkexec.catfish.policy for catfish as follows:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>
    <vendor>catfish</vendor>
    <vendor_url>https://launchpad.net/catfish-search</vendor_url>
    <action id="org.freedesktop.policykit.pkexec.catfish">
    <description>Run catfish program</description>
    <message>Authentication is required to run catfish</message>
    <icon_name>accessories-text-editor</icon_name>
    <defaults>
        <allow_any>auth_admin</allow_any>
        <allow_inactive>auth_admin</allow_inactive>
        <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/catfish</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
    </action>
</policyconfig>
```

obviously the icon_name is wrong.  What should I use for that?

I looked at the policykit manual at freedesktop.  I do not have enough experience with linux / ubuntu / etc. to have a gut sense whether this should be modified in any other way.

I have the same questions for system-config-samba

---

### Post by yetimon_64 on 2015-11-23
The icon name used in the desktop config file for catfish in /usr/share/applications is simply "catfish". Try replacing "accessories-text-editor" in the line "<icon_name>accessories-text-editor</icon_name>" in the policy, with the name "catfish" and see how it looks. Cheers, yeti

Edit: I haven't checked the rest of the policy for accuracy, this is just a suggestion for changing the icon. I'll leave checking the policy for others with more knowledge of such files. :)

---

### Post by lambdafox on 2015-11-26
> **yetimon_64 said:**
> The icon name used in the desktop config file for catfish in /usr/share/applications is simply "catfish". Try replacing "accessories-text-editor" in the line "<icon_name>accessories-text-editor</icon_name>" in the policy, with the name "catfish" and see how it looks. Cheers, yeti

Edit: I haven't checked the rest of the policy for accuracy, this is just a suggestion for changing the icon. I'll leave checking the policy for others with more knowledge of such files. :)

Thank you, yetmon_64.  I copied the icon name from the .desktop file.  I will so the same for the system-config-samba policy.

---

### Post by lambdafox on 2015-11-26
I noticed that the exec line in the .desktop file for system-config-samba is ```
gksu system-config-samba
```.

I deleted the gksu from the destkop file.

Here is my current policy file for system-config-samba:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>
    <vendor>system-config-samba</vendor>
    <vendor_url>https://launchpad.net/ubuntu/+source/system-config-samba</vendor_url>
    <action id="org.freedesktop.policykit.pkexec.system-config-samba">
    <description>Run system-config-samba program</description>
    <message>Authentication is required to run system-config-samba</message>
    <icon_name>system-config-samba</icon_name>
    <defaults>
        <allow_any>auth_admin</allow_any>
        <allow_inactive>auth_admin</allow_inactive>
        <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/system-config-samba</annotate>
    <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
    </action>
</policyconfig>

after these changes, sudo -H system-config-samba runs without error, but still no luck with pkexec:

pkexec system-confi-samba does not
[CODE~$ pkexec system-config-samba
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/share/system-config-samba/mainWindow.py:62: Warning: invalid (NULL) pointer instance
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: Warning: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: Warning: g_object_get: assertion 'G_IS_OBJECT (object)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gdk_pango_context_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_context_set_font_description: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_context_set_base_dir: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_context_set_language: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_new: assertion 'context != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_set_attributes: assertion 'layout != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_set_text: assertion 'layout != NULL' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: PangoWarning: pango_layout_get_unknown_glyphs_count: assertion 'PANGO_IS_LAYOUT (layout)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: Warning: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
/usr/share/system-config-samba/mainWindow.py:62: GtkWarning: IA__gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed
  self.xml = gtk.glade.XML ("/usr/share/system-config-samba/system-config-samba.glade", domain="system-config-samba")
Segmentation fault (core dumped)
][/CODE]

---

