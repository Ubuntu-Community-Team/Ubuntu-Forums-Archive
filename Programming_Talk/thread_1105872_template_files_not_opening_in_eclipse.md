---
title: "template files not opening in eclipse"
date: 2009-03-25
forum: Programming Talk
---

### Post by srinathbtech on 2009-03-25
Hi,
I install updates for eclipse when a update alerts prompted to install.
After installing all updates eclipse asked to restart the IDE and click OK.
and when eclipse restarted and i go through my rails projects and clicked one index.html.erb file to open in editor and suddenly it showed me this error . Here it is ..

Could any one have idea on this issue ??
 
**Unable to create this part due to an internal error. Reason for the failure: The editor class could not be instantiated. This usually indicates that the editor's class name was mistyped in plugin.xml.**

and in Details it is showing this error :

java.lang.NullPointerException
	at com.aptana.ide.editors.unified.UnifiedEditor.addPluginToPreferenceStore(UnifiedEditor.java:432)
	at com.aptana.ide.editor.erb.ERBSourceEditor.<init>(ERBSourceEditor.java:66)
	at com.aptana.ide.editor.erb.ERBEditor.createSourceEditor(ERBEditor.java:53)
	at com.aptana.ide.editor.html.HTMLEditor.<init>(HTMLEditor.java:193)
	at com.aptana.ide.editor.erb.ERBEditor.<init>(ERBEditor.java:45)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at java.lang.Class.newInstance0(Class.java:355)
	at java.lang.Class.newInstance(Class.java:308)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:157)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.ui.internal.WorkbenchPlugin$1.run(WorkbenchPlugin.java:242)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchPlugin.createExtension(WorkbenchPlugin.java:238)
	at org.eclipse.ui.internal.registry.EditorDescriptor.createEditor(EditorDescriptor.java:231)
	at org.eclipse.ui.internal.EditorManager.createPart(EditorManager.java:911)
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:549)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:372)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
	at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:263)
	at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1474)
	at org.eclipse.ui.internal.EditorManager$5.run(EditorManager.java:1008)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.core.runtime.Platform.run(Platform.java:858)
	at org.eclipse.ui.internal.EditorManager.restoreState(EditorManager.java:1003)
	at org.eclipse.ui.internal.WorkbenchPage.restoreState(WorkbenchPage.java:2843)
	at org.eclipse.ui.internal.WorkbenchWindow.restoreState(WorkbenchWindow.java:1936)
	at org.eclipse.ui.internal.Workbench.doRestoreState(Workbench.java:2873)
	at org.eclipse.ui.internal.Workbench.access$14(Workbench.java:2821)
	at org.eclipse.ui.internal.Workbench$19.run(Workbench.java:1697)
	at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)
	at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1695)
	at org.eclipse.ui.internal.Workbench.access$12(Workbench.java:1666)
	at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1545)
	at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
	at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1489)
	at org.eclipse.ui.internal.WorkbenchConfigurer.restoreState(WorkbenchConfigurer.java:183)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:702)
	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)
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

