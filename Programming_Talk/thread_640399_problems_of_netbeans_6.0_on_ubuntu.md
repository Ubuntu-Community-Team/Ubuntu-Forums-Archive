---
title: "problems of netbeans 6.0 on ubuntu"
date: 2007-12-14
forum: Programming Talk
---

### Post by heizyuan on 2007-12-14
I ran into some problems in Netbeans 6.0 (stable release) on Ubuntu 7.10.

I created a new Desktop Application project and deleted the menu bar from the panel. The strange thing was that the codes relating to the menu bar had not been removed from the source files and as a result it could not pass the compiler.

And if I build and run the default project without any modifying, build was okay, but the following errors appeared when running the project:

init:
deps-jar:
compile:
run:
2007-12-14 19:26:12 org.jdesktop.application.Application create
Warning: Couldn't set LookandFeel Application.lookAndFeel = "system"
java.lang.NullPointerException
        at javax.swing.plaf.synth.SynthLookAndFeel$AATextListener.propertyChange(SynthLookAndFeel.java:793)
        at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:339)
        at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:347)
        at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:276)
        at java.awt.Toolkit.setDesktopProperty(Toolkit.java:1784)
        at sun.awt.SunToolkit.fireDesktopFontPropertyChanges(SunToolkit.java:1698)
        at sun.awt.SunToolkit.setAAFontSettingsCondition(SunToolkit.java:1743)
        at sun.swing.SwingUtilities2$AATextInfo.getAATextInfo(SwingUtilities2.java:119)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.initComponentDefaults(GTKLookAndFeel.java:1258)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.getDefaults(GTKLookAndFeel.java:294)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:537)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:581)
        at org.jdesktop.application.Application.create(Application.java:249)
        at org.jdesktop.application.Application$1.run(Application.java:169)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
2007-12-14 19:26:13 org.jdesktop.application.Application$1 run
Critical: Application class desktopapplication1.DesktopApplication1 failed to launch
java.lang.NullPointerException
        at javax.swing.MultiUIDefaults.getUIError(MultiUIDefaults.java:117)
        at javax.swing.UIDefaults.getUI(UIDefaults.java:741)
        at javax.swing.UIManager.getUI(UIManager.java:1012)
        at javax.swing.JPanel.updateUI(JPanel.java:109)
        at javax.swing.JPanel.<init>(JPanel.java:69)
        at javax.swing.JPanel.<init>(JPanel.java:92)
        at javax.swing.JPanel.<init>(JPanel.java:100)
        at desktopapplication1.DesktopApplication1View.initComponents(DesktopApplication1View.java:102)
        at desktopapplication1.DesktopApplication1View.<init>(DesktopApplication1View.java:27)
        at desktopapplication1.DesktopApplication1.startup(DesktopApplication1.java:19)
        at org.jdesktop.application.Application$1.run(Application.java:171)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.Error: Application class desktopapplication1.DesktopApplication1 failed to launch
        at org.jdesktop.application.Application$1.run(Application.java:177)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Caused by: java.lang.NullPointerException
        at javax.swing.MultiUIDefaults.getUIError(MultiUIDefaults.java:117)
        at javax.swing.UIDefaults.getUI(UIDefaults.java:741)
        at javax.swing.UIManager.getUI(UIManager.java:1012)
        at javax.swing.JPanel.updateUI(JPanel.java:109)
        at javax.swing.JPanel.<init>(JPanel.java:69)
        at javax.swing.JPanel.<init>(JPanel.java:92)
        at javax.swing.JPanel.<init>(JPanel.java:100)
        at desktopapplication1.DesktopApplication1View.initComponents(DesktopApplication1View.java:102)
        at desktopapplication1.DesktopApplication1View.<init>(DesktopApplication1View.java:27)
        at desktopapplication1.DesktopApplication1.startup(DesktopApplication1.java:19)
        at org.jdesktop.application.Application$1.run(Application.java:171)
        ... 8 more
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.initSystemColorDefaults(GTKLookAndFeel.java:1267)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.loadStyles(GTKLookAndFeel.java:1509)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.access$000(GTKLookAndFeel.java:37)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel$WeakPCL$1.run(GTKLookAndFeel.java:1449)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.initSystemColorDefaults(GTKLookAndFeel.java:1267)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.loadStyles(GTKLookAndFeel.java:1509)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel.access$000(GTKLookAndFeel.java:37)
        at com.sun.java.swing.plaf.gtk.GTKLookAndFeel$WeakPCL$1.run(GTKLookAndFeel.java:1449)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
BUILD SUCCESSFUL (total time: 2 seconds)

---

### Post by AZzKikR on 2007-12-14
Your application tries to set a look and feel which Swing can not find. It seems to be setting 'system', and it seems that is not a valid look and feel.

---

