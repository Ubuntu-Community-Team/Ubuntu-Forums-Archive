---
title: "debugging segmentaiton violation"
date: 2018-12-02
forum: Programming Talk
---

### Post by kassandr on 2018-12-02
Hello.

I was using some seismology software since January 2018 on Ubuntu 14.04 (32 bit) under Virtual Box and all was fine. I installed some updates suggested by Ubuntu recently, and the app stopped working. I decided to completely reinstall it on a fresh Ubuntu without those updates. Now it starts Ok and loads the interface, but when I try to open a database for an example project I receive a segmentation violation error, then application crashes. Unfortunately, this application is 13 years old and there is no support from developers any more.

I am now trying to get an idea where this error comes from, though I have little to no such experience. So far I used *strace *and backtrace in *gdb*, but I cannot figure out from the output where to look next. I will appreciate if someone can look at the logs below and say whether there is some helpful information or where I need to dig deeper. I have spent some crazy amount of time trying to make it work and I feel there is one small step left - the software was working before on this exact system.

strace: 
```

write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
write(3, "\1\0\0\0\0\0\0\0", 8)         = 8
access("/opt/dsap/3.4/data/wd.cf", R_OK) = 0
open("/opt/dsap/3.4/data/wd.cf", O_RDONLY) = 7
fstat64(7, {st_mode=S_IFREG|0555, st_size=402, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x41d7f000
read(7, "# This file describes a pattern "..., 4096) = 402
read(7, "", 4096)                       = 0
close(7)                                = 0
munmap(0x41d7f000, 4096)                = 0
stat64("/home/aln/Ftan/fmt/example/Seed2Db/Dbase/Colima", 0xbffceab0) = -1 ENOENT (No such file or directory)
access("/home/aln/Ftan/fmt/example/Seed2Db/Dbase/css3.0", F_OK) = -1 ENOENT (No such file or directory)
access("/opt/dsap/3.4/data/schemas2/css3.0", R_OK) = 0
open("/opt/dsap/3.4/data/schemas2/css3.0", O_RDONLY) = 7
ioctl(7, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0xbffce548) = -1 ENOTTY (Inappropriate ioctl for device)
read(7, "\nSchema \"css3.0\"\n\tDescription ( "..., 8192) = 8192
read(7, "a were clipped.  Typically, this"..., 8192) = 8192
read(7, "y.  The value\n\t    increases fro"..., 8192) = 8192
read(7, "e\n\t    last assigned numeric val"..., 8192) = 8192
read(7, "-4s\" ) \n\tNull  ( \"-\"  ) \n\tDescri"..., 8192) = 8192
read(7, "t is found by projecting the cov"..., 8192) = 8192
read(7, "at sxy = syx, etc.,\n\t    (x,y,z,"..., 8192) = 8192
read(7, "nformation for a tape.  \n\t}\n\t; \n"..., 8192) = 8192
read(7, "te\n\t    )\n\tPrimary ( chanid ) \n\t"..., 8192) = 8192
read(7, "ts given by mexpon (which see).\n"..., 8192) = 8192
read(7, "1lf\" )\n\tDescription (\"Rake of Se"..., 8192) = 8192
read(7, "nal digital signal processors ca"..., 8192) = 8192
brk(0x8a36000)                          = 0x8a36000
read(7, "puted from seismic array data.  "..., 8192) = 4173
read(7, "", 8192)                       = 0
ioctl(7, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0xbffce518) = -1 ENOTTY (Inappropriate ioctl for device)
close(7)                                = 0
access("/home/aln/Ftan/fmt/example/Seed2Db/Dbase/Colima.origin", F_OK) = 0
stat64("/home/aln/Ftan/fmt/example/Seed2Db/Dbase/Colima.origin", {st_mode=S_IFREG|0664, st_size=238, ...}) = 0
open("/home/aln/Ftan/fmt/example/Seed2Db/Dbase/Colima.origin", O_RDONLY) = 7
fstat64(7, {st_mode=S_IFREG|0664, st_size=238, ...}) = 0
mmap2(NULL, 238, PROT_READ, MAP_SHARED, 7, 0) = 0x41d7f000
fstat64(7, {st_mode=S_IFREG|0664, st_size=238, ...}) = 0
rt_sigaction(SIGILL, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGTRAP, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGABRT, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGFPE, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGUSR1, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGSEGV, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGUSR2, {0x8104409, [], SA_SIGINFO}, NULL, 8) = 0
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_ACCERR, si_addr=0x812a423} ---
open("/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 8
fstat64(8, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x41d80000
read(8, "# Locale name alias data base.\n#"..., 4096) = 2570
read(8, "", 4096)                       = 0
close(8)                                = 0
munmap(0x41d80000, 4096)                = 0
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "*** *fault*", 11*** *fault*)             = 11
write(2, ": ", 2: )                       = 2
write(2, "segmentation violation\n", 23segmentation violation
) = 23
write(2, "\t", 1    )                       = 1
write(2, "Inappropriate ioctl for device", 30Inappropriate ioctl for device) = 30
write(2, "\n", 1
)                       = 1
write(5, "@", 1)                        = 1
close(5)                                = 0
close(4)                                = 0
rt_sigaction(SIGCHLD, {SIG_DFL, [], SA_NOCLDSTOP}, {0x4120b940, [], SA_NOCLDSTOP}, 8) = 0
exit_group(1)                           = ?
+++ exited with 1 +++


```


gdb backtrace:
```

#0  0x08101914 in zstr2epoch (s=0xbfffc390 "1043201194.61000", e=0xbfffc360) at str2epoch.c:2164
#1  0x08101bc9 in str2epoch (s=0xbfffc390 "1043201194.61000") at str2epoch.c:2236
#2  0x080fafb1 in dbd2c ()
#3  0x080f7dd1 in dbgetv ()
#4  0x080c2153 in OpenOrigin ()
#5  0x080df1fb in NewDialog::getEventInfo() ()
#6  0x080df57f in NewDialog::browseOrigin() ()
#7  0x080f65c3 in NewDialog::qt_metacall(QMetaObject::Call, int, void**) ()
#8  0x411d0f3c in QMetaObject::activate (sender=0x82eebf0, from_signal_index=<optimized out>, 
    to_signal_index=30, argv=0x812a423) at kernel/qobject.cpp:3104
#9  0x411d1388 in QMetaObject::activate (sender=0x82eebf0, m=0x40ddc304 <QAbstractButton::staticMetaObject>, 
    from_local_signal_index=2, to_local_signal_index=3, argv=0xbfffd148) at kernel/qobject.cpp:3198
#10 0x40bfc101 in QAbstractButton::clicked (this=0x82eebf0, _t1=false)
    at .moc/release-shared/moc_qabstractbutton.cpp:200
#11 0x40927449 in QAbstractButtonPrivate::emitClicked (this=0x82eec80) at widgets/qabstractbutton.cpp:543
#12 0x40929094 in QAbstractButtonPrivate::click (this=0x82eec80) at widgets/qabstractbutton.cpp:536
#13 0x40929321 in QAbstractButton::mouseReleaseEvent (this=0x82eebf0, e=0xbfffd6f0)
    at widgets/qabstractbutton.cpp:1115
#14 0x405e9ca2 in QWidget::event (this=0x82eebf0, event=0xbfffd6f0) at kernel/qwidget.cpp:7554
#15 0x409272ee in QAbstractButton::event (this=0x82eebf0, e=0x1) at widgets/qabstractbutton.cpp:1077
#16 0x409d18ad in QPushButton::event (this=0x82eebf0, e=0xbfffd6f0) at widgets/qpushbutton.cpp:662
#17 0x40594cf4 in QApplicationPrivate::notify_helper (this=0x8162100, receiver=0x82eebf0, e=0xbfffd6f0)
    at kernel/qapplication.cpp:4065
#18 0x4059c888 in QApplication::notify (this=0xbffff1ec, receiver=0x82eebf0, e=0xbfffd6f0)
    at kernel/qapplication.cpp:3767
#19 0x411bb44b in QCoreApplication::notifyInternal (this=0xbffff1ec, receiver=0x82eebf0, event=0xbfffd6f0)
    at kernel/qcoreapplication.cpp:610
#20 0x4059b983 in sendSpontaneousEvent (event=<optimized out>, receiver=<optimized out>)
    at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:216
#21 QApplicationPrivate::sendMouseEvent (receiver=0x82eebf0, event=0xbfffd6f0, alienWidget=0x82eebf0, 
    nativeWidget=0xbfffdf0c, buttonDown=0x40de9100 <qt_button_down>, lastMouseReceiver=...)
    at kernel/qapplication.cpp:2924
#22 0x40608d28 in QETWidget::translateMouseEvent (this=0xbfffdf0c, event=0xbfffdc3c)
    at kernel/qapplication_x11.cpp:4411
#23 0x4060786c in QApplication::x11ProcessEvent (this=0xbffff1ec, event=0xbfffdc3c)
    at kernel/qapplication_x11.cpp:3430
#24 0x40631962 in x11EventSourceDispatch (s=0x8165e00, callback=0x0, user_data=0x0)
    at kernel/qguieventdispatcher_glib.cpp:146
#25 0x413141a3 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
#26 0x41314428 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#27 0x413144e8 in g_main_context_iteration () from /lib/i386-linux-gnu/libglib-2.0.so.0
#28 0x411e5fd7 in QEventDispatcherGlib::processEvents (this=0x8163768, flags=...)
    at kernel/qeventdispatcher_glib.cpp:330
#29 0x40631045 in QGuiEventDispatcherGlib::processEvents (this=0x8163768, flags=...)
---Type <return> to continue, or q <return> to quit---
    at kernel/qguieventdispatcher_glib.cpp:202
#30 0x411b99f9 in QEventLoop::processEvents (this=0xbfffdec0, 
    flags=<error reading variable: DWARF-2 expression error: DW_OP_reg operations must be used either alone or in conjunction with DW_OP_piece or DW_OP_bit_piece.>) at kernel/qeventloop.cpp:149
#31 0x411b9e4a in QEventLoop::exec (this=0xbfffdec0, flags=...) at kernel/qeventloop.cpp:201
#32 0x40a5b1d3 in QDialog::exec (this=0xbfffdf0c) at dialogs/qdialog.cpp:498
#33 0x0806fce6 in MainWindow::newLocation() ()
#34 0x080f41ed in MainWindow::qt_metacall(QMetaObject::Call, int, void**) ()
#35 0x411d0f3c in QMetaObject::activate (sender=0x81dd790, from_signal_index=<optimized out>, 
    to_signal_index=10, argv=0x812a423) at kernel/qobject.cpp:3104
#36 0x411d1388 in QMetaObject::activate (sender=0x81dd790, m=0x8149820 <QAction::staticMetaObject>, 
    from_local_signal_index=5, to_local_signal_index=6, argv=0xbfffe118) at kernel/qobject.cpp:3198
#37 0x4058e6bb in QAction::activated (this=0x81dd790, _t1=-2) at .moc/release-shared/moc_qaction.cpp:256
#38 0x4058fcbb in QAction::activate (this=0x81dd790, event=QAction::Trigger) at kernel/qaction.cpp:1170
#39 0x40a0e452 in trigger (this=<optimized out>) at ../../include/QtGui/../../src/gui/kernel/qaction.h:203
#40 QToolButton::nextCheckState (this=0x1) at widgets/qtoolbutton.cpp:1135
#41 0x40929053 in QAbstractButtonPrivate::click (this=0x8210688) at widgets/qabstractbutton.cpp:525
#42 0x40929321 in QAbstractButton::mouseReleaseEvent (this=0x81f5240, e=0xbfffe6f0)
    at widgets/qabstractbutton.cpp:1115
#43 0x40a0e94c in QToolButton::mouseReleaseEvent (this=0x81f5240, e=0xbfffe6f0) at widgets/qtoolbutton.cpp:709
#44 0x405e9ca2 in QWidget::event (this=0x81f5240, event=0xbfffe6f0) at kernel/qwidget.cpp:7554
#45 0x409272ee in QAbstractButton::event (this=0x81f5240, e=0x1) at widgets/qabstractbutton.cpp:1077
#46 0x40a1132a in QToolButton::event (this=0x81f5240, event=0xbfffe6f0) at widgets/qtoolbutton.cpp:1151
#47 0x40594cf4 in QApplicationPrivate::notify_helper (this=0x8162100, receiver=0x81f5240, e=0xbfffe6f0)
    at kernel/qapplication.cpp:4065
#48 0x4059c888 in QApplication::notify (this=0xbffff1ec, receiver=0x81f5240, e=0xbfffe6f0)
    at kernel/qapplication.cpp:3767
#49 0x411bb44b in QCoreApplication::notifyInternal (this=0xbffff1ec, receiver=0x81f5240, event=0xbfffe6f0)
    at kernel/qcoreapplication.cpp:610
#50 0x4059b983 in sendSpontaneousEvent (event=<optimized out>, receiver=<optimized out>)
    at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:216
#51 QApplicationPrivate::sendMouseEvent (receiver=0x81f5240, event=0xbfffe6f0, alienWidget=0x81f5240, 
    nativeWidget=0xbfffef44, buttonDown=0x40de9100 <qt_button_down>, lastMouseReceiver=...)
    at kernel/qapplication.cpp:2924
#52 0x40608d28 in QETWidget::translateMouseEvent (this=0xbfffef44, event=0xbfffec3c)
    at kernel/qapplication_x11.cpp:4411
#53 0x4060786c in QApplication::x11ProcessEvent (this=0xbffff1ec, event=0xbfffec3c)
    at kernel/qapplication_x11.cpp:3430
#54 0x40631962 in x11EventSourceDispatch (s=0x8165e00, callback=0x0, user_data=0x0)
    at kernel/qguieventdispatcher_glib.cpp:146
#55 0x413141a3 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
#56 0x41314428 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#57 0x413144e8 in g_main_context_iteration () from /lib/i386-linux-gnu/libglib-2.0.so.0
#58 0x411e5fd7 in QEventDispatcherGlib::processEvents (this=0x8163768, flags=...)
    at kernel/qeventdispatcher_glib.cpp:330
#59 0x40631045 in QGuiEventDispatcherGlib::processEvents (this=0x8163768, flags=...)
    at kernel/qguieventdispatcher_glib.cpp:202
#60 0x411b99f9 in QEventLoop::processEvents (this=0xbfffeec4, 
    flags=<error reading variable: DWARF-2 expression error: DW_OP_reg operations must be used either alone or in conjunction with DW_OP_piece or DW_OP_bit_piece.>) at kernel/qeventloop.cpp:149
#61 0x411b9e4a in QEventLoop::exec (this=0xbfffeec4, flags=...) at kernel/qeventloop.cpp:201
#62 0x411bc2bf in QCoreApplication::exec () at kernel/qcoreapplication.cpp:888
#63 0x40594b77 in QApplication::exec () at kernel/qapplication.cpp:3525
#64 0x0805c269 in main ()

```


ldd:
```
linux-gate.so.1 =>  (0x400f3000)
libQt3Support.so.4 => /usr/local/Trolltech/Qt-4.5.3/lib/libQt3Support.so.4 (0x400f6000)
libQtSql.so.4 => /usr/local/Trolltech/Qt-4.5.3/lib/libQtSql.so.4 (0x403e6000)
libQtXml.so.4 => /usr/local/Trolltech/Qt-4.5.3/lib/libQtXml.so.4 (0x40422000)
libQtNetwork.so.4 => /usr/local/Trolltech/Qt-4.5.3/lib/libQtNetwork.so.4 (0x40465000)
libQtGui.so.4 => /usr/local/Trolltech/Qt-4.5.3/lib/libQtGui.so.4 (0x40536000)
libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0x40ecf000)
libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0x40ef7000)
libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0x40f00000)
libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0x40f1a000)
libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0x40f26000)
libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0x40f61000)
libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0x41001000)
libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0x41014000)
libQtCore.so.4 => /usr/local/Trolltech/Qt-4.5.3/lib/libQtCore.so.4 (0x41148000)
libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0x4137f000)
libgthread-2.0.so.0 => /usr/lib/i386-linux-gnu/libgthread-2.0.so.0 (0x41399000)
libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0x4139c000)
librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0x414a8000)
libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x414b1000)
libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0x414b7000)
libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0x414d3000)
libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x415bb000)
libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0x41601000)
libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x4161e000)
libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0x417d0000)
libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0x417d6000)
libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0x417ff000)
libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0x41821000)
/lib/ld-linux.so.2 (0x800ae000)
libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0x41860000)
libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0x41864000)
```

---

### Post by TheFu on 2018-12-03
If it was once working, restore from the backup where everything worked and use that.

Also, you'll need to disable all networking for this VM.  It isn't safe to have unpatched computing devices on any network.  If you do this, you should be able to keep using the software with most of the biggest risks mitigated long after official support for 14,04 ends.  Sounds like that is the best you can hope for with this specific program.

---

### Post by kassandr on 2018-12-03
Unfortunately, I have already deleted the old VM image. The only way now is to install the software on a new clean system.

---

### Post by SagaciousKJB on 2018-12-16
Do you have the source for this program or are you using a binary?

Can you start a new project, save it successfully, and load it on the new system?

This is just a hunch, but I am thinking you might be trying to load data created by a 32-bit version of the program into a 64-bit version of it and that is causing problems.  I just noticed that you said you were using 32-bit before, and from your strace it appears you're trying to open it with a 64-bit version of the program now ( assuming you compiled it on the new cpu).

To test this you could compile a 32-bit version of the program using gcc-i386 OR you could download a 32-bit version of Ubuntu ( or can you? I'm not sure if they're still available )

---

