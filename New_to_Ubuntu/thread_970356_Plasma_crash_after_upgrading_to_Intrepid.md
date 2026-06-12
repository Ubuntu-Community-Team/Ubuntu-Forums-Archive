---
title: "Plasma crash after upgrading to Intrepid"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-04
Hi, all:

Here's my problem: I'm trying to mount /home, and each time I do (after mounting it and editing fstab), I try to reboot, and Plasma crashes.  If I don't try to mount /home to its own partition, Plasma begins with no problems.  WTF?

Here's the fstab line: 

/dev/sda6 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /media/secondDrive ext3 nodev,nosuid 0 2

That first one is the home partition.  The second one is an additional internal HD, which mounts just fine whether I'm mounting the home partition or not.  

This started happening after I upgraded to Intrepid.

Here's the debug information:

Application: Plasma Workspace (plasma), signal SIGSEGV
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb47736e0 (LWP 5599)]
[New Thread 0xb2de4b90 (LWP 5604)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb719f394 in QGraphicsLinearLayout::setSpacing ()
   from /usr/lib/libQtGui.so.4
#7  0xb2e08368 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#8  0xb2e08410 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#9  0xb7d48585 in Plasma::Applet::flushPendingConstraintsEvents ()
   from /usr/lib/libplasma.so.2
#10 0xb7d48bc6 in Plasma::Applet::timerEvent () from /usr/lib/libplasma.so.2
#11 0xb766953f in QObject::event () from /usr/lib/libQtCore.so.4
#12 0xb71a23c7 in QGraphicsWidget::event () from /usr/lib/libQtGui.so.4
#13 0xb6be28ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#14 0xb6bea76e in QApplication::notify () from /usr/lib/libQtGui.so.4
#15 0xb7b2872d in KApplication::notify () from /usr/lib/libkdeui.so.5
#16 0xb7659e61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#17 0xb7687d81 in ?? () from /usr/lib/libQtCore.so.4
#18 0xb7684520 in ?? () from /usr/lib/libQtCore.so.4
#19 0xb59666f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#20 0xb5969da3 in ?? () from /usr/lib/libglib-2.0.so.0
#21 0xb5969f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#22 0xb7684478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#23 0xb6c7cee5 in ?? () from /usr/lib/libQtGui.so.4
#24 0xb765852a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#25 0xb76586ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#26 0xb6897cab in KIO::NetAccess::enter_loop () from /usr/lib/libkio.so.5
#27 0xb6897eac in KIO::NetAccess::statInternal () from /usr/lib/libkio.so.5
#28 0xb6898cbb in KIO::NetAccess::stat () from /usr/lib/libkio.so.5
#29 0xb6898d3b in KIO::NetAccess::mostLocalUrl () from /usr/lib/libkio.so.5
#30 0xb2e4cf1e in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#31 0xb2e4d6ff in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#32 0xb7d78737 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.2
#33 0xb7d79531 in Plasma::Corona::initializeLayout ()
   from /usr/lib/libplasma.so.2
#34 0xb7fde199 in ?? () from /usr/lib/libkdeinit4_plasma.so
#35 0xb7fdf880 in ?? () from /usr/lib/libkdeinit4_plasma.so
#36 0xb7fe1a81 in ?? () from /usr/lib/libkdeinit4_plasma.so
#37 0xb7fd343a in kdemain () from /usr/lib/libkdeinit4_plasma.so
#38 0x080485b2 in _start ()
#0  0xb801b430 in __kernel_vsyscall ()

---

### Post by prshah on 2008-11-04
> **tarahmarie said:**
> 
Here's the fstab line: 
/dev/sda6 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /media/secondDrive ext3 nodev,nosuid 0 2


/home cannot have nodev and nosuid (especially!) options; the correct options should be just "defaults". Change the fstab line to ```

/dev/sda6 /home ext3 defaults 0 2
```

---

