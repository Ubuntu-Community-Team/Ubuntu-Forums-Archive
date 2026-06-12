---
title: "Cannot run Eclipse, log posted."
date: 2007-10-30
forum: Programming Talk
---

### Post by fyplinux on 2007-10-30
Hi,

When I startup eclipse, it crashed in about 3 seconds, below is the log(dot symbols are put into some words to get rid of image parsing of the forum feature):

How can I solve this problem?

Regards.

!SESSION 2007-10-30 20:57:27.109 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_03
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x&#65304;6, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x&#65304;6

!ENTRY org.eclipse.osgi 2 1 2007-10-30 20:57:2&#65304;.571
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-10-30 20:57:2&#65304;.571
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-10-30 20:57:2&#65304;.572
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-10-30 20:57:2&#65304;.572
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-10-30 20:57:2&#65304;.599
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (52).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.preFindLocalClass(E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.java:&#65304;&#65304;)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;3)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.preFindLocalClass(E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.java:&#65304;&#65304;)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6&#65304;)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:2&#65304;0)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
    at java.lang.Class.getDeclaredConstructors0(Native Method)
    at java.lang.Class.privateGetDeclaredConstructors(Class.java:23&#65304;9)
    at java.lang.Class.getConstructor0(Class.java:2699)
    at java.lang.Class.newInstance0(Class.java:326)
    at java.lang.Class.newInstance(Class.java:30&#65304;)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
    ... 62 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
    at java.lang.Class.getDeclaredConstructors0(Native Method)
    at java.lang.Class.privateGetDeclaredConstructors(Class.java:23&#65304;9)
    at java.lang.Class.getConstructor0(Class.java:2699)
    at java.lang.Class.newInstance0(Class.java:326)
    at java.lang.Class.newInstance(Class.java:30&#65304;)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.preFindLocalClass(E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.java:&#65304;&#65304;)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;3)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.preFindLocalClass(E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.java:&#65304;&#65304;)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6&#65304;)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:2&#65304;0)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-10-30 20:57:2&#65304;.602
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (&#65304;).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.preFindLocalClass(E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.java:&#65304;&#65304;)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6&#65304;)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:2&#65304;0)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
    ... 32 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
    at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
    at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.preFindLocalClass(E c.l.i.p.s.e.L.a.z.y.S.t.a.rter.java:&#65304;&#65304;)
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:1&#65304;9)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:3&#65304;6)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6&#65304;)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:2&#65304;0)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-10-30 20:57:2&#65304;.653
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(RegistryStrategyOSGI.java:165)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:149)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6&#65304;)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:2&#65304;0)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:&#65304;3)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(B.u.n.d.l.e.L.o.a.d.e.r.j.a.v.a:27&#65304;)
    at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
    at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
    at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
    at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
    at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
    at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:6&#65304;)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:2&#65304;0)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

---

### Post by tenmillionmilesaway on 2007-10-30
Did you use the Ubuntu repo eclipse or eclipse from [www.eclispe.org](www.eclispe.org).

---

### Post by fyplinux on 2007-10-30
> **tenmillionmilesaway said:**
> Did you use the Ubuntu repo eclipse or eclipse from [www.eclispe.org](www.eclispe.org).

I add the program by the "add/remove" menu of Ubuntu

---

### Post by finngruwier on 2007-10-31
Did you upgrade to Ubuntu 7.10 recently?

In that case, take a look at [http://ubuntuforums.org/showthread.php?t=572557](http://ubuntuforums.org/showthread.php?t=572557)

---

### Post by fyplinux on 2007-10-31
I solved the problem by remove eclipse completely, and got another copy form :

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

---

