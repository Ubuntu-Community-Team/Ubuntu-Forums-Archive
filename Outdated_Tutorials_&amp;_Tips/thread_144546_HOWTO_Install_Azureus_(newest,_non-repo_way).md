---
title: "HOWTO: Install Azureus (newest, non-repo way)"
date: 2006-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2006-03-14
**Works for Ubuntu Breezy, Dapper, Edgy and Feisty**

I'm doing this howto on the requests from users: [http://ubuntuforums.org/showthread.php?t=135968](http://ubuntuforums.org/showthread.php?t=135968)
Though there's diffrent Howto install azureus on the howto forum, but not the way I install it.

Before you start you might uninstall your previous version of Azureus.

--------------------------------------------------


**1.** Make sure you have sun Java 1.5 or 1.6 installed and working. To see if what your Java version is set by default type: **java -version** in the terminal.

**2.** Download Azureus 3.0 (Vuze)  linux version: [Here]("http://azureus.sourceforge.net/"). Save it to your Desktop.

**3.** Open up for the terminal:
```
cd Desktop
sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
sudo chown -R <username>:<username> /opt/azureus/

```

**4.** Now we need a launcher from the Application tab, fire up the terminal again:
```

sudo nano /usr/share/applications/Azureus.desktop

```

add:
> [Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;


**5.** This is optional. If you want azureus to launch from a command in the terminal:

```
sudo nano /usr/bin/azureus
```

add:

> #!/bin/sh

/opt/azureus/azureus "$*"

save it and close it.
Now the last thing in the terminal:
```
sudo chmod +x /usr/bin/azureus
azureus
```

Now get the any updates and plugins you need. After that exit Azureus (so there aren't any azureus tray icon). Then;

```
sudo chown -R root:root /opt/azureus/
```




------------------------------------------------
Other HOWTOs by Artificial Intelligence
[HOWTO: Install F-Prot with GTK frontend (anti-virus)]("http://ubuntuforums.org/showthread.php?t=88357") - Dapper and Breezy.
[HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064") - Breezy only.
[HOWTO: Setup Desktop/Eyecandy. Tips'n'Tricks.]("http://ubuntuforums.org/showthread.php?t=77694") - Dapper and Breezy.
[HOWTO: Use 'Create Document' option. Open Office and custom files.]("http://ubuntuforums.org/showthread.php?t=76419") - All Ubuntu releases.
[HOWTO: Automatically play CDs and DVD when inserted.]("http://ubuntuforums.org/showthread.php?t=77146") - Dapper and Breezy.

---

### Post by mrgnash on 2006-03-14
Brilliant! Thanks :KS

---

### Post by Xilon on 2006-03-15
Worked like a charm!! Thanks, and that goes to the others who contributed aswell :)

---

### Post by Upuntu on 2006-03-15
Where I can find .bz version? There is just a .jar version.
EDIT: Now I found it, it wasn't there, it was here: [http://sourceforge.net/project/showfiles.php?group_id=84122](http://sourceforge.net/project/showfiles.php?group_id=84122)

---

### Post by Perfect Storm on 2006-03-15
The .bz2 archive is the where it just says linux: <link>. Just click on it and it takes you there.

---

### Post by Perfect Storm on 2006-03-17
Updated:
- New version is out 2.4.0.0 ---> 2.4.0.2

If you already have installed 2.4.0.0 you don't need to reinstall. Azureus auto update to the latest.

---

### Post by benk on 2006-03-21
Excellent! Thanks.

I have 1 question:

When I try and download a torrent file from Firefox, it asks me if I want to save it to disk or open directly using the default bittorrent client. When I choose to open it using azureus (via /usr/bin/azureus), it doesn't seem to open the torrent at all...it does open azureus, but not the torrent. How can I fix this?

I can get torrents to download by saving the file to disk and then opening that file in azureus by File->open->torrent file.

Also, any reason why you did not choose to link to the azureus file? 
ln -s /opt/azureus/azureus /usr/bin/azureus

And, if you want to install plugins without running azureus as root, you'd have to make /opt/azureus writable to all (although this could be a security risk).

---

### Post by Perfect Storm on 2006-03-22
> When I try and download a torrent file from Firefox, it asks me if I want to save it to disk or open directly using the default bittorrent client. When I choose to open it using azureus (via /usr/bin/azureus), it doesn't seem to open the torrent at all...it does open azureus, but not the torrent. How can I fix this?

I'll will look into this. But if you use 'save as' it should open the torrent automatically with azureus if you use the downloader which comes with epiphany, I'm sure you can set firefox to do too.


> Also, any reason why you did not choose to link to the azureus file?
ln -s /opt/azureus/azureus /usr/bin/azureus


Doesn't worked. Have tried before I decided writing this howto. That's why I use a script instead.

> And, if you want to install plugins without running azureus as root, you'd have to make /opt/azureus writable to all (although this could be a security risk). 

???

All plugins and updates works if you install azureus as I described. I just double checked to be sure in my case.
You can sudo chown -R <username>:<username> /opt/azureus/ or to "all" if you want to change it (on your own risk).

I hope you can use my answers, or just ask again :)

---

### Post by MiniJames on 2006-03-23
THANK YOU VERY MUCH! My version of Java was out of date, all sorted very happy.

---

### Post by ndhskp on 2006-03-23
[quote=Artificial Intelligence]I'll will look into this. But if you use 'save as' it should open the torrent automatically with azureus if you use the downloader which comes with epiphany, I'm sure you can set firefox to do too.[/quote]I may have a solution to this problem.  When I followed your guide the first time Firefox would not successfully pass the torrent.  So I looked at my **".mailcap"** file.  I originally had Azureus listed in mailcap as **"application/x-bittorrent; /usr/bin/azureus"** so I tried this **"application/x-bittorrent; /opt/azureus/azureus"**.

Look in your .mailcap file in **/home/username/.mailcap**.  This file is hidden by default.

Change```
application/x-bittorrent; /usr/bin/azureus
```to```
application/x-bittorrent; /opt/azureus/azureus
```

I use Dapper and the Firefox nightly's so maybe that makes a difference.  I hope this helps you, good luck.

---

### Post by Perfect Storm on 2006-03-24
Sadly I've moved to Dapper now so I can't test it for breezy.
(I'm gonna tests my howtos on Dapper and make the changes if needed)

---

### Post by Perfect Storm on 2006-03-25
Howto tested on Dapper: Works.

---

### Post by arnieboy on 2006-03-25
good job on the howto AI. 
a small correction in the .desktop file:
Instead of
**Categories=Application;Internet;**
it should be
**Categories=Application;Network;**

-Arnie

---

### Post by Perfect Storm on 2006-03-25
ah thanks, my mind must have been somewhere else lol.

---

### Post by hey560 on 2006-03-26
I followed the howto, and azureus starts but no window pops up.  Then i just extracted the tar.bz2 and changed the "azureus" script to executable and ran it from a terminal.  The splash screen comes up and then a couple error toaster pop up messages, but no GUI!!!  Whats going on?

---

### Post by arnieboy on 2006-03-26
[QUOTE=hey560]I followed the howto, and azureus starts but no window pops up.  Then i just extracted the tar.bz2 and changed the "azureus" script to executable and ran it from a terminal.  The splash screen comes up and then a couple error toaster pop up messages, but no GUI!!!  Whats going on?[/QUOTE]
if u are using the 386 version of ubuntu, use Automatix to install Azureus 2.4.0.2
the link is in my signature.

---

### Post by Perfect Storm on 2006-03-26
Aye, try arnie's automatix. My howto is just one of many alternatives on howto install things. There are more than one way to Rome ;)


But if you want to proceed with this one I need the whole terminal output to get a clue what's happening.

---

### Post by arnieboy on 2006-03-26
AI: Automatix uses the procedure in this guide to install the latest version of Azureus (another super howto from you).
You will however be surprised how many users will skip the line which says "Azureus needs java installed" and then wonder why it's not working. Automatix is primarily aimed at such users who also tend to be the majority of computer users.

---

### Post by arnieboy on 2006-03-26
In fact rather than pointing to other links for installing Java you can add the following lines in your howto for installing java on x86 ubuntu installations.
```
wget http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/sun-j2re1.5_1.5.0%2bupdate05_i386.deb
sudo dpkg -i sun-j2re1.5_1.5.0%2bupdate05_i386.deb
```

---

### Post by Perfect Storm on 2006-03-26
> AI: Automatix uses the procedure in this guide to install the latest version of Azureus (another super howto from you).
You will however be surprised how many users will skip the line which says "Azureus needs java installed" and then wonder why it's not working. Automatix is primarily aimed at such users who tend to be the majority of computer users.

Ah, okay didn't knew that :)

---

### Post by hey560 on 2006-03-26
[QUOTE=Artificial Intelligence]Aye, try arnie's automatix. My howto is just one of many alternatives on howto install things. There are more than one way to Rome ;)


But if you want to proceed with this one I need the whole terminal output to get a clue what's happening.[/QUOTE]

I'm sorry but I forgot to mention, that I am using the latest Dapper Drake release as of March 25th 2006.

My terminal output is:

```

Script started on Sun 26 Mar 2006 01:49:49 PM PST
*****@VENICE:~$ cd Desktop/
*****@VENICE:~/Desktop$ sudo tar jxvf Azureus_2.4.0.2_linux.tar.bz2 -C /opt/
azureus/
azureus/azureus
azureus/Azureus.png
azureus/Azureus.torrent.png
azureus/Azureus2.jar
azureus/ChangeLog.txt
azureus/libcairo.so.1
azureus/libswt-atk-gtk-3139.so
azureus/libswt-awt-gtk-3139.so
azureus/libswt-cairo-gtk-3139.so
azureus/libswt-gnome-gtk-3139.so
azureus/libswt-gtk-3139.so
azureus/libswt-mozilla-gtk-3139.so
azureus/libswt-pi-gtk-3139.so
azureus/License.txt
azureus/plugins/
azureus/plugins/azplugins/
azureus/plugins/azplugins/azplugins_1.9.1.jar
azureus/plugins/azrating/
azureus/plugins/azrating/azrating_1.3.jar
azureus/plugins/azupdater/
azureus/plugins/azupdater/azupdaterpatcher_1.8.3.jar
azureus/plugins/azupdater/plugin.properties
azureus/plugins/azupdater/Updater.jar
azureus/README.txt
azureus/swt-about.html
azureus/swt.jar
*****@VENICE:~/Desktop$ sudo chown -R root:root /opt/azureus/
*****@VENICE:~/Desktop$ sudo gedit /usr/share/applicaions/Azureus.desktop
*****@VENICE:~/Desktop$ sudo gedit /usr/bin/azureus
*****@VENICE:~/Desktop$ sudo chmod +x /usr/bin/azureus
*****@VENICE:~/Desktop$ azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
DEBUG::Sun Mar 26 13:51:27 PST 2006::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::141:
  No SSL provider available
    SESecurityManager::initialise::53,ConfigurationChecker::setSystemProperties::144,ConfigurationManager::initialise::140,ConfigurationManager::getInstance::73,LoggerImpl::init::90,Logger::<clinit>::50,Class::initializeClass::-1,StartServer::<init>::69,Main::<init>::56,Main::main::162
DEBUG::Sun Mar 26 13:51:27 PST 2006::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::ensureStoreExists::410:
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance (libgcj.so.7)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists (SESecurityManagerImpl.java:379)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise (SESecurityManagerImpl.java:151)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise (SESecurityManager.java:53)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties (ConfigurationChecker.java:144)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise (ConfigurationManager.java:140)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance (ConfigurationManager.java:73)
   at org.gudy.azureus2.core3.logging.impl.LoggerImpl.init (LoggerImpl.java:90)
   at org.gudy.azureus2.core3.logging.Logger.<clinit> (Logger.java:50)
   at java.lang.Class.initializeClass (libgcj.so.7)
   at org.gudy.azureus2.ui.swt.StartServer.<init> (StartServer.java:69)
   at org.gudy.azureus2.ui.swt.Main.<init> (Main.java:56)
   at org.gudy.azureus2.ui.swt.Main.main (Main.java:162)

DEBUG::Sun Mar 26 13:51:27 PST 2006::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::ensureStoreExists::410:
  java.security.KeyStoreException: JKS
   at java.security.KeyStore.getInstance (libgcj.so.7)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.ensureStoreExists (SESecurityManagerImpl.java:379)
   at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl.initialise (SESecurityManagerImpl.java:153)
   at org.gudy.azureus2.core3.security.SESecurityManager.initialise (SESecurityManager.java:53)
   at org.gudy.azureus2.core3.config.impl.ConfigurationChecker.setSystemProperties (ConfigurationChecker.java:144)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.initialise (ConfigurationManager.java:140)
   at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getInstance (ConfigurationManager.java:73)
   at org.gudy.azureus2.core3.logging.impl.LoggerImpl.init (LoggerImpl.java:90)
   at org.gudy.azureus2.core3.logging.Logger.<clinit> (Logger.java:50)
   at java.lang.Class.initializeClass (libgcj.so.7)
   at org.gudy.azureus2.ui.swt.StartServer.<init> (StartServer.java:69)
   at org.gudy.azureus2.ui.swt.Main.<init> (Main.java:56)
   at org.gudy.azureus2.ui.swt.Main.main (Main.java:162)

changeLocale: *Default Language* != en (CA). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (CA)' (en_CA), using 'English (default)'
Initialize Error
DEBUG::Sun Mar 26 13:51:32 PST 2006::org.gudy.azureus2.ui.swt.mainwindow.MainWindow::runSupport::811:
  java.lang.NullPointerException
   at org.gudy.azureus2.ui.swt.components.BufferedToolItem.setImage (BufferedToolItem.java:79)
   at org.gudy.azureus2.ui.swt.IconBar.createBufferedToolItem (IconBar.java:108)
   at org.gudy.azureus2.ui.swt.IconBar.initBar (IconBar.java:125)
   at org.gudy.azureus2.ui.swt.IconBar.<init> (IconBar.java:63)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.runSupport (MainWindow.java:254)
   at org.gudy.azureus2.core3.util.AERunnable.run (AERunnable.java:43)
   at org.eclipse.swt.widgets.RunnableLock.run (RunnableLock.java:36)
   at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages (Synchronizer.java:123)
   at org.eclipse.swt.widgets.Display.runAsyncMessages (Display.java:2844)
   at org.eclipse.swt.widgets.Display.readAndDispatch (Display.java:2575)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init> (SWTThread.java:114)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance (SWTThread.java:58)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init> (Initializer.java:111)
   at org.gudy.azureus2.ui.swt.Main.<init> (Main.java:147)
   at org.gudy.azureus2.ui.swt.Main.main (Main.java:162)

DEBUG::Sun Mar 26 13:51:33 PST 2006::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::43:
  java.lang.IllegalArgumentException: Argument cannot be null
   at org.eclipse.swt.SWT.error (SWT.java:2926)
   at org.eclipse.swt.SWT.error (SWT.java:2866)
   at org.eclipse.swt.SWT.error (SWT.java:2837)
   at org.eclipse.swt.widgets.Widget.error (Widget.java:409)
   at org.eclipse.swt.widgets.Widget.checkParent (Widget.java:282)
   at org.eclipse.swt.widgets.Widget.<init> (Widget.java:174)
   at org.eclipse.swt.widgets.Item.<init> (Item.java:62)
   at org.eclipse.swt.custom.CTabItem.<init> (CTabItem.java:34)
   at org.gudy.azureus2.ui.swt.Tab.<init> (Tab.java:101)
   at org.gudy.azureus2.ui.swt.Tab.<init> (Tab.java:92)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.showMyTorrents (MainWindow.java:952)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.openMainWindow (MainWindow.java:834)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.access$1200 (MainWindow.java:82)
   at org.gudy.azureus2.ui.swt.mainwindow.MainWindow$32.runSupport (MainWindow.java:1703)
   at org.gudy.azureus2.core3.util.AERunnable.run (AERunnable.java:43)
   at org.eclipse.swt.widgets.RunnableLock.run (RunnableLock.java:36)
   at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages (Synchronizer.java:123)
   at org.eclipse.swt.widgets.Display.runAsyncMessages (Display.java:2844)
   at org.eclipse.swt.widgets.Display.readAndDispatch (Display.java:2575)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init> (SWTThread.java:114)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance (SWTThread.java:58)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init> (Initializer.java:111)
   at org.gudy.azureus2.ui.swt.Main.<init> (Main.java:147)
   at org.gudy.azureus2.ui.swt.Main.main (Main.java:162)

[Sun Mar 26 13:51:34 PST 2006] Connection write error [ae2.aelitis.com/85.31.105.2] [<>]: Connection refused
java.io.IOException: message send attempt failed
   at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage (AEClientService.java:149)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck (VersionCheckClient.java:238)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:101)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getExternalIpAddress (VersionCheckClient.java:136)
   at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.getPublicAddress (UtilitiesImpl.java:346)
   at com.aelitis.azureus.plugins.jpc.discovery.impl.JPCDiscoveryImpl.<init> (JPCDiscoveryImpl.java:76)
   at com.aelitis.azureus.plugins.jpc.discovery.JPCDiscoveryFactory.create (JPCDiscoveryFactory.java:44)
   at com.aelitis.azureus.plugins.jpc.cache.impl.JPCCacheManagerImpl$1.run (JPCCacheManagerImpl.java:63)
   at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl$2.runSupport (UtilitiesImpl.java:248)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)
[Sun Mar 26 13:51:34 PST 2006] Connection write error [ae2.aelitis.com/85.31.105.2] [<>]: Connection refused
java.io.IOException: message send attempt failed
   at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage (AEClientService.java:149)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck (VersionCheckClient.java:238)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:101)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:85)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.DHTEnableAllowed (VersionCheckClient.java:152)
   at com.aelitis.azureus.plugins.dht.DHTPlugin$14.runSupport (DHTPlugin.java:748)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)
DEBUG::Sun Mar 26 13:51:34 PST 2006::com.aelitis.azureus.core.dht.control.impl.DHTControlImpl::<init>::214:
  java.security.NoSuchAlgorithmException: DESede/ECB/PKCS5Padding: class not found: DESede
   at javax.crypto.Cipher.getInstance (libgcj.so.7)
   at com.aelitis.azureus.core.dht.control.impl.DHTControlImpl.<init> (DHTControlImpl.java:204)
   at com.aelitis.azureus.core.dht.control.DHTControlFactory.create (DHTControlFactory.java:53)
   at com.aelitis.azureus.core.dht.impl.DHTImpl.<init> (DHTImpl.java:78)
   at com.aelitis.azureus.core.dht.DHTFactory.create (DHTFactory.java:45)
   at com.aelitis.azureus.plugins.dht.impl.DHTPluginImpl.<init> (DHTPluginImpl.java:199)
   at com.aelitis.azureus.plugins.dht.DHTPlugin$14.runSupport (DHTPlugin.java:758)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)

DEBUG::Sun Mar 26 13:51:34 PST 2006::com.aelitis.azureus.plugins.dht.DHTPlugin$10::log::520:
  java.security.NoSuchAlgorithmException: DESede/ECB/PKCS5Padding: class not found: DESede
   at javax.crypto.Cipher.getInstance (libgcj.so.7)
   at com.aelitis.azureus.core.dht.control.impl.DHTControlImpl.<init> (DHTControlImpl.java:204)
   at com.aelitis.azureus.core.dht.control.DHTControlFactory.create (DHTControlFactory.java:53)
   at com.aelitis.azureus.core.dht.impl.DHTImpl.<init> (DHTImpl.java:78)
   at com.aelitis.azureus.core.dht.DHTFactory.create (DHTFactory.java:45)
   at com.aelitis.azureus.plugins.dht.impl.DHTPluginImpl.<init> (DHTPluginImpl.java:199)
   at com.aelitis.azureus.plugins.dht.DHTPlugin$14.runSupport (DHTPlugin.java:758)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)

[Sun Mar 26 13:51:36 PST 2006] Connection write error [ae2.aelitis.com/85.31.105.2] [<>]: Connection refused
java.io.IOException: message send attempt failed
   at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage (AEClientService.java:149)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck (VersionCheckClient.java:238)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:101)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:85)
   at org.gudy.azureus2.update.CoreUpdateChecker.checkForUpdate (CoreUpdateChecker.java:150)
   at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport (UpdateCheckInstanceImpl.java:145)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)
DEBUG::Sun Mar 26 13:51:36 PST 2006::org.gudy.azureus2.update.CoreUpdateChecker::checkForUpdate::284:
  java.lang.Exception: No version found in reply
   at org.gudy.azureus2.update.CoreUpdateChecker.checkForUpdate (CoreUpdateChecker.java:169)
   at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport (UpdateCheckInstanceImpl.java:145)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)

DEBUG::Sun Mar 26 13:51:36 PST 2006::org.gudy.azureus2.update.CoreUpdateChecker::checkForUpdate::286:
  java.lang.Exception: No version found in reply
   at org.gudy.azureus2.update.CoreUpdateChecker.checkForUpdate (CoreUpdateChecker.java:169)
   at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport (UpdateCheckInstanceImpl.java:145)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)

[Sun Mar 26 13:51:36 PST 2006] Connection write error [ae2.aelitis.com/85.31.105.2] [<>]: Connection refused
java.io.IOException: message send attempt failed
   at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage (AEClientService.java:149)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck (VersionCheckClient.java:238)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:101)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:85)
   at org.gudy.azureus2.ui.swt.updater2.SWTVersionGetter.downloadLatestVersion (SWTVersionGetter.java:98)
   at org.gudy.azureus2.ui.swt.updater2.SWTVersionGetter.needsUpdate (SWTVersionGetter.java:79)
   at org.gudy.azureus2.ui.swt.updater2.SWTUpdateChecker.checkForUpdate (SWTUpdateChecker.java:70)
   at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport (UpdateCheckInstanceImpl.java:145)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)
[Sun Mar 26 13:51:36 PST 2006] Connection write error [ae2.aelitis.com/85.31.105.2] [<>]: Connection refused
java.io.IOException: message send attempt failed
   at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage (AEClientService.java:149)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck (VersionCheckClient.java:238)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:101)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo (VersionCheckClient.java:85)
   at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getRecommendedPlugins (VersionCheckClient.java:200)
   at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin$4.checkForUpdate (PluginUpdatePlugin.java:194)
   at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport (UpdateCheckInstanceImpl.java:145)
   at org.gudy.azureus2.core3.util.AEThread.run (AEThread.java:74)

Script done on Sun 26 Mar 2006 01:52:08 PM PST

```

I exit the program by typing Control-C in the terminal (this is after the splash screen pops up, and the error message is displayed).

I also attached a image of the error message that pops up.  I appreciate the help.

---

### Post by arnieboy on 2006-03-26
u are using blackdown's java 1.4. that why its not working.
do the following from terminal:
```
wget http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/java/sun-j2re1.5_1.5.0%2bupdate05_i386.deb
sudo dpkg -i sun-j2re1.5_1.5.0%2bupdate05_i386.deb
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
rm -rf ~/.Azureus
```
now run azureus again.

---

### Post by hey560 on 2006-03-26
Thanks, that did the trick.  I had version 1.5 of sun's java installed but not as a debian package so it was just sitting in /usr/lib/j2re1.5.  Obviously azureus couldn't find this version so it used version 1.4 and croaked.  Before using the debian package shown, I could also fix the problem by setting the JAVA_PROGRAM_DIR in the azureus startup script to point to the location I extracted 1.5 version of java.  Anway thanks guys for the help!

---

### Post by Don_DiZzLe on 2006-03-30
I use port 32656 for azureus and everything is portforwarded just fine in my router, however I get an NAT error when I initiate the NAT / Firewall test. It seems I'm behind somekind of firewall. Is this a Ubuntu firewall or what? And if so how do I turn if of so I can download files at maximum speed?

---

### Post by Nordoelum on 2006-04-03
I can't run Azureus anymore. Then I tryed it in terminal:
```
nordoelum@nordoelum:~/Desktop$ azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/azureus/libswt-pi-gtk-3139.so: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Azureus TERMINATED.
nordoelum@nordoelum:~/Desktop$
```
What can this be? Do I need to reinstall the Java?

---

### Post by Nordoelum on 2006-04-04
Someone that might have an solution?

---

### Post by Perfect Storm on 2006-04-04
You could try automatix to install Azureus. What I understand from Arnie is that it install Azureus the same way as described in this howto.

---

### Post by Nordoelum on 2006-04-04
[quote=Artificial Intelligence]You could try automatix to install Azureus. What I understand from Arnie is that it install Azureus the same way as described in this howto.[/quote]
I have tryed Automatric, but I rather do it my self.

I find this really stranger though. Since I used Azureus this whole weekend..

---

### Post by Perfect Storm on 2006-04-04
Anything unusual you have done with Azureus or Java before this error shows up? Is it only happen when running azureus in the terminal?

---

### Post by Nordoelum on 2006-04-04
[quote=Artificial Intelligence]Anything unusual you have done with Azureus or Java before this error shows up? Is it only happen when running azureus in the terminal?[/quote]
I know I have changed some sources.list but nothing more then that.. And it accour when I use the start menu button too..

The bundled bt client have stopped working too :(

---

### Post by vxj9219 on 2006-04-10
this is what i keep getting when i try to run azureus

Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/azureus/libswt-pi-gtk-3139.so: /opt/azureus/libswt-pi-gtk-3139.so: ELF file data encoding not little-endian
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
Azureus TERMINATED.

how to fix the problem?

and also sudo apt-get remove azureus does not work. this is what i get

sudo apt-get remove azureus
Reading package lists... Done
Building dependency tree... Done
Package azureus is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

how can i uninstall azureus (so that i can try installing it again)?

---

### Post by Perfect Storm on 2006-04-10
This is the non-repo way so you can't apt-get or dpkg it to remove it. You need to do it manually.
```
cd /opt
sudo rm -r azureus

```

---

### Post by vxj9219 on 2006-04-10
i removed azureus and reinstalled it according to the howto in this thread. nothing happens when i click on the azureus icon in Internet menu. in the command line when i type azureus, i get the same message as in my previous post. is there a way to fix this?

---

### Post by Nordoelum on 2006-04-10
[quote=vxj9219]i removed azureus and reinstalled it according to the howto in this thread. nothing happens when i click on the azureus icon in Internet menu. in the command line when i type azureus, i get the same message as in my previous post. is there a way to fix this?[/quote]

I get the same :(

Tryed to remove 2.0.4.2 and tryed to synaptic release?

---

### Post by Perfect Storm on 2006-04-10
I dunno quite what the problem is...

Try with 
```
sh /opt/azureus/azureus
```
instead.

Also try check /home/<username>/.azureus/logs for possible error logs.

Are you both on i386 structure or other like a64?

---

### Post by vxj9219 on 2006-04-10
i386...

and /home/username/.azureus/logs has this no error logs.

---

### Post by Perfect Storm on 2006-04-10
Open the newest one. Any error shown? There's also a subfolder called 'save' any alert logs there?

---

### Post by vxj9219 on 2006-04-10
there is a thread_1.log file. it has

[1004 02:08:03] Monitoring starts (processors =1)
[1004 02:09:04] Monitoring starts (processors =1)
[1004 02:09:25] Monitoring starts (processors =1)
[1004 02:16:57] Monitoring starts (processors =1)
[1004 02:18:18] Monitoring starts (processors =1)
[1004 02:22:38] Monitoring starts (processors =1)
[1004 02:22:48] Monitoring starts (processors =1)
[1004 02:23:02] Monitoring starts (processors =1)
[1004 02:28:05] Monitoring starts (processors =1)
[1004 02:32:46] Monitoring starts (processors =1)
[1004 02:32:59] Monitoring starts (processors =1)
[1004 02:33:05] Monitoring starts (processors =1)
[1004 11:08:25] Monitoring starts (processors =1)
[1004 11:10:27] Monitoring starts (processors =1)
[1004 11:10:41] Monitoring starts (processors =1)
[1004 11:12:34] Monitoring starts (processors =1)
[1004 11:13:31] Monitoring starts (processors =1)

and save has these files
1144652944730_thread_1.log  1144654366692_thread_1.log
1144652965383_thread_1.log  1144654379114_thread_1.log
1144653417801_thread_1.log  1144654385273_thread_1.log
1144653498310_thread_1.log  1144685305241_thread_1.log
1144653758745_thread_1.log  1144685426996_thread_1.log
1144653768590_thread_1.log  1144685440845_thread_1.log
1144653782783_thread_1.log  1144685554322_thread_1.log
1144654084839_thread_1.log  1144685611313_thread_1.log

and none of them have anything looking like an error message.

---

### Post by Perfect Storm on 2006-04-10
Hmmm....strange.

and you did:
```
sudo update-alternatives --config java
```
and choosed the right one?

Else you might try automatix or easy ubuntu to install azureus.

---

### Post by vxj9219 on 2006-04-10
yes i did, and chose sun's java as the default one.

i was able to install azureus through automatix. thanks AI

---

### Post by exiledsoul on 2006-04-16
I used this guide to install azureus. The auto updates don't work, it says that the directories don't have the right permission but I checked and can't manually change them. I'm a newbie and I'm not an expert with the command line. Can anybody help?

the directory is: ./opt/azureus

the installing window always comes up when I start azureus. I hope there's a solution for this... thanks!

---

### Post by Virak on 2006-04-16
I don't know if anyone has mentioned this yet, but the contents of the /usr/bin/azureus script should be:
```
#!/bin/sh

/opt/azureus/azureus $*
``` The version in the howto won't pass any arguments along to Azureus, which is a bit annoying.

---

### Post by Perfect Storm on 2006-04-16
Thanks. I'll change that.

---

### Post by DevilGhost on 2006-04-17
[QUOTE=exiledsoul]I used this guide to install azureus. The auto updates don't work, it says that the directories don't have the right permission but I checked and can't manually change them. I'm a newbie and I'm not an expert with the command line. Can anybody help?

the directory is: ./opt/azureus

the installing window always comes up when I start azureus. I hope there's a solution for this... thanks![/QUOTE]

I am also seeing this message... Version 2.0 of plugin 'azplugins' failed to install - /opt/azureus/plugins/azplugins/azplugins_2.0.jar (Permission denied). Do I need to change a permission on this directory?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=DevilGhost]I am also seeing this message... Version 2.0 of plugin 'azplugins' failed to install - /opt/azureus/plugins/azplugins/azplugins_2.0.jar (Permission denied). Do I need to change a permission on this directory?[/QUOTE]
No don't change the directory permissions. Just run azureus as root. The new version of the plugin will be applied and then close azureus and don't run it as root. Then you can use it to download all the legal files you want. :)

---

### Post by DevilGhost on 2006-04-17
TY! I didn't think I wanted to change the permissions! hehe, but then again I didn't see anything else about it.

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=DevilGhost]TY! I didn't think I wanted to change the permissions! hehe, but then again I didn't see anything else about it.[/QUOTE]
You don't want to change the permissions because someone could get acess to that folder/directory.

---

### Post by stkaplan on 2006-04-17
I followed the instructions in this guide, and I'm having an issue with the pop-up notifications for Azureus. Everything about the program works fine, except when I try to hide the pop-up notifications, nothing happens. This is on Dapper.

I'm using the Sun j2sdk, version 1.5, installed through the PLF repository. The output of java -version is ```
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```
Any advice?

---

### Post by Nordoelum on 2006-04-20
[quote=Artificial Intelligence]I dunno quite what the problem is...

Try with 
```
sh /opt/azureus/azureus
``` instead.

Also try check /home/<username>/.azureus/logs for possible error logs.

Are you both on i386 structure or other like a64?[/quote]
I use the i386 structure.

---

### Post by Nordoelum on 2006-04-20
[quote=Artificial Intelligence]Hmmm....strange.

and you did:
```
sudo update-alternatives --config java
``` and choosed the right one?

Else you might try automatix or easy ubuntu to install azureus.[/quote] ```
nordoelum@nordoelum:~/.azureus/logs/save$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/j2re1.5-sun/bin/java
 +    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/lib/j2sdk1.5-sun/bin/java
      4        /usr/bin/gij-wrapper-4.0

Press enter to keep the default
[*], or type selection number:
```
This the choices I get.

---

### Post by Perfect Storm on 2006-06-01
Changed the howto to Ubuntu 6.06
Changed the links to Automatix and easy Ubuntu to Dapper/newest version.
Plus some minor fixes.
Still works for Ubuntu Breezy.

---

### Post by michaeljb2005 on 2006-06-01
I thought I might comment that with an OS X theme that I retrieved from gnome-look called "MacOS-X Aqua Theme" that azureus dies with errors when certain menu items are clicked on.  I actually created a Thread on this which has the errors just so you know [http://ubuntuforums.org/showthread.php?t=183257&highlight=azureus](http://ubuntuforums.org/showthread.php?t=183257&highlight=azureus).

---

### Post by warpen on 2006-06-08
Thanks alot. Workes like a charm.

---

### Post by Epperly on 2006-10-12
Im havin a problem no such /opt/azureus or whatever somethin like that can anyone help? thanks

---

### Post by Perfect Storm on 2006-10-18
Updated:
Works on Edgy as well
rewritten a bit of the howto.

---

### Post by Peepsalot on 2006-10-18
I would recommend adding an ampersand in the terminal script.  To allow using/closing of the terminal afterwards.
```
#!/bin/sh

/opt/azureus/azureus& $*
```
I'm not completely sure this still works with the parameters, but then again, I don't know any command line options for Azureus to test it.

Great how-to by the way.  I don't know why they won't just update the broken edgy repositories though...](*,)

---

### Post by rykel on 2006-10-19
This is truly marvelous... I am finally using the latest version of my fav torrent program! Lots of legal programs for me to download speedily without crashes, non-removable pop=ups and a persistent Frog icon in the Ubuntu Notification Area at last!

btw, I access the internet primarily through free SkyNetGlobal wifi at McDonald's... however, with a public connection, I CANNOT set port forwarding, and so with Azureus, I have NEVER got a Green smile whenever I am out there in the restaurant...

Is there a way/plugin/version in/of Azureus which CAN work without having to access the port forwardings in the router web admin?

Thanks for helping...

---

### Post by Epperly on 2006-10-19
> **Artificial Intelligence said:**
> Updated:
Works on Edgy as well
rewritten a bit of the howto.
Artificial: I keep getting this..
```
sammy@SAMMY:~/Desktop$ sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2 -C /opt/
Password:
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
sammy@SAMMY:~/Desktop$ sudo chown -R root:root /opt/azureus/
chown: cannot access `/opt/azureus/': No such file or directory
sammy@SAMMY:~/Desktop$

```

---

### Post by Perfect Storm on 2006-10-20
> **Epperly said:**
> Artificial: I keep getting this..
```
sammy@SAMMY:~/Desktop$ sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2 -C /opt/
Password:
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
sammy@SAMMY:~/Desktop$ sudo chown -R root:root /opt/azureus/
chown: cannot access `/opt/azureus/': No such file or directory
sammy@SAMMY:~/Desktop$

```

Check if you have  /opt

---

### Post by Epperly on 2006-10-20
> **Artificial Intelligence said:**
> Check if you have  /opt

Where do I check? I've searched but can't find.

---

### Post by Perfect Storm on 2006-10-20
The simplest way:
```
cd /opt
```

or you can use the file-browser.

---

### Post by Epperly on 2006-10-20
I have /opt but not /opt/azureus...

---

### Post by Perfect Storm on 2006-10-20
okay try this:
```
sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2
gksudo nautilus
```

from there you move Azureus folder to /opt via the file-browser that shown up and then continue the with the howto from there.

---

### Post by Epperly on 2006-10-20
> **Artificial Intelligence said:**
> okay try this:
```
sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2
gksudo nautilus
```

from there you move Azureus folder to /opt via the file-browser that shown up and then continue the with the howto from there.

Awesome! That's cool thanks.
but now for the last step I get this:
```
sammy@SAMMY:~$ sudo chmod +x /usr/bin/azureus
chmod: cannot access `/usr/bin/azureus': No such file or directory

```

Thanks for the help.

---

### Post by Perfect Storm on 2006-10-20
Did you:
```
sudo nano /usr/bin/azureus
```
first?

---

### Post by Epperly on 2006-10-20
Ahh, that I did not. Thank you for the help!

---

### Post by klato on 2006-10-21
Worked like a charm over here! Thanks!

---

### Post by nandasunu on 2006-10-31
Thanks!

---

### Post by Digital Alchemist on 2006-11-01
Working great here (fresh edgy install).

As I get annoyed at having to use Azureus as root to install/update plugins I setted the groups ownership (recursively) of /opt/azureus/plugins to the group admin and changed the permission to 771 (so root and admin can rwx and others one x). 

```
sudo chown root:admin -R /opt/azureus/plugins
sudo chmod -R 771 /opt/azureus/plugins
```

I believe this is still secure as only the users on the admin group (they have the ability to sudo) will be able to write to the plugins directory. What do you guys think?

---

### Post by loclei on 2006-11-20
can someone tell me how to make azureus work with a proxy?
i have set proxy in system > preferences > proxy
and in azureus
what i want is for someone to explain to me how to set the proxy in azureus
i have http proxy that's like ip: portnumber
thx in advance
also i'm not sure if the java i have installed is the right one 
```

user@monkey-pc:~/Download$ sudo update-alternatives --config java
Password:

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

```

---

### Post by Perfect Storm on 2006-11-20
The java looks okay. The proxy I can't answer.

---

### Post by loclei on 2006-11-20
is there someone who got azureus working behind a proxy?
my proxy is [http://ipnumber:](http://ipnumber:) portnumber
how should i set up proxy in azureus in order for it to work?
thx

---

### Post by Perfect Storm on 2006-11-20
A quick search on the forum: [http://ubuntuforums.org/search.php?searchid=9957034](http://ubuntuforums.org/search.php?searchid=9957034)

---

### Post by loclei on 2006-11-20
> **Artificial Intelligence said:**
> A quick search on the forum: [http://ubuntuforums.org/search.php?searchid=9957034](http://ubuntuforums.org/search.php?searchid=9957034)
I've searched them also but
they didn't help
:(

---

### Post by Perfect Storm on 2006-11-20
The best chance for you will be starting a new thread then (so the right people can spot it). Try start a new thread with headlins like this: Azureus and proxy trouble.
I'm sure someone out there will jump in and help you :)

---

### Post by ThePerformer on 2006-12-06
i just got eft on my computer and am struggling with the azureus install.  I've searched the forums for advice and end up in the same place...after i type in "sudo tar jxvf Azureus_2.5.0.0_linux.tar.bz2 -C /opt/" to the terminal i get this....
"
tar: Azureus_2.5.0.0_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
"
If someone can help me it would be most appreciated, i've got lots of downloading to do...no breaches with respect to copyrights though!

---

### Post by Perfect Storm on 2006-12-06
1) Make sure you run the command where the file is
2) It may borked, try download it again.

---

### Post by jansi on 2007-01-09
Instructions worked as is and great! Thanks! (Edgy machine that was upgraded from Breezy)

---

### Post by schio on 2007-01-16
Wow... it worked just perfect! Thanks AI!  If it so simple why is the version in the repo not working? 
I also hope that developers make java 1.5.0.10 available in the repo very soon, i know I could install it manually, but since this is my first Linux installation I don't want to move too far away from the standard installation and make a mess before even having time to use it!

---

### Post by sapn on 2007-03-21
Thanks for a great howto :D

---

### Post by Perfect Storm on 2007-04-19
Howto updated and tested in Feisty.

---

### Post by sojyujai on 2007-04-21
I'm having a bit of problem with this.  I think it has to do with the $* in this:

> **Artificial Intelligence said:**
> 
 #!/bin/sh

/opt/azureus/azureus $*


from the /usr/bin/azureus file.  

It seems that if there's a space in the torrent file name, or anywhere in the path (if the torrent file is already on the hard drive) that a truncated path/filename will be passed along to /opt/azureus/azureus resulting in an error in azureus when it tries to open it (after double-clicking if it's local, or opening from firefox).  The truncation always seems to happen at the position of the space so I'm pretty sure the space is causing the problem.

I don't know enough about what the $* is doing or how arguments are passed to be able to fix this myself.  Does anyone have a suggestion - how to pass along the full path/filename (including spaces) from /usr/bin/azureus to /opt/azureus/azureus?

Thanks

---

### Post by pain of salvation on 2007-04-24
I got this error:

> alvaro@ubuntu:~$ azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3320 or swt-pi-gtk in swt.library.path, java.libary.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:219)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:89)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:106)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
Azureus TERMINATED.


---

### Post by The Pinny Parlour on 2007-04-27
I'm trying this but have no idea how to save in nano.  What do I need to do?   You just say save and close save how and close how and save where and......?????

---

### Post by sphatiga on 2007-04-30
This is in response to sojyujai and anyone else that has problems with adding torrent files that have whitespaces in its filename. This was annoying the heck out of me too as alot of the torrent filenames that I download have long names with whitespaces. With the provided bash script those files wouldn't load.

The answer is to put the $* in quotations. 

```

#!/bin/sh

/opt/azureus/azureus "$*"
```

I hope that helps and works correctly for everyone else. Thanks OP for the HOWTO

---

### Post by Perfect Storm on 2007-05-01
Added the quote.

---

### Post by XTREEM|RAGE on 2007-05-08
it want to do some plugin update, but i get this:
```
    Downloading: [http://torrents.aelitis.com:88/torrents/azplugins_2.1.4.jar.torrent: torrent,http://azureus.sourceforge.net/plugins/azplugins_2.1.4.jar]
      Downloading: azplugins_2.1.4.jar
Torrent download complete
Installing plugin azplugins, version 2.1.4
    Data verification stage complete
Version 2.1.4 of plugin 'azplugins' failed to install - /opt/azureus/plugins/azplugins/azplugins_2.1.4.jar (Permission denied)
```

---

### Post by Perfect Storm on 2007-05-08
sudo chown -R <username>:<username> /opt/azureus/

when finish updating then;

sudo chown -R root:root /opt/azureus/

---

### Post by XTREEM|RAGE on 2007-05-09
> **Artificial Intelligence said:**
> sudo chown -R <username>:<username> /opt/azureus/

when finish updating then;

sudo chown -R root:root /opt/azureus/

tnx that helped! :)

---

### Post by camposer on 2007-05-17
About problem with swt libraries.

I also had it. I found this: [http://www.centos.org/modules/newbb/viewtopic.php?topic_id=7973](http://www.centos.org/modules/newbb/viewtopic.php?topic_id=7973) , but it wasn't my case: I don't have /tmp as separate filesystem and moreover, no one of my filesystems have "noexec" option set.

So I was trying to dig into it and lost several hours of time --- just for nothing. All this time I was trying to launch AMD64 version of Azureus, since I have EM64T machine. When I lost any hope, I decided to try normal (32 bit) version --- and voila! it works. I suspect there is a conflict in my java installation, but maybe this will help to solve your problem as well...

   Ivan

---

### Post by The other One on 2007-05-22
This worked perfectly for me - Thanks!

---

### Post by Severa on 2007-06-29
This guide worked like a charm for me in GUTSY for version 2.5.0.4. Well done!

---

### Post by jasontan6 on 2007-06-30
Installed v2.5.0.4 on Feisty and worked.

Thanks!

---

### Post by osilee on 2007-07-05
This worked beautifully.  Thanks for the help.  Make sure to run Azureus as Root initially to allow upgrades to install.  Thanks for the help!

---

### Post by dr.koljan on 2007-08-08
i

---

### Post by Perfect Storm on 2007-08-18
The howto is now updated - Changed to Azureus 3.0 - Vuze

---

### Post by small_bigguy on 2007-08-18
Excelent tutorial, thanks

---

### Post by Hoshimaru on 2007-08-19
Ouch ... My Azureus worked fine until today after it got updated to v3.0.2.0
I had a 2.something before.

```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
DEBUG::Sun Aug 19 16:47:57 GMT+02:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::152:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::210,ConfigurationManager::initialise::150,ConfigurationManager::getInstance::83,LoggerImpl::init::88,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::72,Main::<init>::56,Main::main::203
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.internat.MessageText
   at java.lang.Class.initializeClass(libgcj.so.70)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:156)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:100)
   at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:76)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)
Azureus TERMINATED.

```
Any suggestions?

---

### Post by Polygon on 2007-08-19
im getting this as well, i just clicked update from the little azureus updater thing and now it wont start. suggestions?

my error output:

```
mark@ubuntu:~$ /opt/azureus/azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''
WARNING: Error loading security provider org.bouncycastle.jce.provider.BouncyCastleProvider: java.lang.ClassNotFoundException: org.bouncycastle.jce.provider.BouncyCastleProvider
WARNING: Error loading security provider gnu.crypto.jce.GnuCrypto: java.lang.ClassNotFoundException: gnu.crypto.jce.GnuCrypto
DEBUG::Sun Aug 19 08:03:07 GMT-07:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::152:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::210,ConfigurationManager::initialise::150,ConfigurationManager::getInstance::83,LoggerImpl::init::88,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::72,Main::<init>::56,Main::main::203
Exception in thread "main" java.lang.NoClassDefFoundError: org.gudy.azureus2.core3.internat.MessageText
   at java.lang.Class.initializeClass(libgcj.so.70)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl.java:156)
   at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:100)
   at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:76)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)
Caused by: java.lang.ClassNotFoundException: sun.security.action.GetPropertyAction not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/opt/azureus/Azureus2.jar,file:/opt/azureus/swt.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...5 more
Azureus TERMINATED.
mark@ubuntu:~$ 

```

edit: i just reinstalled azureus and it works for me now...

---

### Post by j0v3m on 2007-08-19
I've installed Vuze on Ubuntu Gutsy and it's almost OK, but I'd want to know if the "Browse Content" get more than "Loading.. Please Wait" for someone.

---

### Post by akshunj on 2007-08-20
For those having trouble with the upgrade to Azureus 3.0, I would recommend COMPLETELY removing any old versions and installing the newest version clean.  Worked for me on Kubuntu Feisty.  FYI, I can't figure out how to download Azureus 3.0 from the official site, but I found it here:

[http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=215453](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=215453)

It looks like a beta, but it's version 3.0.2.0,,, Same as the Windows and Mac version.  Finally!  And it's running stable on my rig.

--Akshun J

---

### Post by tmussche on 2007-08-23
[Edit] Problem solved, ignore this post ;-)

Followed the instructions on Ubuntu Feisty system. I used the newest archive:

> **akshunj said:**
> 
[http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=215453](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=215453)

It looks like a beta, but it's version 3.0.2.0,,, Same as the Windows and Mac version.  Finally!  And it's running stable on my rig.

--Akshun J

Everything runs fine except the following error message when i start azureus:

"Can't read 'plugin.properties' for plugin 'eclipse': file may be missing"

How can i solve this problem (if it is a problem because i don't notice any strange behaviour) and get rid of this error message?

Greetz,

T


[Edit] Problem solved, ignore this post ;-)

---

### Post by dr.koljan on 2007-08-24
[Here]("http://ubuntuforums.org/showthread.php?t=529431")'s an easier and cleaner way to install the latest Azureus. :)

---

### Post by split017 on 2007-08-24
i'm getting stuck on step 4 of the guide. after running this command: 

sudo nano /usr/share/applications/Azureus.desktop

I add the text shown:

[Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

how do i save the file now? there is no File>Save nor Edit>Save. what do i need to do to save the changes to the file?

thanks.

---

### Post by Perfect Storm on 2007-08-24
<ctrl> + <o> = save
<ctrl> + <x> = exit

---

### Post by mspendlo on 2007-08-29
Cool, this worked for me with Feisty. Thanks :)

Couldn't get the package version going at all - JVM kept crashing (1.6).

Still, all good going down this root with the tarball. Shouldn't be this fiddly though !

FYI - the tar ball :

[http://downloads.sourceforge.net/azureus/Azureus_3.0.2.0_linux.tar.bz2?modtime=1187317598&big_mirror=0](http://downloads.sourceforge.net/azureus/Azureus_3.0.2.0_linux.tar.bz2?modtime=1187317598&big_mirror=0)

Cheers

---

### Post by mahasmb on 2007-08-29
This is not what I wanted at all. What is this Vuze thing?

I just want Azureus,

---

### Post by Perfect Storm on 2007-08-30
Vuze is Azureus. Vuze is name of Azureus version 3.x.x

---

### Post by kolinab on 2007-09-08
Brilliant! Thanks so much for this howto. Vuze looked a little wierd for me at first but I enabled advanced mode, got rid of the search bar and tab bar, and things look familiar again. 

K

---

### Post by ajmannen on 2007-09-17
> andreas@andreas-laptop:~$ cd Desktop
andreas@andreas-laptop:~/Desktop$ sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
Password:
azureus/
azureus/azureus
azureus/Azureus.png
azureus/Azureus.torrent.png
azureus/Azureus2.jar
azureus/License.txt
azureus/plugins/
azureus/plugins/azplugins/
azureus/plugins/azplugins/azplugins_2.1.4.jar
azureus/plugins/azrating/
azureus/plugins/azrating/azrating_1.3.1.jar
azureus/plugins/azupdater/
azureus/plugins/azupdater/azupdaterpatcher_1.8.5.jar
azureus/plugins/azupdater/plugin.properties
azureus/plugins/azupdater/Updater.jar
azureus/plugins/azupnpav/
azureus/plugins/azupnpav/azupnpav_0.1.3.jar
azureus/plugins/azupnpav/plugin.properties
azureus/README.txt
azureus/swt.jar
azureus/updateAzureus
andreas@andreas-laptop:~/Desktop$ sudo nano /usr/share/applications/Azureus.desktop
andreas@andreas-laptop:~/Desktop$ sudo chmod +x /usr/bin/azureus
chmod: cannot access `/usr/bin/azureus': No such file or directory
andreas@andreas-laptop:~/Desktop$ azureus
The program 'azureus' is currently not installed.  You can install it by typing:
sudo apt-get install azureus
Make sure you have the 'universe' component enabled
bash: azureus: command not found
andreas@andreas-laptop:~/Desktop$ sudo chown -R root:root /opt/azureus/
andreas@andreas-laptop:~/Desktop$ 
Dkdn't work :confused:
Here is what i wrote in the other..thing

---

### Post by Perfect Storm on 2007-09-17
You made a mistake, at sudo nano /usr/share/applications/Azureus.desktop

Try re-check it.

---

### Post by ajmannen on 2007-09-17
Now i get an error when i do the sudo chown -R <username>:<username> /opt/azureus/
> andreas@andreas-laptop:~$ cd Desktop
andreas@andreas-laptop:~/Desktop$ sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
azureus/
azureus/azureus
azureus/Azureus.png
azureus/Azureus.torrent.png
azureus/Azureus2.jar
azureus/License.txt
azureus/plugins/
azureus/plugins/azplugins/
azureus/plugins/azplugins/azplugins_2.1.4.jar
azureus/plugins/azrating/
azureus/plugins/azrating/azrating_1.3.1.jar
azureus/plugins/azupdater/
azureus/plugins/azupdater/azupdaterpatcher_1.8.5.jar
azureus/plugins/azupdater/plugin.properties
azureus/plugins/azupdater/Updater.jar
azureus/plugins/azupnpav/
azureus/plugins/azupnpav/azupnpav_0.1.3.jar
azureus/plugins/azupnpav/plugin.properties
azureus/README.txt
azureus/swt.jar
azureus/updateAzureus
andreas@andreas-laptop:~/Desktop$ sudo chown -R <username>:<username> /opt/azureus/
bash: username: No such file or directory
andreas@andreas-laptop:~/Desktop$ sudo chown -R <andreas>:<andreas> /opt/azureus/
bash: andreas: No such file or directory
andreas@andreas-laptop:~/Desktop$ 
Sorry if i have done a realy stupid mistake, but i'm still newby

---

### Post by synd7 on 2007-09-21
I can confirm this works in gutsy.

Just a quick question, why is it necessary to make root the owner?

---

### Post by Perfect Storm on 2007-09-21
For safty

---

### Post by synd7 on 2007-09-21
oh ok, i would have thought it would be less safe being owned by root
shows how much i know :)

EDIT:
> **ajmannen said:**
> Now i get an error when i do the sudo chown -R <username>:<username> /opt/azureus/

Sorry if i have done a realy stupid mistake, but i'm still newby

That should be 
```
sudo chown -R andreas:andreas /opt/azureus/
```

---

### Post by Gouz on 2007-09-25
Ok about couple of weeks ago I installed azureus and it is working fine from the first time.
I had to format and now I can't get it running.
I am always getting the same message 

An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aaac6cccc9f, pid=20567, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9c9f]
#
# An error report file with more information is saved as hs_err_pid20567.log
Aborted (core dumped)


any idea? I am sure that I have only one version of java cause I have deleted the rest:

sudo update-alternatives --config java
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

any ideas?

thanks

---

### Post by bartfliet on 2007-10-03
Ok, I downloaded the package and opened the terminal to install it and I got this message:

```
bart@bart-desktop:~$ cd Desktop
bart@bart-desktop:~/Desktop$ sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
tar: Azureus_3_0_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
bart@bart-desktop:~/Desktop$ sudo chown -R <username>:<username> /opt/azureus/

```

Could anybody advise to what I'm doing wrong?

---

### Post by Perfect Storm on 2007-10-03
Check the name of the file. It changes time to time.

---

### Post by bartfliet on 2007-10-03
Ok, well, now it did seem to unpack, but then at the end I got this.

```
bart@bart-desktop:~$ sudo chmod +x /usr/bin/azureus
chmod: cannot access `/usr/bin/azureus': No such file or directory
bart@bart-desktop:~$ azureus

```

maybe I should say that I am absolutly new at Linux so if I need to add anything anywhere else...any help appreciated, thanks.

---

### Post by Perfect Storm on 2007-10-03
Seems you forgot to save the file, command: **sudo nano /usr/bin/azureus**

Go back to that part of the guide.
You can save the file with (ctrl)+(o) and exit = (ctrl)+(x)

---

### Post by bartfliet on 2007-10-03
Thanks alot, I got it installed! 

But eum...I shut it down...and I can't seem to find an icon anywhere to start it?

---

### Post by Perfect Storm on 2007-10-03
just type azureus in the terminal.

or try 
```
killall gnome-panel
```
Then the icon should appear under internet.

May I also suggest trying out Deluge. A way better than azureus (and uses way less resources): [http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by bartfliet on 2007-10-03
hmmm typing it in the terminal works, but the code didn't,

Thanks alot anyway!

---

### Post by SaturnTheIcy on 2007-10-08
Thanks a lot for the how to 
:)

---

### Post by joris1977 on 2007-10-12
Really nice howto:

Can conform this works for gutsy!

on a side note:
beats me why azureus never worked in the repos. I thought i read somewhere gutsy would solve this issue, but it didn't....

not a big problem thanks to this thread ;)

Oops : not true: On one of my boxes azureus started crashing when i try to open a torrent file in gutsy. This never happened in Feisty....
 Could be this bug: [https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/80666](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/80666)
I am still using Azureus 2.5.0.4. because some trackers don't like vuze.

It's weird because this problem doesn't occur on another box i'm running. Anyway i solved it with installing azureus the way this howto suggests: [http://ubuntuforums.org/showthread.php?t=529431&highlight=azureus+howto](http://ubuntuforums.org/showthread.php?t=529431&highlight=azureus+howto)

---

### Post by melenor on 2007-10-14
I tried doing this but it didn't work there was no effect it was still 2.5.0.4
this was the output of the last command
overlord@Qwerty:~/Desktop$ azureus
[GUI] SWT update aborted due to previously reported issues regarding its install location
[plug] [CoreUpdater] Failed to read primary mirror list
DEBUG::Sun Oct 14 13:51:13 EDT 2007::org.gudy.azureus2.update.CoreUpdateChecker::getPrimaryDownloaders::504:
  org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: Error on connect for 'http://prdownloads.sourceforge.net:80/azureus/Azureus3.0.2.2.jar.torrent?download': 403 Forbidden
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:486)
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:344)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

[plug] [Plugin Update] Failed to load plugin details
DEBUG::Sun Oct 14 13:51:19 EDT 2007::org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin::checkForUpdateSupport::659:
  java.lang.Exception: Update check cancelled
        at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin.checkForUpdateSupport(PluginUpdatePlugin.java:465)
        at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin$4.checkForUpdate(PluginUpdatePlugin.java:192)
        at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport(UpdateCheckInstanceImpl.java:155)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

[plug] [Plugin Update] Failed to load plugin details
DEBUG::Sun Oct 14 13:51:19 EDT 2007::org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin::checkForUpdateSupport::659:
  java.lang.Exception: Update check cancelled
        at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin.checkForUpdateSupport(PluginUpdatePlugin.java:465)
        at org.gudy.azureus2.pluginsimpl.update.PluginUpdatePlugin$5.checkForUpdate(PluginUpdatePlugin.java:286)
        at org.gudy.azureus2.pluginsimpl.local.update.UpdateCheckInstanceImpl$1.runSupport(UpdateCheckInstanceImpl.java:155)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)

---

### Post by sebadigri on 2007-10-23
If i start azureus in terminal with "azureus" i cant update "Permission Denied"...
If i start azureus in terminal with "sudo azureus" i start the same azureus but with other config and with the vuze skin...but i cant update because i dont have anything when i click "Check Updates"........

What happens in my pc?

---

### Post by Perfect Storm on 2007-10-23
You need to change the permission of Azureus when updating it. (It's decribed in the guide).

---

### Post by beizhudi on 2007-10-28
Thanks for the guide!

Unfortunately I have a noobie question...
When I type 'azureus' into the terminal I get:
Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
Passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]

And then nothing happens. I don't have any azureus process running. Also, if I try to go through Applications->Internet->Azureus nothing happens.

Thanks....

---

### Post by ReyCazador on 2007-10-28
thanx a million most useful

---

### Post by beizhudi on 2007-10-30
It's working now! Thanks :)

---

### Post by stuffer007 on 2007-11-03
> **Artificial Intelligence said:**
> **Works for Ubuntu Breezy, Dapper, Edgy and Feisty**

I'm doing this howto on the requests from users: [http://ubuntuforums.org/showthread.php?t=135968](http://ubuntuforums.org/showthread.php?t=135968)
Though there's diffrent Howto install azureus on the howto forum, but not the way I install it.

Before you start you might uninstall your previous version of Azureus.

--------------------------------------------------


**1.** Make sure you have sun Java 1.5 or 1.6 installed and working. To see if what your Java version is set by default type: **java -version** in the terminal.

**2.** Download Azureus 3.0 (Vuze)  linux version: [Here]("http://azureus.sourceforge.net/"). Save it to your Desktop.

**3.** Open up for the terminal:
```
cd Desktop
sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
sudo chown -R <username>:<username> /opt/azureus/

```

**4.** Now we need a launcher from the Application tab, fire up the terminal again:
```

sudo nano /usr/share/applications/Azureus.desktop

```

add:


**5.** This is optional. If you want azureus to launch from a command in the terminal:

```
sudo nano /usr/bin/azureus
```

add:



save it and close it.
Now the last thing in the terminal:
```
sudo chmod +x /usr/bin/azureus
azureus
```

Now get the any updates and plugins you need. After that exit Azureus (so there aren't any azureus tray icon). Then;

```
sudo chown -R root:root /opt/azureus/
```




------------------------------------------------
Other HOWTOs by Artificial Intelligence
[HOWTO: Install F-Prot with GTK frontend (anti-virus)]("http://ubuntuforums.org/showthread.php?t=88357") - Dapper and Breezy.
[HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064") - Breezy only.
[HOWTO: Setup Desktop/Eyecandy. Tips'n'Tricks.]("http://ubuntuforums.org/showthread.php?t=77694") - Dapper and Breezy.
[HOWTO: Use 'Create Document' option. Open Office and custom files.]("http://ubuntuforums.org/showthread.php?t=76419") - All Ubuntu releases.
[HOWTO: Automatically play CDs and DVD when inserted.]("http://ubuntuforums.org/showthread.php?t=77146") - Dapper and Breezy.

Thanks worked like a charm

---

### Post by zeeduv on 2007-11-09
A.i  <3

---

### Post by noorez on 2007-11-11
I'm still having trouble getting Vuze to work. I think I've made mistakes with the installation steps. How can I clean out EVERYTHING so that I can start again?

---

### Post by Perfect Storm on 2007-11-11
> **noorez said:**
> I'm still having trouble getting Vuze to work. I think I've made mistakes with the installation steps. How can I clean out EVERYTHING so that I can start again?

```
cd /opt
sudo rm -rf azureus
```

---

### Post by noorez on 2007-11-11
Ok, I reinstalled it, however, the gui seems to be messed up. It seems as if it doesn't update itself...ie. when another window is put on top of vuze or when its minimized...

I am sure that I have the correct java installed...

I used the .bin file from jav.sun.com and extracted to /usr/lib and made the alternate links to /usr/bin.

What else could this be?

And what is the purpose of the "$*" parameter? If I use it, azureus gives me the error

Open Error 
" could not be opened:
Not a File

---

### Post by keyboardslave on 2007-12-20
thanks mate much appreciated worked perfectly!! ts even a way better version then in the repositories,:guitar:

---

### Post by zolero on 2007-12-30
Hi buddies! :)

Want to say that i've got problems too with Azu/Vuze and Java installed from repo. Finded that gij-java and icedtea-java messing up with paths and symlinks on Guszty. And it have a bunch of unutil dependencies... Dehhh...

Thus i've proceeded to building the packages from scratch using the tarballs downloaded from respective websites. Made that for Azureus and for Java, and the result: everything runs like a charm on my laptop (Asus A3H). No problems, no errors, no headaches ... nothing.

In my work i saw that is important to have Java in  _**/usr/java**_  and Azureus' default installdir (where Azureus2.jar resides) isn't  _**/usr/share/java**_  but  _**/usr/lib/azureus**_   Just because i've built my packages accordingly and modifying Azureus startup wrapper script.

If anyone will to save himself from these headaches, i upped my packages to RapidShare. Grab them from there, _**remove any Azureus and Java files**_ from computer, and install with my packages. It'll just be OK. As a bonus, my JRE package installs/removes automatically the browser plugin for Firefox (assuming that it is in the default _**/usr/lib/firefox**_ location) Here are the links:

           [COLOR=RED][[COLOR=RED]jre_1.6.0-03_zolerubuntu1_i386.deb[/COLOR]]("http://rapidshare.com/files/80097073/jre_1.6.0-03_zolerubuntu1_i386.deb")    ~ 18,5 Megs
           [[COLOR=RED]jdk_1.6.0-10_zolerubuntu1_i386.deb[/COLOR]]("http://rapidshare.com/files/80095571/jdk_1.6.0-10_zolerubuntu1_i386.deb")    ~ 57 Megs
           [[COLOR=RED]azureus_2.5.0.4_zolerubuntu1_i386.deb[/COLOR]]("http://rapidshare.com/files/80091670/azureus_2.5.0.4_zolerubuntu1_i386.deb")    ~ 9,5 Megs
           [[COLOR=RED]azureus-vuze_3.0.4.2_zolerubuntu1_i386.deb[/COLOR]]("http://rapidshare.com/files/80147522/azureus-vuze_3.0.4.2_zolerubuntu1_i386.deb")    ~ 11 Megs
[/COLOR]
For cleaning up perfectly your system use _**dpkg --purge <package.name_version_arch>**_; or just <package-name> An alternative is to select _**"Mark for complete removal"**_ in Synaptic.

_**Use GDebi to install**_ packages _**and read**_ the description (especially for Vuze) before installing. Packages were tested on my laptop, but i can't guarantee that they work well on yours. You'll decide...

That's all folks. Cheers.    :lolflag:

---

### Post by Sidewinder1 on 2008-01-25
Above command structure does not appear to work in 7.10 Gutsy; no "opt" directory/folder. Do I need to create one in Root, Home, Desktop?

---

### Post by Perfect Storm on 2008-01-26
It should be there;
or else
```
sudo mkdir /opt
```

---

### Post by Sidewinder1 on 2008-01-26
Yes, AI, opt is there, in root under /usr and under /var but there is no /opt  . Should I create it in root? I don't understand this: I do not log in as root; I've only been using linux since 11/07, if /opt is supposed to be in root, what happened to it? I certainly did not remove it. What's causing the confusion on my part is the following error messages.
de@de-desktop:~$ sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
[sudo] password for de:
tar: Azureus_3_0_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
de@de-desktop:~$ cd Desktop
de@de-desktop:~/Desktop$ sudo tar jxvf Azureus_3_0_linux.tar.bz2 -C /opt/
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
de@de-desktop:~/Desktop$ 
I tried to install the previous version of Azureus, through Synaptic and it didn't work properly so I had to "complete" remove it. That's why I'm trying your method. Any assistance is more that greatly appreciated.

---

### Post by Perfect Storm on 2008-01-26
Check if the file you downloaded is the same as the one you put in the terminal eg. it could been updated.

---

### Post by Sidewinder1 on 2008-01-26
Yes, it is the same in the terminal as on the desktop
Azureus_3_0_linux.tar.bz2
As stated earlier the only anomaly that I can see is that there is no opt directory in /. Only in /etc and /var

---

### Post by Perfect Storm on 2008-01-26
Did you try making the /opt as I posted earlier?

---

### Post by Sidewinder1 on 2008-01-26
Not yet. I wanted to make absolutely certain that I would be putting opt in the correct place. It should go in root (/), correct? Also, are there any other places in root where opt should be other than /etc and /var? If so where?

---

### Post by Sidewinder1 on 2008-01-26
AI, I just wanted to thank you for taking your most valuable time to assist me in, what is to me, a most arduous task. Just so that you know, I'm currently trying to give back to the community by helping two 'novices', in "Absolute Beginner" forum who know even less than I do. You didn't think that was possible did you? ;-)

---

### Post by Perfect Storm on 2008-01-26
It goes to root so the path is simple /opt

---

### Post by Sidewinder1 on 2008-01-26
Made the opt directory in root and all seemed to go well until adding the Azureus application to the Applications drop-down menu. It's not there and when I run Azureus from the terminal I get the following errors:de@de-desktop:~$ azureus
Starting Azureus...
Suitable java version found [java = 1.7.0]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)], InvocationTargetException
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/mozilla for GRE
        Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner for GRE
        Can not use GRE from /usr/lib/xulrunner because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Browser check failed with: XPCOM error -2147467259, InvocationTargetException
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" -Dazureus.script="/opt/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
[alert] Alert:3:Failed to access torrent file ''. Ensure sufficient temporary file space available (check browser cache usage).
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Locale Initializing took 710ms
   Core: 157ms for Loading Plugin : azemp
   Core: 105ms for Loading Plugin : azupnpav
   Core: 25ms for Loading Plugin : azrating
   Core: 75ms for Loading Plugin : azplugins
   Core: 402ms for Loading Plugin : Built In
   Core: 301ms for Initializing Global Torrent Manager
   Core: 26ms for Initializing Plugin: Embedded Media Player
   Core: 150ms for Initializing Plugin: UPnP Media Server
   Core: 102ms for Initializing Plugin: Tracker Static Pages
   Core: 25ms for Initializing Plugin: PluginUpdate
   Core: 243ms for Initializing Plugin: DHT
   Core: 26ms for Initializing Plugin: Magnet URI Handler
   Core: 25ms for Initializing Plugin: azextseed
Core Initializing took 1994ms
GUI Initializing took 127ms
DEBUG::Sat Jan 26 14:25:59 GMT 2008  ExternalStimulus debug
   Core: 1059ms for Initializing Plugin: azlocaltracker
   Core: 13ms for Loading Plugin : azemp
   Core: 13ms for Loading Plugin : azplugins
skin init took 6016ms
createWindow init took 384ms
skin layout took 931ms
skin widgets init took 686ms
shell.open took 494ms
processStartupDMS took 0ms

(gecko:5697): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
xEmbed supported in this Mozilla version
Gtk2+ supported in this Mozilla version
NewStream: The full URL is [http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf](http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf)
Closed 74files.
Starting process: /usr/bin/gtk-gnash -v -x 52432987 -j 802 -k 88 -u [http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf](http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf) -U [http://www.vuze.com/browse.start?azid=QYHEI4AKDY6PA4Z73HWHILSTK5PZJDXK&azv=3.0.4.2](http://www.vuze.com/browse.start?azid=QYHEI4AKDY6PA4Z73HWHILSTK5PZJDXK&azv=3.0.4.2) -P allowscriptaccess=always -P bgcolor=#1b1b1b -P flashvars=imgPath=&flvPath=&adType=&viewstyle=&contentType=&detPage=&logUrl=http://www.vuze.com/app;jsessionid=3E9473043E3429BCF24E90B09E8A725B.web05?service=rpc%26cmd=webad;50;impression;log;&userId=11640324&webAdImpressionId=&impressionId=web0533751570838.16499700 -P height=88 -P id=flash_featured -P name=flash_featured -P quality=high -P scale=noborder -P src=http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf -P style= -P type=application/x-shockwave-flash -P width=802 -P wmode=transparent - 
Forked sucessfully, child process PID is 5776
ERROR: can't open debug log file gnash-dbg.log for writing.
Verbose output turned on
5776] 09:26:13: Setting width to 802
5776] 09:26:13: Setting height to 88
5776] 09:26:13: Setting root URL to [http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf](http://cache1.vuze.com/cdnassets/2/1fa2607116674578875eeb498dbe7c79/flash/Fin_banner_012208_US.swf)
5776] 09:26:13: Setting base URL to [http://www.vuze.com/browse.start?azid=QYHEI4AKDY6PA4Z73HWHILSTK5PZJDXK&azv=3.0.4.2](http://www.vuze.com/browse.start?azid=QYHEI4AKDY6PA4Z73HWHILSTK5PZJDXK&azv=3.0.4.2)
5776] 09:26:13: No rendering flags specified, using rcfile
5776] 09:26:13: Your X server expects RGB24 pixmap data for standard mode.
5776] 09:26:13: Created XEmbedded window
5776] 09:26:13: framebuffer pixel format is RGB24
5776] 09:26:13: Base url set to: [http://www.vuze.com/browse.start?azid=QYHEI4AKDY6PA4Z73HWHILSTK5PZJDXK&azv=3.0.4.2](http://www.vuze.com/browse.start?azid=QYHEI4AKDY6PA4Z73HWHILSTK5PZJDXK&azv=3.0.4.2)
5776] 09:26:13: ERROR: Unimplemented: SWF8 is not fully supported, trying anyway but don't expect it to work
5776] 09:26:13: GTK-AGG: 240000 bytes offscreen buffer allocated

5776] 09:26:13: initialized AGG buffer <0xb6b65008>, 240000 bytes, 802x88, rowsize is 2406 bytes
5776] 09:26:13: ERROR: Unimplemented: FileAttributes tag in the SWF requests that network access is not granted to this movie (or application?). Anyway Gnash won't care; use white/black listing in your .gnashrc instead
5776] 09:26:13: ERROR: FIXME: DefineFontAlignZoneTag unfinished
5776] 09:26:13: ERROR: *** no tag loader for type 88 (movie)
5776] 09:26:13: ERROR: Unimplemented:   FIXME: tagtype = 74
5776] 09:26:14: ERROR: Unimplemented:   FIXME: tagtype = 83
5776] 09:26:14: ERROR: FIXME: DefineFontAlignZoneTag unfinished
5776] 09:26:14: ERROR: *** no tag loader for type 88 (movie)
5776] 09:26:14: DEBUG: HTML in a text field is unsupported, gnash will just forget the tags and print their content
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 8657, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 3371, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 8508, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 8508, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 3371, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 8508, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 3371, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 7527, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 3371, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 8662, margin 0 - nothing to align
5776] 09:26:14: DEBUG: TextField text doesn't fit in its boundaries: width 8662, margin 0 - nothing to align
org.gudy.azureus2.plugins.platform.PlatformManagerException: Unsupported capability called on platform manager
        at org.gudy.azureus2.platform.unix.PlatformManagerImpl.showFile(PlatformManagerImpl.java:239)
        at org.gudy.azureus2.ui.swt.debug.UIDebugGenerator.generate(UIDebugGenerator.java:227)
        at com.aelitis.azureus.ui.swt.shells.main.MainMenu$5.handleEvent(MainMenu.java:149)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
        at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3319)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2971)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:156)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:102)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:203)
Child process exited with status 15
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
de@de-desktop:~$ 

If this is becoming too much of a pain in the neck for you, I'll understand and just assume that it wasn't meant to be. I always think ahead and have already written down your 'remove all' command. Hopefully I won't screw that up; and thank you again for all of your most valued assistance.

---

### Post by Perfect Storm on 2008-01-26
Well, I don't use Azureus anymore. Been a long time I did, as Azureus is buggy and resource hog.
You may try Deluge instead, they have uptodate ubuntu packages which are easy to install/uninstall and it doesn't require Java.
[http://deluge-torrent.org/](http://deluge-torrent.org/)


All the errors seems to be theme related, it could be the theme you are using.

---

### Post by Sidewinder1 on 2008-01-26
Thank you again. I think I will try Deluge

---

### Post by SanskritFritz on 2008-01-26
Well, I switched from Deluge to Azureus. The reason: Deluge could not handle more than 15 seeds simultaneously. It started crashing, so I had to look for an alternative. And here I am, using Azureus, very satisfied with it.

---

### Post by Sergiu on 2008-01-29
How to lunch the azureus vuze in the advanced mode?:)

---

### Post by SanskritFritz on 2008-01-30
> **Sergiu said:**
> How to lunch the azureus vuze in the advanced mode?:)
Click the "Advanced" tab on the right side :confused:

---

### Post by macabro22 on 2008-03-12
Someone please help me find out what is going wrong with my installation:

I am running ubuntu gutsy 64bits, and I have sun java 1.6 installed but it seems VUZE is trying to use JRE version 1.4:

```
htorres@GLaDOS:~/Desktop$ azureus
Starting Azureus...
Suitable java version found [java = 1.4.2-02]
Configuring environment...
Java exec found in PATH. Verifying...
find: /home/htorres/.azureus/plugins: No such file or directory
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/xulrunner for GRE
        Can not use GRE from /usr/lib/xulrunner because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Browser check failed with: NoClassDefFoundError
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" -Dazureus.script="/opt/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
[alert] Alert:3:Failed to access torrent file ''. Ensure sufficient temporary file space available (check browser cache usage).
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Wed Mar 12 19:56:42 GMT-03:00 2008::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::68:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to 'null'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::103,Main::<init>::84,Main::main::216
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:177)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:89)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:103)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
htorres@GLaDOS:~/Desktop$ 

```

---

### Post by Perfect Storm on 2008-03-13
You need to install 32-bit version of sun java1.6

---

### Post by macabro22 on 2008-03-13
> **Artificial Intelligence said:**
> You need to install 32-bit version of sun java1.6

I suppose I have it installed since I use it with my 32 bit firefox, but I might be wrong.

Could you please confirm I would have it installed if I followed this HOWTO [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Thanks a lot.

---

### Post by Perfect Storm on 2008-03-13
Use the command:
```
sudo update-alternatives --config java
``` 

to set which java to be the default.

---

### Post by macabro22 on 2008-03-13
Thanks A. I..

I will try that once I get home from work.

---

### Post by ejw2076 on 2008-03-30
> **macabro22 said:**
> Someone please help me find out what is going wrong with my installation:

I am running ubuntu gutsy 64bits, and I have sun java 1.6 installed but it seems VUZE is trying to use JRE version 1.4:

```
htorres@GLaDOS:~/Desktop$ azureus
Starting Azureus...
Suitable java version found [java = 1.4.2-02]
Configuring environment...
Java exec found in PATH. Verifying...
find: /home/htorres/.azureus/plugins: No such file or directory
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/xulrunner for GRE
        Can not use GRE from /usr/lib/xulrunner because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
GRE found at /usr/lib/firefox.
Browser check failed with: NoClassDefFoundError
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope  Azureus has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" -Dazureus.script="/opt/azureus/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
[alert] Alert:3:Failed to access torrent file ''. Ensure sufficient temporary file space available (check browser cache usage).
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Wed Mar 12 19:56:42 GMT-03:00 2008::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::68:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to 'null'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::103,Main::<init>::84,Main::main::216
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:177)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:89)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:68)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:103)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
htorres@GLaDOS:~/Desktop$ 

```



I tried compiling the swt.jar through eclipse myself, but I couldn't figure it out.  After fishing around a bit, I realized that they have a 64-bit swt.jar packaged with the amd64 release of azureus. 

-Go to the azureus homepage and click on downloads
-selece amd64
-unzip it and copy the swt.jar over your installed one.

boots right up.

---

### Post by JacenMandarin on 2008-04-29
I'm having trouble getting rid of azureus. I just want to do a completely fresh install. I've used the terminal and synaptic to remove it but it's still in my system yet the terminal and synaptic both say it's not there. When I try to manually delete the files it wont let me. What do I need to do?

---

### Post by Perfect Storm on 2008-04-30
What do you mean in the system? You have to be more specific.

---

### Post by JacenMandarin on 2008-04-30
I mean that it's still installed. I was able to figure it out thanks to some help in the chat though.

---

### Post by SanskritFritz on 2008-04-30
> **JacenMandarin said:**
> I mean that it's still installed. I was able to figure it out thanks to some help in the chat though.Please care to share your experiences with the community here. ;-)

---

### Post by Perfect Storm on 2008-04-30
```
cd /opt
sudo rm -rf azureus
cd /usr/share/applications
sudo rm -rf Azureus.desktop
cd /usr/bin
sudo rm -rf azureus

```

---

### Post by laeg_ on 2008-05-03
Thanks for the guide, I found it useful but I've had a few problems:

> **benk said:**
> When I try and download a torrent file from Firefox, it asks me if I want to save it to disk or open directly using the default bittorrent client. When I choose to open it using azureus (via /usr/bin/azureus), it doesn't seem to open the torrent at all...it does open azureus, but not the torrent. How can I fix this?

I can get torrents to download by saving the file to disk and then opening that file in azureus by File->open->torrent file.

> **Artificial Intelligence said:**
> I'll will look into this. But if you use 'save as' it should open the torrent automatically with azureus if you use the downloader which comes with epiphany, I'm sure you can set firefox to do too.

On my first install I followed the outlined directions verbatim but still I have the same problem. I cannot set Azureus as my default application for opening torretns. I have tried to do so in Firefox and the 'open with' tab of the properties window of torrent files pointing gnome to /bin/azureus/azureus (*and previously /opt/azureus/azureus) and also /usr/bin/azurues.

*see below.

It is of course possible to automatically download the torrents somewhere that you have preset Azureus to scan, when running, but this of course isn't the same thing and won't make it the default application.

> **benk said:**
> 
And, if you want to install plugins without running azureus as root, you'd have to make /opt/azureus writable to all (although this could be a security risk).


> **Artificial Intelligence said:**
> All plugins and updates works if you install azureus as I described. I just double checked to be sure in my case.
You can sudo chown -R <username>:<username> /opt/azureus/ or to "all" if you want to change it (on your own risk).

*Again I did install azureus _exactly_ as you described but I had the same problem where Azureus gave me an error message everytime I used it telling me it couldn't update because of permissions. I moved the azureus dir to /bin/ instead and substituted my username for root in the chown command. 

If moving it and using chown with my username is the only way to remedy the update problem where is the best place to have the azureus dir?

---

### Post by Perfect Storm on 2008-05-04
Have it in your home directory, it doesn't matter where.

---

### Post by iSplicer on 2008-05-04
Thankyou!

---

### Post by laeg_ on 2008-05-17
> **Artificial Intelligence said:**
> Have it in your home directory, it doesn't matter where.

Did you somehow miss my entire post apart from the last line?

---

### Post by Perfect Storm on 2008-05-17
> **laeg_ said:**
> Did you somehow miss my entire post apart from the last line?

No, I answered to the question of which I knew.
1) I don't use firefox anymore
2) I havn't used Azureus since Feisty, as I have found a better alternative (Deluge). So I can't "officially" support this guide anymore, I should have closed it for good. But it seems it still helps people so I let it stay open until someone else makes a howto for it and can make support on it.

---

### Post by laeg_ on 2008-05-18
Deluge lacks a lot of the functionality of Azureus. It won't even rotate seeding files in the queue based on ratio or activity, oh and there's also a client side ratio bug and virtually no support.

---

### Post by Fireball454 on 2008-05-28
I just installed the latest Azureus on Hardy (8.04)
I followed your instructions and it works perfect!!

Thx a lot this guide was really helpfull!

---

### Post by chootarlaal on 2008-08-27
[PHP]Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
find: /home/user/.azureus/plugins: No such file or directory
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/firefox-addons for GRE
        Can not use GRE from /usr/lib/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox-3.0.1 for GRE
        Can not use GRE from /usr/lib/firefox-3.0.1 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-addons for GRE
        Can not use GRE from /usr/lib/xulrunner-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/xulrunner-1.9.0.1 for GRE
        Can not use GRE from /usr/lib/xulrunner-1.9.0.1 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/firefox for GRE
        Can not use GRE from /usr/lib/firefox because it's missing components/libwidget_gtk2.so.
  checking /usr/lib/mozilla for GRE
        Can not use GRE from /usr/lib/mozilla because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/firefox-addons for GRE
        Can not use GRE from /usr/lib64/firefox-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/firefox-3.0.1 for GRE
        Can not use GRE from /usr/lib64/firefox-3.0.1 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/xulrunner-addons for GRE
        Can not use GRE from /usr/lib64/xulrunner-addons because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/xulrunner-1.9.0.1 for GRE
        Can not use GRE from /usr/lib64/xulrunner-1.9.0.1 because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/firefox for GRE
        Can not use GRE from /usr/lib64/firefox because it's missing components/libwidget_gtk2.so.
  checking /usr/lib64/mozilla for GRE
        Can not use GRE from /usr/lib64/mozilla because it's missing components/libwidget_gtk2.so.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuzehas better luck.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/user/Applications/vuze" -Dazureus.install.path="/home/user/Applications/vuze" -Dazureus.script="/home/user/Applications/vuze/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main
file:/home/user/Applications/vuze/Azureus2.jar ; file:/home/amir/Applications/vuze/swt.jar ; file:/home/user/Applications/vuze/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Wed Aug 27 22:07:00 EDT 2008::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::67:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (amd64).  You can get a new swt.jar (Min Version: 3.4) from http://eclipse.org/swt

(2) No write access to 'null'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::110,Main::<init>::84,Main::main::216,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::57,DelegatingMethodAccessorImpl::invoke::43,Method::invoke::616,MainExecutor$1::run::37,Thread::run::636
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:177)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:88)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:67)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
        at java.lang.Thread.run(Thread.java:636)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.[/PHP]

whats wrong here?  im running x86_64 on Hardy (8.04) and tried to do it this way.
[http://www.myscienceisbetter.info/2008/08/install-vuze-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/2008/08/install-vuze-on-ubuntu-64bit.html)

---

### Post by h2c4life on 2008-08-28
How do i uninstall this??
can anyone help me please? thanks

---

### Post by Tosa on 2008-08-29
@ chootarlaal

I've just installed Vuze on Kubuntu 64 using the guide
[http://www.myscienceisbetter.info/2008/08/install-vuze-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/2008/08/install-vuze-on-ubuntu-64bit.html)
and it works.

According to your console output you haven't replaced 32 bit SWT with 64 bit. Download 64 bit SWT according to the guide, extract SWT.jar to the folder you extracted Vuze to (there already is a 32 bit SWT.jar in that directory, overwrite it) and that's it.

In this how-to Azureus/Vuze is assumed to be extracted to /opt/azureus directory.

The current tarball extracts to /opt/vuze, so you need to change the paths in Azureus.Desktop accordingly.

HTH

---

### Post by Tosa on 2008-08-29
Oops, I almost forgot to thank Artificial Intelligence for this How-To... :oops:

---

### Post by chootarlaal on 2008-08-29
> **Tosa said:**
> @ chootarlaal

I've just installed Vuze on Kubuntu 64 using the guide
[http://www.myscienceisbetter.info/2008/08/install-vuze-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/2008/08/install-vuze-on-ubuntu-64bit.html)
and it works.

According to your console output you haven't replaced 32 bit SWT with 64 bit. Download 64 bit SWT according to the guide, extract SWT.jar to the folder you extracted Vuze to (there already is a 32 bit SWT.jar in that directory, overwrite it) and that's it.

In this how-to Azureus/Vuze is assumed to be extracted to /opt/azureus directory.

The current tarball extracts to /opt/vuze, so you need to change the paths in Azureus.Desktop accordingly.

HTH


i actually did install the 64 bit version, this is where i got it from and here is the name of the file.

swt-3.4-gtk-linux-x86_64.zip

[http://eclipse.ialto.org/eclipse/downloads/drops/R-3.4-200806172000/](http://eclipse.ialto.org/eclipse/downloads/drops/R-3.4-200806172000/)

im not sure why it references the 32bit version.  any ideas on whats going on?


edit: nevermind dude, i cant read.  i never moved the swt.jar over to the vuze directory.  its working now.  thanks a bunch!!

---

### Post by now-new on 2008-09-20
This thing is awesome, thanks for the help setting it up, as it was very annoying having to start it from the command line every time.

Thanks

---

### Post by VuzeLover on 2008-11-27
**[color=red]Updated howto.  I made a few changes for better security and for the name change.**[/color]




**1.** Download Vuze, formerly called Azureus [Here]("http://azureus.sourceforge.net/download.php").

**2.** Open up a terminal:
```
cd to where the download is.
sudo tar jxvf [color=red]REPLACE_WITH_THE_NAME_OF_THE_FILE[/color].tar.bz2 -C /opt/  [color=red]The -C is an upper case letter by the way[/color]
sudo chown -R [color=red]YOUR_USERNAME_GOES_HERE[/color]**:**[color=red]YOUR_USERNAME_GOES_HERE[/color] /opt/vuze/

```




**3.** Now we need a launcher from the Application tab, fire up the terminal again:
```

sudo nano /usr/share/applications/Vuze.desktop

```

add:> [Desktop Entry]
Name=Vuze
Comment=P2P Client
Exec=/opt/vuze/vuze
Icon=/opt/vuze/vuze.png
Terminal=false
Type=Application
Categories=Application;Network;




**4.** This is optional. If you want vuze to launch from a command in the terminal:

```
sudo nano /usr/bin/vuze
```

add:> #!/bin/sh

/opt/vuze/vuze "$*"


save it and close it.
Now the last thing in the terminal:
```
sudo chmod +x /usr/bin/vuze
```


Now get any updates and plugins you need. After that exit vuze (so there aren't any vuze tray icon). Then;

```
sudo adduser --home /opt/vuze --shell /bin/false --no-create-home --disabled-login vuze
```**[color=red]Making sure to simply hit the enter button without filling in any data![/color]**





```
sudo chown -R vuze:vuze /opt/vuze
``````
sudo chown vuze:vuze /usr/bin/vuze
```

---

### Post by coloradogiant on 2009-01-06
Thanks for the great guides! Everything works great with Vuze 4.0 in Ubuntu 8.04 using the guide above.

I do have a question for the experts though. Is there a way to allow vuze to exist as seperate instances for multiple users logged in at the same time?

Scenario: 3 users are logged into Ubuntu all using NoMachine VNC. Each has their own desktop. When user #1 launches Vuze, users #2 and #3 can't. Vuze can apparently only exist for one user per machine? I'd like each user to have their own instance of Azureus (their own torrents, etc)

Anyway to get this working?

---

### Post by OisinT on 2009-05-06
edit: fixed original problem by editing ```
#!/bin/sh

/opt/vuze/vuze "$*" 
```

but now i'm having a problem where it stalls at startup.

```
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:79: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:80: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:95: Murrine configuration option "style" is not supported and will be ignored.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:157: Murrine configuration option "style" is not supported and will be ignored.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:264: Murrine configuration option "style" is not supported and will be ignored.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:298: Murrine configuration option "style" is not supported and will be ignored.
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/usr/share/vuze" -Dazureus.install.path="/usr/share/vuze" -Dazureus.script="/usr/bin/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/usr/share/vuze/Azureus2.jar ; file:/usr/share/vuze/swt.jar ; file:/usr/share/vuze/
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:79: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:80: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:95: Murrine configuration option "style" is not supported and will be ignored.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:157: Murrine configuration option "style" is not supported and will be ignored.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:264: Murrine configuration option "style" is not supported and will be ignored.
/home/oisint/.themes/Dust Burnt/gtk-2.0/gtkrc:298: Murrine configuration option "style" is not supported and will be ignored.
Locale Initializing took 128ms
57401:    Core: 51ms for activity between 'Loading Plugin: azupdater' and 'Loading Plugin: safepeer_2.5.2'
57427:    Core: 26ms for activity between 'Loading Plugin: safepeer_2.5.2' and 'Loading Plugin: azemp'
57452:    Core: 25ms for activity between 'Loading Plugin: rssfeed_1.3.5' and 'Loading Plugin: scanerss'
[alert] Alert:3:Error loading plugin 'scanerss' / 'lbms.plugins.scanerss.azureus.ScanerssAzPlugin'
DEBUG::Wed May 06 16:34:57 GMT 2009::org.gudy.azureus2.pluginsimpl.local.PluginInitializer::loadPluginFromDir::1144:
  java.lang.NoClassDefFoundError: org/jdom/Element
	at java.lang.Class.getDeclaredMethods0(Native Method)
	at java.lang.Class.privateGetDeclaredMethods(Class.java:2444)
	at java.lang.Class.getMethod0(Class.java:2687)
	at java.lang.Class.getMethod(Class.java:1620)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:1117)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:746)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:540)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl$4.run(AzureusCoreImpl.java:557)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:255)
Caused by: java.lang.ClassNotFoundException: org.jdom.Element
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 9 more

Error loading plugin 'scanerss' / 'lbms.plugins.scanerss.azureus.ScanerssAzPlugin': java.lang.NoClassDefFoundError: org/jdom/Element
57502:    Core: 50ms for activity between 'Loading Plugin: scanerss' and 'Loading Plugin: azupnpav'
57527:    Core: 25ms for activity between 'Loading Plugin: azupnpav' and 'Loading Torrents'
57577:    Core: 25ms for activity between 'Loading Plugin: azplugins' and 'Loading Torrent  1 of 3 : Crank.High.Voltage.READNFO.R5.XviD-DEViSE.torrent'
57652:    Core: 75ms for activity between 'Loading Plugin: azrating' and 'Loading Plugin: azupdater'
57728:    Core: 76ms for activity between 'Loading Plugin: Start/Stop Rules' and 'Loading Plugin: Torrent Removal Rules'
57753:    Core: 25ms for activity between 'Loading Plugin: Share Hoster' and 'Loading Plugin: Plugin Update Checker'
57778:    Core: 25ms for activity between 'Loading Plugin: Plugin Update Checker' and 'Loading Plugin: UPnP'
57828:    Core: 50ms for activity between 'Loading Plugin: DHT' and 'Loading Plugin: DHT Tracker'
57853:    Core: 25ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
57932:    Core: 79ms for activity between 'Loading Plugin: Magnet URI Handler' and 'Loading Plugin: Core Update Checker'
57957:    Core: 25ms for activity between 'Loading Plugin: External Seed' and 'Loading Plugin: Local Tracker'
58033:    Core: 76ms for activity between 'Loading Plugin: Buddy' and 'Initialising Global Torrent Manager'

(SWT:19517): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(SWT:19517): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(SWT:19517): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(SWT:19517): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWidget'

(SWT:19517): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
58323:    Core: 290ms for activity between 'Initialising Global Torrent Manager' and 'Initialising Plugin: Azureus Update Support'
should load blocklist from: http://www.bluetack.co.uk/config/spconfig.txt
58603:    Core: 280ms for activity between 'Initialising Plugin: RSSFeed Scanner' and 'Initialising Plugin: ScaneRSS'
58803:    Core: 200ms for activity between 'Initialising Plugin: UPnP Media Server' and 'Initialising Plugin: Tracker Static Pages'
Retrieving data from: http://www.bluetack.co.uk/config/ads-trackers-and-bad-pr0n.zip
58963:    Core: 160ms for activity between 'Initialising Plugin: Tracker Static Pages' and 'Initialising Plugin: Rating'
59018:    Core: 55ms for activity between 'Initialising Plugin: Download Remove Rules' and 'Initialising Plugin: Share Hoster'
59043:    Core: 25ms for activity between 'Initialising Plugin: Distributed DB' and 'Initialising Plugin: Distributed Tracker'
59068:    Core: 25ms for activity between 'Initialising Plugin: CoreUpdater' and 'Initialising Plugin: CorePatcher'
59095:    Core: 27ms for activity between 'Initialising Plugin: LAN Peer Finder' and 'Initialising Plugin: Network Status'
Retrieving data from: http://www.bluetack.co.uk/config/level1.zip
^CExit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.

```

---

### Post by Hardhat_Harry on 2009-06-16
Hi I've got Vuze install issues too.

I'm a bit new to this Linux lark but enjoying it much better than Windows.

I've followed the defaults to install Jrel1.6.0_14 and it installed it into my desktop.

When I run vuse install I get: - 

hhh@nexus1:~/vuze$ ./azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest: No such file or directory
ls: cannot access /usr/java: No such file or directory
ls: cannot access /usr/lib/jvm/latest: No such file or directory
ls: cannot access /usr/lib/jvm: No such file or directory
Re-checking with GCJ (Sun Java recommended)..
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm: No such file or directory
OOPS, unable to locate java exec in  /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
hhh@nexus1:~/vuze$ 

I have also tried ./azureus JAVA_PROGRAM_DIR=Desktop/jre1.6.0_14 but get a similar error message.

How do I tell the Vuse installed where my JRE is?

Thanks for any help!!

---

### Post by Hardhat_Harry on 2009-06-18
DEB package for Vuze can be found here: - 

[http://linux.softpedia.com/progDownload/Vuze-Download-27980.html](http://linux.softpedia.com/progDownload/Vuze-Download-27980.html)

---

### Post by iFuzo on 2009-07-17
Cant you just use "sudo apt-get install azureus" ??

---

