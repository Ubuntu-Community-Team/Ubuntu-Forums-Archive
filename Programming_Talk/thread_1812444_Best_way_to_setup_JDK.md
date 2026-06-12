---
title: "Best way to setup JDK"
date: 2011-07-26
forum: Programming Talk
---

### Post by ki4jgt on 2011-07-26
Read about three websites already which tell me to install jre and jdk, then tell me to edit files which are in folders which don't even exist??? Can someone walk me through default setup of jre and jdk?

Can you also tell me how to set the computer up, so that when ever it get's updates for openjdk, it doesn't uninstall sun-java6-jdk? Because in some past distros, I've installed sun-java6-jre and the system would uninstall it and use open-jdk instead.

Lastly I want to make sun my default java (player??? LOL, if that's the right word) I've been having trouble with software which doesn't want to run b/c it's running on open-jre. I would really like to get this software running.

Thanks guys :-)

---

### Post by Reiger on 2011-07-26
On Debian Linux you'd install it through your package manager of choice. To make it the default Java you would use update-alternatives.

I tend to do something like this, after install SUN/Oracle Java  6:
```

for i in /usr/lib/jvm/java-6-sun/bin/* ; do sudo update-alternatives --config "$i"; done
```

Note that update-alternatives is a Debian & derivatives tool, it may not be available/work on Fedora, SUSE etc.

---

### Post by stchman on 2011-07-26
If you have no JDK simply install SUN/Oracle JDK with plugin from the Partner repository.

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```

After that you will have a JRE, JDK, browser plugin, and fonts.

Easy.

---

### Post by lkjoel on 2011-07-26
Try this: [http://lkubuntu.wordpress.com/2011/02/09/java-installer/](http://lkubuntu.wordpress.com/2011/02/09/java-installer/)

---

### Post by Dhiraj Thakur(Invincible) on 2011-07-27
> **ki4jgt said:**
> Read about three websites already which tell me to install jre and jdk, then tell me to edit files which are in folders which don't even exist??? Can someone walk me through default setup of jre and jdk?

Can you also tell me how to set the computer up, so that when ever it get's updates for openjdk, it doesn't uninstall sun-java6-jdk? Because in some past distros, I've installed sun-java6-jre and the system would uninstall it and use open-jdk instead.

Lastly I want to make sun my default java (player??? LOL, if that's the right word) I've been having trouble with software which doesn't want to run b/c it's running on open-jre. I would really like to get this software running.

Thanks guys :-)
i have written a tutorial on setting up jdk and jre on ubuntu....see if it helps.....
[http://maitnoobsatwork.blogspot.com/2011/07/how-to-install-java-6-and-java-runtime.html](http://maitnoobsatwork.blogspot.com/2011/07/how-to-install-java-6-and-java-runtime.html)

---

