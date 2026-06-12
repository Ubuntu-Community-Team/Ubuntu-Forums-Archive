---
title: "Variety throwing errors I dont understand, how do I correct this?"
date: 2017-04-21
forum: New to Ubuntu
---

### Post by robertzito on 2017-04-21
I noticed my backgrounds were not changing, when I run from command line I get the error below and confirmed that GTK3 is installed I am on Ubuntu 16.04. I noticed in the syslog HTTPError: 405 Client Error: Method Not Allowed for url: [https://vrty.org/api/stats/44towqiaju/report-config](https://vrty.org/api/stats/44towqiaju/report-config) does this have anything to do with it becuase it says the site is down.




/usr/lib/python2.7/dist-packages/variety/__init__.py:108: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GObject # pylint: disable=E0611
/usr/lib/python2.7/dist-packages/variety/VarietyWindow.py:27: PyGIWarning: Notify was imported without specifying a version first. Use gi.require_version('Notify', '0.7') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GdkPixbuf, GObject, Gio, Notify # pylint: disable=E0611
/usr/lib/python2.7/dist-packages/variety/AddPanoramioDialog.py:19: PyGIWarning: WebKit was imported without specifying a version first. Use gi.require_version('WebKit', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, WebKit, GObject # pylint: disable=E0611
/usr/lib/python2.7/dist-packages/variety/QuoteWriter.py:19: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gdk, Pango, PangoCairo, GdkPixbuf, GObject
/usr/lib/python2.7/dist-packages/variety/indicator.py:30: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 # pylint: disable=E0611
Variety is already running. Sending the command to the running instance.

---

### Post by oldos2er on 2017-04-21
> **robertzito said:**
> I noticed my backgrounds were not changing, when I run from command line I get the error below and confirmed that GTK3 is installed I am on Ubuntu 16.04. I noticed in the syslog HTTPError: 405 Client Error: Method Not Allowed for url: [https://vrty.org/api/stats/44towqiaju/report-config](https://vrty.org/api/stats/44towqiaju/report-config) does this have anything to do with it becuase it says the site is down.

If the program can't connect to the site, then yes, I'd say that's the problem.

---

### Post by kostkon on 2017-04-21
It looks like [vrty.org has been shut down]("http://peterlevi.com/variety/2017/03/changes/") and the project semi-abandonded.

---

### Post by robertzito on 2017-04-21
Odd it works in MATE!!!

---

