---
title: "[SOLVED] Is it me or is pynotify buggy as hell?"
date: 2007-09-21
forum: Programming Talk
---

### Post by quirks on 2007-09-21
I use a sweet backup tool called RDiff-Backup ([http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)) to save my files regularly on a second harddisk. Therefore, I set up a cron job for RDiff-Backup. Because I want to know, when it runs (so I don't shut down my PC and thus, interrupt the backup process), I wrote this little piece of Python code. It displays a nice icon in the Gnome Panel and shows a notification, when RDiff-Backup runs. Maybe someone else might want to use it, too.

Installation (Tested on Ubuntu 6.10 Edgy Eft):

Install libnotify support for Python:
```
sudo apt-get install python-notify
```

Create an autostart entry for Gnome /etc/xdg/autostart/rdiff-backup_notifier.py.desktop with the following content:

```
[Desktop Entry]
Name=RDiff-Backup-Notifier
Encoding=UTF-8
Version=1.0
Exec=/usr/local/bin/rdiff-backup_notifier.py
X-GNOME-Autostart-enabled=true
```

Create an executable script /usr/local/bin/rdiff-backup_notifier.py with this content:

```
#!/usr/bin/env python

# WARNING: I have NO clue about Python
# and this is probably the most ugly code you have ever seen!!!
# If you know it better, feel free to improve this.

import gtk
import pynotify
from egg import trayicon
import os
import gobject

tray_icon_file = "/usr/share/icons/Tango/22x22/mimetypes/gnome-mime-application-x-archive.png"
tray_icon = trayicon.TrayIcon("RDiff-Backup")
tray_image = gtk.Image()
tray_image.set_from_file(tray_icon_file)
event_box = gtk.EventBox()
event_box.add(tray_image)
tray_icon.add(event_box)

tooltip_text = "RDiff-Backup is saving your files. Please do not shut down your computer."
tooltips = gtk.Tooltips()
tooltips.set_tip(event_box, tooltip_text)
pynotify.init("RDiff-Backup")
notif = pynotify.Notification("RDiff-Backup", tooltip_text)
notif.set_urgency(pynotify.URGENCY_LOW)
notif.set_timeout(10000)
notif.attach_to_widget(tray_icon)

def check_for_rdiff_backup():
        global tray_icon, tray_icon_visible, notif
        process_running = os.popen("ps -ef | grep -v grep | grep -c 'python /usr/bin/rdiff-backup'").read()
        if (process_running != "0\n") and not tray_icon_visible:
                tray_icon.show_all()
                notif.show()
                notif.show()
                tray_icon_visible = True
        elif (process_running == "0\n") and tray_icon_visible:
                tray_icon.hide_all()
                tray_icon_visible = False
        gobject.timeout_add(15000, check_for_rdiff_backup)

tray_icon_visible = False
check_for_rdiff_backup()
gtk.main()
```

quirks

---

