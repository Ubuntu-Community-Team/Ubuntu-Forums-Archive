---
title: "eclipse or easyeclipse?"
date: 2006-07-20
forum: Programming Talk
---

### Post by jordilin on 2006-07-20
I want to try Eclipse with python. What's the best way to install eclipse? By means of synaptic (repos) or just go to [http://www.easyeclipse.org/site/home/]("http://www.easyeclipse.org/site/home/") 
and download eclipse with python plugin bundled?

---

### Post by timetunnel on 2006-07-20
Since Eclipse doesn't need a real "install" (just copy in a folder and you're done), I downloaded it from [http://www.eclipse.org](http://www.eclipse.org) and installed in /opt. That way you can always have the latest version of Eclipse and the plugins and don't have to wait for Dapper updates or the next ubuntu release.
Easylinux should be the same, I guess.

---

### Post by jordilin on 2006-07-20
> **timetunnel said:**
> Since Eclipse doesn't need a real "install" (just copy in a folder and you're done), I downloaded it from [http://www.eclipse.org](http://www.eclipse.org) and installed in /opt. That way you can always have the latest version of Eclipse and the plugins and don't have to wait for Dapper updates or the next ubuntu release.
Easylinux should be the same, I guess.
Ok, I'll try out downloading Eclipse plus the python plugin. The website easyeclipse provides eclipse packages and its plugins depending on the language you want to use.

---

### Post by timetunnel on 2006-07-20
Additional info:
[LIST]
[*]If you copy Eclipse to /opt, you should do it as root with "sudo". In order to update and install plugins you have to start Eclipse with "gksudo /opt/eclipse/eclipse" then. For normal development work, Eclipse can be run as normal user from there.
[*]Or, if you're the only user on your system, just copy all to you home folder instead and start and update everything as normal user. That's the most simple way.
[/LIST]

---

### Post by timetunnel on 2006-07-20
Oh, and you need SUN's java in order to run Eclipse properly. At least on Breezy it was that way. It didn't run with the java that belongs to the default ubuntu install. Use "sudo update-alternatives --config java" to switch the SUN's java permanently after installing it. Eclipse uses it automatically then.

---

### Post by hod139 on 2006-07-20
Here is a howto for setting up eclipse and Sun's java:
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by timetunnel on 2006-07-20
> **hod139 said:**
> Here is a howto for setting up eclipse and Sun's java:
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

That howto seems to be for Breezy. In Dapper, doing the
```
sudo update-alternatives --config java
```
was sufficient to run Eclipse. No need to edit files in /etc manually.

---

### Post by jordilin on 2006-07-20
thanks, I have already setup the Sun's java.

---

### Post by hod139 on 2006-07-20
> **timetunnel said:**
> That howto seems to be for Breezy. In Dapper, doing the
```
sudo update-alternatives --config java
``` was sufficient to run Eclipse. No need to edit files in /etc manually.
That howto is for Dapper.  There is a bug right now where Eclipse does not respect the java-common settings. It is [bug 45347]("https://launchpad.net/distros/ubuntu/+source/eclipse/+bug/45347").  I would be surprised if you got the ubuntu repository version of eclipse to use Sun's java without editing 
```

/etc/eclipse/java_home

```

If you start eclipse from the command line instead of the menu entry, what output do you see?

---

### Post by timetunnel on 2006-07-20
> **hod139 said:**
> I would be surprised if you got the ubuntu repository version of eclipse to use Sun's java without editing

I didn't use the ubuntu Eclipse packages, I downloaded the latest version from the Eclipse homepage and just unzipped to /opt. Nothing needed to be edited except for the update-alternatives stuff. It just worked.

> If you start eclipse from the command line instead of the menu entry, what output do you see?

Nothing. Not a single line is printed. I just start it:
```
~$: /opt/eclipse3.2/eclipse
```
and it starts and works.

---

### Post by timetunnel on 2006-07-20
Damn it. I was fooled by the new forum layout and mixed up the first "join date" (October 2005) with the time the posting was done. That's why I thought the howto is for Dapper.

Maybe the howto should add the fact that it's talking about Eclipse being installed from the ubuntu repositories.

---

### Post by hod139 on 2006-07-20
> **timetunnel said:**
> I didn't use the ubuntu Eclipse packages, I downloaded the latest version from the Eclipse homepage and just unzipped to /opt. Nothing needed to be edited except for the update-alternatives stuff. It just worked.



Nothing. Not a single line is printed. I just start it:
```
~$: /opt/eclipse3.2/eclipse
``` and it starts and works.

Hmm, I wish we could confirm without a doubt if the downloaded version is actually using Sun's java or Gnu's.  If you run 
```

eclipse -debug

``` and scan all that output (hopefully this time you get some) for 
Start VM:
what VM is it starting with.
> 
Maybe the howto should add the fact that it's talking about Eclipse being installed from the ubuntu repositories.
 After we determine what JVM the downloaded version is actually using, I'll make any necessary changes.

---

### Post by timetunnel on 2006-07-20
> **hod139 said:**
> Hmm, I wish we could confirm without a doubt if the downloaded version is actually using Sun's java or Gnu's.  If you run 
```

eclipse -debug

``` and scan all that output (hopefully this time you get some) for 
Start VM:
what VM is it starting with.
 After we determine what JVM the downloaded version is actually using, I'll make any necessary changes.

Ok, done. Here's the relevant output:
```
Start VM: /usr/bin/java
```
/usr/bin/java actually links to SUN's java this way:
```
/usr/bin/java -> /etc/alternatives/java
```
and
```
/etc/alternatives/java -> /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

Here's the full -debug output, just in case:

```
username@computername:~$ /opt/eclipse3.2/eclipse -debug
Start VM: /usr/bin/java
-Xms40m
-Xmx256m
-jar /opt/eclipse3.2/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /opt/eclipse3.2/eclipse
-name Eclipse
-showsplash 600
-exitdata 708021
-debug
-vm /usr/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /opt/eclipse3.2/startup.jar
Install location:
    file:/opt/eclipse3.2/
Configuration file:
    file:/opt/eclipse3.2/configuration/config.ini loaded
Configuration location:
    file:/home/username/.eclipse/org.eclipse.platform_3.2.0/configuration/
Configuration file:
    file:/home/username/.eclipse/org.eclipse.platform_3.2.0/configuration/config.ini loaded
Shared configuration location:
    file:/opt/eclipse3.2/configuration/
Framework located:
    file:/opt/eclipse3.2/plugins/org.eclipse.osgi_3.2.0.v20060601.jar
Framework classpath:
    file:/opt/eclipse3.2/plugins/org.eclipse.osgi_3.2.0.v20060601.jar
Splash location:
    /opt/eclipse3.2/plugins/org.eclipse.platform_3.2.0.v20060601/splash.bmp
runCommand:
    </opt/eclipse3.2/eclipse><-name><Eclipse><-showsplash><600></opt/eclipse3.2/plugins/org.eclipse.platform_3.2.0.v20060601/splash.bmp>
Debug options:
    file:/home/username/.options not found
Time to load bundles: 463
Starting application: 4633
Application Started: 15341


```

---

### Post by timetunnel on 2006-07-20
I just checked the update-alternatives stuff and realized that not only "java" but "jar" is set to the SUN path as well on my system. Might be relevant, so here's my config for it:

```
:~$ sudo update-alternatives --config jar

There are 3 alternatives which provide `jar'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/fastjar
 +    2        /usr/lib/jvm/java-gcj/jre/bin/jar
*     3        /usr/lib/jvm/java-1.5.0-sun/bin/jar

Press enter to keep the default[*], or type selection number:

```

---

### Post by hod139 on 2006-07-20
Timetunnel, thanks for all the great feedback.  Good to know that changes to Eclipse made by the Ubuntu devs is what caused the bug ](*,)

Anyways, I'll update my howto to make sure it states that the editing of 
```
/etc/eclipse/java_home
``` is only required for the version of eclipse found in the repos.

There are alternatives for:
jar, javac, javadoc, javap, javah, and javaws
all of which are listed in my howto.

Thanks again.

---

### Post by timetunnel on 2006-07-20
Glad to help :) 
Generally, I think it's good to have Eclipse in the repos - if it works. But if the package is more complicated to install than the simple-to-install download from the Eclipse homepage, then it doesn't really make sense to have it in the repos.

---

### Post by saracen on 2006-08-01
I installed eclipse from the repos.  The install worked fine and I can run it smoothly.  Now I want to install the [aptana plugin]("http://www.aptana.com") but i'm wondering if i can do that while running eclipse as a normal user.  Or do i have to run it as root and then install the plugin?

---

### Post by timetunnel on 2006-08-02
That depends on the folder where Eclipse is located. If you have copied it somewhere into your home folder, say /home/me/opt/eclipse, you can run the update as normal user. However, if you've copied Eclipse to a folder that only allows read-access for normal users, like /opt for example, you have to run Eclipse as root, like this:
```
gksudo /opt/eclispe/eclipse
```

Eclipse needs write access to its folder in order to install or update plugins. So generally, it just depends on the rights of the Eclipse directory.

---

