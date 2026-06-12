---
title: "Ubuntu One not working on 11.10"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by rgsantos on 2012-03-02
I discovered that my Ubuntu One is not working since the end of November 2011. I didn't change anything but the frequent updates for the 11.10. I'm running the 11.10 since it was released, upgrading it from the 11.04.

I tried to fix but I can't even start the Ubuntu One anymore. I tried to start the control panel from the terminal but I got the below error:

sudo ubuntuone-control-panel-gtk

Traceback (most recent call last):
  File "/usr/bin/ubuntuone-control-panel-gtk", line 33, in <module>
    from ubuntuone.controlpanel.gui.gtk import main
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/__init__.py", line 28, in <module>
    from ubuntuone.controlpanel.gui.gtk.gui import main
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/gui.py", line 35, in <module>
    from ubuntuone.platform.credentials import (
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/__init__.py", line 10, in <module>
    from ubuntuone.platform import linux
EOFError: EOF read where object expected


I tried to uninstall and and install again but I got pretty much the same error message. Clicking on Ubuntu One at Unity has no effect since the application do not start.

I deleted the Ubuntu One key in the Gnome Keyring as I found some people had this issue but without result.

Can anyone give me a hint?

Thanks a lot.

---

### Post by d4m1r on 2012-03-02
Launch synaptic (not software center) search for "ubuntu-one" or similar and remove all of them. Then reinstall. It looks like you are having issues with a dependent package but not ubuntu-one itself.

---

### Post by rgsantos on 2012-03-02
Thank you d4m1r!!!

I did as you said but I required some additional steps to make it work.

1) I removed Ubuntu One in the Software Center
2) Opened Synaptics and "Completely Removed" all the other Ubuntu One packages.
3) Installed again Ubuntu One from the Software Center
4) Tested Ubuntu One but it didn't worked again
5) Opened Synaptic and manually selected the following packages to install:[INDENT]ubuntuone-control-panel-gtk
ubuntuone-control-panel
ubuntuone-client-gnome
ubuntuone-client
ubuntuone-couch
[/INDENT]6) Tried again to open the Ubuntu One and voilá!

It's working perfectly now!

Thanks a lot.

---

