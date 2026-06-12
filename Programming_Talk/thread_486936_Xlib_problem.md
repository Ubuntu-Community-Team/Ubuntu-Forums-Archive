---
title: "Xlib problem"
date: 2007-06-28
forum: Programming Talk
---

### Post by hydr0g3n on 2007-06-28
Hi,

I'm writing a widget in pyQt4 and I don't want it to have a taskbar entry. I tried to do this with Qt4 only but I could't (I managed to skip the taskbar entry by using "Qt.X11BypassWindowManagerHint" window property but then the window would "always stay on top" and I don't want that).

I read on internet that I could do it with Xlib using "_NET_WM_STATE_SKIP_TASKBAR", and I wrote the following code :

def removeTaskbarEntry():
  d= display.Display(":0")
  props = []
  props.append(d.intern_atom("_NET_WM_STATE_SKIP_TASKBAR"))
  props.append(d.intern_atom("_NET_WM_STATE_SKIP_PAGER"))
  net_wm_state = d.intern_atom("_NET_WM_STATE")
  d.screen().root.change_property(net_wm_state, Xatom.ATOM, 32, props)
  d.sync()
  d.flush()

class Calendar(QtGui.QWidget):
  def  __init__(self, qApp, parent=None):
    QtGui.QWidget.__init__(self, parent, QtCore.Qt.FramelessWindowHint)
    removeTaskbarEntry()

Unfortunately, this doesn't work. This is the first time I'm using Xlib, help would be greatly appreciated.

---

### Post by hydr0g3n on 2007-06-28
I also tried in C++:

qoolendar::qoolendar() {
      Atom props[2];
      props[0] = XInternAtom (QX11Info::display(), "_NET_WM_STATE_SKIP_TASKBAR", False);
      props[1] = XInternAtom (QX11Info::display(), "_NET_WM_STATE_SKIP_PAGER", False);
      Atom net_wm_state = XInternAtom(QX11Info::display(), "_NET_WM_STATE", False);
      XChangeProperty (QX11Info::display(), winId(), net_wm_state, XA_ATOM, 32, PropModeReplace, (unsigned char *)props, 2);

But this has no effect either... Anyone has an idea of what the problem could be?

---

