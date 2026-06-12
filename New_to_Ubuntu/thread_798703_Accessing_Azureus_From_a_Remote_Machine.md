---
title: "Accessing Azureus From a Remote Machine"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by cackles on 2008-05-18
Ive installed Azureus as per instructions for a headless install.

Everything seems to work fine via PuTTY, done a download and stuff.

Updated the Azureus2.jar file manually.

I have downloaded and put Azureus HTML WebUI into a folder of its own, it seems to run because if I put another version of it in another folder it tells me I already have an instance running, I deleted the other copy after I checked that.

I cant seem to connect via my XP machine though. I am trying [http://boxip:6886/](http://boxip:6886/) and all Im getting is 'The page cannot be displayed' dialog, not could not be found, cannot be displayed. My azureus install is at /usr/src/azureus/azureus/ Im new to this so I dunno if that makes a difference, but it does run fine from console.

Does anyone know what it could be please?

---

### Post by EXCiD3 on 2008-05-18
According to this page the default port is 6883, not 6886: [http://azureus.sourceforge.net/plugins/howto/webui.html](http://azureus.sourceforge.net/plugins/howto/webui.html)

---

### Post by cackles on 2008-05-18
Thanks for the reply, but I think 6883 is a typo and also I am now getting this error message:

```
su azureus -c "java -Dazureus.config.path=/home/azureus/azureus -Dazureus.install.path=/home/azureus -jar /home/azureus/azureus/Azureus2.jar --ui=console"




set "General_sDefaultSave_Directory" "/shared"



[plug] [UPnP] UPnP: Mapping 'HTML Web UI (TCP/6886)' failed
DEBUG::Sun May 18 18:23:34 BST 2008::com.aelitis.azureus.plugins.upnp.UPnPPluginService::checkMapping::266:
  com.aelitis.net.upnp.UPnPException: Invoke of 'urn:schemas-upnp-org:service:WANIPConnection:1#AddPortMapping' on 'http:// 192.168.0.1:4444/wipconn' failed: HTTP request failed:HTTP/1.1 500 Internal Server Error
        at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:134)
        at com.aelitis.net.upnp.impl.services.UPnPSSWANConnectionImpl.addPortMapping(UPnPSSWANConnectionImpl.java:336)
        at com.aelitis.azureus.plugins.upnp.UPnPPluginService.checkMapping(UPnPPluginService.java:234)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.checkState(UPnPPlugin.java:1309)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.addService(UPnPPlugin.java:1196)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processServices(UPnPPlugin.java:1090)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:1046)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:1052)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:1052)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.rootDeviceFound(UPnPPlugin.java:814)
        at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(UPnPImpl.java:259)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.gudy.azureus2.core3.util.ThreadPool.runIt(ThreadPool.java:312)
        at org.gudy.azureus2.core3.util.ThreadPool$threadPoolWorker.run(ThreadPool.java:566)
        at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:225)
Caused by: java.io.IOException: HTTP request failed:HTTP/1.1 500 Internal Server Error
        at com.aelitis.azureus.core.util.HTTPUtils.decodeChunkedEncoding(HTTPUtils.java:189)
        at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:742)
        at com.aelitis.net.upnp.impl.UPnPImpl.performSOAPRequest(UPnPImpl.java:630)
        at com.aelitis.net.upnp.impl.services.UPnPActionInvocationImpl.invoke(UPnPActionInvocationImpl.java:98)
        ... 14 more

[alert] Alert:3:UPnP: Mapping 'HTML Web UI (TCP/6886)' failed
UPnP: Mapping 'HTML Web UI (TCP/6886)' failed
Update available for 'azupnpav/UPnP Media Server,UPnP Media Server', new version = 0.2.1_CVS
        The Media Server Plugin provides a simple UPnP Media Server interface.
        This allows conformant media renderers to stream content present in Azureus.
            0.2.1: Close stream immediately to fix buffering issue.
            0.2.0: Reduced memory usage.
            0.1.9: Reduced some wait times; added diagnostic directory print.
            0.1.8: Add to the music/movie/picture subcategories based on content; fix for PS3 empty folder error.
            0.1.7: Security fix.
            0.1.6: Fix bug with delayed content loading.
            0.1.5: Make the plugin unloadable.
            0.1.4: Fix bug with removal of content, name clashes and added option to turn of upnp component.
            0.1.3: Fix to work with 3.0.2.0.
            0.1.2: Fixup context menus.
            0.1.1: Force .asx files to WMP.
            0.1: Initial version.

```

---

### Post by EXCiD3 on 2008-05-18
Well getting an error like this is better than getting "Page cannot be displayed." Have you double checked the configuration settings for http?

---

### Post by cackles on 2008-05-18
Sorted it out :)

Seems ... strange ... I have a DIR-655 router and I have the web ports done via the virtual server settings but I had to put the Azureus browser settings in port forwarding.

---

### Post by cackles on 2008-05-18
Argh, now I have a new problem. I am trying to connect to my machine using XMing to tweak some settings, like add a password for Azureus. I cant seem to get XMing to work though. Im using ./azureus to run it. Im not 100% on the settings or 'how to'. Will I also need to forward port 22 for this to work? I havent had to forward it to get PuTTY to work.


Im getting this:

```
Starting Azureus...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: No more handles [gtk_init_check() failed], Invocation                                         TargetException
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to                                          LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
Browser check failed with: No more handles [gtk_init_check() failed], Invocation                                         TargetException
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has bet                                         ter luck.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./commons-cli.jar:./log4j.jar:./swt.jar" -Djav                                         a.library.path="/usr/src/azureus/azureus" -Dazureus.install.path="/usr/src/azure                                         us/azureus" -Dazureus.script="/usr/src/azureus/azureus/azureus" -Dazureus.script                                         .version=2 org.gudy.azureus2.ui.swt.Main
file:/usr/src/azureus/azureus/Azureus2.jar ; file:/usr/src/azureus/azureus/commo                                         ns-cli.jar ; file:/usr/src/azureus/azureus/log4j.jar ; file:/usr/src/azureus/azu                                         reus/swt.jar ; file:/usr/src/azureus/azureus/
Invoking main failed
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.                                         java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces                                         sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
        at java.lang.Thread.run(Thread.java:619)
Caused by: org.eclipse.swt.SWTError: No more handles [gtk_init_check() failed]
        at org.eclipse.swt.SWT.error(SWT.java:3770)
        at org.eclipse.swt.widgets.Display.createDisplay(Display.java:848)
        at org.eclipse.swt.widgets.Display.create(Display.java:836)
        at org.eclipse.swt.graphics.Device.<init>(Device.java:152)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:464)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:455)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:9   
 0)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThrea                                         d.java:67)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.ja                                         va:109)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
        ... 6 more
Exception in thread "MainRunner" java.lang.SecurityException: VM exit operation                                          prohibited
        at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl$2.checkEx                                         it(SESecurityManagerImpl.java:267)
        at java.lang.Runtime.exit(Runtime.java:88)
        at java.lang.System.exit(System.java:906)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:42)
        at java.lang.Thread.run(Thread.java:619)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
cackles@slavetothebox:~/Azureus Downloads$ cd /usr/src/azureus/azureus/
cackles@slavetothebox:/usr/src/azureus/azureus$ sudo ./azureus
Starting Azureus...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: No more handles [gtk_init_check() failed], InvocationTargetException
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
Browser check failed with: No more handles [gtk_init_check() failed], InvocationTargetException
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./commons-cli.jar:./log4j.jar:./swt.jar" -Djava.library.path="/usr/src/azureus/azureus" -Dazureus.install.path="/usr/src/azureus/azureus" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main
file:/usr/src/azureus/azureus/Azureus2.jar ; file:/usr/src/azureus/azureus/commons-cli.jar ; file:/usr/src/azureus/azureus/log4j.jar ; file:/usr/src/azureus/azureus/swt.jar ; file:/usr/src/azureus/azureus/
Invoking main failed
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
        at java.lang.Thread.run(Thread.java:619)
Caused by: org.eclipse.swt.SWTError: No more handles [gtk_init_check() failed]
        at org.eclipse.swt.SWT.error(SWT.java:3770)
        at org.eclipse.swt.widgets.Display.createDisplay(Display.java:848)
        at org.eclipse.swt.widgets.Display.create(Display.java:836)
        at org.eclipse.swt.graphics.Device.<init>(Device.java:152)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:464)
        at org.eclipse.swt.widgets.Display.<init>(Display.java:455)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:90)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:67)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:109)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
        ... 6 more
Exception in thread "MainRunner" java.lang.SecurityException: VM exit operation prohibited
        at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl$2.checkExit(SESecurityManagerImpl.java:267)
        at java.lang.Runtime.exit(Runtime.java:88)
        at java.lang.System.exit(System.java:906)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:42)
        at java.lang.Thread.run(Thread.java:619)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.


```

---

