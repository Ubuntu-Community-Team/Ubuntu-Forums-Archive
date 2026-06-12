---
title: "Screenlets wont load"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by munkyboy on 2008-06-30
Hello.

Im trying to install and run screenlets but i cant get it to run. it just stops dead and nothing happens.

This is the error message i get from terminal

russ@russ-desktop:~$ emerald-theme-manager
russ@russ-desktop:~$ /usr/share/screenlets-manager/screenlets-manager.py > /dev/                                                                                                                                                            null
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1201, in <mod                                                                                                                                                            ule>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 258, in __ini                                                                                                                                                            t__
    self.create_ui()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 586, in creat                                                                                                                                                            e_ui
    w.set_icon_from_file('/usr/share/icons/screenlets.svg')
gobject.GError: Couldn't recognize the image file format for file '/usr/share/ic                                                                                                                                                            ons/screenlets.svg'
russ@russ-desktop:~$

What does it mean? do i need to install anything else?

Thanks.

---

