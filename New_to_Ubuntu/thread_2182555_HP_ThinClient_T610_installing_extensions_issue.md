---
title: "HP ThinClient T610 installing extensions issue"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by b-h on 2013-10-21
First off, hello message board as this is my 1st post in these forums!!

I am running into difficulty installing an extension into FireFox on an HP ThinClient T610...

I have found via search, my first command to unlock things in this client was -fsunlock...

After doing that I can now "modify" files/folders...

Also, after much trial and error for where "extension files/folders" should go, I have gotten my extensions folder made with the install.rdf em:id and was able to set my extensions.autoDisableScopes to "0" after finding where my "writeable" files are...

Just a side note, it seems this thin client has been really slimmed down as I am missing some functions like yum...

I did un-remark out my sources.list file and was then able to do apt-get update and apt-get install alien in which seemed to help getting a "linux client" to install, but alas I would like to use a browser plug-in...

Some tid-bits about this system - 

There is no "shell" except for an HP deal that is very limited and my only ways of nav'ing around is through the built in text editor (File/Open I can "see" around) and through a terminal...

I am pretty sure there is a 1GB o.s. partition that is "locked" by default by hp...

A re-cap -

I have gotten a browser extension to install
I have enabled it to "auto-load" by setting extensions.autoDisableScopes to "0"
When I load the browser, I am getting an "undefined symbol" error
I need to know how to create a "symbolic link" I think...

Here is an excerpt from a system log - 

```

Connection starting
rm: cannot remove `/home/user/.ICAClient/All_Regions.ini': No such file or directory
WARNING /etc/templates/xen/wfclient.in/182: Could not find regkey tmp/Display/curDepth, but have default value. writing default value 8
tray: another systray already running

(firefox:28694): Gtk-WARNING **: Could not find the icon 'gtk-go-back-ltr'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
    http://icon-theme.freedesktop.org/releases
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgoprintclient.so [/usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgoprintclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgosessionclient.so [/usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgosessionclient.so: undefined symbol: _ZNK8CS_Class24getDefaultRequestRoutingEv]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgoclipboardclient.so [/usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgoclipboardclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgodisplayclient.so [/usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgodisplayclient.so: undefined symbol: _ZN9CS_Thread9terminateEv]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgoaudioclient.so [/usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgoaudioclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgofileclient.so [/usr/lib/firefox-addons/extensions/support.ip@ge.com/plugins/libgofileclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgofileclient.so [/usr/lib/mozilla/plugins/libgofileclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgoclipboardclient.so [/usr/lib/mozilla/plugins/libgoclipboardclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgodisplayclient.so [/usr/lib/mozilla/plugins/libgodisplayclient.so: undefined symbol: _ZN9CS_Thread9terminateEv]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgoaudioclient.so [/usr/lib/mozilla/plugins/libgoaudioclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgosessionclient.so [/usr/lib/mozilla/plugins/libgosessionclient.so: undefined symbol: _ZNK8CS_Class24getDefaultRequestRoutingEv]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libgoprintclient.so [/usr/lib/mozilla/plugins/libgoprintclient.so: undefined symbol: _ZNK12CS_Component11getDataTypeEi]

```
 

It appears I have the lib files in 2 places that FireFox is loading from??

If anyone can help me resolve this issue, I would be more than GREATLY APPRECIATIVE!

Thanks for any tips, pointers, or help!!

Brandon

---

### Post by b-h on 2013-10-22
Ttt?

---

