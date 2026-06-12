---
title: "Kopete, Kontact crashing with SIGABRT"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-10-24
My Kopete crashes when I shut down, and Kontact crashes when I try to delete/purge completed tasks.  I'm using KDE 4.1.2, Hardy 8.04.  Any ideas?

Thanks!

---

### Post by tarahmarie on 2008-10-24
I got Kopete to crash like it has been before, and this time I saved the backtrace:

Application: Kopete (kopete), signal SIGABRT
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
[Thread debugging using libthread_db enabled]
[New Thread 0xb59a46c0 (LWP 6383)]
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb7f2d410 in __kernel_vsyscall ()
#7  0xb63fc085 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb63fda01 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7487367 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb7487458 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb7ec2379 in ?? () from /usr/lib/kde4/lib/libkopete.so.4
#12 0xb7ec28cb in Kopete::PluginManager::slotPluginDestroyed ()
   from /usr/lib/kde4/lib/libkopete.so.4
#13 0xb7ec401c in Kopete::PluginManager::qt_metacall ()
   from /usr/lib/kde4/lib/libkopete.so.4
#14 0xb758ff79 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#15 0xb75903b0 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#16 0xb759043b in QObject::destroyed () from /usr/lib/libQtCore.so.4
#17 0xb759124a in QObject::~QObject () from /usr/lib/libQtCore.so.4
#18 0xb7ec1c58 in Kopete::Plugin::~Plugin ()
   from /usr/lib/kde4/lib/libkopete.so.4
#19 0xb7ec9f3b in Kopete::Protocol::~Protocol ()
   from /usr/lib/kde4/lib/libkopete.so.4
#20 0xb37f9cf3 in ?? () from /usr/lib/kde4/lib/kde4/kopete_jabber.so
#21 0xb7ec69fc in ?? () from /usr/lib/kde4/lib/libkopete.so.4
#22 0xb7ec21ad in ?? () from /usr/lib/kde4/lib/libkopete.so.4
#23 0xb7e5635b in ?? () from /usr/lib/kde4/lib/libkopete.so.4
#24 0xb63ff084 in exit () from /lib/tls/i686/cmov/libc.so.6
#25 0xb63e7458 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#26 0x080644b1 in _start ()
#0  0xb7f2d410 in __kernel_vsyscall ()

---

### Post by tarahmarie on 2008-10-24
and here's the backtrace from the Kontact crash (happens when I try to purge deleted tasks)

Application: Kontact (kontact), signal SIGABRT
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
[Thread debugging using libthread_db enabled]
[New Thread 0xb4e936c0 (LWP 6348)]
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
#6  0xb7fe0410 in __kernel_vsyscall ()
#7  0xb6c0a085 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6c0ba01 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb77a1367 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb77a1458 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb77a1505 in qt_assert () from /usr/lib/libQtCore.so.4
#12 0xb14f13ed in ?? () from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#13 0xb14f8b0e in ?? () from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#14 0xb1507eeb in CalendarView::changeIncidenceDisplay ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#15 0xb1507f91 in CalendarView::incidenceDeleted ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#16 0xb150ca5c in CalendarView::qt_metacall ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#17 0xb78a9f79 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#18 0xb78aa642 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#19 0xb17e4e63 in KOrg::IncidenceChangerBase::incidenceDeleted ()
   from /usr/lib/kde4/lib/libkorganizer_interfaces.so.4
#20 0xb15983c2 in IncidenceChanger::deleteIncidence ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#21 0xb1503486 in CalendarView::purgeCompletedSubTodos ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#22 0xb15083a3 in CalendarView::purgeCompleted ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#23 0xb150d067 in CalendarView::qt_metacall ()
   from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#24 0xb78a9f79 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#25 0xb78aa642 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#26 0xb14f7ec7 in ?? () from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#27 0xb14f8bd6 in ?? () from /usr/lib/kde4/lib/libkorganizerprivate.so.4
#28 0xb78a9f79 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#29 0xb78aa3b0 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#30 0xb6f55151 in QAction::triggered () from /usr/lib/libQtGui.so.4
#31 0xb6f55b2f in QAction::activate () from /usr/lib/libQtGui.so.4
#32 0xb73374c1 in ?? () from /usr/lib/libQtGui.so.4
#33 0xb7339d24 in QMenu::mouseReleaseEvent () from /usr/lib/libQtGui.so.4
#34 0xb6fb3d44 in QWidget::event () from /usr/lib/libQtGui.so.4
#35 0xb7334e45 in QMenu::event () from /usr/lib/libQtGui.so.4
#36 0xb6f5bf9c in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#37 0xb6f61125 in QApplication::notify () from /usr/lib/libQtGui.so.4
#38 0xb7d2a483 in KApplication::notify () from /usr/lib/kde4/lib/libkdeui.so.5
#39 0xb78950b9 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#40 0xb6f5e661 in QApplicationPrivate::sendMouseEvent ()
   from /usr/lib/libQtGui.so.4
#41 0xb6fc876c in ?? () from /usr/lib/libQtGui.so.4
#42 0xb6fc6ee1 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#43 0xb6fefc2a in ?? () from /usr/lib/libQtGui.so.4
#44 0xb5733cc6 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#45 0xb5737083 in ?? () from /usr/lib/libglib-2.0.so.0
#46 0xb573763e in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#47 0xb78c09f8 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#48 0xb6fefa25 in ?? () from /usr/lib/libQtGui.so.4
#49 0xb789433d in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#50 0xb78944cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#51 0xb789674d in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#52 0xb6f5b897 in QApplication::exec () from /usr/lib/libQtGui.so.4
#53 0x0804b326 in _start ()
#0  0xb7fe0410 in __kernel_vsyscall ()

---

### Post by tarahmarie on 2008-10-26
is this the right place to post this question?

---

