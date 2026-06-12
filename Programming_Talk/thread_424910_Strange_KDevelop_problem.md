---
title: "Strange KDevelop problem"
date: 2007-04-27
forum: Programming Talk
---

### Post by fxckkonka on 2007-04-27
My OS is xubuntu 7.04 whit newest kdevelop package installed.

if i enable subversion plugin, then kdevelop hangup at "loading project plugins"

and following is error msg:
---------------------------
QObject::connect: No such slot MakeWidget::slotDocumentOpened(const KURL&)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'make widget')
QLayout "unnamed" added to IndexView "unnamed", which already has a layout
WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig
kdecore (KAction): WARNING: KAction::initPrivate(): trying to assign a shortcut (Alt+Ctrl+Shift+N) to an unnamed action.
kdecore (KProcess): WARNING: _attachPty() 15
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
QObject::connect: No such signal KListBox::clicked(QListBoxItem*item)
QObject::connect:  (sender name:   'srcDistFileListBox')
QObject::connect:  (receiver name: 'dist_widget')
QObject::connect: No such slot GDBDebugger::GDBBreakpointWidget::slotAddBlankBreakpoint()
QObject::connect:  (sender name:   'gdbBreakpointWidget')
QObject::connect:  (receiver name: 'gdbBreakpointWidget')
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
QObject::connect: No such slot subversionPart::projectConfigWidget(KDialogBase*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'Subversion')
QObject::connect: No such slot subversionPart::slotStopButtonClicked(KDevPlugin*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'Subversion')
ASSERT: "part && parent" in /build/buildd/kdevelop-3.4.0/./parts/fileview/partwidget.cpp (41)
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error

---

### Post by kindlychung on 2009-04-11
Maybe you should try this: 

```
sudo aptitude install kdebase
```

---

