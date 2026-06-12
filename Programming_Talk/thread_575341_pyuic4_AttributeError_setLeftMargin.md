---
title: "pyuic4 AttributeError: setLeftMargin"
date: 2007-10-13
forum: Programming Talk
---

### Post by dieselpower on 2007-10-13
I just came back to Kubuntu after a couple years with Gentoo, but have a problem. The ui files I generate with pyuic4 do not work. I'm kind of desperate for a fix as I have a deadline to meet in a week here and have a lot of work to do. The error I get when I run the program is below. pyuic (qt3) generates valid ui files so I don't expect it to be QT-Designer. Please help.

```

Traceback (most recent call last):
  File "./iac-test.py", line 267, in <module>
    win = iaC()
  File "./iac-test.py", line 25, in __init__
    self.ui.setupUi(self)
  File "/home/lawrence/Python/atf_ui.py", line 22, in setupUi
    self.gridlayout.setLeftMargin(9)
AttributeError: setLeftMargin

```

---

### Post by dieselpower on 2007-10-14
OK, this seems to be a standard ubuntu problem. Can anybody tell me if gutsy still has this problem? Is it worth upgrading to gutsy on a production machine yet? I made the mistake of switching all 6 computers to 7.04 from gentoo and do not ave a machine that will generate my pyuic files right now. Or does someone have an updated pyqt-dev-tools package?

---

### Post by dieselpower on 2007-10-16
Is there a better place to get help? or do I go back to gentoo???!

---

