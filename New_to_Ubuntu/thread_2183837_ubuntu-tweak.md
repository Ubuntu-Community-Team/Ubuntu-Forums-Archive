---
title: "ubuntu-tweak"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-10-26
i keep getting this error message when i try to open. i have tried to reinstall and have the current version for 13.10
ray@ray-desktop:~$ ubuntu-tweak

(ubuntu-tweak:6026): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 92, in on_startup
    from ubuntutweak.main import UbuntuTweakWindow
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 36, in <module>
    from ubuntutweak.preferences import PreferencesDialog
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/preferences.py", line 32, in <module>
    from ubuntutweak.factory import WidgetFactory
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/factory.py", line 24, in <module>
    from ubuntutweak.gui.widgets import *
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/gui/widgets.py", line 10, in <module>
    from ubuntutweak.settings.compizsettings import CompizSetting
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/compizsettings.py", line 3, in <module>
    import ccm
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/ccm/__init__.py", line 1, in <module>
    from Conflicts import *
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/ccm/Conflicts.py", line 25, in <module>
    from Constants import *
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/settings/ccm/Constants.py", line 77, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.7/locale.py", line 547, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
TypeError: can't convert return value to desired type
/usr/bin/ubuntu-tweak:123: Warning: g_value_copy: assertion 'G_IS_VALUE (src_value)' failed
  app.run(sys.argv)
/usr/bin/ubuntu-tweak:123: Warning: g_value_reset: assertion 'G_IS_VALUE (value)' failed
  app.run(sys.argv)
/usr/bin/ubuntu-tweak:123: Warning: g_value_unset: assertion 'G_IS_VALUE (value)' failed
  app.run(sys.argv)
ray@ray-desktop:~$ 
any idea how to fix/tks

---

### Post by Frogs Hair on 2013-10-26
Ubuntu Tweak is recommended for Ubuntu and not its derivatives , Many of the settings are Unity specific on the latest version which works fine with Ubuntu. You could try removing the UT folder from .config and re-installing in order to start with fresh profile. It is not intended for use with Xubuntu although you may have gotten it to work in the past.

---

### Post by rburkartjo on 2013-10-26
frog tks have done that and didnt fix. note on my lap top ut is working fine in ubuntu,xubuntu,lubuntu,gnome,and enlightenment.

---

### Post by rburkartjo on 2013-10-26
had the problem when doing 13.10 testing on my desktop. figured it would be fixed when the final came out as on my laptop. has to be something stupid that i am overlooking.

---

### Post by rburkartjo on 2013-10-30
i also have noticed that gnome-do doesnt work either so whatever i have done has also affected this.weird.

---

