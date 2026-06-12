---
title: "JVM terminated with eclipse 3.2"
date: 2007-12-31
forum: Programming Talk
---

### Post by hamvil on 2007-12-31
Hi,

I'm having some problem with eclipse. 

I've installed eclipse 3.2 from the gutsy repositories. Then I've installed some plugins using eclipse (WDT, etc).

However when I try to start a Dynamic Web project eclipse crashes after clicking the finish button. Before crashing i can see a pop-up that asks to accept the sun license for the web-app_2_4.xsd Schema.

I've followed many of the tips available on this forum:
- using update-alternatives or update-java-alternatives
- different jvm (1.5.0, 1.6.0)

So far I had no luck.

This is the error log:

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00000002, pid=7545, tid=3084532624
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  0x00000002
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x08059000):  JavaThread "main" [_thread_in_native, id=7546]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x00000002

Registers:
EAX=0x09f29e94, EBX=0xb3d549f0, ECX=0x08392474, EDX=0x09f29ee8
ESP=0xb7da183c, EBP=0xb7da1878, ESI=0x00000003, EDI=0x09fb79f8
EIP=0x00000002, CR2=0x00000002, EFLAGS=0x00210206

Top of Stack: (sp=0xb7da183c)
0xb7da183c:   b3d322df 09f29ee8 08392474 0a5e2120
0xb7da184c:   080db058 b3fe98e4 08392494 b7da1868
0xb7da185c:   b4085800 081922a0 00000000 09f29ee8
0xb7da186c:   b3d549f0 0a5e2120 08392460 b7da18f8
0xb7da187c:   b3d1d6b0 08392460 08392474 0a5e2120
0xb7da188c:   080db058 0a14e6a4 b7da18e8 b7da18cc
0xb7da189c:   b419d1ed b408b988 b7da18e8 b7da18e0
0xb7da18ac:   b7da18dc b7da18d8 b3d4e4b8 b7da18ec 

Instructions: (pc=0x00000002)
0xfffffff2:   

Stack: [0xb7d53000,0xb7da4000),  sp=0xb7da183c,  free space=314k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  0x00000002
C  [libdocshell.so+0x196b0]
C  [libdocshell.so+0x26598]
C  [libdocshell.so+0x2b15d]
C  [libdocshell.so+0x2b50c]
C  [libdocshell.so+0x2c2fd]
C  [libjar50.so+0xb5b0]
C  [libnecko.so+0x1e55d]
C  [libnecko.so+0x1f294]
C  [libxpcom_core.so+0x5476c]
C  [libxpcom_core.so+0x70b47]  PL_HandleEvent+0x27
C  [libxpcom_core.so+0x70e3b]  PL_ProcessPendingEvents+0x5b
C  [libxpcom_core.so+0x72fa8]
C  [libwidget_gtk2.so+0x14335]
C  [libglib-2.0.so.0+0x5e6ed]
C  [libglib-2.0.so.0+0x2f11c]  g_main_context_dispatch+0x17c
C  [libglib-2.0.so.0+0x3255f]
C  [libglib-2.0.so.0+0x32ac5]  g_main_context_iteration+0x65
C  [libswt-pi-gtk-3236.so+0x46ba5]  Java_org_eclipse_swt_internal_gtk_OS__1g_1main_1context_1iteration+0x25
J  org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(IZ)Z
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
j  org.eclipse.jface.window.Window.runEventLoop(Lorg/eclipse/swt/widgets/Shell;)V+23
j  org.eclipse.jface.window.Window.open()I+49
j  org.eclipse.wst.internet.cache.internal.LicenseAcceptanceDialog.promptForLicense(Lorg/eclipse/swt/widgets/Shell;Ljava/lang/String;Ljava/lang/String;)Z+135
j  org.eclipse.wst.internet.cache.internal.LicenseRegistry$1.run()V+9
j  org.eclipse.ui.internal.UILockListener.doPendingWork()V+27
j  org.eclipse.ui.internal.UISynchronizer$1.run()V+7
j  org.eclipse.swt.widgets.RunnableLock.run()V+11
j  org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Z)Z+29
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
j  org.eclipse.jface.operation.ModalContext$ModalContextThread.block()V+17
j  org.eclipse.jface.operation.ModalContext.run(Lorg/eclipse/jface/operation/IRunnableWithProgress;ZLorg/eclipse/core/runtime/IProgressMonitor;Lorg/eclipse/swt/widgets/Display;)V+123
j  org.eclipse.jface.wizard.WizardDialog.run(ZZLorg/eclipse/jface/operation/IRunnableWithProgress;)V+63
j  org.eclipse.wst.common.project.facet.ui.AddRemoveFacetsWizard.performFinish()Z+86
j  org.eclipse.wst.web.ui.internal.wizards.NewProjectDataModelFacetWizard.performFinish()Z+1
j  org.eclipse.jface.wizard.WizardDialog.finishPressed()V+4
j  org.eclipse.jface.wizard.WizardDialog.buttonPressed(I)V+54
j  org.eclipse.jface.dialogs.Dialog$3.widgetSelected(Lorg/eclipse/swt/events/SelectionEvent;)V+17
j  org.eclipse.swt.widgets.TypedListener.handleEvent(Lorg/eclipse/swt/widgets/Event;)V+198
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/Event;)V
j  org.eclipse.swt.widgets.Widget.sendEvent(Lorg/eclipse/swt/widgets/Event;)V+25
j  org.eclipse.swt.widgets.Display.runDeferredEvents()Z+84
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
j  org.eclipse.jface.window.Window.runEventLoop(Lorg/eclipse/swt/widgets/Shell;)V+23
j  org.eclipse.jface.window.Window.open()I+49
j  org.eclipse.ui.actions.NewProjectAction.run()V+169
j  org.eclipse.jface.action.Action.runWithEvent(Lorg/eclipse/swt/widgets/Event;)V+1
j  org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(Lorg/eclipse/swt/widgets/Event;Z)V+278
j  org.eclipse.jface.action.ActionContributionItem.access$2(Lorg/eclipse/jface/action/ActionContributionItem;Lorg/eclipse/swt/widgets/Event;Z)V+3
j  org.eclipse.jface.action.ActionContributionItem$5.handleEvent(Lorg/eclipse/swt/widgets/Event;)V+60
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/Event;)V
j  org.eclipse.swt.widgets.Widget.sendEvent(Lorg/eclipse/swt/widgets/Event;)V+25
j  org.eclipse.swt.widgets.Display.runDeferredEvents()Z+84
j  org.eclipse.swt.widgets.Display.readAndDispatch()Z+33
j  org.eclipse.ui.internal.Workbench.runEventLoop(Lorg/eclipse/jface/window/Window$IExceptionHandler;Lorg/eclipse/swt/widgets/Display;)V+9
j  org.eclipse.ui.internal.Workbench.runUI()I+225
j  org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor;)I+11
j  org.eclipse.ui.PlatformUI.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor;)I+2
j  org.eclipse.ui.internal.ide.IDEApplication.run(Ljava/lang/Object;)Ljava/lang/Object;+81
j  org.eclipse.core.internal.runtime.PlatformActivator$1.run(Ljava/lang/Object;)Ljava/lang/Object;+219
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Ljava/lang/Object;)Ljava/lang/Object;+103
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Ljava/lang/Object;)Ljava/lang/Object;+29
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run(Ljava/lang/Object;)Ljava/lang/Object;+105
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run([Ljava/lang/String;Ljava/lang/Runnable;)Ljava/lang/Object;+162
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20bc6d]
V  [libjvm.so+0x30a828]
V  [libjvm.so+0x20bb00]
V  [libjvm.so+0x33156f]
V  [libjvm.so+0x333f6c]
V  [libjvm.so+0x277c28]
C  [libjava.so+0x15224]  Java_sun_reflect_NativeMethodAccessorImpl_invoke0+0x34
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+161
j  org.eclipse.core.launcher.Main.invokeFramework([Ljava/lang/String;[Ljava/net/URL;)V+121
j  org.eclipse.core.launcher.Main.basicRun([Ljava/lang/String;)V+107
j  org.eclipse.core.launcher.Main.run([Ljava/lang/String;)I+4
j  org.eclipse.core.launcher.Main.main([Ljava/lang/String;)V+10
v  ~StubRoutines::call_stub
V  [libjvm.so+0x20bc6d]
V  [libjvm.so+0x30a828]
V  [libjvm.so+0x20bb00]
V  [libjvm.so+0x234f26]
V  [libjvm.so+0x2265cb]
C  [java+0x1b98]  JavaMain+0x2c8
C  [libpthread.so.0+0x546b]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(IZ)Z
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
j  org.eclipse.jface.window.Window.runEventLoop(Lorg/eclipse/swt/widgets/Shell;)V+23
j  org.eclipse.jface.window.Window.open()I+49
j  org.eclipse.wst.internet.cache.internal.LicenseAcceptanceDialog.promptForLicense(Lorg/eclipse/swt/widgets/Shell;Ljava/lang/String;Ljava/lang/String;)Z+135
j  org.eclipse.wst.internet.cache.internal.LicenseRegistry$1.run()V+9
j  org.eclipse.ui.internal.UILockListener.doPendingWork()V+27
j  org.eclipse.ui.internal.UISynchronizer$1.run()V+7
j  org.eclipse.swt.widgets.RunnableLock.run()V+11
j  org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Z)Z+29
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
j  org.eclipse.jface.operation.ModalContext$ModalContextThread.block()V+17
j  org.eclipse.jface.operation.ModalContext.run(Lorg/eclipse/jface/operation/IRunnableWithProgress;ZLorg/eclipse/core/runtime/IProgressMonitor;Lorg/eclipse/swt/widgets/Display;)V+123
j  org.eclipse.jface.wizard.WizardDialog.run(ZZLorg/eclipse/jface/operation/IRunnableWithProgress;)V+63
j  org.eclipse.wst.common.project.facet.ui.AddRemoveFacetsWizard.performFinish()Z+86
j  org.eclipse.wst.web.ui.internal.wizards.NewProjectDataModelFacetWizard.performFinish()Z+1
j  org.eclipse.jface.wizard.WizardDialog.finishPressed()V+4
j  org.eclipse.jface.wizard.WizardDialog.buttonPressed(I)V+54
j  org.eclipse.jface.dialogs.Dialog$3.widgetSelected(Lorg/eclipse/swt/events/SelectionEvent;)V+17
j  org.eclipse.swt.widgets.TypedListener.handleEvent(Lorg/eclipse/swt/widgets/Event;)V+198
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/Event;)V
j  org.eclipse.swt.widgets.Widget.sendEvent(Lorg/eclipse/swt/widgets/Event;)V+25
j  org.eclipse.swt.widgets.Display.runDeferredEvents()Z+84
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
j  org.eclipse.jface.window.Window.runEventLoop(Lorg/eclipse/swt/widgets/Shell;)V+23
j  org.eclipse.jface.window.Window.open()I+49
j  org.eclipse.ui.actions.NewProjectAction.run()V+169
j  org.eclipse.jface.action.Action.runWithEvent(Lorg/eclipse/swt/widgets/Event;)V+1
j  org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(Lorg/eclipse/swt/widgets/Event;Z)V+278
j  org.eclipse.jface.action.ActionContributionItem.access$2(Lorg/eclipse/jface/action/ActionContributionItem;Lorg/eclipse/swt/widgets/Event;Z)V+3
j  org.eclipse.jface.action.ActionContributionItem$5.handleEvent(Lorg/eclipse/swt/widgets/Event;)V+60
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/Event;)V
j  org.eclipse.swt.widgets.Widget.sendEvent(Lorg/eclipse/swt/widgets/Event;)V+25
j  org.eclipse.swt.widgets.Display.runDeferredEvents()Z+84
j  org.eclipse.swt.widgets.Display.readAndDispatch()Z+33
j  org.eclipse.ui.internal.Workbench.runEventLoop(Lorg/eclipse/jface/window/Window$IExceptionHandler;Lorg/eclipse/swt/widgets/Display;)V+9
j  org.eclipse.ui.internal.Workbench.runUI()I+225
j  org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor;)I+11
j  org.eclipse.ui.PlatformUI.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor;)I+2
j  org.eclipse.ui.internal.ide.IDEApplication.run(Ljava/lang/Object;)Ljava/lang/Object;+81
j  org.eclipse.core.internal.runtime.PlatformActivator$1.run(Ljava/lang/Object;)Ljava/lang/Object;+219
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Ljava/lang/Object;)Ljava/lang/Object;+103
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Ljava/lang/Object;)Ljava/lang/Object;+29
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run(Ljava/lang/Object;)Ljava/lang/Object;+105
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run([Ljava/lang/String;Ljava/lang/Runnable;)Ljava/lang/Object;+162
v  ~StubRoutines::call_stub
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+161
j  org.eclipse.core.launcher.Main.invokeFramework([Ljava/lang/String;[Ljava/net/URL;)V+121
j  org.eclipse.core.launcher.Main.basicRun([Ljava/lang/String;)V+107
j  org.eclipse.core.launcher.Main.run([Ljava/lang/String;)I+4
j  org.eclipse.core.launcher.Main.main([Ljava/lang/String;)V+10
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0a652000 JavaThread "ModalContext" [_thread_blocked, id=7569]
  0x0a2acc00 JavaThread "Worker-2" [_thread_blocked, id=7568]
  0x09c50000 JavaThread "Worker-1" [_thread_blocked, id=7567]
  0x09e69000 JavaThread "Java indexing" daemon [_thread_blocked, id=7563]
  0x09c30c00 JavaThread "Worker-0" [_thread_blocked, id=7559]
  0x082f1400 JavaThread "Start Level Event Dispatcher" daemon [_thread_blocked, id=7558]
  0x082f3000 JavaThread "Framework Event Dispatcher" daemon [_thread_blocked, id=7557]
  0x082f7800 JavaThread "State Data Manager" daemon [_thread_blocked, id=7556]
  0x0808e000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=7552]
  0x0808c800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=7551]
  0x0808b400 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=7550]
  0x08082400 JavaThread "Finalizer" daemon [_thread_blocked, id=7549]
  0x08081000 JavaThread "Reference Handler" daemon [_thread_blocked, id=7548]
=>0x08059000 JavaThread "main" [_thread_in_native, id=7546]

Other Threads:
  0x0807f800 VMThread [id=7547]
  0x0808fc00 WatcherThread [id=7553]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 2304K, used 1742K [0x8c070000, 0x8c2e0000, 0x8c550000)
  eden space 2112K,  75% used [0x8c070000, 0x8c1fea10, 0x8c280000)
  from space 192K,  77% used [0x8c280000, 0x8c2a4fa8, 0x8c2b0000)
  to   space 192K,   0% used [0x8c2b0000, 0x8c2b0000, 0x8c2e0000)
 tenured generation   total 29548K, used 17277K [0x8c550000, 0x8e22b000, 0x90070000)
   the space 29548K,  58% used [0x8c550000, 0x8d62f6f8, 0x8d62f800, 0x8e22b000)
 compacting perm gen  total 33536K, used 33289K [0x90070000, 0x92130000, 0x94070000)
   the space 33536K,  99% used [0x90070000, 0x920f2490, 0x920f2600, 0x92130000)
    ro space 8192K,  73% used [0x94070000, 0x94652560, 0x94652600, 0x94870000)
    rw space 12288K,  58% used [0x94870000, 0x94f67448, 0x94f67600, 0x95470000)

Dynamic libraries:
06000000-06417000 r-xp 00000000 08:05 146331     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so
06417000-06430000 rwxp 00417000 08:05 146331     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so
06430000-0684f000 rwxp 06430000 00:00 0 
08048000-08052000 r-xp 00000000 08:05 131067     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java
08052000-08053000 rwxp 00009000 08:05 131067     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/java
08053000-0a79a000 rwxp 08053000 00:00 0          [heap]
8c070000-8c2e0000 rwxp 8c070000 00:00 0 
8c2e0000-8c550000 rwxp 8c2e0000 00:00 0 
8c550000-8e22b000 rwxp 8c550000 00:00 0 
8e22b000-90070000 rwxp 8e22b000 00:00 0 
90070000-92130000 rwxp 90070000 00:00 0 
92130000-94070000 rwxp 92130000 00:00 0 
94070000-94653000 r-xs 00001000 08:05 146905     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
94653000-94870000 rwxp 94653000 00:00 0 
94870000-94f68000 rwxp 005e4000 08:05 146905     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
94f68000-95470000 rwxp 94f68000 00:00 0 
95470000-95549000 rwxp 00cdc000 08:05 146905     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
95549000-95870000 rwxp 95549000 00:00 0 
95870000-95874000 r-xs 00db5000 08:05 146905     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/classes.jsa
95874000-95c70000 rwxp 95874000 00:00 0 
af991000-af992000 ---p af991000 00:00 0 
af992000-b0192000 rwxp af992000 00:00 0 
b0192000-b0193000 ---p b0192000 00:00 0 
b0193000-b0993000 rwxp b0193000 00:00 0 
b0993000-b0a17000 r-xp 00000000 08:05 243956     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b0cf6000-b0d2b000 r-xp 00000000 08:05 1025934    /usr/lib/nss/libfreebl3.so
b0d2b000-b0d2c000 rwxp 00035000 08:05 1025934    /usr/lib/nss/libfreebl3.so
b0d2c000-b0d67000 r-xp 00000000 08:05 243960     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
b0d67000-b0d6f000 r-xs 00029000 08:05 458124     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.apache.xerces_2.8.0.v200606131651/xml-apis.jar
b0d6f000-b0d86000 r-xs 0010f000 08:05 458123     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.apache.xerces_2.8.0.v200606131651/xercesImpl.jar
b0d86000-b0d89000 rwxp b0d86000 00:00 0 
b0d89000-b0dd7000 rwxp b0d89000 00:00 0 
b0dd7000-b0dda000 rwxp b0dd7000 00:00 0 
b0dda000-b0e28000 rwxp b0dda000 00:00 0 
b0e28000-b0e2b000 rwxp b0e28000 00:00 0 
b0e2b000-b0e79000 rwxp b0e2b000 00:00 0 
b0e79000-b0e7c000 rwxp b0e79000 00:00 0 
b0e7c000-b0eca000 rwxp b0e7c000 00:00 0 
b0eca000-b0ecd000 rwxp b0eca000 00:00 0 
b0ecd000-b0f1b000 rwxp b0ecd000 00:00 0 
b0f1b000-b0f1d000 r-xp 00000000 08:05 457506     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/72/1/.cp/os/linux/x86/liblocalfile_1_0_0.so
b0f1d000-b0f1e000 rwxp 00001000 08:05 457506     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/72/1/.cp/os/linux/x86/liblocalfile_1_0_0.so
b0f1e000-b0f21000 ---p b0f1e000 00:00 0 
b0f21000-b0f6f000 rwxp b0f21000 00:00 0 
b0f6f000-b0fac000 r-xp 00000000 08:05 243961     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b0fac000-b0fb4000 r-xp 00000000 08:05 263762     /usr/share/locale-langpack/it/LC_MESSAGES/libgnome-2.0.mo
b0fb4000-b0fb5000 ---p b0fb4000 00:00 0 
b0fb5000-b17b5000 rwxp b0fb5000 00:00 0 
b17b5000-b17b6000 ---p b17b5000 00:00 0 
b17b6000-b1fb6000 rwxp b17b6000 00:00 0 
b1fb6000-b1fb7000 ---p b1fb6000 00:00 0 
b1fb7000-b27b7000 rwxp b1fb7000 00:00 0 
b27b7000-b27bb000 r-xp 00000000 08:05 97807      /usr/lib/firefox/components/libmozgnome.so
b27bb000-b27bc000 rwxp 00003000 08:05 97807      /usr/lib/firefox/components/libmozgnome.so
b27bc000-b27c0000 r-xp 00000000 08:05 98607      /usr/lib/firefox/components/libcommandlines.so
b27c0000-b27c1000 rwxp 00004000 08:05 98607      /usr/lib/firefox/components/libcommandlines.so
b27c1000-b27d5000 r-xp 00000000 08:05 98584      /usr/lib/firefox/components/libappcomps.so
b27d5000-b27d6000 rwxp 00014000 08:05 98584      /usr/lib/firefox/components/libappcomps.so
b27d6000-b2893000 r-xp 00000000 08:05 97831      /usr/lib/firefox/components/libuconv.so
b2893000-b2899000 rwxp 000bc000 08:05 97831      /usr/lib/firefox/components/libuconv.so
b2899000-b28a3000 rwxp b2899000 00:00 0 
b28a3000-b28b9000 r-xp 00000000 08:05 81384      /usr/lib/firefox/libjsj.so
b28b9000-b28ba000 rwxp 00016000 08:05 81384      /usr/lib/firefox/libjsj.so
b28ba000-b28ce000 r-xp 00000000 08:05 98571      /usr/lib/firefox/components/liboji.so
b28ce000-b28cf000 rwxp 00014000 08:05 98571      /usr/lib/firefox/components/liboji.so
b28cf000-b28e1000 r-xp 00000000 08:05 98637      /usr/lib/firefox/components/libuniversalchardet.so
b28e1000-b28eb000 rwxp 00012000 08:05 98637      /usr/lib/firefox/components/libuniversalchardet.so
b28eb000-b2e0e000 r-xp 00000000 08:05 98544      /usr/lib/firefox/components/libgklayout.so
b2e0e000-b2e6d000 rwxp 00522000 08:05 98544      /usr/lib/firefox/components/libgklayout.so
b2e6d000-b2e74000 rwxp b2e6d000 00:00 0 
b2e74000-b2e79000 r-xp 00000000 08:05 98635      /usr/lib/firefox/components/libsystem-pref.so
b2e79000-b2e7a000 rwxp 00004000 08:05 98635      /usr/lib/firefox/components/libsystem-pref.so
b2e7a000-b2ea4000 r-xp 00000000 08:05 98558      /usr/lib/firefox/components/libembedcomponents.so
b2ea4000-b2ea6000 rwxp 0002a000 08:05 98558      /usr/lib/firefox/components/libembedcomponents.so
b2ea6000-b2ed9000 r-xp 00000000 08:05 98620      /usr/lib/firefox/components/libxpinstall.so
b2ed9000-b2edc000 rwxp 00033000 08:05 98620      /usr/lib/firefox/components/libxpinstall.so
b2edc000-b2eea000 r-xp 00000000 08:05 98495      /usr/lib/firefox/components/libpref.so
b2eea000-b2eeb000 rwxp 0000e000 08:05 98495      /usr/lib/firefox/components/libpref.so
b2eeb000-b2fab000 r-xp 00000000 08:05 98487      /usr/lib/firefox/components/libnecko.so
b2fab000-b2fb3000 rwxp 000c0000 08:05 98487      /usr/lib/firefox/components/libnecko.so
b2fb3000-b3004000 r-xp 00000000 08:05 98636      /usr/lib/firefox/components/libtransformiix.so
b3004000-b3008000 rwxp 00050000 08:05 98636      /usr/lib/firefox/components/libtransformiix.so
b3008000-b3031000 r-xp 00000000 08:05 98509      /usr/lib/firefox/components/libgkplugin.so
b3031000-b3033000 rwxp 00028000 08:05 98509      /usr/lib/firefox/components/libgkplugin.so
b3033000-b3036000 r-xp 00000000 08:05 98649      /usr/lib/firefox/components/libbrowserdirprovider.so
b3036000-b3037000 rwxp 00002000 08:05 98649      /usr/lib/firefox/components/libbrowserdirprovider.so
b3037000-b306d000 r-xp 00000000 08:05 97840      /usr/lib/firefox/components/libi18n.so
b306d000-b3070000 rwxp 00035000 08:05 97840      /usr/lib/firefox/components/libi18n.so
b3070000-b3086000 r-xp 00000000 08:05 98569      /usr/lib/firefox/components/libnsappshell.so
b3086000-b3088000 rwxp 00015000 08:05 98569      /usr/lib/firefox/components/libnsappshell.so
b3088000-b309a000 r-xp 00000000 08:05 98567      /usr/lib/firefox/components/libcomposer.so
b309a000-b309c000 rwxp 00011000 08:05 98567      /usr/lib/firefox/components/libcomposer.so
b309c000-b30a3000 r-xp 00000000 08:05 98622      /usr/lib/firefox/components/libpipboot.so
b30a3000-b30a4000 rwxp 00006000 08:05 98622      /usr/lib/firefox/components/libpipboot.so
b30a4000-b30dc000 r-xp 00000000 08:05 98505      /usr/lib/firefox/components/libgfx_gtk.so
b30dc000-b30df000 rwxp 00038000 08:05 98505      /usr/lib/firefox/components/libgfx_gtk.so
b30df000-b3112000 r-xp 00000000 08:05 97841      /usr/lib/firefox/components/libmork.so
b3112000-b3115000 rwxp 00032000 08:05 97841      /usr/lib/firefox/components/libmork.so
b3115000-b314b000 r-xp 00000000 08:05 66801      /usr/lib/libhunspell-1.1.so.0.0.0
b314b000-b314f000 rwxp 00036000 08:05 66801      /usr/lib/libhunspell-1.1.so.0.0.0
b314f000-b3151000 r-xs 0000d000 08:05 458122     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.apache.xerces_2.8.0.v200606131651/resolver.jar
b3151000-b315b000 r-xp 00000000 08:05 98488      /usr/lib/firefox/components/libnecko2.so
b315b000-b315c000 rwxp 0000a000 08:05 98488      /usr/lib/firefox/components/libnecko2.so
b315c000-b3195000 r-xp 00000000 08:05 99077      /usr/lib/firefox/components/libbrowsercomps.so
b3195000-b3198000 rwxp 00038000 08:05 99077      /usr/lib/firefox/components/libbrowsercomps.so
b3198000-b31bc000 r-xp 00000000 08:05 98507      /usr/lib/firefox/components/libimglib2.so
b31bc000-b31be000 rwxp 00023000 08:05 98507      /usr/lib/firefox/components/libimglib2.so
b31be000-b3257000 r-xp 00000000 08:05 98563      /usr/lib/firefox/components/libeditor.so
b3257000-b325b000 rwxp 00099000 08:05 98563      /usr/lib/firefox/components/libeditor.so
b325b000-b32a4000 r-xp 00000000 08:05 67038      /usr/lib/libsoftokn3.so.0d
b32a4000-b32a8000 rwxp 00048000 08:05 67038      /usr/lib/libsoftokn3.so.0d
b32a8000-b3314000 r-xp 00000000 08:05 66915      /usr/lib/libnss3.so.0d
b3314000-b3319000 rwxp 0006c000 08:05 66915      /usr/lib/libnss3.so.0d
b3319000-b333a000 r-xp 00000000 08:05 67032      /usr/lib/libsmime3.so.0d
b333a000-b333c000 rwxp 00021000 08:05 67032      /usr/lib/libsmime3.so.0d
b333c000-b3361000 r-xp 00000000 08:05 67048      /usr/lib/libssl3.so.0d
b3361000-b3363000 rwxp 00024000 08:05 67048      /usr/lib/libssl3.so.0d
b3363000-b336a000 r-xp 00000000 08:05 98634      /usr/lib/firefox/components/libautoconfig.so
b336a000-b336b000 rwxp 00006000 08:05 98634      /usr/lib/firefox/components/libautoconfig.so
b336b000-b336f000 r-xp 00000000 08:05 98646      /usr/lib/firefox/components/libmyspell.so
b336f000-b3370000 rwxp 00004000 08:05 98646      /usr/lib/firefox/components/libmyspell.so
b3370000-b33ca000 r-xp 00000000 08:05 98623      /usr/lib/firefox/components/libpipnss.so
b33ca000-b33ce000 rwxp 0005a000 08:05 98623      /usr/lib/firefox/components/libpipnss.so
b33ce000-b33d1000 r-xp 00000000 08:05 98643      /usr/lib/firefox/components/libpermissions.so
b33d1000-b33d2000 rwxp 00002000 08:05 98643      /usr/lib/firefox/components/libpermissions.so
b33d2000-b33eb000 r-xp 00000000 08:05 81387      /usr/lib/firefox/libxpcom_compat.so
b33eb000-b33ec000 rwxp 00018000 08:05 81387      /usr/lib/firefox/libxpcom_compat.so
b33ec000-b33ed000 rwxp b33ec000 00:00 0 
b33ed000-b3410000 r-xp 00000000 08:05 98648      /usr/lib/firefox/components/libsearchservice.so
b3410000-b3411000 rwxp 00022000 08:05 98648      /usr/lib/firefox/components/libsearchservice.so
b3411000-b3418000 r-xp 00000000 08:05 98626      /usr/lib/firefox/components/libpippki.so
b3418000-b3419000 rwxp 00006000 08:05 98626      /usr/lib/firefox/components/libpippki.so
b3419000-b34da000 r-xp 00000000 08:05 66411      /usr/lib/libasound.so.2.0.0
b34da000-b34df000 rwxp 000c0000 08:05 66411      /usr/lib/libasound.so.2.0.0
b34df000-b34ff000 r-xp 00000000 08:05 66421      /usr/lib/libaudiofile.so.0.0.2
b34ff000-b3501000 rwxp 00020000 08:05 66421      /usr/lib/libaudiofile.so.0.0.2
b3501000-b350a000 r-xp 00000000 08:05 66537      /usr/lib/libesd.so.0.2.38
b350a000-b350b000 rwxp 00009000 08:05 66537      /usr/lib/libesd.so.0.2.38
b350b000-b3512000 r-xp 00000000 08:05 66568      /usr/lib/libgailutil.so.18.0.1
b3512000-b3513000 rwxp 00006000 08:05 66568      /usr/lib/libgailutil.so.18.0.1
b3513000-b3532000 r-xp 00000000 08:05 66832      /usr/lib/libjpeg.so.62.0.0
b3532000-b3533000 rwxp 0001e000 08:05 66832      /usr/lib/libjpeg.so.62.0.0
b3533000-b3540000 r-xp 00000000 08:05 66654      /usr/lib/libgnome-keyring.so.0.1.1
b3540000-b3541000 rwxp 0000d000 08:05 66654      /usr/lib/libgnome-keyring.so.0.1.1
b3541000-b3556000 r-xp 00000000 08:05 66409      /usr/lib/libart_lgpl_2.so.2.3.19
b3556000-b3557000 rwxp 00014000 08:05 66409      /usr/lib/libart_lgpl_2.so.2.3.19
b3557000-b356a000 r-xp 00000000 08:05 66442      /usr/lib/libbonobo-activation.so.4.0.0
b356a000-b356c000 rwxp 00013000 08:05 66442      /usr/lib/libbonobo-activation.so.4.0.0
b356c000-b35be000 r-xp 00000000 08:05 66440      /usr/lib/libbonobo-2.so.0.0.0
b35be000-b35c8000 rwxp 00051000 08:05 66440      /usr/lib/libbonobo-2.so.0.0.0
b35c8000-b35cf000 r-xp 00000000 08:05 1219314    /lib/libpopt.so.0.0.0
b35cf000-b35d0000 rwxp 00006000 08:05 1219314    /lib/libpopt.so.0.0.0
b35d0000-b35e4000 r-xp 00000000 08:05 66650      /usr/lib/libgnome-2.so.0.2000.0
b35e4000-b35e5000 rwxp 00014000 08:05 66650      /usr/lib/libgnome-2.so.0.2000.0
b35e5000-b3614000 r-xp 00000000 08:05 66664      /usr/lib/libgnomecanvas-2.so.0.2000.0
b3614000-b3615000 rwxp 0002f000 08:05 66664      /usr/lib/libgnomecanvas-2.so.0.2000.0
b3615000-b3670000 r-xp 00000000 08:05 66444      /usr/lib/libbonoboui-2.so.0.0.0
b3670000-b3673000 rwxp 0005a000 08:05 66444      /usr/lib/libbonoboui-2.so.0.0.0
b3673000-b36fb000 r-xp 00000000 08:05 65632      /usr/lib/libgnomeui-2.so.0.2000.1
b36fb000-b36ff000 rwxp 00087000 08:05 65632      /usr/lib/libgnomeui-2.so.0.2000.1
b3700000-b3705000 r-xp 00000000 08:05 97819      /usr/lib/firefox/components/libxpcom_compat_c.so
b3705000-b3706000 rwxp 00005000 08:05 97819      /usr/lib/firefox/components/libxpcom_compat_c.so
b3706000-b370b000 r-xp 00000000 08:05 98564      /usr/lib/firefox/components/libtxmgr.so
b370b000-b370c000 rwxp 00004000 08:05 98564      /usr/lib/firefox/components/libtxmgr.so
b370c000-b3713000 r-xp 00000000 08:05 97810      /usr/lib/firefox/components/libimgicon.so
b3713000-b3714000 rwxp 00007000 08:05 97810      /usr/lib/firefox/components/libimgicon.so
b3714000-b376b000 r-xp 00000000 08:05 97844      /usr/lib/firefox/components/libstoragecomps.so
b376b000-b376d000 rwxp 00057000 08:05 97844      /usr/lib/firefox/components/libstoragecomps.so
b376d000-b377c000 r-xp 00000000 08:05 98576      /usr/lib/firefox/components/libchrome.so
b377c000-b377d000 rwxp 0000f000 08:05 98576      /usr/lib/firefox/components/libchrome.so
b377d000-b37c8000 r-xp 00000000 08:05 97828      /usr/lib/firefox/components/libxpconnect.so
b37c8000-b37cc000 rwxp 0004b000 08:05 97828      /usr/lib/firefox/components/libxpconnect.so
b37cc000-b37dd000 r-xp 00000000 08:05 66365      /usr/lib/libXft.so.2.1.2
b37dd000-b37de000 rwxp 00010000 08:05 66365      /usr/lib/libXft.so.2.1.2
b37de000-b37df000 r-xp 00000000 08:05 98580      /usr/lib/firefox/components/libmozfind.so
b37df000-b37e0000 rwxp 00001000 08:05 98580      /usr/lib/firefox/components/libmozfind.so
b37e0000-b37e4000 r-xp 00000000 08:05 66330      /usr/lib/libORBitCosNaming-2.so.0.1.0
b37e4000-b37e5000 rwxp 00003000 08:05 66330      /usr/lib/libORBitCosNaming-2.so.0.1.0
b37e5000-b37ea000 r-xp 00000000 08:05 98632      /usr/lib/firefox/components/libxmlextras.so
b37ea000-b37eb000 rwxp 00004000 08:05 98632      /usr/lib/firefox/components/libxmlextras.so
b37eb000-b37ed000 r-xp 00000000 08:05 81380      /usr/lib/firefox/libgfxpsshar.so
b37ed000-b37ee000 rwxp 00001000 08:05 81380      /usr/lib/firefox/libgfxpsshar.so
b37ee000-b382e000 r-xp 00000000 08:05 98504      /usr/lib/firefox/components/libgfxps.so
b382e000-b3830000 rwxp 00040000 08:05 98504      /usr/lib/firefox/components/libgfxps.so
b3830000-b389a000 r-xp 00000000 08:05 98574      /usr/lib/firefox/components/libaccessibility.so
b389a000-b38ac000 rwxp 00069000 08:05 98574      /usr/lib/firefox/components/libaccessibility.so
b38ac000-b38f1000 r-xp 00000000 08:05 98610      /usr/lib/firefox/components/libtoolkitcomps.so
b38f1000-b38f4000 rwxp 00045000 08:05 98610      /usr/lib/firefox/components/libtoolkitcomps.so
b38f4000-b38fa000 r-xp 00000000 08:05 98586      /usr/lib/firefox/components/libfileview.so
b38fa000-b38fb000 rwxp 00005000 08:05 98586      /usr/lib/firefox/components/libfileview.so
b38fb000-b390c000 r-xp 00000000 08:05 98489      /usr/lib/firefox/components/libjar50.so
b390c000-b390e000 rwxp 00010000 08:05 98489      /usr/lib/firefox/components/libjar50.so
b390e000-b3935000 r-xp 00000000 08:05 98499      /usr/lib/firefox/components/librdf.so
b3935000-b3937000 rwxp 00026000 08:05 98499      /usr/lib/firefox/components/librdf.so
b3937000-b394a000 r-xp 00000000 08:05 97846      /usr/lib/firefox/components/libjsd.so
b394a000-b394b000 rwxp 00012000 08:05 97846      /usr/lib/firefox/components/libjsd.so
b394b000-b3981000 r-xp 00000000 08:05 1219325    /lib/libsepol.so.1
b3981000-b3982000 rwxp 00035000 08:05 1219325    /lib/libsepol.so.1
b3982000-b398c000 rwxp b3982000 00:00 0 
b398c000-b39db000 r-xp 00000000 08:05 66583      /usr/lib/libgcrypt.so.11.2.3
b39db000-b39dd000 rwxp 0004e000 08:05 66583      /usr/lib/libgcrypt.so.11.2.3
b39dd000-b39e0000 r-xp 00000000 08:05 66690      /usr/lib/libgpg-error.so.0.3.0
b39e0000-b39e1000 rwxp 00002000 08:05 66690      /usr/lib/libgpg-error.so.0.3.0
b39e1000-b39f0000 r-xp 00000000 08:05 67058      /usr/lib/libtasn1.so.3.0.9
b39f0000-b39f1000 rwxp 0000e000 08:05 67058      /usr/lib/libtasn1.so.3.0.9
b39f1000-b39f3000 r-xp 00000000 08:05 33542      /lib/tls/i686/cmov/libutil-2.6.1.so
b39f3000-b39f5000 rwxp 00001000 08:05 33542      /lib/tls/i686/cmov/libutil-2.6.1.so
b39f5000-b3a09000 r-xp 00000000 08:05 1219324    /lib/libselinux.so.1
b3a09000-b3a0b000 rwxp 00013000 08:05 1219324    /lib/libselinux.so.1
b3a0b000-b3a1a000 r-xp 00000000 08:05 33538      /lib/tls/i686/cmov/libresolv-2.6.1.so
b3a1a000-b3a1c000 rwxp 0000f000 08:05 33538      /lib/tls/i686/cmov/libresolv-2.6.1.so
b3a1c000-b3a1e000 rwxp b3a1c000 00:00 0 
b3a1e000-b3a2c000 r-xp 00000000 08:05 66423      /usr/lib/libavahi-client.so.3.2.2
b3a2c000-b3a2d000 rwxp 0000e000 08:05 66423      /usr/lib/libavahi-client.so.3.2.2
b3a2d000-b3a37000 r-xp 00000000 08:05 66425      /usr/lib/libavahi-common.so.3.4.4
b3a37000-b3a38000 rwxp 00009000 08:05 66425      /usr/lib/libavahi-common.so.3.4.4
b3a38000-b3a3a000 r-xp 00000000 08:05 66429      /usr/lib/libavahi-glib.so.1.0.1
b3a3a000-b3a3b000 rwxp 00001000 08:05 66429      /usr/lib/libavahi-glib.so.1.0.1
b3a3b000-b3aa5000 r-xp 00000000 08:05 66686      /usr/lib/libgnutls.so.13.3.0
b3aa5000-b3aab000 rwxp 0006a000 08:05 66686      /usr/lib/libgnutls.so.13.3.0
b3aab000-b3adf000 r-xp 00000000 08:05 66486      /usr/lib/libdbus-1.so.3.3.0
b3adf000-b3ae0000 rwxp 00033000 08:05 66486      /usr/lib/libdbus-1.so.3.3.0
b3ae0000-b3afa000 r-xp 00000000 08:05 66488      /usr/lib/libdbus-glib-1.so.2.1.0
b3afa000-b3afb000 rwxp 0001a000 08:05 66488      /usr/lib/libdbus-glib-1.so.2.1.0
b3afb000-b3c13000 r-xp 00000000 08:05 67116      /usr/lib/libxml2.so.2.6.30
b3c13000-b3c18000 rwxp 00118000 08:05 67116      /usr/lib/libxml2.so.2.6.30
b3c18000-b3c19000 rwxp b3c18000 00:00 0 
b3c19000-b3c62000 r-xp 00000000 08:05 66326      /usr/lib/libORBit-2.so.0.1.0
b3c62000-b3c6b000 rwxp 00049000 08:05 66326      /usr/lib/libORBit-2.so.0.1.0
b3c6b000-b3c6c000 rwxp b3c6b000 00:00 0 
b3c6c000-b3c9b000 r-xp 00000000 08:05 66581      /usr/lib/libgconf-2.so.4.1.2
b3c9b000-b3c9e000 rwxp 0002e000 08:05 66581      /usr/lib/libgconf-2.so.4.1.2
b3c9e000-b3cf4000 r-xp 00000000 08:05 66680      /usr/lib/libgnomevfs-2.so.0.2000.0
b3cf4000-b3cf7000 rwxp 00055000 08:05 66680      /usr/lib/libgnomevfs-2.so.0.2000.0
b3cf7000-b3cfa000 r-xp 00000000 08:05 98588      /usr/lib/firefox/components/libremoteservice.so
b3cfa000-b3cfb000 rwxp 00002000 08:05 98588      /usr/lib/firefox/components/libremoteservice.so
b3cfb000-b3d03000 r-xp 00000000 08:05 98627      /usr/lib/firefox/components/libcookie.so
b3d03000-b3d04000 rwxp 00007000 08:05 98627      /usr/lib/firefox/components/libcookie.so
b3d04000-b3d51000 r-xp 00000000 08:05 98547      /usr/lib/firefox/components/libdocshell.so
b3d51000-b3d55000 rwxp 0004d000 08:05 98547      /usr/lib/firefox/components/libdocshell.so
b3d55000-b3d64000 r-xp 00000000 08:05 98644      /usr/lib/firefox/components/libspellchecker.so
b3d64000-b3d65000 rwxp 0000f000 08:05 98644      /usr/lib/firefox/components/libspellchecker.so
b3d65000-b3dbe000 r-xp 00000000 08:05 98502      /usr/lib/firefox/components/libhtmlpars.so
b3dbe000-b3dc6000 rwxp 00058000 08:05 98502      /usr/lib/firefox/components/libhtmlpars.so
b3dc6000-b3dd9000 r-xp 00000000 08:05 98497      /usr/lib/firefox/components/libcaps.so
b3dd9000-b3dda000 rwxp 00013000 08:05 98497      /usr/lib/firefox/components/libcaps.so
b3dda000-b3def000 r-xp 00000000 08:05 66316      /usr/lib/libICE.so.6.3.0
b3def000-b3df1000 rwxp 00014000 08:05 66316      /usr/lib/libICE.so.6.3.0
b3df1000-b3df2000 rwxp b3df1000 00:00 0 
b3df2000-b3df9000 r-xp 00000000 08:05 66334      /usr/lib/libSM.so.6.0.0
b3df9000-b3dfa000 rwxp 00006000 08:05 66334      /usr/lib/libSM.so.6.0.0
b3dfa000-b3e47000 r-xp 00000000 08:05 66385      /usr/lib/libXt.so.6.0.0
b3e47000-b3e4b000 rwxp 0004c000 08:05 66385      /usr/lib/libXt.so.6.0.0
b3e4b000-b3e4c000 r-xp b3e4b000 00:00 0 
b3e4c000-b3e51000 r-xp 00000000 08:05 97809      /usr/lib/firefox/components/libnkgnomevfs.so
b3e51000-b3e52000 rwxp 00004000 08:05 97809      /usr/lib/firefox/components/libnkgnomevfs.so
b3e52000-b3e57000 r-xp 00000000 08:05 98642      /usr/lib/firefox/components/libauth.so
b3e57000-b3e58000 rwxp 00004000 08:05 98642      /usr/lib/firefox/components/libauth.so
b3e58000-b3e5b000 r-xp 00000000 08:05 81383      /usr/lib/firefox/libgtkxtbin.so
b3e5b000-b3e5c000 rwxp 00003000 08:05 81383      /usr/lib/firefox/libgtkxtbin.so
b3e5c000-b3e79000 r-xp 00000000 08:05 81381      /usr/lib/firefox/libgkgfx.so
b3e79000-b3e7b000 rwxp 0001c000 08:05 81381      /usr/lib/firefox/libgkgfx.so
b3e7b000-b3ea6000 r-xp 00000000 08:05 98529      /usr/lib/firefox/components/libwidget_gtk2.so
b3ea6000-b3eaa000 rwxp 0002b000 08:05 98529      /usr/lib/firefox/components/libwidget_gtk2.so
b3eaa000-b3f51000 r-xp 00000000 08:05 81385      /usr/lib/firefox/libmozjs.so
b3f51000-b3f56000 rwxp 000a7000 08:05 81385      /usr/lib/firefox/libmozjs.so
b3f56000-b3fca000 r-xp 00000000 08:05 98640      /usr/lib/firefox/components/libwebsrvcs.so
b3fca000-b3fd0000 rwxp 00074000 08:05 98640      /usr/lib/firefox/components/libwebsrvcs.so
b3fd0000-b3fe1000 r-xp 00000000 08:05 98560      /usr/lib/firefox/components/libwebbrwsr.so
b3fe1000-b3fe3000 rwxp 00010000 08:05 98560      /usr/lib/firefox/components/libwebbrwsr.so
b3fe3000-b4085000 r-xp 00000000 08:05 81388      /usr/lib/firefox/libxpcom_core.so
b4085000-b408d000 rwxp 000a1000 08:05 81388      /usr/lib/firefox/libxpcom_core.so
b408d000-b4097000 r-xp 00000000 08:05 1219267    /lib/libgcc_s.so.1
b4097000-b4098000 rwxp 0000a000 08:05 1219267    /lib/libgcc_s.so.1
b4098000-b4180000 r-xp 00000000 08:05 67052      /usr/lib/libstdc++.so.6.0.9
b4180000-b4183000 r-xp 000e8000 08:05 67052      /usr/lib/libstdc++.so.6.0.9
b4183000-b4185000 rwxp 000eb000 08:05 67052      /usr/lib/libstdc++.so.6.0.9
b4185000-b418b000 rwxp b4185000 00:00 0 
b418b000-b41b9000 r-xp 00000000 08:05 66914      /usr/lib/libnspr4.so.0d
b41b9000-b41ba000 rwxp 0002e000 08:05 66914      /usr/lib/libnspr4.so.0d
b41ba000-b41bc000 rwxp b41ba000 00:00 0 
b41bc000-b41c0000 r-xp 00000000 08:05 66967      /usr/lib/libplc4.so.0d
b41c0000-b41c1000 rwxp 00003000 08:05 66967      /usr/lib/libplc4.so.0d
b41c1000-b41c3000 r-xp 00000000 08:05 66968      /usr/lib/libplds4.so.0d
b41c3000-b41c4000 rwxp 00001000 08:05 66968      /usr/lib/libplds4.so.0d
b41c4000-b41cc000 r-xp 00000000 08:05 97832      /usr/lib/firefox/components/libucvmath.so
b41cc000-b41cd000 rwxp 00008000 08:05 97832      /usr/lib/firefox/components/libucvmath.so
b41cd000-b41cf000 r-xp 00000000 08:05 81795      /usr/lib/gconv/UTF-16.so
b41cf000-b41d1000 rwxp 00001000 08:05 81795      /usr/lib/gconv/UTF-16.so
b41d1000-b41d3000 r-xp 00000000 08:05 81386      /usr/lib/firefox/libxpcom.so
b41d3000-b41d4000 rwxp 00002000 08:05 81386      /usr/lib/firefox/libxpcom.so
b41d4000-b41e1000 r-xp 00000000 08:05 457106     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-mozilla-gtk-3236.so
b41e1000-b41e2000 rwxp 0000c000 08:05 457106     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-mozilla-gtk-3236.so
b41e2000-b41e4000 r-xs 00011000 08:05 130959     /usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.1.R321_v20060905/universal.jar
b41e4000-b41e7000 ---p b41e4000 00:00 0 
b41e7000-b4235000 rwxp b41e7000 00:00 0 
b4235000-b423c000 r-xs 00106000 08:05 132694     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/resources.jar
b423c000-b4247000 r-xp 00000000 08:05 457041     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-cairo-gtk-3236.so
b4247000-b4248000 rwxp 0000a000 08:05 457041     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-cairo-gtk-3236.so
b4248000-b424e000 r-xp 00000000 08:05 457040     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-atk-gtk-3236.so
b424e000-b424f000 rwxp 00006000 08:05 457040     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-atk-gtk-3236.so
b424f000-b4252000 r-xp 00000000 08:05 263783     /usr/share/locale-langpack/it/LC_MESSAGES/atk10.mo
b4252000-b42dd000 r-xp 00000000 08:05 243957     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b42dd000-b42df000 r-xp 00000000 08:05 98425      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b42df000-b42e0000 rwxp 00001000 08:05 98425      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b42e0000-b4340000 rwxs 00000000 00:09 2261007    /SYSV00000000 (deleted)
b4340000-b4343000 rwxs 00000000 00:09 2228238    /SYSV00000000 (deleted)
b4343000-b4346000 ---p b4343000 00:00 0 
b4346000-b4394000 rwxp b4346000 00:00 0 
b4394000-b439a000 r-xs 00000000 08:05 343605     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b439a000-b439d000 r-xs 00000000 08:05 343603     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b439d000-b43a1000 r-xs 00000000 08:05 343602     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b43a1000-b43a2000 r-xs 00000000 08:05 343601     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b43a2000-b43a3000 r-xs 00000000 08:05 343600     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b43a3000-b43a6000 r-xs 00000000 08:05 343599     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b43a6000-b43a7000 r-xs 00000000 08:05 343598     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b43a7000-b43aa000 r-xs 00000000 08:05 343597     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b43aa000-b43ac000 r-xs 00000000 08:05 343596     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b43ac000-b43b4000 r-xs 00000000 08:05 343595     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b43b4000-b43ba000 r-xs 00000000 08:05 343594     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b43ba000-b43bb000 r-xs 00000000 08:05 343593     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b43bb000-b43bd000 r-xs 00000000 08:05 343592     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b43bd000-b43c3000 r-xs 00000000 08:05 343591     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b43c3000-b43c7000 r-xs 00000000 08:05 343590     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b43c7000-b43c9000 r-xs 00000000 08:05 343584     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b43c9000-b43ca000 r-xs 00000000 08:05 347037     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b43ca000-b43cb000 r-xs 00000000 08:05 347036     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b43cb000-b43cc000 r-xs 00000000 08:05 347035     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b43cc000-b43cf000 r-xs 00000000 08:05 347034     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b43cf000-b43d2000 r-xs 00000000 08:05 347033     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b43d2000-b43d4000 r-xs 00000000 08:05 347032     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b43d4000-b43d5000 r-xs 00000000 08:05 347031     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b43d5000-b43d6000 r-xs 00000000 08:05 346999     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b43d6000-b43d7000 r-xs 00000000 08:05 346998     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b43d7000-b43dc000 r-xs 00000000 08:05 346865     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b43dc000-b43e1000 r-xs 00000000 08:05 346863     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b43e1000-b43e3000 r-xs 00000000 08:05 346860     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b43e3000-b43e6000 r-xs 00000000 08:05 346854     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b43e6000-b43e7000 r-xs 00000000 08:05 346853     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b43e7000-b43e8000 r-xs 00000000 08:05 346723     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b43e8000-b43eb000 r-xs 00000000 08:05 346720     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b43eb000-b43f1000 r-xs 00000000 08:05 346712     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b43f1000-b43f2000 r-xs 00000000 08:05 346710     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b43f2000-b43f6000 r-xs 00000000 08:05 346697     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b43f6000-b43f8000 r-xs 00000000 08:05 346694     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b43f8000-b43fc000 r-xs 00000000 08:05 346692     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b43fc000-b43ff000 ---p b43fc000 00:00 0 
b43ff000-b444d000 rwxp b43ff000 00:00 0 
b444d000-b4453000 r-xp 00000000 08:05 263758     /usr/share/locale-langpack/it/LC_MESSAGES/glib20.mo
b4453000-b44b3000 rwxs 00000000 00:09 2195469    /SYSV00000000 (deleted)
b44b3000-b44ce000 r-xp 00000000 08:05 264041     /usr/share/locale-langpack/it/LC_MESSAGES/libc.mo
b44ce000-b44f4000 r-xp 00000000 08:05 113899     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b44f4000-b44f5000 rwxp 00025000 08:05 113899     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b44f5000-b452d000 r-xp 00000000 08:05 457029     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-gtk-3236.so
b452d000-b452f000 rwxp 00037000 08:05 457029     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-gtk-3236.so
b452f000-b4530000 rwxp b452f000 00:00 0 
b4530000-b4531000 r-xp 00000000 08:05 81741      /usr/lib/gconv/ISO8859-1.so
b4531000-b4533000 rwxp 00000000 08:05 81741      /usr/lib/gconv/ISO8859-1.so
b4533000-b4558000 r-xp 00000000 08:05 263829     /usr/share/locale-langpack/it/LC_MESSAGES/gtk20-properties.mo
b4558000-b4569000 r-xp 00000000 08:05 263755     /usr/share/locale-langpack/it/LC_MESSAGES/gtk20.mo
b4569000-b4649000 r-xp 00000000 08:05 115386     /usr/lib/locale/it_IT.utf8/LC_COLLATE
b4649000-b4667000 r-xp 00000000 08:05 66546      /usr/lib/libexpat.so.1.0.0
b4667000-b4669000 rwxp 0001e000 08:05 66546      /usr/lib/libexpat.so.1.0.0
b4669000-b468b000 r-xp 00000000 08:05 65127      /usr/lib/libpng12.so.0.15.0
b468b000-b468c000 rwxp 00021000 08:05 65127      /usr/lib/libpng12.so.0.15.0
b468c000-b4690000 r-xp 00000000 08:05 66355      /usr/lib/libXdmcp.so.6.0.0
b4690000-b4691000 rwxp 00003000 08:05 66355      /usr/lib/libXdmcp.so.6.0.0
b4691000-b4693000 r-xp 00000000 08:05 66344      /usr/lib/libXau.so.6.0.0
b4693000-b4694000 rwxp 00001000 08:05 66344      /usr/lib/libXau.so.6.0.0
b4694000-b46a8000 r-xp 00000000 08:05 67122      /usr/lib/libz.so.1.2.3.3
b46a8000-b46a9000 rwxp 00013000 08:05 67122      /usr/lib/libz.so.1.2.3.3
b46a9000-b4715000 r-xp 00000000 08:05 66560      /usr/lib/libfreetype.so.6.3.16
b4715000-b4719000 rwxp 0006b000 08:05 66560      /usr/lib/libfreetype.so.6.3.16
b4719000-b4746000 r-xp 00000000 08:05 65144      /usr/lib/libpangoft2-1.0.so.0.1800.3
b4746000-b4747000 rwxp 0002c000 08:05 65144      /usr/lib/libpangoft2-1.0.so.0.1800.3
b4747000-b474f000 r-xp 00000000 08:05 66351      /usr/lib/libXcursor.so.1.0.2
b474f000-b4750000 rwxp 00007000 08:05 66351      /usr/lib/libXcursor.so.1.0.2
b4750000-b4755000 r-xp 00000000 08:05 66379      /usr/lib/libXrandr.so.2.1.0
b4755000-b4756000 rwxp 00005000 08:05 66379      /usr/lib/libXrandr.so.2.1.0
b4756000-b475d000 r-xp 00000000 08:05 66367      /usr/lib/libXi.so.6.0.0
b475d000-b475e000 rwxp 00006000 08:05 66367      /usr/lib/libXi.so.6.0.0
b475e000-b4760000 r-xp 00000000 08:05 66369      /usr/lib/libXinerama.so.1.0.0
b4760000-b4761000 rwxp 00001000 08:05 66369      /usr/lib/libXinerama.so.1.0.0
b4761000-b4768000 r-xp 00000000 08:05 66381      /usr/lib/libXrender.so.1.3.0
b4768000-b4769000 rwxp 00006000 08:05 66381      /usr/lib/libXrender.so.1.3.0
b4769000-b478c000 r-xp 00000000 08:05 66552      /usr/lib/libfontconfig.so.1.2.0
b478c000-b4794000 rwxp 00023000 08:05 66552      /usr/lib/libfontconfig.so.1.2.0
b4794000-b47a1000 r-xp 00000000 08:05 66359      /usr/lib/libXext.so.6.4.0
b47a1000-b47a2000 rwxp 0000d000 08:05 66359      /usr/lib/libXext.so.6.4.0
b47a2000-b4817000 r-xp 00000000 08:05 65131      /usr/lib/libcairo.so.2.11.5
b4817000-b4819000 rwxp 00074000 08:05 65131      /usr/lib/libcairo.so.2.11.5
b4819000-b48d5000 r-xp 00000000 08:05 66638      /usr/lib/libglib-2.0.so.0.1400.1
b48d5000-b48d6000 rwxp 000bc000 08:05 66638      /usr/lib/libglib-2.0.so.0.1400.1
b48d6000-b48d9000 r-xp 00000000 08:05 66648      /usr/lib/libgmodule-2.0.so.0.1400.1
b48d9000-b48da000 rwxp 00002000 08:05 66648      /usr/lib/libgmodule-2.0.so.0.1400.1
b48da000-b4914000 r-xp 00000000 08:05 66688      /usr/lib/libgobject-2.0.so.0.1400.1
b4914000-b4915000 rwxp 0003a000 08:05 66688      /usr/lib/libgobject-2.0.so.0.1400.1
b4915000-b492e000 r-xp 00000000 08:05 66417      /usr/lib/libatk-1.0.so.0.2009.1
b492e000-b4930000 rwxp 00018000 08:05 66417      /usr/lib/libatk-1.0.so.0.2009.1
b4930000-b4934000 r-xp 00000000 08:05 66361      /usr/lib/libXfixes.so.3.1.0
b4934000-b4935000 rwxp 00003000 08:05 66361      /usr/lib/libXfixes.so.3.1.0
b4935000-b4937000 r-xp 00000000 08:05 66353      /usr/lib/libXdamage.so.1.1.0
b4937000-b4938000 rwxp 00001000 08:05 66353      /usr/lib/libXdamage.so.1.1.0
b4938000-b493a000 r-xp 00000000 08:05 66349      /usr/lib/libXcomposite.so.1.0.0
b493a000-b493b000 rwxp 00001000 08:05 66349      /usr/lib/libXcomposite.so.1.0.0
b493b000-b4a28000 r-xp 00000000 08:05 66338      /usr/lib/libX11.so.6.2.0
b4a28000-b4a2c000 rwxp 000ed000 08:05 66338      /usr/lib/libX11.so.6.2.0
b4a2c000-b4a67000 r-xp 00000000 08:05 65141      /usr/lib/libpango-1.0.so.0.1800.3
b4a67000-b4a69000 rwxp 0003b000 08:05 65141      /usr/lib/libpango-1.0.so.0.1800.3
b4a69000-b4a71000 r-xp 00000000 08:05 65143      /usr/lib/libpangocairo-1.0.so.0.1800.3
b4a71000-b4a72000 rwxp 00007000 08:05 65143      /usr/lib/libpangocairo-1.0.so.0.1800.3
b4a72000-b4af6000 r-xp 00000000 08:05 66598      /usr/lib/libgdk-x11-2.0.so.0.1200.0
b4af6000-b4af9000 rwxp 00084000 08:05 66598      /usr/lib/libgdk-x11-2.0.so.0.1200.0
b4af9000-b4b10000 r-xp 00000000 08:05 66600      /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b4b10000-b4b11000 rwxp 00016000 08:05 66600      /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b4b11000-b4b15000 r-xp 00000000 08:05 66387      /usr/lib/libXtst.so.6.1.0
b4b15000-b4b16000 rwxp 00004000 08:05 66387      /usr/lib/libXtst.so.6.1.0
b4b16000-b4b1a000 r-xp 00000000 08:05 66750      /usr/lib/libgthread-2.0.so.0.1400.1
b4b1a000-b4b1b000 rwxp 00003000 08:05 66750      /usr/lib/libgthread-2.0.so.0.1400.1
b4b1b000-b4e98000 r-xp 00000000 08:05 66753      /usr/lib/libgtk-x11-2.0.so.0.1200.0
b4e98000-b4e9f000 rwxp 0037c000 08:05 66753      /usr/lib/libgtk-x11-2.0.so.0.1200.0
b4e9f000-b4ea0000 rwxp b4e9f000 00:00 0 
b4ea0000-b4ea3000 r-xs 00000000 08:05 346688     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b4ea3000-b4ea4000 r-xp 00000000 08:05 115150     /usr/lib/locale/it_IT.utf8/LC_NUMERIC
b4ea4000-b4ea5000 r-xp 00000000 08:05 167147     /usr/lib/locale/it_IT.utf8/LC_TIME
b4ea5000-b4ea6000 r-xp 00000000 08:05 115203     /usr/lib/locale/it_IT.utf8/LC_MONETARY
b4ea6000-b4ea7000 r-xp 00000000 08:05 130099     /usr/lib/locale/it_IT.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b4ea7000-b4ea8000 r-xp 00000000 08:05 115393     /usr/lib/locale/it_IT.utf8/LC_PAPER
b4ea8000-b4ea9000 r-xp 00000000 08:05 115127     /usr/lib/locale/it_IT.utf8/LC_NAME
b4ea9000-b4eaa000 r-xp 00000000 08:05 167149     /usr/lib/locale/it_IT.utf8/LC_ADDRESS
b4eaa000-b4eab000 r-xp 00000000 08:05 167150     /usr/lib/locale/it_IT.utf8/LC_TELEPHONE
b4eab000-b4eac000 r-xp 00000000 08:05 115389     /usr/lib/locale/it_IT.utf8/LC_MEASUREMENT
b4eac000-b4ead000 r-xp 00000000 08:05 167151     /usr/lib/locale/it_IT.utf8/LC_IDENTIFICATION
b4ead000-b4f05000 r-xp 00000000 08:05 457028     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-pi-gtk-3236.so
b4f05000-b4f07000 rwxp 00058000 08:05 457028     /home/hamvil/.eclipse/org.eclipse.platform_3.2.0/configuration/org.eclipse.osgi/bundles/62/1/.cp/libswt-pi-gtk-3236.so
b4f07000-b4f08000 r-xs 00000000 08:05 132656     /usr/lib/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.2.0.I20060605-1400/compatibility.jar
b4f08000-b4f0a000 r-xs 00003000 08:05 458085     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.xsd.ecore.importer_2.2.0.v200702131851.jar
b4f0a000-b4f14000 r-xs 0006c000 08:05 459316     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.css.core_1.1.1.v200609140550.jar
b4f14000-b4f16000 r-xs 00006000 08:05 459859     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.axis.ui.doc.user_1.0.203.v200609221649.jar
b4f16000-b4f18000 r-xs 00006000 08:05 459215     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.dtdeditor.doc.user_1.0.203.v200609221649.jar
b4f18000-b4f1a000 r-xs 0000d000 08:05 459734     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.ui_1.0.104.v20070401b.jar
b4f1a000-b4f1b000 r-xs 00004000 08:05 459295     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.ws.ui_1.0.103.v200704042036.jar
b4f1b000-b4f1f000 r-xs 00027000 08:05 459268     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsdl.validation_1.1.102.v200704111356.jar
b4f1f000-b4f23000 r-xs 00033000 08:05 458064     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.edit_2.2.2.v200702131851.jar
b4f23000-b4f24000 r-xs 00002000 08:05 459634     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.db2.iseries_1.0.106.v200704191851.jar
b4f24000-b4f28000 r-xs 00017000 08:05 459716     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.jca_1.1.4.v200704161800.jar
b4f28000-b4f2b000 r-xs 00015000 08:05 459174     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.validation.ui_1.1.2.v200612061436.jar
b4f2b000-b4f2d000 r-xs 0000a000 08:05 459645     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.mysql_1.0.105.v200703122014.jar
b4f2d000-b4f2f000 r-xs 00009000 08:05 459877     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.axis.consumption.core_1.0.104.v200704200400.jar
b4f2f000-b4f31000 r-xs 0001c000 08:05 459218     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xsdeditor.doc.user_1.0.203.v200609221649.jar
b4f31000-b4f33000 r-xs 00002000 08:05 459642     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.sqlserver_1.0.105.v200610161905.jar
b4f33000-b4f35000 r-xs 00012000 08:05 459705     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.equinox.servlet.api_1.0.0.v20060601.jar
b4f35000-b4f37000 r-xs 0000d000 08:05 459229     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xsd.core_1.1.101.v200701312359.jar
b4f37000-b4f3a000 r-xs 00018000 08:05 459150     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.frameworks_1.1.4.v200704191600.jar
b4f3a000-b4f3c000 r-xs 0000b000 08:05 459360     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.data.core_1.0.108.v200703122014.jar
b4f3c000-b4f3f000 r-xs 00018000 08:05 458013     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/com.ibm.etools.emf.event_3.0.0.v20060918_M.jar
b4f3f000-b4f40000 r-xs 00002000 08:05 459892     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.infopop_1.0.202.v200609150300.jar
b4f40000-b4f41000 r-xs 0000b000 08:05 459857     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ejb.doc.user_1.0.203.v200609221649.jar
b4f41000-b4f44000 r-xs 0000f000 08:05 458029     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve.propertysheet_1.2.0.v20060824_M.jar
b4f44000-b4f46000 r-xs 00026000 08:05 459359     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.models.dbdefinition_1.0.103.v200702062139.jar
b4f46000-b4f48000 r-xs 000bd000 08:05 459306     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.doc.user_1.0.203.v200608231821.jar
b4f48000-b4f49000 r-xs 00005000 08:05 458089     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.xsd2ecore_2.1.0.v200702131851.jar
b4f49000-b4f4b000 r-xs 00005000 08:05 458090     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.xsd2ecore.editor_2.1.0.v200702131851.jar
b4f4b000-b4f51000 r-xs 00038000 08:05 459194     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.server.core_1.0.106.v20070401b.jar
b4f51000-b4f54000 r-xs 00016000 08:05 459307     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.webtools.doc.user_1.0.203.v200609221649.jar
b4f54000-b4f55000 r-xs 00002000 08:05 459655     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst_1.0.1.v200605040144.jar
b4f55000-b4f56000 r-xs 00000000 08:05 459331     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.web.ui.infopop_1.0.201.v200605070230.jar
b4f56000-b4f57000 r-xs 00001000 08:05 459345     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.datatools.fe.ui.doc.user_1.0.203.v200608310305.jar
b4f57000-b4f58000 r-xs 00000000 08:05 459896     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.infopop_1.0.201.v200605162034.jar
b4f58000-b4f5a000 r-xs 0001c000 08:05 459217     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xmleditor.doc.user_1.0.203.v200609221649.jar
b4f5a000-b4f5b000 r-xs 00001000 08:05 459848     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.jsp.ui.infopop_1.0.2.v200605040115.jar
b4f5b000-b4f5d000 r-xs 00007000 08:05 458068     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.ecore2ecore_2.2.0.v200702131851.jar
b4f5d000-b4f5e000 r-xs 00001000 08:05 459205     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.server.ui.infopop_1.0.3.v200609140551.jar
b4f5e000-b4f61000 r-xs 0000a000 08:05 459147     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.command.env.core_1.0.103.v200704200400.jar
b4f61000-b4f74000 r-xs 001b9000 08:05 458028     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve.jfc_1.2.1.v20060918_M.jar
b4f74000-b4f76000 r-xs 00012000 08:05 459673     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.core_1.0.106.v20070412.jar
b4f76000-b4f78000 r-xs 00003000 08:05 459698     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.common.annotations.core_1.1.1.v200609132124.jar
b4f78000-b4f7b000 r-xs 0002b000 08:05 459154     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.validation_1.1.4.v200704161800.jar
b4f7b000-b4f80000 r-xs 00027000 08:05 458066     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping_2.2.0.v200702131851.jar
b4f80000-b4f8f000 r-xs 000b6000 08:05 459269     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsi_1.0.104.v200702021430.jar
b4f8f000-b4f93000 r-xs 00024000 08:05 459374     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.connection.ui_1.0.107.v200703122014.jar
b4f93000-b4f94000 r-xs 00006000 08:05 459636     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.db2.zseries_1.0.107.v200704121755.jar
b4f94000-b4f98000 r-xs 0001b000 08:05 459165     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.frameworks.ui_1.1.2.v200702071605.jar
b4f98000-b4f99000 r-xs 00000000 08:05 459370     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.fe.ui.infopop_1.0.0.v200605040131.jar
b4f99000-b4f9a000 r-xs 00000000 08:05 459166     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.infopop_1.0.1.v200605270041.jar
b4f9a000-b4f9d000 r-xs 00014000 08:05 458015     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jem.util_1.2.1.v20060918_M.jar
b4f9d000-b4fa9000 r-xs 000ad000 08:05 458058     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore_2.2.2.v200702131851.jar
b4fa9000-b4faa000 r-xs 00004000 08:05 459641     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.oracle_1.0.104.v200704102203.jar
b4faa000-b4fac000 r-xs 00008000 08:05 459879     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.ui_1.0.102.v200704041932.jar
b4fac000-b4fb2000 r-xs 00037000 08:05 459714     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.webservice_1.1.4.v200704161800.jar
b4fb2000-b4fb3000 r-xs 00008000 08:05 458075     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.importer.java_2.2.1.v200702131851.jar
b4fb3000-b4fb9000 r-xs 0003c000 08:05 458011     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jem_1.2.1.v20060918_M.jar
b4fb9000-b4fc2000 r-xs 0006e000 08:05 459702     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.jsp.core_1.1.104.v200704191900.jar
b4fc2000-b4fc3000 r-xs 00003000 08:05 459347     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.sqleditor.doc.user_1.0.2.v200608310308.jar
b4fc3000-b4fc8000 r-xs 0002c000 08:05 459265     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.ws_1.0.102.v200702021949.jar
b4fc8000-b4fcb000 r-xs 00027000 08:05 458063     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.xmi_2.2.2.v200702131851.jar
b4fcb000-b4fe9000 r-xs 00185000 08:05 459703     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.core_1.1.53.v200704191600.jar
b4fe9000-b4feb000 r-xs 00001000 08:05 459895     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.consumption.infopop_1.0.202.v20070131.jar
b4feb000-b4fed000 r-xs 0000e000 08:05 459725     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.ui.doc.user_1.0.203.v200609221649.jar
b4fed000-b4fef000 r-xs 00027000 08:05 458098     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.sdo_2.2.1.v200702131851.jar
b4fef000-b4ff5000 r-xs 00047000 08:05 459701     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.web_1.1.3.v200701242244.jar
b4ff5000-b4ff7000 r-xs 00008000 08:05 459149     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.environment_1.0.100.v200608251934.jar
b4ff7000-b4ff8000 r-xs 00001000 08:05 458097     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.commonj.sdo_2.1.0.v200702131851.jar
b4ff8000-b4ff9000 r-xs 00001000 08:05 459329     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.html.ui.infopop_1.0.1.v200605040131.jar
b4ff9000-b5006000 r-xs 0007c000 08:05 459317     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.html.core_1.1.2.v200612200820.jar
b5006000-b500f000 r-xs 0008a000 08:05 459358     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.models.sql_1.0.104.v200612130213.jar
b500f000-b5010000 r-xs 00000000 08:05 459829     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.installable_1.5.2.v20061018.jar
b5010000-b5015000 r-xs 00026000 08:05 459239     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.dtd.ui_1.0.102.v200702021750.jar
b5015000-b501a000 r-xs 0002c000 08:05 459332     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.css.ui_1.0.101.v200609140550.jar
b501a000-b501b000 r-xs 00001000 08:05 459484     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.fe.ui.actions_1.0.103.v200612130213.jar
b501b000-b501f000 r-xs 00016000 08:05 459170     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.ui.properties_1.0.101.v200609140551.jar
b501f000-b5022000 r-xs 00015000 08:05 459204     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.internet.monitor.ui_1.0.103.v20060809.jar
b5022000-b5023000 r-xs 00000000 08:05 459278     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.ws.infopop_1.0.202.v20070131.jar
b5023000-b5026000 r-xs 00011000 08:05 459873     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.axis.consumption.ui_1.0.103.v200704200400.jar
b5026000-b5028000 r-xs 00007000 08:05 459903     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.xdoclet.runtime_1.1.1.v200609140551.jar
b5028000-b502a000 r-xs 0000b000 08:05 459318     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.javascript.core_1.0.1.v200609140550.jar
b502a000-b5032000 r-xs 00058000 08:05 459228     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.dtd.core_1.1.1.v200609210600.jar
b5032000-b504e000 r-xs 00177000 08:05 458027     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve.java.core_1.2.1.v20060918_M.jar
b504e000-b5050000 r-xs 00012000 08:05 459254     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsdl.ui.doc.user_1.0.203.v200609221649.jar
b5050000-b5052000 r-xs 00004000 08:05 459874     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.jca.ui_1.1.1.v200609132124.jar
b5052000-b5055000 r-xs 0000d000 08:05 459297     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsi.ui_1.0.101.v20060850312.jar
b5055000-b505d000 r-xs 00044000 08:05 459847     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.jsp.ui_1.1.100.v200608142042.jar
b505d000-b505e000 r-xs 00000000 08:05 459371     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.outputview.infopop_1.0.0.v200605040131.jar
b505e000-b5060000 r-xs 0000b000 08:05 459900     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.ejb.annotation.model_1.1.1.v200609140551.jar
b5060000-b5061000 r-xs 00001000 08:05 459241     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.sse.ui.infopop_1.0.101.v200605040131.jar
b5061000-b5064000 r-xs 0000c000 08:05 459195     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.internet.monitor.core_1.0.103.v20060809.jar
b5064000-b5067000 r-xs 00013000 08:05 459482     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.data.ui_1.0.111.v200703122014.jar
b5067000-b5068000 r-xs 00005000 08:05 459639     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.informix_1.0.104.v200610261819.jar
b5068000-b506d000 r-xs 0002c000 08:05 458087     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.xsd.edit_2.2.1.v200702131851.jar
b506d000-b5071000 r-xs 00023000 08:05 458056     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.common_2.2.1.v200702131851.jar
b5071000-b5075000 r-xs 00037000 08:05 459715     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.ejb_1.1.4.v200704261800.jar
b5075000-b5077000 r-xs 00010000 08:05 458061     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.change_2.2.1.v200702131851.jar
b5077000-b5080000 r-xs 0006e000 08:05 458040     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.draw2d_3.2.2.v20070208.jar
b5080000-b5081000 r-xs 00003000 08:05 458074     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.importer.ecore_2.2.0.v200702131851.jar
b5081000-b5083000 r-xs 0000b000 08:05 458077     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.exporter_2.2.0.v200702131851.jar
b5083000-b5085000 r-xs 0000b000 08:05 459335     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.web.ui_1.1.1.v200609132124.jar
b5085000-b5087000 r-xs 0000e000 08:05 458073     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.importer_2.2.2.v200702131851.jar
b5087000-b5088000 r-xs 00000000 08:05 459372     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.server.ui.infopop_1.0.0.v200605040131.jar
b5088000-b5089000 r-xs 00001000 08:05 459893     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.servlet.ui.infopop_1.0.201.v200606130315.jar
b5089000-b508b000 r-xs 00008000 08:05 459699     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.common.annotations.controller_1.1.1.v200609132124.jar
b508b000-b508c000 r-xs 00006000 08:05 459256     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.command.env.doc.user_1.5.0.v20060831345.jar
b508c000-b508e000 r-xs 00024000 08:05 459858     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.doc.user_1.0.203.v200609182036.jar
b508e000-b5092000 r-xs 0001f000 08:05 459875     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.navigator.ui_1.1.2.v200702021430.jar
b5092000-b5096000 r-xs 0001b000 08:05 459169     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.ui_1.1.101.v200702021750.jar
b5096000-b5098000 r-xs 00001000 08:05 458050     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf_2.2.0.v200702131851.jar
b5098000-b509a000 r-xs 00004000 08:05 459348     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.datatools.data.ui.doc.user_1.0.203.v200608310305.jar
b509a000-b509c000 r-xs 00007000 08:05 459171     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.internet.proxy_1.0.101.v200702021949.jar
b509c000-b509d000 r-xs 00004000 08:05 458051     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ant_2.2.0.v200702131851.jar
b509d000-b509f000 r-xs 0000f000 08:05 458012     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jem.workbench_1.2.1.v20060918_M.jar
b509f000-b50a1000 r-xs 00005000 08:05 458053     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.codegen.ui_2.1.0.v200702131851.jar
b50a1000-b50a4000 r-xs 00010000 08:05 458059     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.edit_2.2.0.v200702131851.jar
b50a4000-b50b4000 r-xs 000ab000 08:05 459296     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsdl.ui_1.1.102.v200704192000.jar
b50b4000-b50b8000 r-xs 00017000 08:05 459878     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.servlet.ui_1.1.2.v200702021430.jar
b50b8000-b50bf000 r-xs 000b7000 08:05 458054     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.codegen.ecore_2.2.2.v200702131851.jar
b50bf000-b50c0000 r-xs 00001000 08:05 459894     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.axis.infopop_1.0.201.v200605152241.jar
b50c0000-b50c3000 r-xs 00038000 08:05 459881     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.creation.ui_1.0.105.v200704041932.jar
b50c3000-b50c8000 r-xs 00023000 08:05 459611     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.server.ui_1.0.111.v200703122014.jar
b50c8000-b50ca000 r-xs 00019000 08:05 458055     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.codegen.ecore.ui_2.2.1.v200702131851.jar
b50ca000-b50cd000 r-xs 0000c000 08:05 459700     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.common.frameworks_1.1.4.v200702021430.jar
b50cd000-b50cf000 r-xs 00002000 08:05 459643     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.sybase_1.0.106.v200610261819.jar
b50cf000-b50d1000 r-xs 00001000 08:05 459640     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.mysql_1.0.101.v200610161905.jar
b50d1000-b50d2000 r-xs 00005000 08:05 458062     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.change.edit_2.2.0.v200702131851.jar
b50d2000-b50d3000 r-xs 00000000 08:05 459175     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.command.env.infopop_1.0.2.v200605070230.jar
b50d3000-b50d4000 r-xs 00005000 08:05 458099     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.sdo.edit_2.2.0.v200702131851.jar
b50d4000-b50d8000 r-xs 00023000 08:05 459357     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.core_1.1.121.v200704131847.jar
b50d8000-b50f4000 r-xs 00142000 08:05 459704     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee_1.1.4.v200704261800.jar
b50f4000-b50f8000 r-xs 0001c000 08:05 459130     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.emfworkbench.integration_1.1.4.v200704111300.jar
b50f8000-b50fc000 r-xs 0001f000 08:05 459674     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.generic.core_1.0.101.v200608301011.jar
b50fc000-b5101000 r-xs 00034000 08:05 459898     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ejb.ui_1.1.1.v200609132124.jar
b5101000-b5106000 r-xs 0002a000 08:05 459333     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.html.ui_1.0.102.v200702021750.jar
b5106000-b5108000 r-xs 00013000 08:05 458071     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.ecore2xml.ui_2.2.0.v200702131851.jar
b5108000-b510a000 r-xs 0000b000 08:05 459319     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.web_1.1.2.v200610182223.jar
b510a000-b510c000 r-xs 00012000 08:05 459746     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.tomcat.ui_1.0.103.v20060906.jar
b510c000-b510e000 r-xs 00016000 08:05 458076     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.importer.rose_2.2.0.v200702131851.jar
b510e000-b5111000 r-xs 00017000 08:05 459185     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.server.ui.doc.user_1.0.203.v200609221649.jar
b5111000-b5118000 r-xs 000a6000 08:05 458084     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.xsd_2.2.2.v200702131851.jar
b5118000-b511c000 r-xs 0001d000 08:05 458014     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jem.ui_1.2.1.v20060918_M.jar
b511c000-b511f000 r-xs 00017000 08:05 459870     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws_1.0.104.v200703212342.jar
b511f000-b5120000 r-xs 00008000 08:05 458069     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.ecore2ecore.editor_2.2.0.v200702131851.jar
b5120000-b5121000 r-xs 00001000 08:05 459242     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xml.ui.infopop_1.0.1.v200605040131.jar
b5121000-b5123000 r-xs 00000000 08:05 459240     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.dtd.ui.infopop_1.0.1.v200605040131.jar
b5123000-b5124000 r-xs 00000000 08:05 459172     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.internet.proxy.infopop_1.0.0.v200605070230.jar
b5124000-b5127000 r-xs 00015000 08:05 459164     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.command.env.ui_1.0.103.v200703212342.jar
b5127000-b5135000 r-xs 000ac000 08:05 459871     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.ui_1.1.3.v200704261800.jar
b5135000-b5143000 r-xs 00093000 08:05 459244     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xml.ui_1.0.201.v200702021717.jar
b5143000-b5144000 r-xs 00006000 08:05 459846     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.common.annotations.ui_1.1.1.v200609132124.jar
b5144000-b514a000 r-xs 00035000 08:05 459168     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.snippets_1.1.1.v200609140550.jar
b514a000-b514d000 r-xs 00010000 08:05 458072     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.converter_2.2.1.v200702131851.jar
b514d000-b5151000 r-xs 00026000 08:05 459745     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.tomcat.core_1.0.104.v20070202b.jar
b5151000-b5154000 r-xs 00013000 08:05 458100     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.sdo.editor_2.2.0.v200702131851.jar
b5154000-b5160000 r-xs 000a1000 08:05 459882     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.consumption.ui_1.0.105.v200704251610.jar
b5160000-b5162000 r-xs 00007000 08:05 459155     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.core_1.1.100.v200608220540.jar
b5162000-b5170000 r-xs 00097000 08:05 459243     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.sse.ui_1.0.202.v200701252330.jar
b5170000-b5172000 r-xs 00011000 08:05 458060     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.ecore.editor_2.2.0.v200702131851.jar
b5172000-b5174000 r-xs 00000000 08:05 459330     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.javascript.ui.infopop_1.0.1.v200605040131.jar
b5174000-b517a000 r-xs 000ac000 08:05 459267     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsdl_1.0.104.v200704111356.jar
b517a000-b517b000 r-xs 00002000 08:05 459346     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.datatools.server.ui.doc.user_1.0.203.v200608310305.jar
b517b000-b517c000 r-xs 00004000 08:05 459635     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.db2.luw_1.0.107.v200702021852.jar
b517c000-b517f000 r-xs 00014000 08:05 459872     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.axis.creation.ui_1.0.105.v200704200400.jar
b517f000-b5180000 r-xs 00000000 08:05 459176     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.validation.infopop_1.0.201.v200606130645.jar
b5180000-b5182000 r-xs 00006000 08:05 459625     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.sqlscrapbook_1.0.103.v200612130213.jar
b5182000-b5183000 r-xs 00000000 08:05 459373     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.sqleditor.infopop_1.0.0.v200605040131.jar
b5183000-b518a000 r-xs 00036000 08:05 459485     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.models.sql.edit_1.0.103.v200612130213.jar
b518a000-b518f000 r-xs 0002b000 08:05 459148     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.emf_1.1.3.v200612061436.jar
b518f000-b5190000 r-xs 00000000 08:05 459369     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.connection.ui.infopop_1.0.0.v200605040131.jar
b5190000-b5192000 r-xs 00008000 08:05 459173     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.internet.cache_1.0.103.v200612070353.jar
b5192000-b5194000 r-xs 00005000 08:05 459646     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.derby.ui_1.0.103.v200612130213.jar
b5194000-b5197000 r-xs 00081000 08:05 459860     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.consumption.ui.doc.user_1.0.202.v200609221649.jar
b5197000-b5198000 r-xs 00002000 08:05 458086     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.xsd.ecore.exporter_2.2.1.v200702131851.jar
b5198000-b519d000 r-xs 000e5000 08:05 458030     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve.doc_1.2.0.v20060824_M.jar
b519d000-b51b3000 r-xs 00147000 08:05 458031     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve.swt_1.2.1.v20060918_M.jar
b51b3000-b51c3000 r-xs 0008c000 08:05 459206     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.server.ui_1.0.106.v20070425b.jar
b51c3000-b51c5000 r-xs 00008000 08:05 459876     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.webservice.ui_1.1.3.v200704161800.jar
b51c5000-b51c6000 r-xs 00001000 08:05 459638     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.generic.jdbc_1.0.101.v200605040131.jar
b51c6000-b51c9000 r-xs 0002c000 08:05 458052     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.codegen_2.2.2.v200702131851.jar
b51c9000-b51cc000 r-xs 00013000 08:05 459899     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.ejb.annotations.ui_1.1.1.v200609070230.jar
b51cc000-b51ce000 r-xs 00005000 08:05 459880     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.uddiregistry_1.0.100.v200608221651.jar
b51ce000-b51d0000 r-xs 0000b000 08:05 459483     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.fe.ui_1.0.104.v200612130213.jar
b51d0000-b51d7000 r-xs 0003b000 08:05 459151     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.modulecore_1.1.53.v200704161800.jar
b51d7000-b51d8000 r-xs 00001000 08:05 458025     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve_1.2.0.v20060518_RC1.jar
b51d8000-b51ee000 r-xs 000e5000 08:05 459245     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xsd.ui_1.1.103.v200704260345.jar
b51ee000-b51f7000 r-xs 00052000 08:05 459230     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.sse.core_1.1.101.v200611210021.jar
b51f7000-b5203000 r-xs 00088000 08:05 458010     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jem.proxy_1.2.0.v20060918_M.jar
b5203000-b5205000 r-xs 0001c000 08:05 459216     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.sse.doc.user_1.0.203.v200608300230.jar
b5205000-b5207000 r-xs 00001000 08:05 459637     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.derby_1.0.104.v200610161905.jar
b5207000-b520c000 r-xs 00025000 08:05 459152     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.project.facet.core_1.1.1.v200608112156.jar
b520c000-b521c000 r-xs 000a7000 08:05 458041     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.gef_3.2.2.v20070208.jar
b521c000-b5220000 r-xs 0001c000 08:05 459902     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.ejb.annotations.xdoclet_1.1.1.v200609141515.jar
b5220000-b5223000 r-xs 0001c000 08:05 458065     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.edit.ui_2.2.1.v200702131851.jar
b5223000-b5224000 r-xs 00000000 08:05 459897     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.creation.ejb.ui_1.0.0.v200606130315.jar
b5224000-b5225000 r-xs 0001a000 08:05 459320     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.html.standard.dtds_1.0.1.v200608220315.jar
b5225000-b5227000 r-xs 00010000 08:05 459644     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.rdb.derby_1.0.107.v200703122014.jar
b5227000-b522c000 r-xs 00040000 08:05 458008     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar
b522c000-b5230000 r-xs 0001d000 08:05 458067     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.ui_2.2.1.v200702131851.jar
b5230000-b5231000 r-xs 00001000 08:05 459736     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.ui.infopop_1.0.2.v200605040115.jar
b5231000-b5232000 r-xs 00002000 08:05 459912     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst_1.0.1.v200605040115.jar
b5232000-b5243000 r-xs 00071000 08:05 459334     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.javascript.ui_1.0.2.v200701250230.jar
b5243000-b5248000 r-xs 00026000 08:05 459167     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.project.facet.ui_1.1.2.v200701192142.jar
b5248000-b524a000 r-xs 00009000 08:05 459255     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.wsi.ui.doc.user_1.0.202.v200609221649.jar
b524a000-b524c000 r-xs 00009000 08:05 459266     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.ws.parser_1.0.101.v200609062128.jar
b524c000-b524d000 r-xs 00005000 08:05 459901     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.j2ee.ejb.annotations.emitter_1.1.1.v200609140551.jar
b524d000-b525c000 r-xs 0009e000 08:05 458026     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ve.cde_1.2.0.v20060918_M.jar
b525c000-b525f000 r-xs 00012000 08:05 458088     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.xsd.editor_2.2.0.v200702131851.jar
b525f000-b5261000 r-xs 00007000 08:05 459153     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.common.uriresolver_1.1.101.v200702021717.jar
b5261000-b5263000 r-xs 00014000 08:05 458057     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.common.ui_2.2.1.v200702131851.jar
b5263000-b5265000 r-xs 00016000 08:05 459861     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.ws.doc.user_1.0.203.v200609221649.jar
b5265000-b5267000 r-xs 00008000 08:05 459735     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.server.generic.ui_1.0.100.v200608221634.jar
b5267000-b5274000 r-xs 00087000 08:05 459227     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.xml.core_1.1.101.v200704111417.jar
b5274000-b5275000 r-xs 00002000 08:05 459664     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.jst.common.project.facet.core_1.1.0.v200608141517.jar
b5275000-b5277000 r-xs 00007000 08:05 459344     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.wst.datatools.connection.ui.doc.user_1.0.203.v200608310305.jar
b5277000-b5278000 r-xs 0000b000 08:05 458070     /home/hamvil/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.emf.mapping.ecore2xml_2.2.0.v200702131851.jar
b5278000-b5279000 r-xs 00009000 08:05 71208      /usr/lib/eclipse/plugins/org.eclipse.jdt_3.2.1.r321_v20060823.jar
b5279000-b527a000 r-xs 00004000 08:05 68681      /usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility.auth_3.2.0.v20060601.jar
b527a000-b527e000 r-xs 0001e000 08:05 68708      /usr/lib/eclipse/plugins/org.eclipse.ui.console_3.1.100.v20060605.jar
b527e000-b5281000 r-xs 0001c000 08:05 68669      /usr/lib/eclipse/plugins/com.jcraft.jsch_0.1.28.jar
b5281000-b5283000 r-xs 0000d000 08:05 68702      /usr/lib/eclipse/plugins/org.eclipse.team.cvs.ssh2_3.2.1.M20061205.jar
b5283000-b528c000 r-xs 00060000 08:05 71199      /usr/lib/eclipse/plugins/org.eclipse.ui.workbench.texteditor_3.2.0.v20060605-1400.jar
b528c000-b5296000 r-xs 00066000 08:05 71189      /usr/lib/eclipse/plugins/org.eclipse.ui.editors_3.2.1.r321_v20060721.jar
b5296000-b5298000 r-xs 00005000 08:05 68682      /usr/lib/eclipse/plugins/org.eclipse.core.variables_3.1.100.v20060605.jar
b5298000-b52a2000 r-xs 0007b000 08:05 68700      /usr/lib/eclipse/plugins/org.eclipse.team.cvs.core_3.2.2.M20061205.jar
b52a2000-b52a3000 r-xs 00000000 08:05 68672      /usr/lib/eclipse/plugins/org.eclipse.core.boot_3.1.100.v20060603.jar
b52a3000-b52ad000 r-xs 0005f000 08:05 68695      /usr/lib/eclipse/plugins/org.eclipse.ltk.ui.refactoring_3.2.2.r322_v20070124.jar
b52ad000-b52b2000 r-xs 00040000 08:05 68689      /usr/lib/eclipse/plugins/org.eclipse.help.base_3.2.2.R322_v20061207.jar
b52b2000-b52b4000 r-xs 0000d000 08:05 71214      /usr/lib/eclipse/plugins/org.eclipse.pde_3.2.1.v20060810-0800.jar
b52b4000-b52b6000 r-xs 00015000 08:05 68670      /usr/lib/eclipse/plugins/org.eclipse.ant.core_3.1.100.v20060531.jar
b52b6000-b52b8000 r-xs 00005000 08:05 71203      /usr/lib/eclipse/plugins/org.eclipse.update.scheduler_3.2.2.R32x_v20061214.jar
b52b8000-b52c9000 r-xs 000ae000 08:05 68693      /usr/lib/eclipse/plugins/org.eclipse.jface.text_3.2.2.r322_v20070104.jar
b52c9000-b52ca000 r-xs 00003000 08:05 68697      /usr/lib/eclipse/plugins/org.eclipse.osgi.util_3.1.100.v20060601.jar
b52ca000-b52d1000 r-xs 0003f000 08:05 71194      /usr/lib/eclipse/plugins/org.eclipse.ui.navigator_3.2.1.M20060913-0800.jar
b52d1000-b52db000 r-xs 00097000 08:05 68678      /usr/lib/eclipse/plugins/org.eclipse.core.resources_3.2.2.R32x_v20061218.jar
b52db000-b52e1000 r-xs 00035000 08:05 68694      /usr/lib/eclipse/plugins/org.eclipse.ltk.core.refactoring_3.2.1.r321_v20060823.jar
b52e1000-b52e4000 r-xs 0000e000 08:05 71197      /usr/lib/eclipse/plugins/org.eclipse.ui.views_3.2.1.M20060906-0800.jar
b52e4000-b52e6000 r-xs 00011000 08:05 68673      /usr/lib/eclipse/plugins/org.eclipse.core.contenttype_3.2.0.v20060603.jar
b52e6000-b52e7000 r-xs 00002000 08:05 68627      /usr/lib/eclipse/plugins/org.eclipse.rcp_3.2.0.v20060605.jar
b52e7000-b52ea000 r-xs 0000a000 08:05 68696      /usr/lib/eclipse/plugins/org.eclipse.osgi.services_3.1.100.v20060601.jar
b52ea000-b52ec000 r-xs 0000b000 08:05 68701      /usr/lib/eclipse/plugins/org.eclipse.team.cvs.ssh_3.2.1.M20061205.jar
b52ec000-b52ed000 r-xs 00001000 08:05 71210      /usr/lib/eclipse/plugins/org.eclipse.jdt.core.manipulation_1.0.1.r321_v20060721.jar
b52ed000-b52f0000 r-xs 0001b000 08:05 68635      /usr/lib/eclipse/plugins/org.eclipse.help_3.2.2.R322_v20061213.jar
b52f0000-b530d000 r-xs 0017c000 08:05 71192      /usr/lib/eclipse/plugins/org.eclipse.ui.ide_3.2.1.M20060915-1030.jar
b530d000-b5311000 r-xs 00036000 08:05 71212      /usr/lib/eclipse/plugins/org.eclipse.jdt.launching_3.2.2.r322_v20061114.jar
b5311000-b5321000 r-xs 00183000 08:05 68616      /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar
b5321000-b532a000 r-xs 0004f000 08:05 68699      /usr/lib/eclipse/plugins/org.eclipse.team.core_3.2.2.M20061114.jar
b532a000-b532d000 r-xs 00013000 08:05 71198      /usr/lib/eclipse/plugins/org.eclipse.ui.views.properties.tabbed_3.2.1.M20060830-0800.jar
b532d000-b5343000 r-xs 000f0000 08:05 68704      /usr/lib/eclipse/plugins/org.eclipse.team.ui_3.2.1.M200608151725.jar
b5343000-b534c000 r-xs 00058000 08:05 68690      /usr/lib/eclipse/plugins/org.eclipse.help.ui_3.2.0.v20060602.jar
b534c000-b5355000 r-xs 0006f000 08:05 71204      /usr/lib/eclipse/plugins/org.eclipse.update.ui_3.2.2.R32x_v20070111.jar
b5355000-b535b000 r-xs 00044000 08:05 71193      /usr/lib/eclipse/plugins/org.eclipse.ui.intro_3.2.2.R322_v20061214.jar
b535b000-b5362000 r-xs 00041000 08:05 68707      /usr/lib/eclipse/plugins/org.eclipse.ui.cheatsheets_3.2.1.R321_v20060720.jar
b5362000-b5367000 r-xs 00026000 08:05 68706      /usr/lib/eclipse/plugins/org.eclipse.ui.browser_3.2.0.v20060602.jar
b5367000-b536c000 r-xs 00030000 08:05 68705      /usr/lib/eclipse/plugins/org.eclipse.text_3.2.0.v20060605-1400.jar
b536c000-b5371000 r-xs 00036000 08:05 71191      /usr/lib/eclipse/plugins/org.eclipse.ui.forms_3.2.0.v20060602.jar
b5371000-b5372000 r-xs 00001000 08:05 71216      /usr/lib/eclipse/plugins/org.eclipse.pde.junit.runtime_3.2.0.v20060605.jar
b5372000-b5375000 r-xs 00014000 08:05 71196      /usr/lib/eclipse/plugins/org.eclipse.ui.presentations.r21_3.2.0.I20060605-1400.jar
b5375000-b538d000 r-xs 00306000 08:05 68655      /usr/lib/eclipse/plugins/com.ibm.icu_3.4.5.20061213.jar
b538d000-b5397000 r-xs 00038000 08:05 68692      /usr/lib/eclipse/plugins/org.eclipse.jface.databinding_1.0.0.I20060605-1400.jar
b5397000-b5399000 r-xs 00013000 08:05 68680      /usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar
b5399000-b539b000 r-xs 00002000 08:05 68675      /usr/lib/eclipse/plugins/org.eclipse.core.filesystem.linux.x86_1.0.0.v20060603.jar
b539b000-b539d000 r-xs 00007000 08:05 68676      /usr/lib/eclipse/plugins/org.eclipse.core.filesystem_1.0.0.v20060603.jar
b539d000-b53a1000 r-xs 0001d000 08:05 71190      /usr/lib/eclipse/plugins/org.eclipse.ui.externaltools_3.1.101.r321_v20060802.jar
b53a1000-b5421000 r-xs 0074f000 08:05 71213      /usr/lib/eclipse/plugins/org.eclipse.jdt.ui_3.2.2.r322_v20070124.jar
b5421000-b5424000 r-xs 00014000 08:05 68686      /usr/lib/eclipse/plugins/org.eclipse.equinox.preferences_3.2.1.R32x_v20060717.jar
b5424000-b5427000 r-xs 00013000 08:05 68628      /usr/lib/eclipse/plugins/org.eclipse.core.commands_3.2.0.I20060605-1400.jar
b5427000-b544d000 r-xs 003a6000 08:05 71209      /usr/lib/eclipse/plugins/org.eclipse.jdt.core_3.2.3.v_686_R32x.jar
b544d000-b544e000 r-xs 00002000 08:05 68636      /usr/lib/eclipse/plugins/org.eclipse.swt_3.2.2.v3236b.jar
b544e000-b5465000 r-xs 000fd000 08:05 71211      /usr/lib/eclipse/plugins/org.eclipse.jdt.debug.ui_3.2.2.r322_v20061205.jar
b5465000-b5467000 r-xs 0000e000 08:05 68629      /usr/lib/eclipse/plugins/org.eclipse.core.expressions_3.2.2.r322_v20070109a.jar
b5467000-b546d000 r-xs 00035000 08:05 68683      /usr/lib/eclipse/plugins/org.eclipse.debug.core_3.2.1.v20060823.jar
b546d000-b5471000 r-xs 0001a000 08:05 68637      /usr/lib/eclipse/plugins/org.eclipse.ui_3.2.1.M20061108.jar
b5471000-b547e000 r-xs 000b3000 08:05 71215      /usr/lib/eclipse/plugins/org.eclipse.pde.core_3.2.1.v20060915-0800.jar
b547e000-b5481000 r-xs 00015000 08:05 71195      /usr/lib/eclipse/plugins/org.eclipse.ui.navigator.resources_3.2.1.M20060906-0800b.jar
b5481000-b54bd000 r-xs 00309000 08:05 71218      /usr/lib/eclipse/plugins/org.eclipse.pde.ui_3.2.1.v20060816-0800.jar
b54bd000-b54c0000 r-xs 00014000 08:05 68674      /usr/lib/eclipse/plugins/org.eclipse.core.filebuffers_3.2.1.r321_v20060721.jar
b54c0000-b54c2000 r-xs 00002000 08:05 68688      /usr/lib/eclipse/plugins/org.eclipse.help.appserver_3.1.100.v20060602.jar
b54c2000-b54c5000 r-xs 0001a000 08:05 68679      /usr/lib/eclipse/plugins/org.eclipse.core.resources.compatibility_3.2.0.v20060603.jar
b54c5000-b54d5000 r-xs 000b9000 08:05 68691      /usr/lib/eclipse/plugins/org.eclipse.jface_3.2.2.M20061214-1200.jar
b54d5000-b54de000 r-xs 00064000 08:05 68698      /usr/lib/eclipse/plugins/org.eclipse.search_3.2.1.r321_v20060726.jar
b54de000-b54e0000 r-xs 00011000 08:05 68677      /usr/lib/eclipse/plugins/org.eclipse.core.jobs_3.2.0.v20060603.jar
b54e0000-b54fc000 r-xs 00155000 08:05 68703      /usr/lib/eclipse/plugins/org.eclipse.team.cvs.ui_3.2.2.M20061121.jar
b54fc000-b5533000 r-xs 002bf000 08:05 68638      /usr/lib/eclipse/plugins/org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar
b5533000-b5537000 r-xs 0001e000 08:05 71217      /usr/lib/eclipse/plugins/org.eclipse.pde.runtime_3.2.0.v20060605.jar
b5537000-b5540000 r-xs 0006a000 08:05 68671      /usr/lib/eclipse/plugins/org.eclipse.compare_3.2.1.M20060711.jar
b5540000-b5542000 r-xs 00000000 08:05 71202      /usr/lib/eclipse/plugins/org.eclipse.update.core.linux_3.2.0.v20060605.jar
b5542000-b554b000 r-xs 00085000 08:05 71201      /usr/lib/eclipse/plugins/org.eclipse.update.core_3.2.3.R32x_v20070118.jar
b554b000-b555c000 r-xs 000f4000 08:05 71207      /usr/lib/eclipse/plugins/org.eclipse.ant.ui_3.2.1.r321_v20060828.jar
b555c000-b5583000 r-xs 001a0000 08:05 68684      /usr/lib/eclipse/plugins/org.eclipse.debug.ui_3.2.2.r322_v20070202.jar
b5583000-b5584000 r-xs 00001000 08:05 130554     /usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility.registry_3.2.1.R32x_v20060907/runtime_registry_compatibility.jar
b5584000-b5588000 r-xs 00020000 08:05 68687      /usr/lib/eclipse/plugins/org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar
b5588000-b558f000 r-xp 00000000 08:05 131102     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnio.so
b558f000-b5590000 rwxp 00006000 08:05 131102     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnio.so
b5590000-b55a3000 r-xp 00000000 08:05 131101     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnet.so
b55a3000-b55a4000 rwxp 00013000 08:05 131101     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libnet.so
b55a4000-b55a7000 r-xs 00014000 08:05 71200      /usr/lib/eclipse/plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar
b55a7000-b55aa000 r-xs 00011000 08:05 68685      /usr/lib/eclipse/plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar
b55aa000-b55ad000 ---p b55aa000 00:00 0 
b55ad000-b55fb000 rwxp b55ad000 00:00 0 
b55fb000-b55fe000 ---p b55fb000 00:00 0 
b55fe000-b564c000 rwxp b55fe000 00:00 0 
b564c000-b564f000 ---p b564c000 00:00 0 
b564f000-b569d000 rwxp b564f000 00:00 0 
b569d000-b56aa000 r-xs 000c5000 08:05 68634      /usr/lib/eclipse/plugins/org.eclipse.osgi_3.2.2.R32x_v20070118.jar
b56aa000-b56ad000 ---p b56aa000 00:00 0 
b56ad000-b572b000 rwxp b56ad000 00:00 0 
b572b000-b58a7000 r-xs 02c8f000 08:05 132740     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/rt.jar
b58a7000-b58a8000 ---p b58a7000 00:00 0 
b58a8000-b5928000 rwxp b58a8000 00:00 0 
b5928000-b592b000 ---p b5928000 00:00 0 
b592b000-b5979000 rwxp b592b000 00:00 0 
b5979000-b597c000 ---p b5979000 00:00 0 
b597c000-b59fa000 rwxp b597c000 00:00 0 
b59fa000-b59fd000 ---p b59fa000 00:00 0 
b59fd000-b5a4b000 rwxp b59fd000 00:00 0 
b5a4b000-b5a52000 r-xs 00000000 08:05 81800      /usr/lib/gconv/gconv-modules.cache
b5a52000-b5a91000 r-xp 00000000 08:05 115387     /usr/lib/locale/it_IT.utf8/LC_CTYPE
b5a91000-b5a94000 ---p b5a91000 00:00 0 
b5a94000-b5ae2000 rwxp b5a94000 00:00 0 
b5ae2000-b5ae5000 ---p b5ae2000 00:00 0 
b5ae5000-b5b33000 rwxp b5ae5000 00:00 0 
b5b33000-b5b34000 ---p b5b33000 00:00 0 
b5b34000-b5bcc000 rwxp b5b34000 00:00 0 
b5bcc000-b5bdc000 rwxp b5bcc000 00:00 0 
b5bdc000-b5beb000 rwxp b5bdc000 00:00 0 
b5beb000-b5bfa000 rwxp b5beb000 00:00 0 
b5bfa000-b5bfc000 rwxp b5bfa000 00:00 0 
b5bfc000-b5c0b000 rwxp b5bfc000 00:00 0 
b5c0b000-b5c1a000 rwxp b5c0b000 00:00 0 
b5c1a000-b5c2b000 rwxp b5c1a000 00:00 0 
b5c2b000-b5c3a000 rwxp b5c2b000 00:00 0 
b5c3a000-b5c51000 rwxp b5c3a000 00:00 0 
b5c51000-b5cc5000 rwxp b5c51000 00:00 0 
b5cc5000-b5f95000 rwxp b5cc5000 00:00 0 
b5f95000-b7cc5000 rwxp b5f95000 00:00 0 
b7cc5000-b7cd4000 r-xp 00000000 08:05 131097     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libzip.so
b7cd4000-b7cd6000 rwxp 0000e000 08:05 131097     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libzip.so
b7cd6000-b7cf9000 r-xp 00000000 08:05 131096     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjava.so
b7cf9000-b7cfb000 rwxp 00023000 08:05 131096     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjava.so
b7cfb000-b7d06000 r-xp 00000000 08:05 131095     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libverify.so
b7d06000-b7d07000 rwxp 0000b000 08:05 131095     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libverify.so
b7d07000-b7d10000 r-xp 00000000 08:05 33532      /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7d10000-b7d12000 rwxp 00008000 08:05 33532      /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7d12000-b7d1a000 r-xp 00000000 08:05 33534      /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7d1a000-b7d1c000 rwxp 00007000 08:05 33534      /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7d1c000-b7d23000 r-xp 00000000 08:05 33530      /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7d23000-b7d25000 rwxp 00006000 08:05 33530      /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7d25000-b7d39000 r-xp 00000000 08:05 33529      /lib/tls/i686/cmov/libnsl-2.6.1.so
b7d39000-b7d3b000 rwxp 00013000 08:05 33529      /lib/tls/i686/cmov/libnsl-2.6.1.so
b7d3b000-b7d42000 rwxp b7d3b000 00:00 0 
b7d42000-b7d4a000 rwxs 00000000 08:05 504012     /tmp/hsperfdata_hamvil/7545
b7d4a000-b7d51000 r-xp 00000000 08:05 33539      /lib/tls/i686/cmov/librt-2.6.1.so
b7d51000-b7d53000 rwxp 00006000 08:05 33539      /lib/tls/i686/cmov/librt-2.6.1.so
b7d53000-b7d56000 ---p b7d53000 00:00 0 
b7d56000-b7da4000 rwxp b7d56000 00:00 0 
b7da4000-b7dc7000 r-xp 00000000 08:05 33527      /lib/tls/i686/cmov/libm-2.6.1.so
b7dc7000-b7dc9000 rwxp 00023000 08:05 33527      /lib/tls/i686/cmov/libm-2.6.1.so
b7dc9000-b7dca000 rwxp b7dc9000 00:00 0 
b7dca000-b7f0e000 r-xp 00000000 08:05 33523      /lib/tls/i686/cmov/libc-2.6.1.so
b7f0e000-b7f0f000 r-xp 00143000 08:05 33523      /lib/tls/i686/cmov/libc-2.6.1.so
b7f0f000-b7f11000 rwxp 00144000 08:05 33523      /lib/tls/i686/cmov/libc-2.6.1.so
b7f11000-b7f14000 rwxp b7f11000 00:00 0 
b7f14000-b7f16000 r-xp 00000000 08:05 33526      /lib/tls/i686/cmov/libdl-2.6.1.so
b7f16000-b7f18000 rwxp 00001000 08:05 33526      /lib/tls/i686/cmov/libdl-2.6.1.so
b7f18000-b7f1f000 r-xp 00000000 08:05 146342     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/jli/libjli.so
b7f1f000-b7f21000 rwxp 00006000 08:05 146342     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/jli/libjli.so
b7f21000-b7f22000 rwxp b7f21000 00:00 0 
b7f22000-b7f36000 r-xp 00000000 08:05 33537      /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f36000-b7f38000 rwxp 00013000 08:05 33537      /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f38000-b7f3a000 rwxp b7f38000 00:00 0 
b7f3a000-b7f3c000 r-xs 00012000 08:05 68633      /usr/lib/eclipse/plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar
b7f3c000-b7f3e000 r-xs 00007000 08:05 68641      /usr/lib/eclipse/startup.jar
b7f3e000-b7f44000 r-xp 00000000 08:05 131087     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/native_threads/libhpi.so
b7f44000-b7f45000 rwxp 00006000 08:05 131087     /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/native_threads/libhpi.so
b7f45000-b7f46000 rwxp b7f45000 00:00 0 
b7f46000-b7f47000 r-xp b7f46000 00:00 0 
b7f47000-b7f49000 rwxp b7f47000 00:00 0 
b7f49000-b7f63000 r-xp 00000000 08:05 1219213    /lib/ld-2.6.1.so
b7f63000-b7f65000 rwxp 00019000 08:05 1219213    /lib/ld-2.6.1.so
bfc63000-bfc9a000 rwxp bfc63000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.locking=none
java_command: /usr/lib/eclipse/startup.jar -os linux -ws gtk -arch x86 -launcher /usr/lib/eclipse/eclipse -name Eclipse -showsplash 600 -exitdata 20800b -install /usr/lib/eclipse -vm /usr/lib/jvm/java-6-sun/bin/java -vmargs -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.locking=none -jar /usr/lib/eclipse/startup.jar
Launcher Type: SUN_STANDARD

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-6-sun
PATH=/home/hamvil/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=hamvil
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../lib/i386:/usr/lib/firefox
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3b29c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3b29c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x309ec0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGILL: [libjvm.so+0x309ec0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30bef0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30b910], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR2: [libjvm.so+0x30bef0], sa_mask[0]=0x00000000, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 8190, NOFILE 1024, AS infinity
load average:0,26 0,24 0,28

CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 13 stepping 8, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1035508k(56960k free), swap 506008k(506008k free)

vm_info: Java HotSpot(TM) Client VM (1.6.0_03-b05) for linux-x86, built on Sep 24 2007 22:45:46 by "java_re" with gcc 3.2.1-7a (J2SE release)

```

---

### Post by mexpolk on 2008-01-15
I have found some workaround... and should work without problems.

1. Install Java enviroment:

$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

2. Update alternatives:

$ sudo update-java-alternatives -s /usr/lib/jvm/java-6-sun

[B]3. Install eclipse:

$ sudo apt-get install eclipse

4. Once that Eclipse IDE is installed, download Easyeclipse and extract the contents of the tar file:

 tar -zxvf Desktop/easyeclipse-lamp-1.2.2.2.tar.gz

5. Finally copy al the contents of easyeclipse-lamp-1.2.2.2/plugins to /usr/local/lib/eclipse/plugins/[/B]

And that's it! You got Eclipse with all the functionality of Easyeclipse for LAMP (or whatever the flavor you need).

Best!

---

### Post by mnk0 on 2008-01-15
yeah. im gettin the same crash, and that last posted solution didnt seem to work for me either.

--
Omar Samad

---

### Post by mexpolk on 2008-01-16
Omar...

I think I've found a solution at last:

[http://ubuntuforums.org/showthread.php?p=4141478#post4141478]("http://ubuntuforums.org/showthread.php?p=4141478#post4141478")

It worked for me. It's really a workaround.

---

### Post by wiesbert on 2008-01-19
I got the same errors, after trying for hours i followed this:
[http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse)

and it works now.

HTH
wiesbert

---

### Post by toolweb on 2008-02-27
Eclipse works fine after Installing the sun-java6-bin jre packages.
Thanks...

---

### Post by spamalot on 2008-04-13
Hello everyone,

I am dealing with a similar problem.

Result from creating a new project, adding a main.cpp file to it and try to edit it:

Unable to create this part due to an internal error. Reason for the failure: An exception was thrown during initialization
java.lang.ClassNotFoundException: org.eclipse.core.runtime.Plugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)

etc..

Here's my config:

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-4.1
          3    /usr/bin/gij-4.2
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java
*         5    /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by spamalot on 2008-04-13
PS:

of no help to me:

sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8

I'm able to modify *.cpp files using "open as text file" within eclipse, but sooner or later, eclipse crashes...

---

### Post by dpolishannu on 2008-04-21
Some updates received today (don't know what, don't know how to find what those were) broke eclipse.
(edit:actually it was yesterday, and they were -  
Upgraded the following packages:
apt (0.7.6ubuntu14) to 0.7.6ubuntu14.1
apt-utils (0.7.6ubuntu14) to 0.7.6ubuntu14.1
)

First symptom was that it started to crash when saving. Since then I have upgraded java, reinstalled eclipse, had various other problems during but now I am back where I started - more or less.

This is the dump that comes when saving:
VM terminated. Exit code=1
/usr/lib/jvm/java-6-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 39000c
-install /usr/lib/eclipse
-clean
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

As I started eclipse from shell got the following too:
-copy pasted from shell-
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x8fff8fab, pid=10319, tid=3084807056
#
# Java VM: Java HotSpot(TM) Server VM (10.0-b22 mixed mode linux-x86)
# Problematic frame:
# C  [libxpcom_core.so+0x95fab]  _ZN18nsAString_internal6AssignERKS_+0x1b
#
# An error report file with more information is saved as:
# /home/xxx/hs_err_pid10319.log
#
--

and some of ther file err_pid10319.log
------------------
VM Arguments:
jvm_args: -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/g
cj-4.2/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.loc
king=none 
java_command: /usr/lib/eclipse/startup.jar -os linux -ws gtk -arch x86 -launcher /u
sr/lib/eclipse/eclipse -name Eclipse -showsplash 600 -exitdata 39000c -install /usr
/lib/eclipse -clean -vm /usr/lib/jvm/java-6-sun/bin/java -vmargs -Djava.library.pat
h=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db -Dgnu.gcj
.runtime.VMClassLoader.library_control=never -Dosgi.locking=none -jar /usr/lib/ecli
pse/startup.jar
Launcher Type: SUN_STANDARD

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-6-sun
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=hannu
LD_LIBRARY_PATH=/usr/lib/jvm/jre1.6.0_06/lib/i386/server:/usr/lib/jvm/jre1.6.0_06/l
ib/i386:/usr/lib/jvm/jre1.6.0_06/../lib/i386:/usr/lib/firefox
SHELL=/bin/bash
DISPLAY=:1.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x5edbc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x5edbc0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4fc630], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x4fc630], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4fc630], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4fe670], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4fe410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4fe410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4fe410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4fe410], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 15351, NOFILE 1024, AS infinity
load average:0.72 0.38 0.29

CPU:total 2 (2 cores per cpu, 1 threads per core) family 15 model 107 stepping 2, c
mov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 1944820k(60448k free), swap 1951888k(1951888k free)

vm_info: Java HotSpot(TM) Server VM (10.0-b22) for linux-x86 JRE (1.6.0_06-b02), bu
ilt on Mar 25 2008 00:26:44 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Mon Apr 21 17:44:59 2008
elapsed time: 62 seconds


------------------

As you can see, I set the JAVA_HOME

I installed Ubuntu few days ago as I would like to move using linux instead windows. Please tell me (lie if it is not true :) ) that this is exceptional behavioral with Ubuntu.

---

### Post by dpolishannu on 2008-04-21
Searching more and  found that it is possibly even firefox update related issue...

[http://bbs.archlinux.org/viewtopic.php?id=47353](http://bbs.archlinux.org/viewtopic.php?id=47353)

(edit: and i uninstalled ff2 and eclipse worked fine, just says that no browser for it found, installed ff3 preview and same - works and no browser for eclipse.)

It is just, that some webdevelopers plugins are not ready for ff3. What a mess.

(edit again, because I seem to be in too much hurry to searc first and then post: FireBug, which is essential tool, has 1.10b that works with ff3. And the journey continues...)

---

