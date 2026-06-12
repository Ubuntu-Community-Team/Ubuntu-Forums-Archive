---
title: "[SOLVED] need help in installing java jdk"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-26
I installed sun-java6 jdk and ant from the Synaptic. the result is ant is not working properly:

```
ant -version
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
```

Is that because I installed a wrong jdk?

I tried to search out where is the tools.jar, I got this:
```
locate tools.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/tools.jar
```

Is the the same tools.jar that required by ant? If it is how can I point ant to this file?

---

### Post by iaculallad on 2008-07-26
> **imjscn said:**
> I installed sun-java6 jdk and ant from the Synaptic. the result is ant is not working properly:

```
ant -version
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
```

Is that because I installed a wrong jdk?

I tried to search out where is the tools.jar, I got this:
```
locate tools.jar
/usr/lib/jvm/java-6-sun-1.6.0.06/lib/tools.jar
```

Is the the same tools.jar that required by ant? If it is how can I point ant to this file?

Try:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by imjscn on 2008-07-26
I have sun-java6-jre,plugin and fonts installed, and they are working nicely. Anyway, instead of fix a problem, I decide to remove the jdk that I installed from Sypnatic. I download newest version of jdk from Sun. According to the instruction, I'll need to be the root to extract and install like this:
```
chmod a+x jdk-6u7-linux-i586-rpm.bin
./jdk-6u7-linux-i586-rpm.bin
```

To become the root, I typed in su and password, it returns:
```
su: Authentication failure
```

if I type in sudo, it doesn't work--it returns nothing
 ```
sudo chmod a+x jdk-6u7-linux-i586-rpm.bin
```

What's the right way to do the job?

---

### Post by iaculallad on 2008-07-26
> **imjscn said:**
> I have sun-java6-jre,plugin and fonts installed, and they are working nicely. Anyway, instead of fix a problem, I decide to remove the jdk that I installed from Sypnatic. I download newest version of jdk from Sun. According to the instruction, I'll need to be the root to extract and install like this:
```
chmod a+x jdk-6u7-linux-i586-rpm.bin
./jdk-6u7-linux-i586-rpm.bin
```

To become the root, I typed in su and password, it returns:
```
su: Authentication failure
```

Root password is disabled by default in Ubuntu. You have to enable it first and set the password.

To become root, you could just do:

```
sudo -i
```

and enter your own password.

> **imjscn said:**
> if I type in sudo, it doesn't work--it returns nothing
 ```
sudo chmod a+x jdk-6u7-linux-i586-rpm.bin
```

What's the right way to do the job?

```
sudo chmod +x jdk-6u7-linux-i586-rpm.bin
```
```
sudo ./jdk-6u7-linux-i586-rpm.bin
```

---

### Post by tinny on 2008-07-26
Definitely use the Sun JDK from the Ubuntu repositories.

1. Make sure you have the "multiverse" repositories enabled.

2. Install all Sun Java 6 packages...

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6* 

```

3. Check that you are using the newly installed JDK...

```

javac -version

```

The output should be something like...

```

javac 1.6.0_06

```

4. Check that you are using the correct JRE...

```

java -version

```

The output should be something like...

```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

If you find you are not using the correct Sun Java 6 JRE you can fix it by...

```

sudo update-alternatives --config java

```

The above command will let you choose which JRE to make default if you have multiple JRE's installed.

---

### Post by imjscn on 2008-07-26
Thanks! I managed the root permission and installed the RPM.bin file. Now the real problem comes---after install, it says
 ```
inflating: sun-javadb-javadoc-10.3.1-4.1.i386.rpm  
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found
Installing JavaDB
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found

```

When the **** hits the fan, it hits big time :confused:

Please...how to uninstall the rpm file manually? After uninstall, I'll go with repositories.

---

### Post by gandaran on 2008-07-26
> **imjscn said:**
> Thanks! I managed the root permission and installed the RPM.bin file. Now the real problem comes---after install, it says
 ```
inflating: sun-javadb-javadoc-10.3.1-4.1.i386.rpm  
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found
Installing JavaDB
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found

```

When the **** hits the fan, it hits big time :confused:

Please...how to uninstall the rpm file manually? After uninstall, I'll go with repositories.

did you really installed this package? to install it you have to convert the .rpm to .deb with alien.
rpm don't work with debian/ubuntu systems
you should just download the simple bin file from the sun website, but it's best you stick with the repos java, you don't get a firefox plugin with the sun bin file.

---

### Post by imjscn on 2008-07-26
I see, perhaps it was just extracted but didn't install. That's a great thing.So, now, where can I go to delete those extracted files?

---

### Post by scorp123 on 2008-07-26
> **imjscn said:**
> Please...how to uninstall the rpm file manually? After uninstall, I'll go with repositories. RPM's (= **_R_**ed Hat **_P_**ackage **_M_**anager) are for RPM-based Linux distributions such as Red Hat, Fedora, OpenSUSE, SLES, SLED, NLD, and so on.

Distributions based on Debian Linux such as Ubuntu don't use RPM packages. Here you're supposed to use *.deb packages and preferably those which you can easily get from your distribution's APT repositories!

As for your question: The RPM package is not even installed, so all you have to do is to delete the *.rpm file(s) which you downloaded.

Don't forget to do what "tinny" a few postings further up told you.

---

### Post by gandaran on 2008-07-26
and check with synaptic if you also have open-java/open-jdk installed
remove all the open-jdk packages if they are installed, just keep the sun-java installed.

---

### Post by imjscn on 2008-07-26
Thanks!!!!!!!
Now, removed the rpm file, followed tinny's steps, installed all sun java6

javac 1.6.0_06
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
:guitar:

---

### Post by Ro_han on 2008-10-17
I had the exact same problem. I installed java 6 and NetBeans with no prior software downloaded directly from Sun, but when trying to compile a project with ant I got:

```
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
```

Similarly trying to locate tools.jar I got:

```
/usr/lib/jvm/cacao/lib/tools.jar
/usr/lib/jvm/java-6-sun-1.6.0.07/lib/tools.jar
/usr/lib/jvm/java-6-sun-1.6.0.07/lib/visualvm/visualvm/modules/com-sun-tools-visualvm-tools.jar
/usr/share/netbeans/ide8/modules/org-netbeans-modules-xml-tools.jar

```

with the second file being the relevant one.

As suggested I tried updating but everything was up to date excepts fonts which didn't seem to matter.

I tried the suggestion of changing jre:

```
han@hanbox:~/mich/javah/ant_proj$  sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          4    /usr/bin/cacao
          5    /usr/lib/jvm/java-6-sun/jre/bin/java

```

And I chose option 5. This fixed the problem.

I don't fully understand why this works. It seems to be a matter of connecting ant to the right jre.

---

