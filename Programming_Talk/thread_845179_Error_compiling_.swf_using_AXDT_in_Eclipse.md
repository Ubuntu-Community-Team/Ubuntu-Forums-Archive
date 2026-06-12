---
title: "Error compiling .swf using AXDT in Eclipse"
date: 2008-06-30
forum: Programming Talk
---

### Post by lynndylan on 2008-06-30
I've been trying all day to get a working axdt setup, but I'm new to eclipse and googling my errors has yet to provide a solution.

When I select "Compile and Open a swf file", this is the error I receive:

Message:
> org.axdt.as3.launcher.AS3LauncherShortcut

Exception Stack Track:
> java.lang.NoClassDefFoundError: org.axdt.as3.launcher.AS3LauncherShortcut
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:157)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.debug.internal.ui.launchConfigurations.LaunchShortcutExtension.getDelegate(LaunchShortcutExtension.java:345)
   at org.eclipse.debug.internal.ui.launchConfigurations.LaunchShortcutExtension.launch(LaunchShortcutExtension.java:357)
   at org.eclipse.debug.internal.ui.actions.LaunchShortcutAction.run(LaunchShortcutAction.java:63)
   at org.eclipse.jface.action.Action.runWithEvent(Action.java:499)
   at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539)
   at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488)
   at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400)
   at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
   at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085)
   at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3180)
   at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2856)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)


Session Data:
> 
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86


---

