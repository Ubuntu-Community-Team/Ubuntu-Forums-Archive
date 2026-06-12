---
title: "Azureus"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Nikunj93 on 2008-05-09
i am installing azureus
and i have jre
when i open terminal and type
./azureus
in the setup directory to install this haoppenes
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/niks/Desktop/azureus/Azureus2.jar" -Djava.library.path="/home/niks/Desktop/azureus" -Dazureus.install.path="/home/niks/Desktop/azureus" org.gudy.azureus2.ui.swt.Main ''
DEBUG::Sat May 10 08:49:25 GMT+05:30 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::146,ConfigurationManager::initialise::150,ConfigurationManager::getInstance::83,LoggerImpl::init::90,Logger::<clinit>::48,StartServer::<init>::72,Main::<init>::56,Main::main::180
changeLocale: *Default Language* != en (IN). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (IN)' (en_IN), using 'English (default)'
DEBUG::Sat May 10 08:49:26 GMT+05:30 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::36,AzureusCoreImpl::<init>::160,AzureusCoreImpl::create::93,AzureusCoreFactory::create::46,Main::<init>::76,Main::main::180
[alert] Alert:3:Installation of at least one component failed - see 'update.log' for details
Exception in thread "main" java.lang.NoClassDefFoundError: org.eclipse.swt.SWT not found in java.lang.ClassLoader$1{urls=[file:/home/niks/Desktop/azureus/Azureus2.jar], parent=null}
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:62)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:106)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:80)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:180)
Azureus TERMINATED.


PLZ HELP

---

### Post by Nikunj93 on 2008-05-09
fasty fasty!

---

### Post by Xiong Chiamiov on 2008-05-09
Install it instead through apt, like this:
```

sudo apt-get install azureus

```
[Here's]("http://http://monkeyblog.org/ubuntu/installing/") a very good guide on how to install things in Ubuntu.

That said, you should also give [this]("http://linux.oneandoneis2.org/LNW.htm") article a read, particularly section 3a.

---

### Post by Nikunj93 on 2008-05-09
that sudo apt-get
is very slow
takes hell time
anyotha way?

---

### Post by Xiong Chiamiov on 2008-05-09
It's going to be a lot faster than anything else, since you're downloading precompiled binaries from the Canonical servers.  My guess is that there are many other packages that you need to make it work, and they are being downloaded as well.

Did you read the links I gave you?

---

### Post by Nikunj93 on 2008-05-10
well thanks:)

---

