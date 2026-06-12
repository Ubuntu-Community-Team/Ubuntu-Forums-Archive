---
title: "Eclipse crashes frequently Ubuntu 13.10"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by u04f0612 on 2014-02-19
I am using eclipse based IDE from a commercial vendor. It has been working fine untill today's updates. I received ubuntu base updates today and restared my system. After restarts, all my eclipse instances crash in a minute or two. Attached is eclipse error log. Sorry the attachment is not working for me. Here is reproduced version of error log:
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xaac43bfe, pid=10754, tid=4136905536
#
# JRE version: 7.0_07-b10
# Java VM: Java HotSpot(TM) Server VM (23.3-b01 mixed mode linux-x86 )
# Problematic frame:
# C  [libgobject-2.0.so.0+0x16bfe]  g_object_get_qdata+0x1e
#
# Failed to write core dump. Core dumps have been disabled. To enable  core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please visit:
#   [http://bugreport.sun.com/bugreport/crash.jsp](http://bugreport.sun.com/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0xf6707000):  JavaThread "main" [_thread_in_native, id=10755, stack(0xf68f2000,0xf6943000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000e00

Registers:
EAX=0x00000e00, EBX=0xaac7e000, ECX=0xa24e52d0, EDX=0xf6707128
ESP=0xf6940b00, EBP=0xf6940b38, ESI=0xa24e52d0, EDI=0xf6707000
EIP=0xaac43bfe, EFLAGS=0x00010206, CR2=0x00000e00

Top of Stack: (sp=0xf6940b00)
0xf6940b00:   00000021 f6940b04 f6940b50 f3703487
0xf6940b10:   00000000 a79c1958 f6940b58 a799d7f4
0xf6940b20:   a24e52d0 000003ff 000003ff a24eb590
0xf6940b30:   f6940b30 005f62fd f6940b68 f3a09e26
0xf6940b40:   f6707128 f6940b58 a24e52d0 000003ff
0xf6940b50:   af2a2a80 00000000 bec5e3b0 f6940b88
0xf6940b60:   f37035cf e8f6ef58 f6707000 f3a1a208
0xf6940b70:   f6940b94 af3f1cd8 a24e52d0 000003ff 

Instructions: (pc=0xaac43bfe)
0xaac43bde:   00 00 56 53 83 ec 14 8b 74 24 20 e8 22 1d ff ff
0xaac43bee:   81 c3 12 a4 03 00 85 f6 74 1f 8b 06 85 c0 74 05
0xaac43bfe:   83 38 50 74 45 c7 44 24 04 50 00 00 00 89 34 24
0xaac43c0e:   e8 2d 9b 01 00 85 c0 75 31 8d 83 5f a0 fe ff 89 

Register to memory mapping:

EAX=0x00000e00 is an unknown value
EBX=0xaac7e000: <offset 0x51000> in /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 at 0xaac2d000
ECX=0xa24e52d0 is an unknown value
EDX=0xf6707128 is an unknown value
ESP=0xf6940b00 is pointing into the stack for thread: 0xf6707000
EBP=0xf6940b38 is pointing into the stack for thread: 0xf6707000
ESI=0xa24e52d0 is an unknown value
EDI=0xf6707000 is a thread


Stack: [0xf68f2000,0xf6943000],  sp=0xf6940b00,  free space=314k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libgobject-2.0.so.0+0x16bfe]  g_object_get_qdata+0x1e
J  org.eclipse.swt.internal.gtk.OS._g_object_get_qdata(II)I

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  org.eclipse.swt.internal.gtk.OS._g_object_get_qdata(II)I
J  org.eclipse.swt.internal.gtk.OS.g_object_get_qdata(II)I
j  org.eclipse.swt.widgets.Display.removeWidget(I)Lorg/eclipse/swt/widgets/Widget;+17
j  org.eclipse.swt.widgets.Combo.deregister()V+19
j  org.eclipse.swt.widgets.Widget.releaseWidget()V+1
j  org.eclipse.swt.widgets.Control.releaseWidget()V+1
j  org.eclipse.swt.widgets.Composite.releaseWidget()V+1
j  org.eclipse.swt.widgets.Combo.releaseWidget()V+1
j  org.eclipse.swt.widgets.Widget.release(Z)V+82
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Composite.releaseChildren(Z)V+31
j  org.eclipse.swt.widgets.Canvas.releaseChildren(Z)V+42
j  org.eclipse.swt.widgets.Decorations.releaseChildren(Z)V+22
j  org.eclipse.swt.widgets.Shell.releaseChildren(Z)V+100
j  org.eclipse.swt.widgets.Widget.release(Z)V+38
j  org.eclipse.swt.widgets.Control.release(Z)V+94
j  org.eclipse.swt.widgets.Widget.dispose()V+23
j  org.eclipse.swt.widgets.Shell.dispose()V+20
j  org.eclipse.jface.window.Window.close()Z+65
j  org.eclipse.jface.dialogs.Dialog.close()Z+26
j  org.eclipse.jface.wizard.WizardDialog.hardClose()Z+83
j  org.eclipse.jface.wizard.WizardDialog.finishPressed()V+56
j  org.eclipse.jface.wizard.WizardDialog.buttonPressed(I)V+54
j  org.eclipse.jface.dialogs.Dialog$2.widgetSelected(Lorg/eclipse/swt/events/SelectionEvent:wink:V+17
j  org.eclipse.swt.widgets.TypedListener.handleEvent(Lorg/eclipse/swt/widgets/Event:wink:V+1133
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/Event:wink:V
j  org.eclipse.swt.widgets.Widget.sendEvent(Lorg/eclipse/swt/widgets/Event:wink:V+25
j  org.eclipse.swt.widgets.Display.runDeferredEvents()Z+92
j  org.eclipse.swt.widgets.Display.readAndDispatch()Z+46
j  org.eclipse.jface.window.Window.runEventLoop(Lorg/eclipse/swt/widgets/Shell:wink:V+23
j  org.eclipse.jface.window.Window.open()I+49
j  org.eclipse.ui.internal.actions.NewWizardShortcutAction.run()V+311
j  org.eclipse.jface.action.Action.runWithEvent(Lorg/eclipse/swt/widgets/Event:wink:V+1
j  org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(Lorg/eclipse/swt/widgets/Event;Z)V+354
j   org.eclipse.jface.action.ActionContributionItem.access$2(Lorg/eclipse/jface/action/ActionContributionItem;Lorg/eclipse/swt/widgets/Event;Z)V+3
j  org.eclipse.jface.action.ActionContributionItem$5.handleEvent(Lorg/eclipse/swt/widgets/Event:wink:V+60
J  org.eclipse.swt.widgets.EventTable.sendEvent(Lorg/eclipse/swt/widgets/Event:wink:V
j  org.eclipse.swt.widgets.Widget.sendEvent(Lorg/eclipse/swt/widgets/Event:wink:V+25
j  org.eclipse.swt.widgets.Display.runDeferredEvents()Z+92
j  org.eclipse.swt.widgets.Display.readAndDispatch()Z+46
j   org.eclipse.ui.internal.Workbench.runEventLoop(Lorg/eclipse/jface/window/Window$IExceptionHandler;Lorg/eclipse/swt/widgets/Display:wink:V+9
j  org.eclipse.ui.internal.Workbench.runUI()I+555
j  org.eclipse.ui.internal.Workbench.access$4(Lorg/eclipse/ui/internal/Workbench:wink:I+1
j  org.eclipse.ui.internal.Workbench$7.run()V+73
j   org.eclipse.core.databinding.observable.Realm.runWithDefault(Lorg/eclipse/core/databinding/observable/Realm;Ljava/lang/Runnable:wink:V+12
j   org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor:wink:I+18
j  org.eclipse.ui.PlatformUI.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor:wink:I+2
j  org.eclipse.ui.internal.ide.application.IDEApplication.start(Lorg/eclipse/equinox/app/IApplicationContext:wink:Ljava/lang/Object;+108
j  org.eclipse.equinox.internal.app.EclipseAppHandle.run(Ljava/lang/Object:wink:Ljava/lang/Object;+135
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Ljava/lang/Object:wink:Ljava/lang/Object;+103
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Ljava/lang/Object:wink:Ljava/lang/Object;+29
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run(Ljava/lang/Object:wink:Ljava/lang/Object;+149
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run([Ljava/lang/String;Ljava/lang/Runnable:wink:Ljava/lang/Object;+183
v  ~StubRoutines::call_stub
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object:wink:Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object:wink:Ljava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object:wink:Ljava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object:wink:Ljava/lang/Object;+57
j  org.eclipse.equinox.launcher.Main.invokeFramework([Ljava/lang/String;[Ljava/net/URL:wink:V+211
j  org.eclipse.equinox.launcher.Main.basicRun([Ljava/lang/String:wink:V+126
j  org.eclipse.equinox.launcher.Main.run([Ljava/lang/String:wink:I+4
j  org.eclipse.equinox.launcher.Main.main([Ljava/lang/String:wink:V+10
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0xa197f000 JavaThread "Worker-15" [_thread_blocked, id=11319, stack(0xa50af000,0xa5100000)]
  0xa4530800 JavaThread "Worker-14" [_thread_blocked, id=11316, stack(0xa5639000,0xa568a000)]
  0xae20ec00 JavaThread "Worker-12" [_thread_blocked, id=11192, stack(0xa2908000,0xa2959000)]
  0xae21ac00 JavaThread "Worker-9" [_thread_in_vm, id=10855, stack(0xa5da0000,0xa5df1000)]
  0xae422400 JavaThread "[ThreadPool Manager] - Idle Thread" daemon [_thread_blocked, id=10852, stack(0xa3aeb000,0xa3b3c000)]
  0xa288d400 JavaThread "Java indexing" daemon [_thread_blocked, id=10843, stack(0xa3caf000,0xa3d00000)]
  0xa3328800 JavaThread  "org.eclipse.jface.text.reconciler.MonoReconciler" daemon  [_thread_blocked, id=10842, stack(0xa3c0d000,0xa3c5e000)]
  0xa7bcc400 JavaThread "Thread-10" [_thread_blocked, id=10825, stack(0xa38af000,0xa3900000)]
  0xa390f800 JavaThread "Bundle File Closer" daemon [_thread_blocked, id=10822, stack(0xa3c5e000,0xa3caf000)]
  0xa3d39c00 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=10813, stack(0xa4805000,0xa4856000)]
  0xa5a8e400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=10812, stack(0xa4856000,0xa48a7000)]
  0xadf7a000 JavaThread "Worker-6" [_thread_blocked, id=10797, stack(0xa48af000,0xa4900000)]
  0xa7c95c00 JavaThread "Worker-JM" [_thread_blocked, id=10780, stack(0xa7d5e000,0xa7daf000)]
  0xae207c00 JavaThread "[Timer] - Main Queue Handler" daemon [_thread_blocked, id=10779, stack(0xa7daf000,0xa7e00000)]
  0xadfcf400 JavaThread "Framework Event Dispatcher" daemon [_thread_blocked, id=10777, stack(0xa7f5e000,0xa7faf000)]
  0xa80a8400 JavaThread "Start Level Event Dispatcher" daemon [_thread_blocked, id=10776, stack(0xa7faf000,0xa8000000)]
  0xa80a5c00 JavaThread "State Data Manager" daemon [_thread_blocked, id=10775, stack(0xa814f000,0xa81a0000)]
  0xa805e400 JavaThread "Framework Active Thread" [_thread_blocked, id=10774, stack(0xa81a0000,0xa81f1000)]
  0xaafe5400 JavaThread "Service Thread" daemon [_thread_blocked, id=10766, stack(0xaae2e000,0xaae7f000)]
  0xaafe3800 JavaThread "C2 CompilerThread1" daemon [_thread_in_vm, id=10765, stack(0xaa70f000,0xaa790000)]
  0xaafe1800 JavaThread "C2 CompilerThread0" daemon [_thread_in_native, id=10764, stack(0xaac7f000,0xaad00000)]
  0xaafdfc00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=10763, stack(0xae02e000,0xae07f000)]
  0xaafa7800 JavaThread "Finalizer" daemon [_thread_blocked, id=10762, stack(0xae32e000,0xae37f000)]
  0xaafa5c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=10761, stack(0xae52d000,0xae57e000)]
=>0xf6707000 JavaThread "main" [_thread_in_native, id=10755, stack(0xf68f2000,0xf6943000)]

Other Threads:
  0xaafa0400 VMThread [stack: 0xaae7f000,0xaaf00000] [id=10760]
  0xaafe7400 WatcherThread [stack: 0xaa68e000,0xaa70f000] [id=10767]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0xf6705030] Compile_lock - owner thread: 0xaafe3800

Heap
 PSYoungGen      total 168640K, used 80833K [0xe1af0000, 0xefe60000, 0xf3640000)
  eden space 117056K, 36% used [0xe1af0000,0xe45383c8,0xe8d40000)
  from space 51584K, 72% used [0xe8d40000,0xeb1e8190,0xebfa0000)
  to   space 55040K, 0% used [0xec8a0000,0xec8a0000,0xefe60000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 52064K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 62% used [0xaea40000,0xb1d18370,0xb3c40000)

Card table byte_map: [0xae819000,0xaea40000] byte_map_base: 0xae2a3e00

Polling page: 0xf77b7000

Code Cache  [0xf3700000, 0xf3c18000, 0xf6700000)
 total_blobs=1953 nmethods=1667 adapters=237 free_code_cache=43991Kb largest_free_block=44990592

Compilation events (10 events):
Event: 374.294 Thread 0xaafe3800 nmethod 1803 0xf3b60e88 code [0xf3b60f80, 0xf3b61090]
Event: 374.295 Thread 0xaafe3800 1804             org.eclipse.cdt.internal.core.model.PathEntry::hashCode (60 bytes)
Event: 374.297 Thread 0xaafe3800 nmethod 1804 0xf3b56008 code [0xf3b56100, 0xf3b561d0]
Event: 374.297 Thread 0xaafe3800 1805             org.eclipse.cdt.internal.core.model.APathEntry::hashCode (68 bytes)
Event: 374.302 Thread 0xaafe3800 nmethod 1805 0xf3b59108 code [0xf3b59220, 0xf3b59510]
Event: 374.302 Thread 0xaafe3800 1806              org.eclipse.cdt.internal.core.model.PathEntryManager::getCachedResolvedPathEntries  (252 bytes)
Event: 374.303 Thread 0xaafe1800 nmethod 1797 0xf3b42548 code [0xf3b42860, 0xf3b443cc]
Event: 374.304 Thread 0xaafe1800 1807              org.eclipse.cdt.internal.core.model.PathEntryManager::getResolvedPathEntries  (613 bytes)
Event: 374.315 Thread 0xaafe3800 nmethod 1806 0xf3b5a308 code [0xf3b5a4c0, 0xf3b5a980]
Event: 374.315 Thread 0xaafe3800 1808   !         org.eclipse.jdt.internal.core.DeltaProcessor::traverseDelta (646 bytes)

GC Heap History (10 events):
Event: 251.882 GC heap before
{Heap before GC invocations=38 (full 5):
 PSYoungGen      total 151296K, used 111576K [0xe1af0000, 0xee4a0000, 0xf3640000)
  eden space 107328K, 100% used [0xe1af0000,0xe83c0000,0xe83c0000)
  from space 43968K, 9% used [0xeadd0000,0xeb1f6060,0xed8c0000)
  to   space 43072K, 0% used [0xe83c0000,0xe83c0000,0xeadd0000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51205K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 60% used [0xaea40000,0xb1c41760,0xb3c40000)
Event: 251.898 GC heap after
Heap after GC invocations=38 (full 5):
 PSYoungGen      total 150400K, used 13771K [0xe1af0000, 0xede10000, 0xf3640000)
  eden space 107328K, 0% used [0xe1af0000,0xe1af0000,0xe83c0000)
  from space 43072K, 31% used [0xe83c0000,0xe9132e28,0xeadd0000)
  to   space 40320K, 0% used [0xeb6b0000,0xeb6b0000,0xede10000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51205K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 60% used [0xaea40000,0xb1c41760,0xb3c40000)
}
Event: 329.443 GC heap before
{Heap before GC invocations=39 (full 5):
 PSYoungGen      total 150400K, used 121099K [0xe1af0000, 0xede10000, 0xf3640000)
  eden space 107328K, 100% used [0xe1af0000,0xe83c0000,0xe83c0000)
  from space 43072K, 31% used [0xe83c0000,0xe9132e28,0xeadd0000)
  to   space 40320K, 0% used [0xeb6b0000,0xeb6b0000,0xede10000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51206K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 60% used [0xaea40000,0xb1c41998,0xb3c40000)
Event: 329.468 GC heap after
Heap after GC invocations=39 (full 5):
 PSYoungGen      total 153728K, used 23499K [0xe1af0000, 0xedc00000, 0xf3640000)
  eden space 115520K, 0% used [0xe1af0000,0xe1af0000,0xe8bc0000)
  from space 38208K, 61% used [0xeb6b0000,0xecda2e28,0xedc00000)
  to   space 41088K, 0% used [0xe8bc0000,0xe8bc0000,0xeb3e0000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51206K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 60% used [0xaea40000,0xb1c41998,0xb3c40000)
}
Event: 347.574 GC heap before
{Heap before GC invocations=40 (full 5):
 PSYoungGen      total 153728K, used 139019K [0xe1af0000, 0xedc00000, 0xf3640000)
  eden space 115520K, 100% used [0xe1af0000,0xe8bc0000,0xe8bc0000)
  from space 38208K, 61% used [0xeb6b0000,0xecda2e28,0xedc00000)
  to   space 41088K, 0% used [0xe8bc0000,0xe8bc0000,0xeb3e0000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51216K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 60% used [0xaea40000,0xb1c442b0,0xb3c40000)
Event: 347.602 GC heap after
Heap after GC invocations=40 (full 5):
 PSYoungGen      total 156608K, used 35115K [0xe1af0000, 0xeec70000, 0xf3640000)
  eden space 115520K, 0% used [0xe1af0000,0xe1af0000,0xe8bc0000)
  from space 41088K, 85% used [0xe8bc0000,0xeae0af78,0xeb3e0000)
  to   space 45888K, 0% used [0xebfa0000,0xebfa0000,0xeec70000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51216K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 60% used [0xaea40000,0xb1c442b0,0xb3c40000)
}
Event: 349.900 GC heap before
{Heap before GC invocations=41 (full 5):
 PSYoungGen      total 156608K, used 150635K [0xe1af0000, 0xeec70000, 0xf3640000)
  eden space 115520K, 100% used [0xe1af0000,0xe8bc0000,0xe8bc0000)
  from space 41088K, 85% used [0xe8bc0000,0xeae0af78,0xeb3e0000)
  to   space 45888K, 0% used [0xebfa0000,0xebfa0000,0xeec70000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51499K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 61% used [0xaea40000,0xb1c8ae88,0xb3c40000)
Event: 349.947 GC heap after
Heap after GC invocations=41 (full 5):
 PSYoungGen      total 162944K, used 40475K [0xe1af0000, 0xef750000, 0xf3640000)
  eden space 117056K, 0% used [0xe1af0000,0xe1af0000,0xe8d40000)
  from space 45888K, 88% used [0xebfa0000,0xee726d80,0xeec70000)
  to   space 51584K, 0% used [0xe8d40000,0xe8d40000,0xebfa0000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 51499K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 61% used [0xaea40000,0xb1c8ae88,0xb3c40000)
}
Event: 373.805 GC heap before
{Heap before GC invocations=42 (full 5):
 PSYoungGen      total 162944K, used 157531K [0xe1af0000, 0xef750000, 0xf3640000)
  eden space 117056K, 100% used [0xe1af0000,0xe8d40000,0xe8d40000)
  from space 45888K, 88% used [0xebfa0000,0xee726d80,0xeec70000)
  to   space 51584K, 0% used [0xe8d40000,0xe8d40000,0xebfa0000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 52049K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 61% used [0xaea40000,0xb1d14500,0xb3c40000)
Event: 373.845 GC heap after
Heap after GC invocations=42 (full 5):
 PSYoungGen      total 168640K, used 37536K [0xe1af0000, 0xefe60000, 0xf3640000)
  eden space 117056K, 0% used [0xe1af0000,0xe1af0000,0xe8d40000)
  from space 51584K, 72% used [0xe8d40000,0xeb1e8190,0xebfa0000)
  to   space 55040K, 0% used [0xec8a0000,0xec8a0000,0xefe60000)
 ParOldGen       total 144448K, used 120621K [0xbe440000, 0xc7150000, 0xe1af0000)
  object space 144448K, 83% used [0xbe440000,0xc5a0b490,0xc7150000)
 PSPermGen       total 83968K, used 52049K [0xaea40000, 0xb3c40000, 0xbe440000)
  object space 83968K, 61% used [0xaea40000,0xb1d14500,0xb3c40000)
}

Deoptimization events (10 events):
Event: 374.239 Thread 0xa1c55800 Uncommon trap -34 fr.pc 0xf3b5ca98
Event: 374.292 Thread 0xa1c55800 Uncommon trap -58 fr.pc 0xf3bf64ec
Event: 374.292 Thread 0xa1c55800 Uncommon trap -58 fr.pc 0xf3bff200
Event: 374.293 Thread 0xae21ac00 Uncommon trap -83 fr.pc 0xf386361c
Event: 374.294 Thread 0xae21ac00 Uncommon trap -83 fr.pc 0xf3861684
Event: 374.296 Thread 0xae21ac00 Uncommon trap -34 fr.pc 0xf3865010
Event: 374.296 Thread 0xae21ac00 Uncommon trap -34 fr.pc 0xf3865010
Event: 374.297 Thread 0xae21ac00 Uncommon trap -34 fr.pc 0xf3865010
Event: 374.298 Thread 0xae21ac00 Uncommon trap -34 fr.pc 0xf3865010
Event: 374.307 Thread 0xf6707000 Uncommon trap -83 fr.pc 0xf37e7600

Internal exceptions (10 events):
Event: 365.724 Thread 0xa1c55800 Implicit null exception at 0xf3ae0e67 to 0xf3ae1039
Event: 365.754 Thread 0xae48f800 Threw 0xe7c8ca40 at  /HUDSON/workspace/jdk7u7-2-build-linux-i586-product/jdk7u7/hotspot/src/share/vm/prims/nativeLookup.cpp:376
Event: 374.034 Thread 0xa1c55800 Implicit null exception at 0xf3bd4d57 to 0xf3bd7545
Event: 374.060 Thread 0xae466c00 Threw 0xe3af43a8 at  /HUDSON/workspace/jdk7u7-2-build-linux-i586-product/jdk7u7/hotspot/src/share/vm/prims/nativeLookup.cpp:376
Event: 374.061 Thread 0xae466c00 Threw 0xe3af55c0 at  /HUDSON/workspace/jdk7u7-2-build-linux-i586-product/jdk7u7/hotspot/src/share/vm/prims/nativeLookup.cpp:376
Event: 374.065 Thread 0xae466800 Threw 0xe3a9e908 at  /HUDSON/workspace/jdk7u7-2-build-linux-i586-product/jdk7u7/hotspot/src/share/vm/prims/nativeLookup.cpp:376
Event: 374.103 Thread 0xae466c00 Threw 0xe3b11a88 at  /HUDSON/workspace/jdk7u7-2-build-linux-i586-product/jdk7u7/hotspot/src/share/vm/prims/nativeLookup.cpp:376
Event: 374.170 Thread 0xae466800 Threw 0xe3b79170 at  /HUDSON/workspace/jdk7u7-2-build-linux-i586-product/jdk7u7/hotspot/src/share/vm/prims/nativeLookup.cpp:376
Event: 374.293 Thread 0xae21ac00 Implicit null exception at 0xf3862be3 to 0xf3863609
Event: 374.294 Thread 0xae21ac00 Implicit null exception at 0xf38612df to 0xf3861675

Events (10 events):
Event: 374.297 Thread 0xae21ac00 DEOPT PACKING pc=0xf3865010 sp=0xa5defb30
Event: 374.297 Thread 0xae21ac00 DEOPT UNPACKING pc=0xf372defc sp=0xa5defb18 mode 2
Event: 374.298 Thread 0xae21ac00 DEOPT PACKING pc=0xf3865010 sp=0xa5defb30
Event: 374.298 Thread 0xae21ac00 DEOPT UNPACKING pc=0xf372defc sp=0xa5defb18 mode 2
Event: 374.302 Thread 0xaafe3800 flushing nmethod 0xf3a39c48
Event: 374.303 Thread 0xa1c55800 Thread exited: 0xa1c55800
Event: 374.303 Thread 0xaafe1800 flushing nmethod 0xf3abf8c8
Event: 374.303 Thread 0xaafe1800 flushing nmethod 0xf3accf48
Event: 374.307 Thread 0xf6707000 DEOPT PACKING pc=0xf37e7600 sp=0xf6940ec0
Event: 374.307 Thread 0xf6707000 DEOPT UNPACKING pc=0xf372defc sp=0xf6940ea0 mode 2


Dynamic libraries:
08048000-08049000 r-xp 00000000 08:01 1448203                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/bin/java
08049000-0804a000 rw-p 00000000 08:01 1448203                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/bin/java
08448000-086f9000 rw-p 00000000 00:00 0                                  [heap]
a1100000-a11e9000 rw-p 00000000 00:00 0 
a11e9000-a1200000 ---p 00000000 00:00 0 
a1200000-a12f9000 rw-p 00000000 00:00 0 
a12f9000-a1300000 ---p 00000000 00:00 0 
a1300000-a13d7000 rw-p 00000000 00:00 0 
a13d7000-a1400000 ---p 00000000 00:00 0 
a1400000-a14f2000 rw-p 00000000 00:00 0 
a14f2000-a1500000 ---p 00000000 00:00 0 
a1500000-a15fd000 rw-p 00000000 00:00 0 
a15fd000-a1600000 ---p 00000000 00:00 0 
a1600000-a16f1000 rw-p 00000000 00:00 0 
a16f1000-a1700000 ---p 00000000 00:00 0 
a1700000-a17f9000 rw-p 00000000 00:00 0 
a17f9000-a1800000 ---p 00000000 00:00 0 
a1900000-a19ff000 rw-p 00000000 00:00 0 
a19ff000-a1a00000 ---p 00000000 00:00 0 
a1b00000-a1bfe000 rw-p 00000000 00:00 0 
a1bfe000-a1c00000 ---p 00000000 00:00 0 
a1c00000-a1cff000 rw-p 00000000 00:00 0 
a1cff000-a1d00000 ---p 00000000 00:00 0 
a1e00000-a1f00000 rw-p 00000000 00:00 0 
a2000000-a20ff000 rw-p 00000000 00:00 0 
a20ff000-a2100000 ---p 00000000 00:00 0 
a2100000-a21fa000 rw-p 00000000 00:00 0 
a21fa000-a2200000 ---p 00000000 00:00 0 
a2200000-a22f2000 rw-p 00000000 00:00 0 
a22f2000-a2300000 ---p 00000000 00:00 0 
a2300000-a23e9000 rw-p 00000000 00:00 0 
a23e9000-a2400000 ---p 00000000 00:00 0 
a2400000-a2500000 rw-p 00000000 00:00 0 
a2500000-a25fb000 rw-p 00000000 00:00 0 
a25fb000-a2600000 ---p 00000000 00:00 0 
a2600000-a27ff000 rw-p 00000000 00:00 0 
a27ff000-a2800000 ---p 00000000 00:00 0 
a2800000-a2900000 rw-p 00000000 00:00 0 
a2908000-a290b000 ---p 00000000 00:00 0 
a290b000-a2959000 rwxp 00000000 00:00 0                                  [stack:11192]
a2959000-a295c000 ---p 00000000 00:00 0 
a295c000-a29aa000 rwxp 00000000 00:00 0 
a29aa000-a31aa000 rw-s 00000000 00:04 16908298                           /SYSV00000000 (deleted)
a31aa000-a31f7000 r--p 00000000 08:01 5900042                             /usr/share/fonts/truetype/dejavu/DejaVuSansMono-Bold.ttf
a31f7000-a324f000 r--p 00000000 08:01 5899921                             /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-BI.ttf
a324f000-a32ae000 r--p 00000000 08:01 5900032                             /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-RI.ttf
a32ae000-a3300000 r--p 00000000 08:01 5900031                             /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
a3300000-a3400000 rw-p 00000000 00:00 0 
a3410000-a34a6000 r--s 00944000 08:01 1317151                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.jdt.ui_3.8.1.v20120814-144251.jar
a34a6000-a3500000 r--s 0052c000 08:01 1317005                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.ui_5.4.0.410755.jar
a3500000-a35ff000 rw-p 00000000 00:00 0 
a35ff000-a3600000 ---p 00000000 00:00 0 
a36af000-a36b2000 ---p 00000000 00:00 0 
a36b2000-a3700000 rwxp 00000000 00:00 0 
a3700000-a3800000 rw-p 00000000 00:00 0 
a3842000-a3864000 r--s 00184000 08:01 1317200                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.tasks.ui_3.8.1.v20120725-0100.jar
a38af000-a38b2000 ---p 00000000 00:00 0 
a38b2000-a3900000 rwxp 00000000 00:00 0                                  [stack:10825]
a3900000-a3a00000 rw-p 00000000 00:00 0 
a3a3b000-a3a9a000 r-xp 00000000 08:01 1447455                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libt2k.so
a3a9a000-a3a9e000 rw-p 0005f000 08:01 1447455                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libt2k.so
a3a9e000-a3aa2000 rw-p 00000000 00:00 0 
a3aa2000-a3ae4000 r-xp 00000000 08:01 1447463                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libfontmanager.so
a3ae4000-a3ae7000 rw-p 00041000 08:01 1447463                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libfontmanager.so
a3ae7000-a3aeb000 rw-p 00000000 00:00 0 
a3aeb000-a3aee000 ---p 00000000 00:00 0 
a3aee000-a3b3c000 rwxp 00000000 00:00 0                                  [stack:10852]
a3b3c000-a3b5a000 r--s 00180000 08:01 1317278                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.team.cvs.ui_3.3.500.v20120522-1148.jar
a3b5a000-a3b75000 r--s 0018b000 08:01 1317162                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.jgit_2.2.0.201212191850-r.jar
a3b75000-a3b9f000 r--s 0044e000 08:01 1317143                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.jdt.core_3.8.2.v20120814-155456.jar
a3bbc000-a3bbf000 ---p 00000000 00:00 0 
a3bbf000-a3c0d000 rwxp 00000000 00:00 0 
a3c0d000-a3c10000 ---p 00000000 00:00 0 
a3c10000-a3c5e000 rwxp 00000000 00:00 0                                  [stack:10842]
a3c5e000-a3c61000 ---p 00000000 00:00 0 
a3c61000-a3caf000 rwxp 00000000 00:00 0                                  [stack:10822]
a3caf000-a3cb2000 ---p 00000000 00:00 0 
a3cb2000-a3d00000 rwxp 00000000 00:00 0                                  [stack:10843]
a3d00000-a3df9000 rw-p 00000000 00:00 0 
a3df9000-a3e00000 ---p 00000000 00:00 0 
a3e00000-a3e09000 r--s 00063000 08:01 1316999                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.make.core_7.2.0.410755.jar
a3e09000-a3e1a000 r--s 00137000 08:01 1317001                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.managedbuilder.core_8.1.0.410755.jar
a3e1c000-a3e30000 r-xp 00000000 08:01 1444795                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.vista.vp.profiler.native.linux_3.0.0.201304171241/libmgc_vp_analysis_db_reader.so
a3e30000-a3e31000 r--p 00014000 08:01 1444795                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.vista.vp.profiler.native.linux_3.0.0.201304171241/libmgc_vp_analysis_db_reader.so
a3e31000-a3e32000 rw-p 00015000 08:01 1444795                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.vista.vp.profiler.native.linux_3.0.0.201304171241/libmgc_vp_analysis_db_reader.so
a3e4f000-a3ed5000 r-xp 00000000 08:01 1447446                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libawt.so
a3ed5000-a3edc000 rw-p 00086000 08:01 1447446                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libawt.so
a3edc000-a3f00000 rw-p 00000000 00:00 0 
a3f00000-a3f21000 rw-p 00000000 00:00 0 
a3f21000-a4000000 ---p 00000000 00:00 0 
a4001000-a400a000 r--s 00089000 08:01 1317315                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.update.core_3.2.600.v20120530-120908.jar
a400a000-a4053000 r-xp 00000000 08:01 1447427                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/xawt/libmawt.so
a4053000-a4056000 rw-p 00048000 08:01 1447427                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/xawt/libmawt.so
a4059000-a4068000 r--s 000b4000 08:01 1704751                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/36/1/.cp/library.jar
a4068000-a4070000 r--s 00000000 08:01 18899957                            /home/eejaz/.local/share/gvfs-metadata/root-88886952.log (deleted)
a4070000-a407a000 r--s 00071000 08:01 1317003                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.managedbuilder.ui_8.1.0.410755.jar
a407a000-a4091000 r-xp 00000000 08:01 1444772                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.ui.linux.x86_1.1.0.410755/os/linux/x86/libplatform.so
a4091000-a4093000 rw-p 00016000 08:01 1444772                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.ui.linux.x86_1.1.0.410755/os/linux/x86/libplatform.so
a4093000-a4098000 rw-p 00000000 00:00 0 
a409b000-a409e000 ---p 00000000 00:00 0 
a409e000-a40ac000 rwxp 00000000 00:00 0 
a40ac000-a40af000 r--s 0002e000 08:01 1447409                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/ext/sunjce_provider.jar
a40af000-a40e2000 r-xp 00000000 08:01 1447459                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libsunec.so
a40e2000-a40e6000 rw-p 00032000 08:01 1447459                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libsunec.so
a40e6000-a40ea000 rw-p 00000000 00:00 0 
a40ea000-a40ed000 r--s 00038000 08:01 1447408                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/ext/sunpkcs11.jar
a40ed000-a40f0000 r--s 00018000 08:01 1447571                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/jce.jar
a40f0000-a40f7000 r--s 00000000 08:01 5382507                            /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
a40f7000-a4100000 r--s 00059000 08:01 1317275                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.team.core_3.6.100.v20120524-0627.jar
a4100000-a41fc000 rw-p 00000000 00:00 0 
a41fc000-a4200000 ---p 00000000 00:00 0 
a4200000-a4300000 rw-p 00000000 00:00 0 
a4300000-a43ff000 rw-p 00000000 00:00 0 
a43ff000-a4400000 ---p 00000000 00:00 0 
a4400000-a44fd000 rw-p 00000000 00:00 0 
a44fd000-a4500000 ---p 00000000 00:00 0 
a4500000-a45c9000 rw-p 00000000 00:00 0 
a45c9000-a4600000 ---p 00000000 00:00 0 
a4600000-a46ff000 rw-p 00000000 00:00 0 
a46ff000-a4700000 ---p 00000000 00:00 0 
a4700000-a47f7000 rw-p 00000000 00:00 0 
a47f7000-a4800000 ---p 00000000 00:00 0 
a4800000-a4801000 rw-s 00000000 08:01 14169524                           /tmp/mgls_shared_mutex_10754
a4805000-a4808000 ---p 00000000 00:00 0 
a4808000-a4856000 rwxp 00000000 00:00 0                                  [stack:10813]
a4856000-a4859000 ---p 00000000 00:00 0 
a4859000-a48a7000 rwxp 00000000 00:00 0                                  [stack:10812]
a48a7000-a48af000 r--s 00070000 08:01 1317245                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.rse.files.ui_3.2.100.201205300905.jar
a48af000-a4900000 rwxp 00000000 00:00 0                                  [stack:10797]
a4900000-a4b00000 rw-p 00000000 00:00 0 
a4b00000-a4bfd000 rw-p 00000000 00:00 0 
a4bfd000-a4c00000 ---p 00000000 00:00 0 
a4c00000-a4cfb000 rw-p 00000000 00:00 0 
a4cfb000-a4d00000 ---p 00000000 00:00 0 
a4d00000-a4efb000 rw-p 00000000 00:00 0 
a4efb000-a4f00000 ---p 00000000 00:00 0 
a4f00000-a4ffc000 rw-p 00000000 00:00 0 
a4ffc000-a5000000 ---p 00000000 00:00 0 
a5000000-a5005000 r--s 00024000 08:01 1317184                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.commons.workbench_3.8.1.v20120725-0100.jar
a5005000-a500d000 r--s 0004d000 08:01 1317060                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.debug.core_3.7.100.v20120521-2012.jar
a500d000-a5010000 ---p 00000000 00:00 0 
a5010000-a505e000 rwxp 00000000 00:00 0 
a505e000-a5061000 ---p 00000000 00:00 0 
a5061000-a50af000 rwxp 00000000 00:00 0 
a50af000-a50b2000 ---p 00000000 00:00 0 
a50b2000-a5100000 rwxp 00000000 00:00 0                                  [stack:11319]
a5100000-a51fc000 rw-p 00000000 00:00 0 
a51fc000-a5200000 ---p 00000000 00:00 0 
a5200000-a52d9000 rw-p 00000000 00:00 0 
a52d9000-a5300000 ---p 00000000 00:00 0 
a5300000-a5400000 rw-p 00000000 00:00 0 
a5400000-a5600000 rw-p 00000000 00:00 0 
a5608000-a560c000 r--s 00021000 08:01 1704765                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/50/1/.cp/library.jar
a560c000-a5628000 r--s 00145000 08:01 1317279                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.team.ui_3.6.200.v20120522-1148.jar
a5628000-a5639000 r--s 00106000 08:01 1316836                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.codesourcery.target_2013.5.0.26.jar
a5639000-a563c000 ---p 00000000 00:00 0 
a563c000-a568a000 rwxp 00000000 00:00 0                                  [stack:11316]
a568d000-a569b000 r--s 00099000 08:01 1573899                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.toolchains.ui.nucleus_1.0.0.201307231101/toolchains.ui.nucleus.jar
a569b000-a56e7000 r--s 0047e000 08:01 1316980                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.core_5.4.0.410755.jar
a56e7000-a5700000 r--s 00105000 08:01 1316986                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.debug.ui_7.2.0.410755.jar
a5700000-a5743000 rw-p 00000000 00:00 0 
a5743000-a5800000 ---p 00000000 00:00 0 
a5800000-a58fb000 rw-p 00000000 00:00 0 
a58fb000-a5900000 ---p 00000000 00:00 0 
a5900000-a5a00000 rw-p 00000000 00:00 0 
a5a00000-a5afe000 rw-p 00000000 00:00 0 
a5afe000-a5b00000 ---p 00000000 00:00 0 
a5b06000-a5b0e000 r--s 00074000 08:01 1316743                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.ashling.pf.trace.ui_1.0.0.201304181957.jar
a5b0e000-a5b16000 r--s 0004c000 08:01 1317111                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.metadata_2.1.0.v20120430-2001.jar
a5b16000-a5b49000 r--s 00265000 08:01 1317061                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.debug.ui_3.8.150.410755.jar
a5b49000-a5b4d000 r--s 00022000 08:01 1317286                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui_3.8.0.v20120523-1546.jar
a5b54000-a5b5e000 r--s 0005e000 08:01 1317297                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.navigator_3.5.250.410755.jar
a5b5e000-a5b61000 ---p 00000000 00:00 0 
a5b61000-a5baf000 rwxp 00000000 00:00 0 
a5bb0000-a5bba000 r--s 0006c000 08:01 1317000                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.make.ui_7.2.0.410755.jar
a5bba000-a5bce000 r--s 000df000 08:01 1317161                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.jface.text_3.8.1.v20120828-155502.jar
a5bce000-a5bda000 r--s 00081000 08:01 1317290                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.editors_3.8.0.v20120523-1540.jar
a5bdc000-a5be1000 r--s 0001b000 08:01 1317203                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.team.ui_3.8.1.v20120725-0100.jar
a5be1000-a5bec000 r--s 00084000 08:01 1317313                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.workbench.texteditor_3.8.0.v20120523-1310.jar
a5bed000-a5bf1000 r--s 0001d000 08:01 1317118                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.repository_2.2.0.v20120524-1945.jar
a5bf1000-a5bf4000 r--s 0000f000 08:01 1317103                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.core_2.2.50.410755.jar
a5bf4000-a5bf7000 r--s 00018000 08:01 1317131                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.security_1.1.100.v20120522-1841.jar
a5bf7000-a5bfb000 r--s 00024000 08:01 1317289                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.console_3.5.100.v20120521-2012.jar
a5bfb000-a5bfe000 r--s 0001b000 08:01 1317298                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.navigator.resources_3.4.450.410755.jar
a5bfe000-a5c00000 r--s 0000e000 08:01 1317007                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.compare.core_3.5.200.v20120522-1148.jar
a5c00000-a5d00000 rw-p 00000000 00:00 0 
a5d00000-a5d01000 r--s 00003000 08:01 1447407                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/ext/sunec.jar
a5d01000-a5d06000 r--s 00038000 08:01 1317280                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.text_3.5.200.v20120523-1310.jar
a5d10000-a5d14000 r--s 0002d000 08:01 1317108                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.engine_2.2.0.v20120501-1502.jar
a5d14000-a5d1b000 r-xp 00000000 08:01 1447442                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libmanagement.so
a5d1b000-a5d1c000 rw-p 00006000 08:01 1447442                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libmanagement.so
a5d1c000-a5d1f000 ---p 00000000 00:00 0 
a5d1f000-a5d6d000 rwxp 00000000 00:00 0 
a5d6d000-a5d76000 r--s 0005a000 08:01 1317197                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.tasks.core_3.8.1.v20120725-0100.jar
a5d76000-a5da0000 r--s 00212000 08:01 1317078                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.egit.ui_2.2.0.201212191850-r.jar
a5da0000-a5da3000 ---p 00000000 00:00 0 
a5da3000-a5df1000 rwxp 00000000 00:00 0                                  [stack:10855]
a5df1000-a5e51000 rw-s 00000000 00:04 16711709                           /SYSV00000000 (deleted)
a5e51000-a5e52000 ---p 00000000 00:00 0 
a5e52000-a6652000 rwxp 00000000 00:00 0 
a6652000-a6653000 ---p 00000000 00:00 0 
a6653000-a6e53000 rwxp 00000000 00:00 0 
a6e53000-a6ea7000 r-xp 00000000 08:01 5244169                            /usr/lib/i386-linux-gnu/libibus-1.0.so.5.0.503
a6ea7000-a6ea8000 r--p 00054000 08:01 5244169                            /usr/lib/i386-linux-gnu/libibus-1.0.so.5.0.503
a6ea8000-a6ea9000 rw-p 00055000 08:01 5244169                            /usr/lib/i386-linux-gnu/libibus-1.0.so.5.0.503
a6ea9000-a6eab000 r--s 00009000 08:01 1316877                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.vista.vp.mi_3.0.0.201304171241.jar
a6eab000-a6eb5000 r--s 00085000 08:01 1317276                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.team.cvs.core_3.3.500.v20120522-1148.jar
a6eb5000-a6eb8000 r--s 00038000 08:01 1316842                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.jcraft.jsch_0.1.46.v201205102330.jar
a6eb8000-a6ebe000 r--s 0003d000 08:01 1317169                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.bugzilla.ui_3.8.1.v20120725-0100.jar
a6ebe000-a6ec4000 r--s 0004b000 08:01 1317074                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.egit.core_2.2.0.201212191850-r.jar
a6ec4000-a6ec6000 r--s 00017000 08:01 1317314                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.update.configurator_3.3.200.v20120523-1742.jar
a6ec6000-a6ecf000 r-xp 00000000 08:01 1704668                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-atk-gtk-3834.so
a6ecf000-a6ed0000 rw-p 00009000 08:01 1704668                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-atk-gtk-3834.so
a6ed0000-a6ed6000 r-xp 00000000 08:01 7867231                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
a6ed6000-a6ed7000 r--p 00005000 08:01 7867231                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
a6ed7000-a6ed8000 rw-p 00006000 08:01 7867231                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
a6ed8000-a6f00000 r--s 00219000 08:01 1317293                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.ide_3.8.1.v20120829-085332.jar
a6f00000-a7000000 rw-p 00000000 00:00 0 
a7000000-a7003000 r--s 00013000 08:01 1835546                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/57/1/.cp/library.jar
a7003000-a700d000 r-xp 00000000 08:01 1704661                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-cairo-gtk-3834.so
a700d000-a700e000 rw-p 0000a000 08:01 1704661                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-cairo-gtk-3834.so
a700e000-a7012000 r-xp 00000000 08:01 6817571                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
a7012000-a7013000 r--p 00003000 08:01 6817571                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
a7013000-a7014000 rw-p 00004000 08:01 6817571                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
a7015000-a7067000 r--p 00000000 08:01 5900041                            /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
a7067000-a70be000 r--p 00000000 08:01 5899951                             /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
a70be000-a70bf000 r--s 00000000 08:01 18878954                             /home/eejaz/.cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-4
a70bf000-a70c7000 r--s 00000000 08:01 18878953                             /home/eejaz/.cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
a70c7000-a70cd000 r--s 00000000 08:01 18879305                             /home/eejaz/.cache/fontconfig/a6d8cf8e4ec09cdbc8633c31745a07dd-le32d4.cache-4
a70cd000-a70d1000 r--s 00000000 08:01 18878951                             /home/eejaz/.cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
a70d1000-a7100000 r--s 00000000 08:01 18879302                             /home/eejaz/.cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-4
a7100000-a7102000 r--s 00008000 08:01 1317163                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.jsch.core_1.1.400.v20120522-1148.jar
a7102000-a7104000 r--s 0000f000 08:01 1317201                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.tasks.search_3.8.1.v20120725-0100.jar
a7104000-a7107000 r--s 0000e000 08:01 1317294                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.ide.application_1.0.400.v20120523-1956.jar
a7107000-a710a000 r--s 00013000 08:01 1317087                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.app_1.3.100.v20120522-1841.jar
a7111000-a7114000 r-xp 00000000 08:01 1835559                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/195/1/.cp/os/linux/x86/libspawner.so
a7114000-a7115000 rw-p 00002000 08:01 1835559                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/195/1/.cp/os/linux/x86/libspawner.so
a7115000-a711c000 r--s 00041000 08:01 1317183                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.commons.ui_3.8.1.v20120725-0100.jar
a711c000-a711e000 r--s 0000b000 08:01 1317194                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.monitor.ui_3.8.1.v20120725-0100.jar
a711e000-a7121000 r--s 00014000 08:01 1317303                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.600.v20120521-2344/universal.jar
a7121000-a7127000 r-xp 00000000 08:01 6817575                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-gif.so
a7127000-a7128000 r--p 00005000 08:01 6817575                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-gif.so
a7128000-a7129000 rw-p 00006000 08:01 6817575                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-gif.so
a7129000-a712b000 r--s 0000d000 08:01 1317113                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.operations_2.2.0.v20120524-0542.jar
a712b000-a712d000 r--s 00005000 08:01 1316979                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.codan.ui.cxx_3.0.0.410755.jar
a712d000-a712f000 r--s 00001000 08:01 1704943                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/30/1/.cp/library.jar
a712f000-a7131000 r--s 00014000 08:01 1316849                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.profiler.develop_2013.5.0.201305081124-60126.jar
a7131000-a7134000 r--s 00013000 08:01 1317015                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.expressions_3.4.400.v20120523-2004.jar
a7134000-a7136000 r--s 00015000 08:01 1317020                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.jobs_3.5.200.v20120521-2346.jar
a7137000-a713a000 r--s 0001a000 08:01 1317112                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.metadata.repository_1.2.100.v20120524-1717.jar
a713a000-a713d000 r--s 00011000 08:01 1317135                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.util_1.0.400.v20120522-2049.jar
a713e000-a7141000 r--s 0001a000 08:01 1317186                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.context.core_3.8.1.v20120725-0100.jar
a7141000-a7143000 r--s 00008000 08:01 1317193                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.monitor.core_3.8.1.v20120725-0100.jar
a7143000-a7146000 r--s 000da000 08:01 1316848                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.profiler.core_2013.5.0.201305081124-60126.jar
a7146000-a7148000 r-xp 00000000 08:01 1704681                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/232/1/.cp/os/linux/x86/libunixfile_1_0_0.so
a7148000-a7149000 rw-p 00001000 08:01 1704681                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/232/1/.cp/os/linux/x86/libunixfile_1_0_0.so
a7149000-a714b000 r--s 0000c000 08:01 1316844                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.profiler_2013.5.0.201305081124-60126.jar
a714c000-a7157000 r--s 000bb000 08:01 1317023                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.resources_3.8.1.v20120802-154922.jar
a7157000-a7200000 r--p 00000000 08:01 5900040                            /usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf
a7200000-a7300000 rw-p 00000000 00:00 0 
a7300000-a73fe000 rw-p 00000000 00:00 0 
a73fe000-a7400000 ---p 00000000 00:00 0 
a7400000-a74fa000 rw-p 00000000 00:00 0 
a74fa000-a7500000 ---p 00000000 00:00 0 
a7500000-a76fc000 rw-p 00000000 00:00 0 
a76fc000-a7700000 ---p 00000000 00:00 0 
a7700000-a77fd000 rw-p 00000000 00:00 0 
a77fd000-a7800000 ---p 00000000 00:00 0 
a7800000-a78fa000 rw-p 00000000 00:00 0 
a78fa000-a7900000 ---p 00000000 00:00 0 
a7900000-a7902000 r--s 00000000 08:01 18878952                             /home/eejaz/.cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-4
a7902000-a7903000 r--s 00000000 08:01 18878950                             /home/eejaz/.cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-4
a7903000-a7904000 r--s 00000000 08:01 18878949                             /home/eejaz/.cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-4
a7904000-a7909000 r--s 00000000 08:01 18878948                             /home/eejaz/.cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4
a7909000-a790c000 r--s 00000000 08:01 18878947                             /home/eejaz/.cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
a790c000-a791b000 r--s 00000000 08:01 18878946                             /home/eejaz/.cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4
a791b000-a791c000 r--s 00000000 08:01 18878945                             /home/eejaz/.cache/fontconfig/1ac9eb803944fde146138c791f5cc56a-le32d4.cache-4
a791c000-a791f000 r--s 00000000 08:01 18878944                             /home/eejaz/.cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4
a791f000-a7920000 r--s 00000000 08:01 18878943                             /home/eejaz/.cache/fontconfig/dc05db6664285cc2f12bf69c139ae4c3-le32d4.cache-4
a7920000-a7923000 r--s 00000000 08:01 18899894                             /home/eejaz/.cache/fontconfig/0640bd2b628cb180ad47a3bf3cc9c40e-le32d4.cache-4
a7923000-a7925000 r--s 00000000 08:01 18878942                             /home/eejaz/.cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4
a7925000-a7927000 r--s 00000000 08:01 18879101                             /home/eejaz/.cache/fontconfig/2fe16cf53f8bd2da9ea33d9eb6e69eee-le32d4.cache-4
a7927000-a7928000 r--s 00000000 08:01 18878941                             /home/eejaz/.cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-4
a7928000-a792b000 r--s 00000000 08:01 18878940                             /home/eejaz/.cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4
a792b000-a792e000 r--s 00000000 08:01 18879002                             /home/eejaz/.cache/fontconfig/c57959a16110560c8d0fcea73374aeeb-le32d4.cache-4
a792e000-a7933000 r--s 00000000 08:01 18878939                             /home/eejaz/.cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le32d4.cache-4
a7933000-a7934000 r--s 00000000 08:01 18878938                             /home/eejaz/.cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le32d4.cache-4
a7934000-a7935000 r--s 00000000 08:01 18878937                             /home/eejaz/.cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le32d4.cache-4
a7935000-a7939000 r--s 00000000 08:01 18878936                             /home/eejaz/.cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le32d4.cache-4
a7939000-a7940000 r--s 00000000 08:01 18879299                             /home/eejaz/.cache/fontconfig/52f7bdb7ce746bfd7eaa1985bd9cfa93-le32d4.cache-4
a7940000-a7950000 r--s 00000000 08:01 18878935                             /home/eejaz/.cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-4
a7950000-a7957000 r--s 00000000 08:01 18879297                             /home/eejaz/.cache/fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-4
a7957000-a795a000 r--s 00000000 08:01 18878934                             /home/eejaz/.cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-le32d4.cache-4
a795a000-a795c000 r--s 00000000 08:01 18899897                             /home/eejaz/.cache/fontconfig/c19b55eb3b4c5b40ea175e31682068a5-le32d4.cache-4
a795c000-a7966000 r--s 00000000 08:01 18878924                             /home/eejaz/.cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-4
a7966000-a79c1000 r-xp 00000000 08:01 1704660                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-pi-gtk-3834.so
a79c1000-a79c3000 rw-p 0005a000 08:01 1704660                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-pi-gtk-3834.so
a79c3000-a79c4000 rw-p 00000000 00:00 0 
a79c4000-a7a00000 r--s 00629000 08:01 1316841                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.ibm.icu_4.4.2.v20110823.jar
a7a00000-a7afc000 rw-p 00000000 00:00 0 
a7afc000-a7b00000 ---p 00000000 00:00 0 
a7b00000-a7bf8000 rw-p 00000000 00:00 0 
a7bf8000-a7c00000 ---p 00000000 00:00 0 
a7c00000-a7cee000 rw-p 00000000 00:00 0 
a7cee000-a7d00000 ---p 00000000 00:00 0 
a7d00000-a7d01000 r--s 00000000 08:01 18899893                             /home/eejaz/.cache/fontconfig/50a3e3d330c3bfb1cc2f322b9f98a2ef-le32d4.cache-4
a7d01000-a7d04000 r--s 00000000 08:01 18899888                             /home/eejaz/.cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-4
a7d04000-a7d09000 r--s 00000000 08:01 18899213                             /home/eejaz/.cache/fontconfig/dca44306019589c3e1b1d3d84e2ead21-le32d4.cache-4
a7d09000-a7d0d000 rwxp 00000000 00:00 0 
a7d0d000-a7d12000 r-xp 00000000 08:01 5245415                            /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
a7d12000-a7d13000 r--p 00004000 08:01 5245415                            /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
a7d13000-a7d14000 rw-p 00005000 08:01 5245415                            /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
a7d14000-a7d15000 r-xp 00000000 08:01 5248231                            /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3800.1
a7d15000-a7d16000 r--p 00000000 08:01 5248231                            /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3800.1
a7d16000-a7d17000 rw-p 00001000 08:01 5248231                            /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3800.1
a7d17000-a7d5e000 r--s 003b4000 08:01 1317312                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.workbench_3.8.1.v20120816-082703.jar
a7d5e000-a7e00000 rwxp 00000000 00:00 0                                  [stack:10779]
a7e00000-a7efc000 rw-p 00000000 00:00 0 
a7efc000-a7f00000 ---p 00000000 00:00 0 
a7f00000-a7f01000 r--s 00000000 08:01 18878933                             /home/eejaz/.cache/fontconfig/0c9eb80ebd1c36541ebe2852d3bb0c49-le32d4.cache-4
a7f01000-a7f04000 r-xp 00000000 08:01 1704659                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-gtk-3834.so
a7f04000-a7f05000 rw-p 00002000 08:01 1704659                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/486/1/.cp/libswt-gtk-3834.so
a7f05000-a7f06000 rw-p 00000000 00:00 0 
a7f07000-a7f0a000 r--s 00022000 08:01 1316878                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.vista.vp.profiler_3.0.0.201304171241.jar
a7f0a000-a7f0d000 r--s 00014000 08:01 1317196                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.tasks.bugs_3.8.1.v20120725-0100.jar
a7f0d000-a7f10000 ---p 00000000 00:00 0 
a7f10000-a8000000 rwxp 00000000 00:00 0                                  [stack:10776]
a8000000-a80f8000 rw-p 00000000 00:00 0 
a80f8000-a8100000 ---p 00000000 00:00 0 
a8100000-a8115000 r--s 000f6000 08:01 1317159                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.jface_3.8.0.v20120521-2332.jar
a8115000-a812b000 r--s 00230000 08:01 1317274                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.8.1.v3834e.jar
a812b000-a812c000 r--s 00004000 08:01 1317273                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.swt_3.8.1.v3834e.jar
a812c000-a812d000 r--s 00002000 08:01 1447292                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.2.101.v20120523-1956/compatibility.jar
a812d000-a812f000 r--s 0000d000 08:01 1573821                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.toolchains.core.nucleus_1.0.0.201307231101/toolchains.core.jar
a8133000-a8135000 r--s 00004000 08:01 1317202                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.team.cvs_3.8.1.v20120725-0100.jar
a8135000-a8138000 r--s 0001a000 08:01 1316978                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.codan.ui_2.1.0.410755.jar
a8138000-a8139000 r--s 00002000 08:01 1316981                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.core.linux_5.2.0.410755.jar
a8139000-a813b000 r--s 0000f000 08:01 1317339                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.toolchains.core_1.0.0.201307231101/toolchains.core.jar
a813b000-a813e000 r--s 00014000 08:01 1316740                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.ashling.pf.tm.firmware_1.0.0.201304181957.jar
a813e000-a8141000 r--s 00018000 08:01 1317009                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.commands_3.6.1.v20120521-2332.jar
a8141000-a8143000 r--s 0000d000 08:01 1317126                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.ui.sdk.scheduler_1.1.0.v20110815-1744.jar
a8143000-a8145000 r--s 0000d000 08:01 1317018                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.filesystem_1.3.200.v20120522-2012.jar
a8145000-a814f000 r--s 00254000 08:01 1448155                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/resources.jar
a814f000-a81f1000 rwxp 00000000 00:00 0                                  [stack:10774]
a81f1000-a81ff000 r-xp 00000000 08:01 1447452                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libnio.so
a81ff000-a8200000 rw-p 0000e000 08:01 1447452                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libnio.so
a8200000-a8300000 rw-p 00000000 00:00 0 
a8300000-a8301000 r--s 00002000 08:01 1317019                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.filesystem.linux.x86_1.4.0.v20120522-1137.jar
a8301000-a8303000 r--s 0000a000 08:01 1316882                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.vista.vp.ui_3.0.0.201304171241.jar
a8303000-a8305000 r--s 0000d000 08:01 1706519                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/37/1/.cp/library.jar
a8305000-a8308000 r--s 0002a000 08:01 1317130                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.registry_3.5.200.v20120522-1841.jar
a8308000-a830a000 r--s 00007000 08:01 1317317                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.update.scheduler_3.2.400.v20120530-120908.jar
a830a000-a830c000 r--s 00007000 08:01 1317190                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.mylyn.ide.ui_3.8.1.v20120725-0100.jar
a830c000-a830e000 r--s 00005000 08:01 1704761                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/configuration/org.eclipse.osgi/bundles/48/1/.cp/library.jar
a830e000-a8322000 r-xp 00000000 08:01 1447479                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libnet.so
a8322000-a8323000 rw-p 00014000 08:01 1447479                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libnet.so
a8323000-a8337000 r--s 00141000 08:01 1317218                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.osgi_3.8.1.v20120830-144521.jar
a8337000-a8397000 rw-s 00000000 00:04 16678940                           /SYSV00000000 (deleted)
a8397000-a8398000 ---p 00000000 00:00 0 
a8398000-a8b98000 rwxp 00000000 00:00 0                                  [stack:10773]
a8b98000-a8b99000 ---p 00000000 00:00 0 
a8b99000-a9399000 rwxp 00000000 00:00 0                                  [stack:10772]
a9399000-a93cb000 r-xp 00000000 08:01 8520133                            /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
a93cb000-a93cd000 r--p 00032000 08:01 8520133                            /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
a93cd000-a93ce000 rw-p 00034000 08:01 8520133                            /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
a93ce000-a93fe000 r-xp 00000000 08:01 5768855                            /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
a93fe000-a93ff000 r--p 0002f000 08:01 5768855                            /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
a93ff000-a9400000 rw-p 00030000 08:01 5768855                            /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
a9400000-a94f4000 rw-p 00000000 00:00 0 
a94f4000-a9500000 ---p 00000000 00:00 0 
a9500000-a9501000 r--s 00017000 08:01 1316872                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.mentor.embedded.profiler.tmf_2013.5.0.201305081124-60126.jar
a9501000-a9503000 r--s 00003000 08:01 1317127                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.p2.updatechecker_1.1.200.v20110808-1657.jar
a9503000-a9506000 r--s 00018000 08:01 1317089                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.common_3.6.100.v20120522-1841.jar
a9506000-a9517000 r-xp 00000000 08:01 10749087                           /lib/i386-linux-gnu/libudev.so.1.3.5
a9517000-a9518000 r--p 00010000 08:01 10749087                           /lib/i386-linux-gnu/libudev.so.1.3.5
a9518000-a9519000 rw-p 00011000 08:01 10749087                           /lib/i386-linux-gnu/libudev.so.1.3.5
a9519000-a957c000 rw-p 00000000 00:00 0 
a957c000-a95a5000 r-xp 00000000 08:01 5247841                            /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
a95a5000-a95a6000 ---p 00029000 08:01 5247841                            /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
a95a6000-a95a7000 r--p 00029000 08:01 5247841                            /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
a95a7000-a95a8000 rw-p 0002a000 08:01 5247841                            /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
a95a8000-a95b1000 r-xp 00000000 08:01 5246373                            /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
a95b1000-a95b2000 r--p 00008000 08:01 5246373                            /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
a95b2000-a95b3000 rw-p 00009000 08:01 5246373                            /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
a95b3000-a95c5000 r-xp 00000000 08:01 5247798                            /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
a95c5000-a95c6000 ---p 00012000 08:01 5247798                            /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
a95c6000-a95c7000 r--p 00012000 08:01 5247798                            /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
a95c7000-a95c8000 rw-p 00013000 08:01 5247798                            /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
a95c8000-a95d0000 r-xp 00000000 08:01 5248001                            /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
a95d0000-a95d1000 r--p 00007000 08:01 5248001                            /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
a95d1000-a95d2000 rw-p 00008000 08:01 5248001                            /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
a95d2000-a95d3000 r--s 00000000 08:01 18899317                           /home/eejaz/.local/share/gvfs-metadata/root (deleted)
a95d3000-a95d6000 r-xp 00000000 08:01 6817568                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
a95d6000-a95d7000 r--p 00002000 08:01 6817568                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
a95d7000-a95d8000 rw-p 00003000 08:01 6817568                              /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
a95d8000-a95f9000 r--s 00000000 08:01 5374969                            /usr/share/mime/mime.cache
a95f9000-a962e000 r-xp 00000000 08:01 8129261                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
a962e000-a962f000 r--p 00034000 08:01 8129261                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
a962f000-a9630000 rw-p 00035000 08:01 8129261                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
a9630000-a964b000 r-xp 00000000 08:01 10748990                           /lib/i386-linux-gnu/libgcc_s.so.1
a964b000-a964c000 r--p 0001a000 08:01 10748990                           /lib/i386-linux-gnu/libgcc_s.so.1
a964c000-a964d000 rw-p 0001b000 08:01 10748990                           /lib/i386-linux-gnu/libgcc_s.so.1
a964d000-a972a000 r-xp 00000000 08:01 5245368                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
a972a000-a972e000 r--p 000dc000 08:01 5245368                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
a972e000-a972f000 rw-p 000e0000 08:01 5245368                            /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
a972f000-a9736000 rw-p 00000000 00:00 0 
a9736000-a9865000 r-xp 00000000 08:01 8129265                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
a9865000-a9866000 ---p 0012f000 08:01 8129265                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
a9866000-a9869000 r--p 0012f000 08:01 8129265                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
a9869000-a986a000 rw-p 00132000 08:01 8129265                             /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so
a986a000-a986b000 rw-p 00000000 00:00 0 
a986b000-a9889000 r-xp 00000000 08:01 5245345                            /usr/lib/i386-linux-gnu/libatk-1.0.so.0.21009.1
a9889000-a988b000 r--p 0001d000 08:01 5245345                            /usr/lib/i386-linux-gnu/libatk-1.0.so.0.21009.1
a988b000-a988c000 rw-p 0001f000 08:01 5245345                            /usr/lib/i386-linux-gnu/libatk-1.0.so.0.21009.1
a988c000-a9cf3000 r-xp 00000000 08:01 5247290                            /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.20
a9cf3000-a9cf7000 r--p 00466000 08:01 5247290                            /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.20
a9cf7000-a9cf9000 rw-p 0046a000 08:01 5247290                            /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.20
a9cf9000-a9cfb000 rw-p 00000000 00:00 0 
a9cfb000-a9d13000 r-xp 00000000 08:01 5247240                            /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
a9d13000-a9d14000 ---p 00018000 08:01 5247240                            /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
a9d14000-a9d15000 r--p 00018000 08:01 5247240                            /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
a9d15000-a9d16000 rw-p 00019000 08:01 5247240                            /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
a9d16000-a9d1b000 r-xp 00000000 08:01 5246726                            /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
a9d1b000-a9d1c000 r--p 00004000 08:01 5246726                            /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
a9d1c000-a9d1d000 rw-p 00005000 08:01 5246726                            /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
a9d1d000-a9d6e000 r-xp 00000000 08:01 5247228                            /usr/lib/i386-linux-gnu/libharfbuzz.so.0.919.0
a9d6e000-a9d6f000 r--p 00051000 08:01 5247228                            /usr/lib/i386-linux-gnu/libharfbuzz.so.0.919.0
a9d6f000-a9d70000 rw-p 00052000 08:01 5247228                            /usr/lib/i386-linux-gnu/libharfbuzz.so.0.919.0
a9d70000-a9d8f000 r-xp 00000000 08:01 5245403                            /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
a9d8f000-a9d90000 r--p 0001f000 08:01 5245403                            /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
a9d90000-a9d91000 rw-p 00020000 08:01 5245403                            /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
a9d91000-a9db7000 r-xp 00000000 08:01 10749068                           /lib/i386-linux-gnu/libpng12.so.0.49.0
a9db7000-a9db8000 r--p 00025000 08:01 10749068                           /lib/i386-linux-gnu/libpng12.so.0.49.0
a9db8000-a9db9000 rw-p 00026000 08:01 10749068                           /lib/i386-linux-gnu/libpng12.so.0.49.0
a9db9000-a9e5d000 r-xp 00000000 08:01 5245358                            /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
a9e5d000-a9e62000 r--p 000a4000 08:01 5245358                            /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
a9e62000-a9e63000 rw-p 000a9000 08:01 5245358                            /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
a9e63000-a9e88000 r-xp 00000000 08:01 10749056                           /lib/i386-linux-gnu/libexpat.so.1.6.0
a9e88000-a9e89000 ---p 00025000 08:01 10749056                           /lib/i386-linux-gnu/libexpat.so.1.6.0
a9e89000-a9e8b000 r--p 00025000 08:01 10749056                           /lib/i386-linux-gnu/libexpat.so.1.6.0
a9e8b000-a9e8c000 rw-p 00027000 08:01 10749056                           /lib/i386-linux-gnu/libexpat.so.1.6.0
a9e8c000-a9eac000 r-xp 00000000 08:01 10749047                           /lib/i386-linux-gnu/libselinux.so.1
a9eac000-a9ead000 r--p 0001f000 08:01 10749047                           /lib/i386-linux-gnu/libselinux.so.1
a9ead000-a9eae000 rw-p 00020000 08:01 10749047                           /lib/i386-linux-gnu/libselinux.so.1
a9eae000-a9f48000 r-xp 00000000 08:01 5245362                            /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
a9f48000-a9f4c000 r--p 00099000 08:01 5245362                            /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
a9f4c000-a9f4d000 rw-p 0009d000 08:01 5245362                            /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
a9f4d000-aa07d000 r-xp 00000000 08:01 5245405                            /usr/lib/i386-linux-gnu/libX11.so.6.3.0
aa07d000-aa07e000 ---p 00130000 08:01 5245405                            /usr/lib/i386-linux-gnu/libX11.so.6.3.0
aa07e000-aa07f000 r--p 00130000 08:01 5245405                            /usr/lib/i386-linux-gnu/libX11.so.6.3.0
aa07f000-aa081000 rw-p 00131000 08:01 5245405                            /usr/lib/i386-linux-gnu/libX11.so.6.3.0
aa081000-aa082000 rw-p 00000000 00:00 0 
aa082000-aa19f000 r-xp 00000000 08:01 5244659                            /usr/lib/i386-linux-gnu/libcairo.so.2.11200.16
aa19f000-aa1a1000 r--p 0011d000 08:01 5244659                            /usr/lib/i386-linux-gnu/libcairo.so.2.11200.16
aa1a1000-aa1a2000 rw-p 0011f000 08:01 5244659                            /usr/lib/i386-linux-gnu/libcairo.so.2.11200.16
aa1a2000-aa1a3000 rw-p 00000000 00:00 0 
aa1a3000-aa1db000 r-xp 00000000 08:01 5245364                            /usr/lib/i386-linux-gnu/libfontconfig.so.1.7.0
aa1db000-aa1dc000 r--p 00038000 08:01 5245364                            /usr/lib/i386-linux-gnu/libfontconfig.so.1.7.0
aa1dc000-aa1dd000 rw-p 00039000 08:01 5245364                            /usr/lib/i386-linux-gnu/libfontconfig.so.1.7.0
aa1dd000-aa349000 r-xp 00000000 08:01 5248232                            /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
aa349000-aa34a000 ---p 0016c000 08:01 5248232                            /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
aa34a000-aa34c000 r--p 0016c000 08:01 5248232                            /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
aa34c000-aa34d000 rw-p 0016e000 08:01 5248232                            /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
aa34d000-aa34e000 rw-p 00000000 00:00 0 
aa34e000-aa3f9000 r-xp 00000000 08:01 5243225                            /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.20
aa3f9000-aa3fb000 r--p 000ab000 08:01 5243225                            /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.20
aa3fb000-aa3fc000 rw-p 000ad000 08:01 5243225                            /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.20
aa3fc000-aa4fe000 r-xp 00000000 08:01 10748994                           /lib/i386-linux-gnu/libglib-2.0.so.0.3800.1
aa4fe000-aa4ff000 r--p 00101000 08:01 10748994                           /lib/i386-linux-gnu/libglib-2.0.so.0.3800.1
aa4ff000-aa500000 rw-p 00102000 08:01 10748994                           /lib/i386-linux-gnu/libglib-2.0.so.0.3800.1
aa500000-aa600000 rw-p 00000000 00:00 0 
aa600000-aa64a000 r-xp 00000000 08:01 5247234                            /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
aa64a000-aa64b000 ---p 0004a000 08:01 5247234                            /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
aa64b000-aa64c000 r--p 0004a000 08:01 5247234                            /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
aa64c000-aa64d000 rw-p 0004b000 08:01 5247234                            /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
aa64d000-aa68c000 r-xp 00000000 08:01 10748981                           /lib/i386-linux-gnu/libpcre.so.3.13.1
aa68c000-aa68d000 r--p 0003f000 08:01 10748981                           /lib/i386-linux-gnu/libpcre.so.3.13.1
aa68d000-aa68e000 rw-p 00040000 08:01 10748981                           /lib/i386-linux-gnu/libpcre.so.3.13.1
aa68e000-aa68f000 ---p 00000000 00:00 0 
aa68f000-aa70f000 rwxp 00000000 00:00 0                                  [stack:10767]
aa70f000-aa710000 ---p 00000000 00:00 0 
aa710000-aa790000 rwxp 00000000 00:00 0                                  [stack:10765]
aa790000-aa900000 r--p 001bc000 08:01 4986868                            /usr/lib/locale/locale-archive
aa900000-aab00000 r--p 00000000 08:01 4986868                            /usr/lib/locale/locale-archive
aab00000-aabff000 rw-p 00000000 00:00 0 
aabff000-aac00000 ---p 00000000 00:00 0 
aac00000-aac01000 r--s 00003000 08:01 1316982                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.cdt.core.linux.x86_5.2.0.410755.jar
aac01000-aac07000 r-xp 00000000 08:01 5243358                            /usr/lib/i386-linux-gnu/libdatrie.so.1.2.0
aac07000-aac08000 r--p 00006000 08:01 5243358                            /usr/lib/i386-linux-gnu/libdatrie.so.1.2.0
aac08000-aac09000 rw-p 00007000 08:01 5243358                            /usr/lib/i386-linux-gnu/libdatrie.so.1.2.0
aac09000-aac11000 r-xp 00000000 08:01 5244653                            /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
aac11000-aac12000 r--p 00008000 08:01 5244653                            /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
aac12000-aac13000 rw-p 00009000 08:01 5244653                            /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
aac13000-aac2b000 r-xp 00000000 08:01 10749060                           /lib/i386-linux-gnu/libz.so.1.2.8
aac2b000-aac2c000 r--p 00017000 08:01 10749060                           /lib/i386-linux-gnu/libz.so.1.2.8
aac2c000-aac2d000 rw-p 00018000 08:01 10749060                           /lib/i386-linux-gnu/libz.so.1.2.8
aac2d000-aac7d000 r-xp 00000000 08:01 5248168                            /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3800.1
aac7d000-aac7e000 r--p 0004f000 08:01 5248168                            /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3800.1
aac7e000-aac7f000 rw-p 00050000 08:01 5248168                            /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3800.1
aac7f000-aac80000 ---p 00000000 00:00 0 
aac80000-aad00000 rwxp 00000000 00:00 0                                  [stack:10764]
aad00000-aadf2000 rw-p 00000000 00:00 0 
aadf2000-aae00000 ---p 00000000 00:00 0 
aae00000-aae02000 r--s 00007000 08:01 1316752                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/com.codesourcery.help_2013.5.0.26.jar
aae02000-aae15000 r-xp 00000000 08:01 10749218                           /lib/i386-linux-gnu/libresolv-2.17.so
aae15000-aae16000 r--p 00013000 08:01 10749218                           /lib/i386-linux-gnu/libresolv-2.17.so
aae16000-aae17000 rw-p 00014000 08:01 10749218                           /lib/i386-linux-gnu/libresolv-2.17.so
aae17000-aae19000 rw-p 00000000 00:00 0 
aae19000-aae2c000 r-xp 00000000 08:01 5247238                            /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
aae2c000-aae2d000 r--p 00013000 08:01 5247238                            /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
aae2d000-aae2e000 rw-p 00014000 08:01 5247238                            /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
aae2e000-aae7f000 rwxp 00000000 00:00 0                                  [stack:10766]
aae7f000-aae80000 ---p 00000000 00:00 0 
aae80000-aaf00000 rwxp 00000000 00:00 0                                  [stack:10760]
aaf00000-aafff000 rw-p 00000000 00:00 0 
aafff000-ab000000 ---p 00000000 00:00 0 
ab000000-ab002000 r-xp 00000000 08:01 5245401                            /usr/lib/i386-linux-gnu/libXau.so.6.0.0
ab002000-ab003000 r--p 00001000 08:01 5245401                            /usr/lib/i386-linux-gnu/libXau.so.6.0.0
ab003000-ab004000 rw-p 00002000 08:01 5245401                            /usr/lib/i386-linux-gnu/libXau.so.6.0.0
ab004000-ab00c000 r-xp 00000000 08:01 5243500                            /usr/lib/i386-linux-gnu/libthai.so.0.2.0
ab00c000-ab00d000 r--p 00007000 08:01 5243500                            /usr/lib/i386-linux-gnu/libthai.so.0.2.0
ab00d000-ab00e000 rw-p 00008000 08:01 5243500                            /usr/lib/i386-linux-gnu/libthai.so.0.2.0
ab00e000-ab011000 r-xp 00000000 08:01 5248167                            /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3800.1
ab011000-ab012000 r--p 00002000 08:01 5248167                            /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3800.1
ab012000-ab013000 rw-p 00003000 08:01 5248167                            /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3800.1
ab013000-ab024000 r-xp 00000000 08:01 5245407                            /usr/lib/i386-linux-gnu/libXext.so.6.4.0
ab024000-ab025000 r--p 00010000 08:01 5245407                            /usr/lib/i386-linux-gnu/libXext.so.6.4.0
ab025000-ab026000 rw-p 00011000 08:01 5245407                            /usr/lib/i386-linux-gnu/libXext.so.6.4.0
ab026000-ab1e2000 r--s 031b4000 08:01 1447421                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/rt.jar
ab1e2000-adf00000 rw-p 00000000 00:00 0 
adf00000-adffa000 rw-p 00000000 00:00 0 
adffa000-ae000000 ---p 00000000 00:00 0 
ae000000-ae002000 r-xp 00000000 08:01 5244656                            /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
ae002000-ae003000 r--p 00001000 08:01 5244656                            /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
ae003000-ae004000 rw-p 00002000 08:01 5244656                            /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
ae004000-ae008000 r-xp 00000000 08:01 5243256                            /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
ae008000-ae009000 r--p 00003000 08:01 5243256                            /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
ae009000-ae00a000 rw-p 00004000 08:01 5243256                            /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
ae00a000-ae00c000 r-xp 00000000 08:01 5247282                            /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
ae00c000-ae00d000 r--p 00001000 08:01 5247282                            /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
ae00d000-ae00e000 rw-p 00002000 08:01 5247282                            /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
ae00e000-ae010000 r-xp 00000000 08:01 5243250                            /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
ae010000-ae011000 r--p 00001000 08:01 5243250                            /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
ae011000-ae012000 rw-p 00002000 08:01 5243250                            /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
ae012000-ae01b000 r-xp 00000000 08:01 5243726                            /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
ae01b000-ae01c000 r--p 00008000 08:01 5243726                            /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
ae01c000-ae01d000 rw-p 00009000 08:01 5243726                            /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
ae01d000-ae02c000 r-xp 00000000 08:01 5243222                            /usr/lib/i386-linux-gnu/libXi.so.6.1.0
ae02c000-ae02d000 r--p 0000e000 08:01 5243222                            /usr/lib/i386-linux-gnu/libXi.so.6.1.0
ae02d000-ae02e000 rw-p 0000f000 08:01 5243222                            /usr/lib/i386-linux-gnu/libXi.so.6.1.0
ae02e000-ae07f000 rwxp 00000000 00:00 0                                  [stack:10763]
ae07f000-ae080000 ---p 00000000 00:00 0 
ae080000-ae100000 rwxp 00000000 00:00 0                                  [stack:10759]
ae100000-ae200000 rw-p 00000000 00:00 0 
ae200000-ae2f8000 rw-p 00000000 00:00 0 
ae2f8000-ae300000 ---p 00000000 00:00 0 
ae300000-ae309000 r-xp 00000000 08:01 5246777                            /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
ae309000-ae30a000 r--p 00008000 08:01 5246777                            /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
ae30a000-ae30b000 rw-p 00009000 08:01 5246777                            /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
ae30b000-ae32c000 r-xp 00000000 08:01 5243247                            /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.1
ae32c000-ae32d000 r--p 00020000 08:01 5243247                            /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.1
ae32d000-ae32e000 rw-p 00021000 08:01 5243247                            /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.1
ae32e000-ae37f000 rwxp 00000000 00:00 0                                  [stack:10762]
ae37f000-ae380000 ---p 00000000 00:00 0 
ae380000-ae400000 rwxp 00000000 00:00 0                                  [stack:10758]
ae400000-ae4b5000 rw-p 00000000 00:00 0 
ae4b5000-ae500000 ---p 00000000 00:00 0 
ae500000-ae502000 r--s 00002000 08:01 1446278                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.runtime.compatibility.registry_3.5.100.v20120521-2346/runtime_registry_compatibility.jar
ae502000-ae504000 r-xp 00000000 08:01 5247227                            /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
ae504000-ae505000 r--p 00001000 08:01 5247227                            /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
ae505000-ae506000 rw-p 00002000 08:01 5247227                            /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
ae506000-ae50d000 r-xp 00000000 08:01 5245717                            /usr/lib/i386-linux-gnu/libogg.so.0.8.1
ae50d000-ae50e000 r--p 00006000 08:01 5245717                            /usr/lib/i386-linux-gnu/libogg.so.0.8.1
ae50e000-ae50f000 rw-p 00007000 08:01 5245717                            /usr/lib/i386-linux-gnu/libogg.so.0.8.1
ae50f000-ae51e000 r-xp 00000000 08:01 5248003                            /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
ae51e000-ae51f000 r--p 0000e000 08:01 5248003                            /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
ae51f000-ae520000 rw-p 0000f000 08:01 5248003                            /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
ae520000-ae524000 r-xp 00000000 08:01 5248005                            /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.9
ae524000-ae525000 r--p 00003000 08:01 5248005                            /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.9
ae525000-ae526000 rw-p 00004000 08:01 5248005                            /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.9
ae526000-ae52b000 r-xp 00000000 08:01 8520100                             /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
ae52b000-ae52c000 r--p 00004000 08:01 8520100                             /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
ae52c000-ae52d000 rw-p 00005000 08:01 8520100                             /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
ae52d000-ae57e000 rwxp 00000000 00:00 0                                  [stack:10761]
ae57e000-ae57f000 ---p 00000000 00:00 0 
ae57f000-ae5ff000 rwxp 00000000 00:00 0                                  [stack:10757]
ae5ff000-ae600000 ---p 00000000 00:00 0 
ae600000-ae680000 rwxp 00000000 00:00 0                                  [stack:10756]
ae680000-ae6a9000 rw-p 00000000 00:00 0 
ae6a9000-ae6fd000 rw-p 00000000 00:00 0 
ae6fd000-ae744000 rw-p 00000000 00:00 0 
ae744000-ae819000 rw-p 00000000 00:00 0 
ae819000-ae842000 rw-p 00000000 00:00 0 
ae842000-ae896000 rw-p 00000000 00:00 0 
ae896000-ae8dd000 rw-p 00000000 00:00 0 
ae8dd000-ae9b1000 rw-p 00000000 00:00 0 
ae9b1000-aea24000 rw-p 00000000 00:00 0 
aea24000-aea3f000 rw-p 00000000 00:00 0 
aea3f000-b3c40000 rw-p 00000000 00:00 0 
b3c40000-be440000 rw-p 00000000 00:00 0 
be440000-c7150000 rw-p 00000000 00:00 0 
c7150000-e1af0000 rw-p 00000000 00:00 0 
e1af0000-efe60000 rw-p 00000000 00:00 0 
efe60000-f3640000 rw-p 00000000 00:00 0 
f3640000-f3655000 rw-p 00000000 00:00 0 
f3655000-f3700000 rw-p 00000000 00:00 0 
f3700000-f3c18000 rwxp 00000000 00:00 0 
f3c18000-f67fa000 rw-p 00000000 00:00 0 
f67fa000-f6800000 ---p 00000000 00:00 0 
f6800000-f6809000 r-xp 00000000 08:01 5247245                            /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
f6809000-f680a000 r--p 00008000 08:01 5247245                            /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
f680a000-f680b000 rw-p 00009000 08:01 5247245                            /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
f680b000-f6816000 r-xp 00000000 08:01 5247236                            /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
f6816000-f6817000 r--p 0000a000 08:01 5247236                            /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
f6817000-f6818000 rw-p 0000b000 08:01 5247236                            /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
f6818000-f681d000 r-xp 00000000 08:01 5245395                            /usr/lib/i386-linux-gnu/libffi.so.6.0.1
f681d000-f681e000 r--p 00005000 08:01 5245395                            /usr/lib/i386-linux-gnu/libffi.so.6.0.1
f681e000-f681f000 rw-p 00006000 08:01 5245395                            /usr/lib/i386-linux-gnu/libffi.so.6.0.1
f681f000-f682c000 r-xp 00000000 08:01 1446338                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.200.v20120522-1813/eclipse_1502.so
f682c000-f682d000 rw-p 0000c000 08:01 1446338                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.200.v20120522-1813/eclipse_1502.so
f682d000-f6878000 rw-p 00000000 00:00 0 
f6878000-f6883000 r-xp 00000000 08:01 10749246                           /lib/i386-linux-gnu/libnss_files-2.17.so
f6883000-f6884000 r--p 0000a000 08:01 10749246                           /lib/i386-linux-gnu/libnss_files-2.17.so
f6884000-f6885000 rw-p 0000b000 08:01 10749246                           /lib/i386-linux-gnu/libnss_files-2.17.so
f6885000-f689a000 r-xp 00000000 08:01 10747999                           /lib/i386-linux-gnu/libnsl-2.17.so
f689a000-f689b000 r--p 00014000 08:01 10747999                           /lib/i386-linux-gnu/libnsl-2.17.so
f689b000-f689c000 rw-p 00015000 08:01 10747999                           /lib/i386-linux-gnu/libnsl-2.17.so
f689c000-f689e000 rw-p 00000000 00:00 0 
f689e000-f68a0000 r--s 00015000 08:01 1317010                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.core.contenttype_3.4.200.v20120523-2004.jar
f68a0000-f68a1000 r--s 00000000 08:01 2763404                            /home/eejaz/.local/share/mime/mime.cache
f68a1000-f68a5000 r--s 0007c000 08:01 1448133                             /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/jsse.jar
f68a5000-f68bc000 r-xp 00000000 08:01 1447423                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libzip.so
f68bc000-f68bd000 rw-p 00017000 08:01 1447423                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libzip.so
f68bd000-f68c5000 rw-s 00000000 08:01 14423269                           /tmp/hsperfdata_eejaz/10754
f68c5000-f68e8000 r-xp 00000000 08:01 1447439                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libjava.so
f68e8000-f68e9000 rw-p 00023000 08:01 1447439                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libjava.so
f68e9000-f68f0000 r-xp 00000000 08:01 10747928                           /lib/i386-linux-gnu/librt-2.17.so
f68f0000-f68f1000 r--p 00006000 08:01 10747928                           /lib/i386-linux-gnu/librt-2.17.so
f68f1000-f68f2000 rw-p 00007000 08:01 10747928                           /lib/i386-linux-gnu/librt-2.17.so
f68f2000-f68f3000 ---p 00000000 00:00 0 
f68f3000-f6943000 rwxp 00000000 00:00 0                                  [stack:10755]
f6943000-f6984000 r-xp 00000000 08:01 10749234                           /lib/i386-linux-gnu/libm-2.17.so
f6984000-f6985000 r--p 00040000 08:01 10749234                           /lib/i386-linux-gnu/libm-2.17.so
f6985000-f6986000 rw-p 00041000 08:01 10749234                           /lib/i386-linux-gnu/libm-2.17.so
f6986000-f713f000 r-xp 00000000 08:01 1447487                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/server/libjvm.so
f713f000-f7191000 rw-p 007b8000 08:01 1447487                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/server/libjvm.so
f7191000-f75b4000 rw-p 00000000 00:00 0 
f75b4000-f7762000 r-xp 00000000 08:01 10749222                           /lib/i386-linux-gnu/libc-2.17.so
f7762000-f7764000 r--p 001ae000 08:01 10749222                           /lib/i386-linux-gnu/libc-2.17.so
f7764000-f7765000 rw-p 001b0000 08:01 10749222                           /lib/i386-linux-gnu/libc-2.17.so
f7765000-f7768000 rw-p 00000000 00:00 0 
f7768000-f776b000 r-xp 00000000 08:01 10749224                           /lib/i386-linux-gnu/libdl-2.17.so
f776b000-f776c000 r--p 00002000 08:01 10749224                           /lib/i386-linux-gnu/libdl-2.17.so
f776c000-f776d000 rw-p 00003000 08:01 10749224                           /lib/i386-linux-gnu/libdl-2.17.so
f776d000-f7780000 r-xp 00000000 08:01 1447458                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/jli/libjli.so
f7780000-f7781000 rw-p 00012000 08:01 1447458                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/jli/libjli.so
f7781000-f7782000 rw-p 00000000 00:00 0 
f7782000-f7799000 r-xp 00000000 08:01 10749232                           /lib/i386-linux-gnu/libpthread-2.17.so
f7799000-f779a000 r--p 00016000 08:01 10749232                           /lib/i386-linux-gnu/libpthread-2.17.so
f779a000-f779b000 rw-p 00017000 08:01 10749232                           /lib/i386-linux-gnu/libpthread-2.17.so
f779b000-f779d000 rw-p 00000000 00:00 0 
f779d000-f779e000 r--s 00004000 08:01 1317243                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.rse.efs.ui_2.1.400.201205300905.jar
f779e000-f77a0000 r--s 0000b000 08:01 1317100                              /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar
f77a0000-f77a1000 r--p 00469000 08:01 4986868                            /usr/lib/locale/locale-archive
f77a1000-f77ab000 r-xp 00000000 08:01 10749238                           /lib/i386-linux-gnu/libnss_nis-2.17.so
f77ab000-f77ac000 r--p 00009000 08:01 10749238                           /lib/i386-linux-gnu/libnss_nis-2.17.so
f77ac000-f77ad000 rw-p 0000a000 08:01 10749238                           /lib/i386-linux-gnu/libnss_nis-2.17.so
f77ad000-f77b4000 r-xp 00000000 08:01 10749228                           /lib/i386-linux-gnu/libnss_compat-2.17.so
f77b4000-f77b5000 r--p 00006000 08:01 10749228                           /lib/i386-linux-gnu/libnss_compat-2.17.so
f77b5000-f77b6000 rw-p 00007000 08:01 10749228                           /lib/i386-linux-gnu/libnss_compat-2.17.so
f77b6000-f77b7000 rw-p 00000000 00:00 0 
f77b7000-f77b8000 r--p 00000000 00:00 0 
f77b8000-f77c3000 r-xp 00000000 08:01 1447445                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libverify.so
f77c3000-f77c4000 rw-p 0000b000 08:01 1447445                              /home/eejaz/mgc/embedded/readystart-arm/codebench/jre/lib/i386/libverify.so
f77c4000-f77c6000 rw-p 00000000 00:00 0 
f77c6000-f77c7000 r-xp 00000000 00:00 0                                  [vdso]
f77c7000-f77e7000 r-xp 00000000 08:01 10748009                           /lib/i386-linux-gnu/ld-2.17.so
f77e7000-f77e8000 r--p 0001f000 08:01 10748009                           /lib/i386-linux-gnu/ld-2.17.so
f77e8000-f77e9000 rw-p 00020000 08:01 10748009                           /lib/i386-linux-gnu/ld-2.17.so
ffbdc000-ffbfc000 rwxp 00000000 00:00 0                                  [stack]
ffbfc000-ffbfd000 rw-p 00000000 00:00 0 

VM Arguments:
jvm_args: -Dorg.eclipse.swt.browser.DefaultType=mozilla -XX:MaxPermSize=250m -Xms40m -Xmx850m 
java_command:  /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar  -os linux -ws gtk -arch x86 -showsplash  /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse//plugins/com.codesourcery.ide_2013.5.0.26/splash.bmp  -launcher  /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse/eclipse -name  Eclipse --launcher.library  /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.200.v20120522-1813/eclipse_1502.so  -startup  /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar  --launcher.overrideVmargs -exitdata fd001b -product  com.codesourcery.ide.ide -vm  /home/eejaz/mgc/embedded/readystart-arm/codebench/bin/../jre/bin/java  -vmargs -Dorg.eclipse.swt.browser.DefaultType=mozilla  -XX:MaxPermSize=250m -Xms40m -Xmx850m -jar  /home/eejaz/mgc/embedded/readystart-arm/codebench/eclipse//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/home/eejaz/mgc/embedded/readystart-arm/codebench/bin:/home/eejaz/mgc/embedded/readystart-arm/codebench/bin:/home/eejaz/mgc/embedded/readystart-arm/codebench/bin_cache:/home/eejaz/mgc/embedded/readystart-ppc/codebench/bin:/home/eejaz/mgc/embedded/readystart-ppc/codebench/bin/cache:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x720d30], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x720d30], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5d9b80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x5d9b80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5d9b80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x5d9460], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5dba50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x5dba50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x5dba50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5dba50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:wheezy/sid

uname:Linux 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64
libc:glibc 2.17 NPTL 2.17 
rlimit: STACK 8192k, CORE 0k, NPROC 63316, NOFILE 4096, AS infinity
load average:2.25 1.62 1.08

/proc/meminfo:
MemTotal:        8132208 kB
MemFree:         1782284 kB
Buffers:          312520 kB
Cached:          2803348 kB
SwapCached:            0 kB
Active:          3293068 kB
Inactive:        2530256 kB
Active(anon):    2708540 kB
Inactive(anon):    48028 kB
Active(file):     584528 kB
Inactive(file):  2482228 kB
Unevictable:          64 kB
Mlocked:              64 kB
SwapTotal:       8343548 kB
SwapFree:        8343548 kB
Dirty:              4140 kB
Writeback:             0 kB
AnonPages:       2707592 kB
Mapped:           414460 kB
Shmem:             49288 kB
Slab:             327260 kB
SReclaimable:     279576 kB
SUnreclaim:        47684 kB
KernelStack:        6000 kB
PageTables:        55236 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12409652 kB
Committed_AS:    7200340 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      125400 kB
VmallocChunk:   34359598588 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      226768 kB
DirectMap2M:     8118272 kB


CPU:total 4 (2 cores per cpu, 2 threads per core) family 6 model 42  stepping 7, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1,  sse4.2, popcnt, avx, ht, tsc, tscinvbit

/proc/cpuinfo:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
stepping    : 7
microcode    : 0x12
cpu MHz        : 2501.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology  nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx  smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt  tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts  dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4989.26
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
stepping    : 7
microcode    : 0x12
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology  nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx  smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt  tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts  dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4989.26
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
stepping    : 7
microcode    : 0x12
cpu MHz        : 2501.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology  nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx  smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt  tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts  dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4989.26
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
stepping    : 7
microcode    : 0x12
cpu MHz        : 2501.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca  cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall  nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology  nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx  smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt  tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts  dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4989.26
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:



Memory: 4k page, physical 8132208k(1782284k free), swap 8343548k(8343548k free)

vm_info: Java HotSpot(TM) Server VM (23.3-b01) for linux-x86 JRE  (1.7.0_07-b10), built on Aug 28 2012 18:02:17 by "java_re" with gcc  4.3.0 20080428 (Red Hat 4.3.0-8)

time: Wed Feb 19 19:08:52 2014
elapsed time: 374 seconds
```

---

### Post by mire on 2014-03-23
I don't have the bug number off hand but this is a known issue with the gtk+ oxygen theme and java based applications. Switch your gtk applications to use something else and eclispe should work fine. The problem triggers when the applicataion tryies to show a dialog which eclispe does on startup if no default workspace is configured.

---

