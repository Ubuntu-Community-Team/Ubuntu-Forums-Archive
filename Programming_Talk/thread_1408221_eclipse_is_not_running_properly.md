---
title: "eclipse is not running properly"
date: 2010-02-16
forum: Programming Talk
---

### Post by rejuvenate on 2010-02-16
while i am running my small c code in eclipse 
the eclipse is giving the following error..

```
Unable to create editor ID org.eclipse.cdt.ui.editor.CEditor: No editor descriptor for id org.eclipse.cdt.ui.editor.CEditor
```

```
org.eclipse.ui.PartInitException: No editor descriptor for id org.eclipse.cdt.ui.editor.CEditor
at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:598)
at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:462)
at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:271)
at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1417)
at org.eclipse.ui.internal.EditorManager$5.runWithException(EditorManager.java:942)
at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:134)
at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3468)
at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3115)
at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
at org.eclipse.ui.internal.Workbench$28.runWithException(Workbench.java:1384)
at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:134)
at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3468)
at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3115)
at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2316)
at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2221)
at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:500)
at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:493)
at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:616)
at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
at org.eclipse.equinox.launcher.Main.run(Main.java:1311)

```

i have install the eclipse,eclipse-cdt package and eclox..
thanx in advnce

---

### Post by rejuvenate on 2010-02-16
i think i have posted the thread in a wrong forum..can any one tell me where to post this thread..

---

