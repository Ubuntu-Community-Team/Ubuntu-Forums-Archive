---
title: "[SOLVED] Eclipse exits for &amp;quot;SWT Error&amp;quot;"
date: 2008-05-19
forum: Programming Talk
---

### Post by tigerchan on 2008-05-19
Hi all,
My eclipse frequently exits complaining that an SWT error occurred. Actually I had done little before it happened, sometimes just editing. How to solve this? Thanks.

The following are some info about the environment:
ubuntu: 8.04
eclipse: 3.2.2
jdk: sun 1.6.0_06-b02

Detailed error log:
!SESSION 2008-05-19 15:02:40.794 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=zh_CN
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-05-19 15:02:42.202
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-05-19 15:02:42.206
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-05-19 15:02:42.206
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-05-19 15:02:42.206
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.ui 4 4 2008-05-19 15:03:03.085
!MESSAGE Unhandled event loop exception

!ENTRY org.eclipse.ui 4 0 2008-05-19 15:03:03.086
!MESSAGE XPCOM error -2147221164
!STACK 0
org.eclipse.swt.SWTError: XPCOM error -2147221164
	at org.eclipse.swt.browser.Browser.error(Browser.java:1382)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:1865)
	at org.eclipse.jdt.internal.ui.text.java.hover.BrowserInformationControl.setInformation(BrowserInformationControl.java:324)
	at org.eclipse.jface.text.AbstractInformationControlManager.internalShowInformationControl(AbstractInformationControlManager.java:860)
	at org.eclipse.jface.text.AbstractInformationControlManager.presentInformation(AbstractInformationControlManager.java:837)
	at org.eclipse.jface.text.AbstractHoverInformationControlManager.presentInformation(AbstractHoverInformationControlManager.java:502)
	at org.eclipse.jface.text.TextViewerHoverManager.doPresentInformation(TextViewerHoverManager.java:231)
	at org.eclipse.jface.text.TextViewerHoverManager$5.run(TextViewerHoverManager.java:221)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1930)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1894)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

---

### Post by jespdj on 2008-05-19
It's hard to say what's wrong. You could try starting Eclipse with the -clean option:
```
eclipse -clean
```
Or delete the hidden .eclipse (dot-eclipse) folder in your home directory before starting Eclipse (note, that will delete all your configuration settings).

---

### Post by tigerchan on 2008-05-19
The -clean option seems not work. The error info remains the same...

---

### Post by tigerchan on 2008-05-19
I just re-installed eclipse downloaded from eclipse.org and the new one works fine. Thanks.

---

