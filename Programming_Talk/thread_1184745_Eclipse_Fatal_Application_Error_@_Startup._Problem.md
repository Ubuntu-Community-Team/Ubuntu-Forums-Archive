---
title: "Eclipse Fatal Application Error @ Startup. Problem AND solution!"
date: 2009-06-11
forum: Programming Talk
---

### Post by Crimsonblah on 2009-06-11
Thought I'd share this with the community because it took me some serious time to figure out.

I use Eclipse with the CDT, SVN and other handy Plugins for C++ development.

I recently restarted my computer, began loading Eclipse and experienced an fatal error on startup, directing me to check out ~/workspace/.metadata/.log for further information.

In the error log, i found the following information :
```

!ENTRY org.eclipse.core.resources 2 10035 2009-06-11 10:58:26.574
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2009-06-11 10:58:26.630
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (61).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
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
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /LTS/Images/InputImages/Output/Output/Image002.bmp not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /LTS/Images/InputImages/Output/Output/Image002.bmp not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
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

!ENTRY org.eclipse.osgi 4 0 2009-06-11 10:58:26.693
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
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
```

I finally was able to solve this problem by *deleting* the .metadata directory under my workspace location. I found this solution by this thread (click next thread) twice 

[http://dev.eclipse.org/newslists/news.eclipse.platform/msg47858.html](http://dev.eclipse.org/newslists/news.eclipse.platform/msg47858.html)

I only found this solution after completely reinstalling eclipse, which *didn't* solve the problem for me. 

the moral of the story for me is - If you run into serious problems with eclipse and try an uninstall/reinstall, try using a *new* workspace directory, or delete your .metadata directory under the work space directory.

Hope this proves to be of help to someone else.

---

### Post by abhishek_kr7 on 2009-12-07
Thanks. That saved me quite some time.
The issue with me was that eclipse failed to start after a crash and it couldnt find the resources to restore the workspace.

---

