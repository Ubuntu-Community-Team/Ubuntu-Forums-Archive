---
title: "completely uninstall a program"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by damonjablons on 2008-06-26
hey guys,

i recently installed eclipse and i'm having some trouble with it.  i've tried "**completely remove**" via synaptic, but when i reinstall it (via synaptic) it gives me the same issue - an improper configuration file.  i'm positive that this error is caused by complete removal not deleting all of the necessary files.  can someone please shed some light on this for me?

regards,
damon j.

---

### Post by Elfy on 2008-06-26
Removing the program as youhave found out doesn't touch the config files - these are hidden in your home 

Open nautilus do a Ctrl+H too view hidden files and then look for .eclipse (guess at name) and delete it

Any file willbe hidden if you put . in front of it

---

### Post by hyper_ch on 2008-06-26
```

sudo apt-get remove --purge eclipse

```

---

### Post by damonjablons on 2008-06-26
Hey again,

So I attempted this.  I've tried removing the *~/.eclipse* folder before.  I ran the following:

```
# apt-get remove --purge eclipse
$ rm -rfv ~/home/.eclipse/
# apt-get install eclipse
```

and when i tried starting the program, it gave me the following error box:

```
An error has occurred. See the log file
/home/damon/.eclipse/org.eclipse.platform_3.2.0/configuration/1214510427792.log.
```

and if i view the error log, here are the error messages:

```
!SESSION 2008-06-26 16:00:27.547 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2008-06-26 16:00:31.246
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-06-26 16:00:31.247
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-06-26 16:00:31.247
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-06-26 16:00:31.247
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2008-06-26 16:00:31.495
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (63).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
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
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   ...58 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...61 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.newInstance(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
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
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.VMClassLoader.defineClass(libgcj.so.81)
   at java.lang.ClassLoader.defineClass(libgcj.so.81)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...61 more

!ENTRY org.eclipse.osgi 4 0 2008-06-26 16:00:31.680
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (32).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   ...29 more
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-06-26 16:00:31.689
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
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
```

thanks in advance for the help, i appreciate it.

-d

---

### Post by hyper_ch on 2008-06-26
```

~/home/USER/[...]

```
is wrong....

~  ==  /home/USER

so

~/home  ==  /home/USER/home

---

### Post by damonjablons on 2008-06-26
sorry, you're right.

what i did run was:

```
$rm -rfv ~/.eclipse/
```

-d

---

### Post by stchman on 2008-06-26
> **damonjablons said:**
> hey guys,

i recently installed eclipse and i'm having some trouble with it.  i've tried "**completely remove**" via synaptic, but when i reinstall it (via synaptic) it gives me the same issue - an improper configuration file.  i'm positive that this error is caused by complete removal not deleting all of the necessary files.  can someone please shed some light on this for me?

regards,
damon j.

To remove software packages completely use autoremove.

```
sudo apt-get autoremove eclipse
```

This will remove eclipse and all unused dependencies.

Also delete the ~/.eclipse folder in your home.

---

### Post by damonjablons on 2008-06-26
> **stchman said:**
> To remove software packages completely use autoremove.

```
sudo apt-get autoremove eclipse
```

This will remove eclipse and all unused dependencies.

Also delete the ~/.eclipse folder in your home.

Thank you very very much!!!  This worked!

-d:guitar:

---

