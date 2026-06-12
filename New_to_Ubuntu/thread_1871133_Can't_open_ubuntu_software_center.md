---
title: "Can't open ubuntu software center"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by anzure on 2011-10-28
Hi my ubuntu software center cannot open
And when I type software-center in terminal there are lines:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 53, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 35, in <module>
    from softwarepane import SoftwarePane
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 49, in <module>
    from purchaseview import PurchaseView
  File "/usr/share/software-center/softwarecenter/view/purchaseview.py", line 27, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.7/webkit/__init__.py", line 21, in <module>
    import webkit
ImportError: /usr/lib/libwebkitgtk-1.0.so.0: undefined symbol: gst_x_overlay_set_window_handle

Can anyone show me how to fix this. Thanks

---

### Post by sadaruwan12 on 2011-10-28
It seems like your full software center application got damaged did you tried removing and reinstalling software center.

---

### Post by anzure on 2011-10-28
I tried many times with synaptic but it had the same problems
Can u suggest other solution?

---

### Post by deloquencia on 2011-10-28
I don't think this problem will be solved only by re-installing software-center. The undefined symbol *gst_x_overlay_set_window_handle* looks more that in Pythons Webkit Library is something missing or it was set to hold and was not updated recently.

Try to re-install the package libwebkitgtk-1.0-0.

To exclude some miss-configuration just rename $HOME/.cache/software-center and start again the software-center, but I don't think this will solve your issue.

---

### Post by sadaruwan12 on 2011-10-28
Sorry for overlooking the webkit try redoing that and the option suggested by deloquencia.

---

### Post by deloquencia on 2011-10-28
No problem,

I checked the code and guess these decision in /usr/share/software-center/softwarecenter/view/softwarepane.py is making the trouble:

```

if "SOFTWARE_CENTER_APPDETAILS_WEBKIT" in os.environ:
    from appdetailsview_webkit import AppDetailsViewWebkit as AppDetailsView
else:
    from  appdetailsview_gtk import AppDetailsViewGtk as AppDetailsView
```

Try taking the decision for the software-center, instead of importing AppDetailsViewWebkit it should take AppDetailsViewGtk and using it for the object AppDetailsView.

It would just look like this...

```

from  appdetailsview_gtk import AppDetailsViewGtk as AppDetailsView
```

Let's see what happens - like that we could get closer to the problem and to a solution :)

Sorry I'm not so much familiar with Python...

---

