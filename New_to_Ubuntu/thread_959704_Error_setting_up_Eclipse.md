---
title: "Error setting up Eclipse"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by lokisapocalypse on 2008-10-26
Hello all, 

I went through the Package Manager to set up Eclipse but now when I try to start it, I get a large series of error messages:

```

!SESSION 2008-10-26 17:42:02.077 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-10-26 17:42:13.215
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-26 17:42:13.216
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-26 17:42:13.216
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-10-26 17:42:13.216
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2008-10-26 17:42:13.808
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (159).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.gcj.runtime.SharedLibHelper.ensureSupersLinked(libgcj.so.81)
   at gnu.gcj.runtime.SharedLibHelper.findClass(libgcj.so.81)
   at java.lang.VMCompiler.loadSharedLibrary(libgcj.so.81)
   at java.lang.VMCompiler.compileClass(libgcj.so.81)
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   ...62 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...65 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.gcj.runtime.SharedLibHelper.ensureSupersLinked(libgcj.so.81)
   at gnu.gcj.runtime.SharedLibHelper.findClass(libgcj.so.81)
   at java.lang.VMCompiler.loadSharedLibrary(libgcj.so.81)
   at java.lang.VMCompiler.compileClass(libgcj.so.81)
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...65 more

!ENTRY org.eclipse.osgi 4 0 2008-10-26 17:42:14.301
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (159).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.internal.WorkbenchPlugin
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   ...58 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.WorkbenchPlugin
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-10-26 17:42:14.332
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (394).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   ...29 more
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-10-26 17:42:14.439
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.core.ui_1.0.1.200708201.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.ecore.xmi_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.mysql_1.0.0.200706071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.mysql 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.server.ui_1.0.0.200709141.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.server.ui 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.edit.ui_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.parsers.sql.query_1.0.0.200711281.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql.query 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.parsers.sql_1.0.0.200801071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.766
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.oda.design_3.0.5.200709071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.oda.design 2 0 2008-10-26 17:42:14.766
!MESSAGE Missing required bundle org.eclipse.emf.ecore.xmi_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.oda.design 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.derby_1.0.0.200706071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.plan_1.0.0.200709061.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.plan 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.draw2d_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.sql_1.0.0.200708161.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore.sdo_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.core_1.0.1.200801111.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore.xmi_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.sybase_1.0.1.200707131.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.derby.ui_1.0.0.200706071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.common_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.sybase.asa.models_1.0.0.200706071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa.models 2 0 2008-10-26 17:42:14.767
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.767
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.sql.edit_1.0.0.200706071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.768
!MESSAGE Missing required bundle org.eclipse.emf.edit_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.768
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.768
!MESSAGE Missing required bundle org.eclipse.emf.ecore.edit_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.768
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.dbdefinition_1.0.0.200706071.jar was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.dbdefinition 2 0 2008-10-26 17:42:14.768
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).

!ENTRY org.eclipse.osgi 2 0 2008-10-26 17:42:14.824
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.824
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.common.ui_1.0.0.200708161.jar [523] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.common.ui 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.common.ui 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.824
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.hsqldb_1.0.0.200706071.jar [525] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.hsqldb 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.hsqldb 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.hsqldb 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.hsqldb 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.hsqldb 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[1.0.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.824
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.core_1.0.1.200801111.jar [526] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.emf.ecore.xmi_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.824
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.data.ui_1.0.1.200711091.jar [532] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.824
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.data.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.result_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.tabledataeditor_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.825
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.routineeditor_1.0.0.200708161.jar [534] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.query_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.routineeditor 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.plan_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.825
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.derby.ui_1.0.0.200706071.jar [536] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.emf.common_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.825
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.derby_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby.ui 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.derby_[0.9.1,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.826
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.sybase.asa_1.0.0.200706071.jar [539] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa 2 0 2008-10-26 17:42:14.826
!MESSAGE Missing required bundle org.eclipse.datatools.enablement.sybase.asa.models_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.enablement.sybase_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.827
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.oda.design_3.0.5.200709071.jar [540] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.oda.design 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.oda.design 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.emf.ecore.xmi_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.827
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.sql_1.0.0.200708161.jar [542] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.emf.ecore.sdo_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.827
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.db.derby_1.0.0.200706071.jar [543] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.db.generic_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.routineeditor_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.derby 2 0 2008-10-26 17:42:14.827
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.827
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.parsers.sql_1.0.0.200801071.jar [546] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.query_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.828
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.fe.ui_1.0.0.200706071.jar [548] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[1.0.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.828
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.result_1.0.0.200711021.jar [550] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.result 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.828
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.data.core_1.0.0.200712191.jar [551] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.core 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.data.core 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.828
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.sql_1.0.0.200706111.jar [552] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.sql 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sql 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sql 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sql 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.query_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.828
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.derby_1.0.0.200706071.jar [553] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby 2 0 2008-10-26 17:42:14.828
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.derby 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.derby_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.829
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.editor.core_1.0.0.200709261.jar [554] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.query_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.plan_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.829
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.editor.core 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.result_[0.9.0,1.5.0].
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.830
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.core.ui_1.0.1.200708201.jar [556] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.emf.ecore.xmi_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.core.ui 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.830
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.parsers.sql.query_1.0.0.200711281.jar [557] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql.query 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql.query 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.query_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql.query 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.parsers.sql_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.830
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.sql.xml.query_1.0.0.200706151.jar [559] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.xml.query 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.query_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.xml.query 2 0 2008-10-26 17:42:14.830
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.830
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.parsers.sql.xml.query_1.0.0.200706151.jar [560] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql.xml.query 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.parsers.sql.query_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.parsers.sql.xml.query 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.xml.query_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.831
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.sql.edit_1.0.0.200706071.jar [561] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.emf.edit_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.edit 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.emf.ecore.edit_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.831
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.mysql_1.0.0.200706071.jar [562] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.mysql 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.mysql 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.mysql 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.mysql 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.831
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.oda.flatfile.ui_3.0.5.200711121.jar [565] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.oda.flatfile.ui 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.oda.design.ui_[3.0.4,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.831
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.oda.design.ui_3.0.6.200710051.jar [568] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.oda.design.ui 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.oda.design_[3.0.4,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.831
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.debugger.core_1.0.0.200709251.jar [572] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.debugger.core 2 0 2008-10-26 17:42:14.831
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.debugger.core 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.debugger.core 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.result_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.debugger.core 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.debugger.core 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.routineeditor_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.debugger.core 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.832
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.db.derby_1.0.0.200706071.jar [573] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.db.derby 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.832
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.sybase.asa.models_1.0.0.200706071.jar [575] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa.models 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa.models 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase.asa.models 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.enablement.sybase_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.832
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.fe.ui.actions_1.0.0.200706071.jar [576] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui.actions 2 0 2008-10-26 17:42:14.832
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.server.ui_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui.actions 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui.actions 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.fe.ui_[1.0.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.fe.ui.actions 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[1.0.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.833
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.db.generic_1.0.0.200706131.jar [577] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.generic 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.generic 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.db.generic 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.833
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.oda.ws.ui_1.0.2.200711191.jar [578] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.oda.ws.ui 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.oda.design.ui_[3.0.4,4.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.oda.ws.ui 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.enablement.oda.xml.ui_[1.0.1,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.833
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.sybase_1.0.1.200707131.jar [580] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.enablement.sybase 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.833
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.dbdefinition_1.0.0.200706071.jar [581] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.dbdefinition 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.emf.ecore_[2.2.0,3.0.0).
!SUBENTRY 2 org.eclipse.datatools.modelbase.dbdefinition 2 0 2008-10-26 17:42:14.833
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.833
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.connectivity.sqm.server.ui_1.0.0.200709141.jar [582] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.server.ui 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql.edit_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.server.ui 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.server.ui 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.server.ui 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.connectivity.sqm.server.ui 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.emf.edit.ui_[2.2.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.834
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.derby_1.0.0.200706071.jar [583] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.derby 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.834
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.plan_1.0.0.200709061.jar [585] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.plan 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.draw2d_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.plan 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.834
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.sqlscrapbook_1.0.0.200709141.jar [587] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqlscrapbook 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqlscrapbook 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqlscrapbook 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqlscrapbook 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqlscrapbook 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqlscrapbook 2 0 2008-10-26 17:42:14.834
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.834
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.oda.xml.ui_1.0.3.200711191.jar [588] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.oda.xml.ui 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.oda.design.ui_[3.0.4,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.835
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.postgresql.profile_1.0.1.200711121.jar [589] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.postgresql.profile 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.835
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.modelbase.sql.query_1.0.0.200706151.jar [591] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.modelbase.sql.query 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.835
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.tabledataeditor_1.0.0.200706071.jar [592] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.tabledataeditor 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tabledataeditor 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tabledataeditor 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.result_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tabledataeditor 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_[0.9.1,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tabledataeditor 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[0.9.1,1.5.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.835
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.enablement.msft.sqlserver.profile_1.0.1.200709041.jar [597] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.enablement.msft.sqlserver.profile 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_0.0.0.
!SUBENTRY 2 org.eclipse.datatools.enablement.msft.sqlserver.profile 2 0 2008-10-26 17:42:14.835
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.836
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.tablewizard_1.0.0.200710041.jar [598] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.tablewizard 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.core.ui_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tablewizard 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tablewizard 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sqleditor_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tablewizard 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.tablewizard 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.connectivity.sqm.fe.ui_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-10-26 17:42:14.836
!MESSAGE Bundle update@../../../home/blamb/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.datatools.sqltools.sqleditor_1.0.0.200709061.jar [599] was not resolved.
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.modelbase.dbdefinition_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.editor.core_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.sql_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.result_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.common.ui_[0.9.0,1.5.0).
!SUBENTRY 2 org.eclipse.datatools.sqltools.sqleditor 2 0 2008-10-26 17:42:14.836
!MESSAGE Missing required bundle org.eclipse.datatools.sqltools.plan_[0.9.0,1.5.0).

```

and that continues on for a while. I've tried to completely remove Eclipse with apt-get and the Package Manager but each time, the folder /usr/lib/eclipse still exists. 

I try to reinstall it but each time I open it, I get the same error messages. Is there anything I can do to COMPLETELY remove Eclipse?

I've tried:

Via package manager
sudo apt-get remove eclipse
sudo apt-get autoremove eclipse

But nothing seems to help. 

Alternatively, if there were something I could do to fix this problem, it would be fine.

---

### Post by spiderbatdad on 2008-10-26
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

also, did you install other supporting packages (aside from jdk) like:
ecj-gcj, ecj, libecj-java-gcj, libecj-java,

---

### Post by lokisapocalypse on 2008-10-26
I found the solution [here. ](http://ubuntuforums.org/archive/index.php/t-320899.html)

```

sudo aptitude reinstall libswt3.2-gtk-java

```

---

