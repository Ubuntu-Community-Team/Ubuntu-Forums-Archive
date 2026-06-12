---
title: "I broke my eclipse install"
date: 2006-03-14
forum: Programming Talk
---

### Post by elpresidente on 2006-03-14
Actually, I was hving difficulties getting phpeclipse to work after installed and wanted a fresh uninstall and reinstall but eclipse still saw phpeclipse as installed. So I apt removed it and went to rm -ing some eclipse directories (I got heavy-handed and rm 'd them all inclusing /etc/eclipse). The later dir included java_home I think and now, after apt installing eclipse again I receive an "A suitable Java Virtual Machine for running the Eclipse Platform could not be located." error. I know I shouldn't have deleted that but I don't know how to fix it. My google searches bore no fruit.

---

### Post by hod139 on 2006-03-14
You can try ```

sudo update-alternatives --config java

```
and selecting the desired JRE.  You can also edit /etc/jvm and make sure a path to a JRE exists.  Lastly, you can start eclipse by passing it the -vm flag, followed by a path to a vm.
```
eclipse -vm /usr/lib/j2sdk1.5-sun/jre/
```
Hope one of those work.

---

### Post by elpresidente on 2006-03-14
Thank you. I tried those but it did not help. I did, however, manage to grab a copy of java_home off my nearly identical ubuntu install at home and copy it to /etc/eclipse and have created ~/.eclipse/eclipserc to include:

JAVA_HOME=/usr/lib/j2re1.5-sun

Now any attempts to run it results in an error message:

An error has occurred. See the log file /home/username/.eclipse/org.eclipse.platform_3.1.1/configuration/xxxxxxxxxxxxx.log

That log contains:
```
!SESSION Tue Mar 14 12:10:52 EST 2006 ------------------------------------------
!ENTRY org.eclipse.core.launcher 4 0 2006-03-14 12:10:52.740
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ArrayIndexOutOfBoundsException: 0
        at org.eclipse.core.launcher.Main.getSplashLocation(Main.java:1638)
        at org.eclipse.core.launcher.Main.handleSplash(Main.java:1535)
        at org.eclipse.core.launcher.Main.basicRun(Main.java:276)
        at org.eclipse.core.launcher.Main.run(Main.java:973)
        at org.eclipse.core.launcher.Main.main(Main.java:948)
```

Not sure how to rectify this. Any suggestions would be appreciated.

---

### Post by mlind on 2006-03-14
you could try to remove eclipse using *apt-get remove --purge*
then start eclipse using -clean switch and preferably create new workspace.

---

### Post by elpresidente on 2006-03-14
> you could try to remove eclipse using apt-get remove --purge
then start eclipse using -clean switch and preferably create new workspace.

I did try that and the issue did not go away. I just now downloaded eclipse from eclipse.org. After extracting the archive, it seems to be running just fine. I just edited my menu file (fluxbox) to point to the extracted eclipse archive. I'm attempting to install phpEclipse right now and will report back after that.

Thanks for the suggestions.

---

### Post by mlind on 2006-03-14
usually funny stacktraces like that one are caused by eclipse GUI running on
non-sun jvm.

does *java -version* say that it's sun's jvm

---

### Post by elpresidente on 2006-03-15
[QUOTE=mlind]usually funny stacktraces like that one are caused by eclipse GUI running on
non-sun jvm.

does *java -version* say that it's sun's jvm[/QUOTE]

It did. I had actually switched it to gnu when I installed eclipse directly downloaded from eclipse.org and it worked. I did just switch it to sun as the PHP browser was giving me a not available error. After switching it, I get now error but no PHP browser either. Not a high priority - will try to take care of it another time.

---

