---
title: "Aptana anf GTK"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by ianb72 on 2008-06-03
I have downloaded Aptana web design software but when I go to install it I get pointed to an error file:
[HTML]!SESSION 2008-06-03 12:47:56.758 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.4.2-02
java.vendor=Blackdown Java-Linux Team
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2008-06-03 12:47:58.917
!MESSAGE An error occurred while automatically activating bundle com.aptana.ide.rcp (118).
!STACK 0
org.osgi.framework.BundleException: The activator com.aptana.ide.rcp.IdePlugin for bundle com.aptana.ide.rcp is invalid
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
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.UnsupportedClassVersionError: com/aptana/ide/rcp/IdePlugin (Unsupported major.minor version 49.0)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
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
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	... 32 more
Root exception:
java.lang.UnsupportedClassVersionError: com/aptana/ide/rcp/IdePlugin (Unsupported major.minor version 49.0)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
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
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
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
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-06-03 12:47:58.955
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in com.aptana.ide.rcp was unable to load class com.aptana.ide.rcp.Application.
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
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: com.aptana.ide.rcp.Application
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-06-03 12:47:58.965
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-06-03 12:47:58.965
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-06-03 12:47:58.965
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2008-06-03 12:47:58.965
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-06-03 12:47:58.966
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.0.0.009905.jar [122] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2008-06-03 12:47:58.966
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.[/HTML]

Can anyone help me please so I can install this software

Thanks
Ian

---

### Post by alexandremrj on 2008-06-09
I think you are using the Open source Java.

I would recomend trying it with Sun Java, perhaps it will give less errors.

---

### Post by leon.hh on 2008-06-09
I believe that alexandremrj is right, try to enable ubuntu backports repositories, update and install sun-java6-bin sun-java6-jdk and sun-java6-jre.

Then execute ```
sudo update-alternatives --config java
``` and select the jre-sun one

---

