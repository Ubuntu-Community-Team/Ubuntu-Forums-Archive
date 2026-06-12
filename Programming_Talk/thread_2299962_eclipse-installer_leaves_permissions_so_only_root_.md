---
title: "eclipse-installer leaves permissions so only root can run"
date: 2015-10-22
forum: Programming Talk
---

### Post by frank110 on 2015-10-22
I've switched from Windows to Ubuntu.   And having several issues with getting eclipse running to same level as Kepler version.   

I am using [eclipse.org/downloads/index.php?show_instructions=TRUE]("https://www.eclipse.org/downloads/index.php?show_instructions=TRUE") instructions for Linux. 
(Full disclosure: I tried to install eclipse directly and had troubles with interpreters... see original eclipse issue. )
Refer to[ [SOLVED] Problem with Eclipse, denied permission]("http://ubuntuforums.org/showthread.php?t=908896") 

After using sudo eclipse-inst the regular user can not start eclipse.  It seems that eclipse refers to /root/.p2 and /root/.eclipse. 
Can someone provide a tip on what too do?  Remove /.eclipse?   Reinstall with different sequence?   What should I clean up before reinstall?? 
Can I remove /root/.p2?

INSTALLING MARS ECLIPSE
1. download eclipse-installer and extract into /opt --> /opt/eclips-installer
2. sudo /opt/eclipse-installer/eclipse-inst 
            --> it installs and I  am able to Launch OK...  exit eclipse (running under sudo)
3. cd 
4. /opt/eclipse/jee-mars/eclipse/eclipse

This fails with message in  pop-up [The Eclipse executable launcher was unable to locate its  companion shared library] and on cmd line it gives
[TABLE="width: 500"]
[TR]
[TD]../../../../root/.p2/pool/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_* &#8203;1.1.300.v20150602-1417: cannot open shared object file: Permission  denied 

 ** (eclipse:2889): WARNING **: Couldn't register with  accessibility bus: Did not receive a reply. Possible causes include: the  remote application did not send a reply, the message bus security  policy blocked the reply, the reply timeout expired, or the network  connection was broken.[/TD]
[/TR]
[/TABLE]



Original Eclipse -prior to re-installing eclipse... pydev interperter is not loading correct pandas. 
   - see [http://stackoverflow.com/questions/33273793/elipse-imports-wrong-verison-of-pandas-in-pydev-enviornment](http://stackoverflow.com/questions/33273793/elipse-imports-wrong-verison-of-pandas-in-pydev-enviornment).
   - so to uninstalled eclipse... 
        sudo apt-get remove eclipse eclipse-platform
        sudo rm -rf /opt/eclipse
        rm -rf $HOME/.ecplise
-----------------------------

---

### Post by mystics on 2015-10-22
Maybe I'm missing something, but is there any reason you're not just installing it from repositories? You can get it at the Ubuntu Software Center or Synaptic Package Manager. It would also be possible to run

```
sudo apt-get install eclipse
```

All of those would be preferable to downloading the installer. Those should also handle getting the libraries necessary to run it.

Edit: You may need to run the following command before doing the above

```
sudo apt-get update
```

---

### Post by frank110 on 2015-10-23
The problem is running eclipse-inst as root (sudo).   When you run eclipse-inst, it will set the target dir from $HOME. 
I create a dir in /opt/eclipse but made it owned by my userid.

---

### Post by frank110 on 2015-10-23
@mystics - The documentation is mixed about getting Eclipse from Linux repositories (don't get the latest).   Basically I wanted the latest Mars version.   And this is why I went down the eclipse-installer. 
Sorry, I ran out of time in my trials on using apt-get.

---

### Post by Paul_Braman on 2015-11-13
I'm having the same problem. The reason not to install "eclipse" as provided is because it's a really old version.

I'm trying to use the new installer but it doesn't make things easier when it comes to trying to run as any normal user account when I install it "system-wide".

```
[user@hostname:~] /opt/eclipse/eclipse
../../root/.p2/pool/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.300.v20150602-1417: cannot open shared object file: Permission denied
```

---

