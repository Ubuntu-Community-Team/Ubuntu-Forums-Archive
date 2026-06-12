---
title: "A java-based software crashes"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by g.a. on 2008-09-19
Hi,

I have a problem with the installation of a recent version of Scilab, a numerical computation software, that is using Java in its last release.

Thanks in advance for any kind of help.

Best,
g.


I have tried to install scilab 5.0.1 under Linux (Kubuntu 7.10 with
graphics card Intel 85x and i810 graphics driver). I read on the
release note that

"Errors often appear on Intel cards under Linux"

I wonder if this is my case and if there is a solution for it. Details
of my problem follows:

The main scilab window opens with a warning on the linux shell:

(<unknown>:8441): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

but seems to work for command line commands. As soon as I try to open
a graphic window the program crashes and the command line is
full of messages such as:

Exception in thread "AWT-EventQueue-0" javax.media.opengl.GLException:
Error mak
ing context current
        at
com.sun.opengl.impl.x11.X11GLContext.makeCurrentImpl(X11GLContext.java:
141)
        at
com.sun.opengl.impl.x11.X11OffscreenGLContext.makeCurrentImpl(X11Offs
creenGLContext.java:74)
        at
com.sun.opengl.impl.GLContextImpl.makeCurrent(GLContextImpl.java:134)
        at
com.sun.opengl.impl.GLDrawableHelper.invokeGL(GLDrawableHelper.java:1
82)
        at javax.media.opengl.GLJPanel.paintComponent(GLJPanel.java:
661)
        at javax.swing.JComponent.paint(Unknown Source)
        at javax.swing.JComponent.paintChildren(Unknown Source)
...

continues for several lines

....

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb590f2d7, pid=8441, tid=2630708112
#
# Java VM: Java HotSpot(TM) Server VM (10.0-b22 mixed mode linux-x86)
# Problematic frame:
# C  [libX11.so.6+0x322d7]  XQueryExtension+0x17
#
# An error report file with more information is saved as:
# /home/scilab/scilab-5.0.1/hs_err_pid8441.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)

---

### Post by gsantini on 2008-10-02
I had the same problem with Ubuntu 8.04 runing Scilab 5.0.1 and 5.0.2 !

---

