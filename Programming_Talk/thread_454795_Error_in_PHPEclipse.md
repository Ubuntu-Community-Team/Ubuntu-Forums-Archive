---
title: "Error in PHPEclipse"
date: 2007-05-25
forum: Programming Talk
---

### Post by hjanssen on 2007-05-25
Hi,

I just installed Eclipse with the PHPEclipse plugin successfully. After that, I installed XAMPP using the instructions on [this page]("http://www.synergymx.com/page.php?Title=Guide_to_installing_a_LAMPP_Server_with_GUI/).

I then reopened Eclipse and saved my default workspace to /opt/lampp/htdocs/. After that, Eclipse showed me an error message and closed down. I have received this error message ever since, and have not been able to start up Eclipse.

The error message said:

> 
An error has occurred. See the log file /home/harmen/.eclipse/org.eclipse.platform_3.2.0/configuration/1180142557450.log


I haven't been able to find this file, and a search on "eclipse" does not return any results. I'm a beginning Ubuntu user, with no Linux experience whatsoever. Does any of you have got a clue to how to solve this problem?

Thanks very much!

---

### Post by mrpeenut24 on 2007-06-12
Files and folders with a '.' in front are hidden.  In order to see them in nautilus, you have to turn on hidden files and folders.  Go to Places > Home Folder.  This will put you at '/home/harmen/'.  Then click on View > Show Hidden Files and then find the '.eclipse' folder and navigate from there.  When you find the file, post the output here.

---

### Post by hjanssen on 2007-06-19
Hi,

thanks for your reply. The output of the Log file is rather lengthy, but I reckon you can find the solution to the problem pretty fast when you know what to look for. 
Hoping you, or anyone else on the forum knows this, here's the contents of the Log file:

```

!SESSION 2007-06-20 01:04:09.555 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-06-20 01:04:13.879
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-06-20 01:04:13.891
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-06-20 01:04:13.891
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-06-20 01:04:13.891
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.ui.ide 4 4 2007-06-20 01:04:14.817
!MESSAGE Could not write version file

!ENTRY org.eclipse.ui.ide 4 4 2007-06-20 01:04:14.817
!MESSAGE /opt/lampp/htdocs/.metadata/version.ini (Permission denied)
!STACK 0
java.io.FileNotFoundException: /opt/lampp/htdocs/.metadata/version.ini (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
	at org.eclipse.ui.internal.ide.IDEApplication.writeWorkspaceVersion(IDEApplication.java:389)
	at org.eclipse.ui.internal.ide.IDEApplication.checkInstanceLocation(IDEApplication.java:204)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:81)
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

!ENTRY org.eclipse.osgi 4 0 2007-06-20 01:04:14.935
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (97).
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
Caused by: java.lang.IllegalStateException: The platform metadata area could not be written: /opt/lampp/htdocs/.metadata.  By default the platform writes its content
under the current working directory when the platform is launched.  Use the -data parameter to
specify a different content area for the platform.
	at org.eclipse.core.internal.runtime.DataArea.assertLocationInitialized(DataArea.java:55)
	at org.eclipse.core.internal.runtime.DataArea.getStateLocation(DataArea.java:77)
	at org.eclipse.core.internal.runtime.InternalPlatform.getStateLocation(InternalPlatform.java:723)
	at org.eclipse.core.runtime.Plugin.getStateLocation(Plugin.java:300)
	at org.eclipse.core.internal.resources.LocalMetaArea.<init>(LocalMetaArea.java:52)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:359)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
java.lang.IllegalStateException: The platform metadata area could not be written: /opt/lampp/htdocs/.metadata.  By default the platform writes its content
under the current working directory when the platform is launched.  Use the -data parameter to
specify a different content area for the platform.
	at org.eclipse.core.internal.runtime.DataArea.assertLocationInitialized(DataArea.java:55)
	at org.eclipse.core.internal.runtime.DataArea.getStateLocation(DataArea.java:77)
	at org.eclipse.core.internal.runtime.InternalPlatform.getStateLocation(InternalPlatform.java:723)
	at org.eclipse.core.runtime.Plugin.getStateLocation(Plugin.java:300)
	at org.eclipse.core.internal.resources.LocalMetaArea.<init>(LocalMetaArea.java:52)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:359)
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

!ENTRY org.eclipse.osgi 4 0 2007-06-20 01:04:14.942
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
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2007-06-20 01:04:15.050
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-06-20 01:04:15.050
!MESSAGE Bundle update@../../../home/harmen/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.pde.runtime_3.1.1.jar [112] was not resolved.

!ENTRY org.eclipse.osgi 4 0 2007-06-20 01:04:15.096
!MESSAGE Error while stopping "org.eclipse.ui.ide_3.2.1.M20060915-1030".
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.ui.internal.ide.IDEWorkbenchPlugin.stop() of bundle org.eclipse.ui.ide.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1048)
	at org.eclipse.osgi.framework.internal.core.BundleHost.stopWorker(BundleHost.java:396)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.stop(AbstractBundle.java:400)
	at org.eclipse.core.runtime.internal.adaptor.BundleStopper.basicStopBundles(BundleStopper.java:86)
	at org.eclipse.core.runtime.internal.adaptor.BundleStopper.stopBundles(BundleStopper.java:73)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAdaptorHook.frameworkStopping(EclipseAdaptorHook.java:156)
	at org.eclipse.osgi.baseadaptor.BaseAdaptor.frameworkStopping(BaseAdaptor.java:288)
	at org.eclipse.osgi.framework.internal.core.Framework.shutdown(Framework.java:538)
	at org.eclipse.osgi.framework.internal.core.Framework.close(Framework.java:449)
	at org.eclipse.osgi.framework.internal.core.OSGi.close(OSGi.java:41)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.shutdown(EclipseStarter.java:423)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:193)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.IllegalStateException: The platform metadata area could not be written: /opt/lampp/htdocs/.metadata.  By default the platform writes its content
under the current working directory when the platform is launched.  Use the -data parameter to
specify a different content area for the platform.
	at org.eclipse.core.internal.runtime.DataArea.assertLocationInitialized(DataArea.java:55)
	at org.eclipse.core.internal.runtime.DataArea.getStateLocation(DataArea.java:82)
	at org.eclipse.core.internal.preferences.InstancePreferences.getBaseLocation(InstancePreferences.java:44)
	at org.eclipse.core.internal.preferences.InstancePreferences.initializeChildren(InstancePreferences.java:199)
	at org.eclipse.core.internal.preferences.InstancePreferences.<init>(InstancePreferences.java:59)
	at org.eclipse.core.internal.preferences.InstancePreferences.internalCreate(InstancePreferences.java:209)
	at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:289)
	at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:277)
	at org.eclipse.core.internal.preferences.PreferencesService.createNode(PreferencesService.java:356)
	at org.eclipse.core.internal.preferences.RootPreferences.getChild(RootPreferences.java:63)
	at org.eclipse.core.internal.preferences.RootPreferences.getNode(RootPreferences.java:96)
	at org.eclipse.core.internal.preferences.RootPreferences.node(RootPreferences.java:85)
	at org.eclipse.core.internal.preferences.legacy.PreferenceForwarder.<init>(PreferenceForwarder.java:39)
	at org.eclipse.core.runtime.Plugin$1.run(Plugin.java:349)
	at org.eclipse.core.runtime.Plugin.getPluginPreferences(Plugin.java:352)
	at org.eclipse.core.runtime.Plugin.savePluginPreferences(Plugin.java:373)
	at org.eclipse.ui.plugin.AbstractUIPlugin.savePreferenceStore(AbstractUIPlugin.java:526)
	at org.eclipse.ui.plugin.AbstractUIPlugin.stop(AbstractUIPlugin.java:630)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$3.run(BundleContextImpl.java:1032)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1028)
	... 19 more
Root exception:
java.lang.IllegalStateException: The platform metadata area could not be written: /opt/lampp/htdocs/.metadata.  By default the platform writes its content
under the current working directory when the platform is launched.  Use the -data parameter to
specify a different content area for the platform.
	at org.eclipse.core.internal.runtime.DataArea.assertLocationInitialized(DataArea.java:55)
	at org.eclipse.core.internal.runtime.DataArea.getStateLocation(DataArea.java:82)
	at org.eclipse.core.internal.preferences.InstancePreferences.getBaseLocation(InstancePreferences.java:44)
	at org.eclipse.core.internal.preferences.InstancePreferences.initializeChildren(InstancePreferences.java:199)
	at org.eclipse.core.internal.preferences.InstancePreferences.<init>(InstancePreferences.java:59)
	at org.eclipse.core.internal.preferences.InstancePreferences.internalCreate(InstancePreferences.java:209)
	at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:289)
	at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:277)
	at org.eclipse.core.internal.preferences.PreferencesService.createNode(PreferencesService.java:356)
	at org.eclipse.core.internal.preferences.RootPreferences.getChild(RootPreferences.java:63)
	at org.eclipse.core.internal.preferences.RootPreferences.getNode(RootPreferences.java:96)
	at org.eclipse.core.internal.preferences.RootPreferences.node(RootPreferences.java:85)
	at org.eclipse.core.internal.preferences.legacy.PreferenceForwarder.<init>(PreferenceForwarder.java:39)
	at org.eclipse.core.runtime.Plugin$1.run(Plugin.java:349)
	at org.eclipse.core.runtime.Plugin.getPluginPreferences(Plugin.java:352)
	at org.eclipse.core.runtime.Plugin.savePluginPreferences(Plugin.java:373)
	at org.eclipse.ui.plugin.AbstractUIPlugin.savePreferenceStore(AbstractUIPlugin.java:526)
	at org.eclipse.ui.plugin.AbstractUIPlugin.stop(AbstractUIPlugin.java:630)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$3.run(BundleContextImpl.java:1032)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.stop(BundleContextImpl.java:1028)
	at org.eclipse.osgi.framework.internal.core.BundleHost.stopWorker(BundleHost.java:396)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.stop(AbstractBundle.java:400)
	at org.eclipse.core.runtime.internal.adaptor.BundleStopper.basicStopBundles(BundleStopper.java:86)
	at org.eclipse.core.runtime.internal.adaptor.BundleStopper.stopBundles(BundleStopper.java:73)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAdaptorHook.frameworkStopping(EclipseAdaptorHook.java:156)
	at org.eclipse.osgi.baseadaptor.BaseAdaptor.frameworkStopping(BaseAdaptor.java:288)
	at org.eclipse.osgi.framework.internal.core.Framework.shutdown(Framework.java:538)
	at org.eclipse.osgi.framework.internal.core.Framework.close(Framework.java:449)
	at org.eclipse.osgi.framework.internal.core.OSGi.close(OSGi.java:41)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.shutdown(EclipseStarter.java:423)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:193)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

```

---

### Post by Mirrorball on 2007-06-20
I recommend you install this other plugin for Eclipse. It's newer and better IMHO.
[http://www.eclipse.org/pdt/](http://www.eclipse.org/pdt/)

---

### Post by hjanssen on 2007-06-20
> **Mirrorball said:**
> I recommend you install this other plugin for Eclipse. It's newer and better IMHO.
[http://www.eclipse.org/pdt/](http://www.eclipse.org/pdt/)

Thanks! I will give that a shot. 
But how would I go about that, considering Eclipse won't start anymore? Can I do that from outside Eclipse?

---

### Post by hjanssen on 2007-06-20
A small update: I have removed Eclipse and installed it again, but the same error message keeps popping up as if nothing happened...
So I guess I really need someone who understands Eclipse's error log to tell me what to do to fix this.

---

### Post by mrpeenut24 on 2007-06-26
Try running eclipse with sudo.  The first error java is throwing seems to be a FileNotFoundException and says that the permission is denied.  If it runs with sudo try
> sudo apt-get --purge remove eclipse*
This should purge any config files and then try to reinstall it.

---

### Post by Boipster on 2007-06-26
try this:
Ubuntu Feisty 7.04 Fix @ [PHPEclipse Wiki page]("https://help.ubuntu.com/community/PHPEclipse?highlight=%28phpeclipse%29")

---

### Post by hjanssen on 2007-07-02
> **mrpeenut24 said:**
> Try running eclipse with sudo.  The first error java is throwing seems to be a FileNotFoundException and says that the permission is denied.  If it runs with sudo try

This should purge any config files and then try to reinstall it.

Wow, this is starting to get real ugly.
I did exactly what you said, but I'm still getting the error dialog when starting Eclipse...

---

### Post by Rytmis on 2007-08-07
The problem is not your eclipse install but your local settings.

If you're sure you don't have anything you're afraid of losing in your eclipse settings, do this:

```
cd ~
rm -rf .eclipse
```

now try restarting eclipse.

The problem may also be your workspace. If that is the case, do this (assuming your workspace directory is /home/yourusername/workspace):

```
cd ~
mv workspace workspace_old
```

HTH,

-Rytmis

---

### Post by EndPerform on 2007-08-07
Eclipse isn't the issue here.  Looking at the log file, you see this:

```

java.io.FileNotFoundException: /opt/lampp/htdocs/.metadata/version.ini (Permission denied)

java.lang.IllegalStateException: The platform metadata area could not be written: /opt/lampp/htdocs/.metadata.  By default the platform writes its content
under the current working directory when the platform is launched.  Use the -data parameter to
specify a different content area for the platform.
```

I'm betting you don't have permissions on the htdocs folder mentioned above.  Check your permissions and make sure your user can write to the location, then try again.

---

### Post by Rytmis on 2007-08-07
> **EndPerform said:**
> Eclipse isn't the issue here.  Looking at the log file, you see this:
.

Correct, but it's not wise to assume that your apps will have write access to /opt. User *writable* things should be under the user's home directory.

Removing the settings like I advised before should allow eclipse to start up properly. :)

---

### Post by EndPerform on 2007-08-07
> **Rytmis said:**
> Correct, but it's not wise to assume that your apps will have write access to /opt. User *writable* things should be under the user's home directory.

Removing the settings like I advised before should allow eclipse to start up properly. :)

I'm not assuming anything, I was just pointing out that was the issue. :)  It seems like he's trying to save his work to that folder, and therein lies the original cause of his problem.  So, he'll either need to work on his project in his home dir and do a sudo cp every time he wants to test, or change ownership of the htdocs directory to his user so he can write to it.

---

### Post by Rytmis on 2007-08-07
> **EndPerform said:**
> I'm not assuming anything, I was just pointing out that was the issue. :)  It seems like he's trying to save his work to that folder, and therein lies the original cause of his problem.  So, he'll either need to work on his project in his home dir and do a sudo cp every time he wants to test, or change ownership of the htdocs directory to his user so he can write to it.

Yeah, that was intended for the original poster more than you. :)

When I work on web projects, I usually symlink them to the web directory so I don't have to do anything else to deploy.

---

### Post by EndPerform on 2007-08-07
Yep, that's how I do it too, works like a charm, although I like installing each piece rather than downloading an all-in-one package.  Hopefully this gets the OP sorted out.

---

