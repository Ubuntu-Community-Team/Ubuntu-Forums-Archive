---
title: "Eclipse will only run in root"
date: 2009-12-12
forum: Programming Talk
---

### Post by dannyek7 on 2009-12-12
I am running ubuntu 8.10. I had Eclipse running fine for months. I attempted to add some plugins and install a separate instance of 3.4

Since then, i get error messages whenever i try to start either eclipse (3.2 as added from the add/remove programs menu or 3.4) I am able to start either by doing sudo eclipse


Here is my error codes below:


!SESSION 2009-12-12 10:12:14.741 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.830
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.830
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.831
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.831
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2009-12-12 10:12:17.462
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2009-12-12 10:12:17.517
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (99).
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
    at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:7
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /TestAspect not found.
    at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
    at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
    at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
    at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
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
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /TestAspect not found.
    at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
    at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
    at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
    at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
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
    at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2009-12-12 10:12:17.523
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
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
    ... 14 more

!ENTRY org.eclipse.osgi 2 0 2009-12-12 10:12:17.642
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.ui_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.ui_1.4.0.20060629124300.jar[/EMAIL] [101] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.visualiser_2.2.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.visualiser_2.2.0.20060629124300.jar[/EMAIL] [102] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.exampl"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.exampl[/EMAIL]es_1.4.0.20060629124300/ [103] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.aspectj.ajde"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.aspectj.ajde[/EMAIL]_1.5.2.20060629124300/ [105] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.core_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.core_1.4.0.20060629124300.jar[/EMAIL] [111] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.source"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.source[/EMAIL]_1.4.0.20060629124300/ [113] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.ui_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.ui_1.4.0.20060629124300.jar[/EMAIL] [115] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.core_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.core_1.4.0.20060629124300.jar[/EMAIL] [121] was not resolved.

---

