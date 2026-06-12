---
title: "problems with printdialog in java"
date: 2007-11-01
forum: Programming Talk
---

### Post by larsk on 2007-11-01
I am creating an application with Java 6 under Ubuntu 7.10 that will be able to print. But when I use the printDialog the program throws an exception under Ubuntu. But it works when I run the application under Windows 2000.
It works in both OS:s if I don't use printDialog.
Does anyone know what's wrong? Does linux os:s need extra treatment?


I get the following error under Ubuntu:

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException: null attribute
        at sun.print.IPPPrintService.isAttributeValueSupported(IPPPrintService.java:1147)
        at sun.print.ServiceDialog$OrientationPanel.updateInfo(ServiceDialog.java:2121)
        at sun.print.ServiceDialog$PageSetupPanel.updateInfo(ServiceDialog.java:1263)
        at sun.print.ServiceDialog.updatePanels(ServiceDialog.java:437)
        at sun.print.ServiceDialog.initPrintDialog(ServiceDialog.java:195)
        at sun.print.ServiceDialog.<init>(ServiceDialog.java:124)
        at javax.print.ServiceUI.printDialog(ServiceUI.java:188)
        at sun.print.RasterPrinterJob.printDialog(RasterPrinterJob.java:855)
        at sun.print.PSPrinterJob.printDialog(PSPrinterJob.java:421)
        at coverprinter.CoverToPrint.execute(CoverToPrint.java:23)
        at coverprinter.CoverPrinterUI.jButtonPrintMouseClicked(CoverPrinterUI.java:108)
        at coverprinter.CoverPrinterUI.access$000(CoverPrinterUI.java:8)
        at coverprinter.CoverPrinterUI$1.mouseClicked(CoverPrinterUI.java:37)
        at java.awt.AWTEventMulticaster.mouseClicked(AWTEventMulticaster.java:253)
        at java.awt.Component.processMouseEvent(Component.java:6041)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3995)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

---

### Post by ccfiel on 2007-11-06
yes i also have a problem with gutsy but it works in feisty. what is wrong with gutsy???

---

### Post by davidsarmstrong on 2007-11-07
I've got the same problem. I'll be checking [www.javasoft.com](www.javasoft.com) for references.

Dave

---

