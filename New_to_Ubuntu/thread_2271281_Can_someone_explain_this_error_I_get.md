---
title: "Can someone explain this error I get?"
date: 2015-03-28
forum: New to Ubuntu
---

### Post by frankentower on 2015-03-28
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-johnb" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-johnb" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-johnb" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-johnb" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.

After all these errors I am still able to write to files, but it does look like there is a problem somewhere

Thanks for any info

---

### Post by Vladlenin5000 on 2015-03-28
[http://ubuntuforums.org/showthread.php?t=1080625](http://ubuntuforums.org/showthread.php?t=1080625)

Sounds familiar?

---

### Post by frankentower on 2015-03-28
So am I right to assume I should run 'kdesu' instead of the regular 'sudo' commands, on aps such as kate or leafpad, etc.?

---

### Post by frankentower on 2015-03-28
Just tired that and it says kdesu....command not found...

---

### Post by deadflowr on 2015-03-28
Try kdesudo

---

### Post by frankentower on 2015-03-28
I got rid of most all the errors by chown root.root /var  & /tmp

But I get this one that crashes plasma:

QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon

---

### Post by frankentower on 2015-03-28
kdesudo gave me this would not open heres the error:

 > kdesudo kate .bashrc
kdesudo(7884) KDESu::KDESuPrivate::KCookie::getXCookie: No X authentication info set for display  ":0" 


QProcess: Destroyed while process is still running.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
No protocol specified
kate: cannot connect to X server :0


sudo kate opened the file but gave me this error:

> sudo kate .bashrc
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-johnbWlowxL" is owned by uid 1000 instead of uid 0.

---

### Post by ajgreeny on 2015-03-29
If the situation is the same as Ubuntu, try ```
sudo -H kate
``` but not to open and edit your own **.bashrc** as you show in your example as that file must must be owned by you, not root, if your bash configuration is to remain as you want it.

There has been a huge amount of discussion about the inadvisability of using **sudo** with GUI applications recently as a result of **gksu** and **gksudo** no longer being available by default in the OS, though still possible to install and use.

In Ubuntu and the other gtk versions it is intended that **pkexec** will take over from these alternatives, but it is not there yet for most of us, though it is possible to enable it with a bit of configuration of policy files.  I have no idea about Kubuntu's intentions in this matter.

---

