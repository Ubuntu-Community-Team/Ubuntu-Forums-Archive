---
title: "[Tutorial] Manually installing the JDK 6 Update 13"
date: 2009-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by James_Lochhead on 2009-03-31
_**[SIZE="4"]Introduction[/SIZE]**_

This tutorial is meant to help someone install the latest version of the JDK, currently the JDK 6 Update 13. Included in the tutorial is the installation of the JDK itself, as well as installation of the included JRE and Java Web Plugin for Firefox. The instructions may work for other versions of the JDK. Please use your own discretion when deciding whether to use this tutorial with other versions of the JDK. It should be noted that this tutorial also deals with the installation of the new 64 bit Java Web Plugin.

Also please note that this tutorial is meant to be very user friendly. If you are an advanced user you should be able to skim through in five minutes and get everything working.

If you have anything to add please post away.

**_[SIZE="4"]Uninstallation of the current Sun JDK[/SIZE]_**

If you have the currently have the Sun JDK installed you need to remove it. Use the following command in the terminal:

```

sudo apt-get remove sun-java6-jre sun-java6-jdk sun-java6-bin

```

If you want to installed the Sun Java Web Plugin for Firefox you will have to remove that as well using:

```

sudo apt-get remove sun-java6-plugin

```

By default Ubuntu comes with the OpenJDK JRE, IcedTea Java Web Plugin and a few other dependant packages. If you leave these (I believe) after the tutorial Firefox will still use the OpenJDK JRE for applets. In my opinion, there is no point having multiple packages with the same function installed so I removed them with the following command:

```

sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless icedtea-6-jre-cacao icedtea6-plugin default-jre default-jre-headless icedtea-gcjwebplugin

```

Everything should have been uninstalled correctly. However, to make sure we do not have any additional unused packages around that we no longer need, type the following in the terminal:

```

sudo apt-get autoremove

```

**_[SIZE="4"]Download of the correct JDK bin file[/SIZE]_**

Go to [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) in your browser. On this page the current JREs and JDKs are listed along with some other tools. This tutorial was built for the the JDK 6 Update 13. However, it will probably work for newer/older updates of the 6 series as well. If there is a newer JDK available you may want to grab it and adapt the tutorial.

After choosing the appropriate JDK click on the download link next to it. If you use i386 (32 bit) Ubuntu you will want to download the “Linux” version on the next page, however if you are on amd64 (64 bit) Ubuntu you will want to download the “Linux x64” version. Once the JDK file (jdk<something>.bin) has finished downloading you need to move it to your home directory.

_**[SIZE="4"]Extract and install the Java bin file[/SIZE]**_

Open a terminal and type the following commands:

```

chmod +x jdk*.bin
sudo ./jdk*.bin

```

Before the bin file will extract you have to agree to the terms and conditions (by typing yes or no). To skip through the agreement simply press q. 

Now you have an extracted JDK directory (with root ownership) in your home directory. At this point please note down the name of the JDK folder in your home folder, you will need to type it in for later commands. For me the name of the folder is :

```

jdk1.6.0_13 

```

Henceforth the folder will be refered to as <JAVA_FOLDER>. If you see <JAVA_FOLDER> in any of the commands replace it with the folder name.

Now we need to move tge Java folder to somewhere a little more appropriate. I moved mine to /usr/local/. If you are an advanced user you can pretty much put in anywhere you want. Just make sure you adapt the tutorial accordingly.

```

sudo mv <JAVA_FOLDER>/ /usr/local/

```

[B][U][SIZE="4"]
Setting up the JAVA_HOME and PATH variables[/SIZE][/U][/B]

In order to use the java and javac commands in the terminal you need to set the JAVA_HOME and PATH variables in your bashrc file. Please note that if you want to use the commands on multiple accounts you must set these variables on each of the accounts. Edit the baschrc file using the following terminal commands:

```

echo “export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java” >> ~/.bashrc
echo “export PATH=$PATH:/usr/local/<JAVA_FOLDER>/bin” >> ~/.bashrc

```

Now if you close the terminal and open it again the java and javac commands should work. If they do not something has gone wrong.

[SIZE="4"]**_Setting up the default JRE_**[/SIZE]

In order to use the JRE we just installed we need to tell Ubuntu to use it as default. If you didn't uninstall the OpenJDK and still want to use it as default you do not need to do this. The JRE can be set as default using the following terminal commands:

```

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/<JAVA_FOLDER>/jre/bin/java" 1
sudo update-alternatives --set java /usr/local/<JAVA_FOLDER>/jre/bin/java

```

**_[SIZE="4"]Setting up the Java Web Plugin[/SIZE]_**

If you didn't remove the OpenJDK and IcedTea Java Web Plugin and still want to use them you do not have to do this part. If you did uninstall them you will need to do this section in order for Java to work in Firefox. The commands are different for 32 and 64 bit. 

**_32 bit:_**

```

mkdir ~/.mozilla/plugins
ln -s /usr/local/<JAVA_FOLDER>/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/


```

Now restart Firefox. In the Firefox URL input box type:

```

about:config 

```

Next click agree. In the search box at the top on the next page type in java. Somewhere in this list is an entry for java.java_plugin_library_name. You must change this to:

```

libjavaplugin_oji

```

In the same list there is an entry for java.default_java_location_others. You must change this to:

```

/usr/local/<JAVA_FOLDER>/jre/

```

**_64 bit:_**

```

mkdir ~/.mozilla/plugins
ln -s /usr/local/<JAVA_FOLDER>/jre/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

```

Now restart Firefox. In the Firefox URL input box type:

```

about:config 

```

Next click agree. In the search box at the top on the next page type in java. Somewhere in this list is an entry for java.java_plugin_library_name. You must change this to:

```

libnpjp2

```

In the same list there is an entry for java.default_java_location_others. You must change this to:

```

/usr/local/<JAVA_FOLDER>/jre/

```

Please note that this installs the plugin for a single account. If you want to use the plugin on another account you will have to repeat this section.

**The End.**

---

### Post by aszxcv on 2009-03-31
great tutorial thanks

---

### Post by slavik on 2009-03-31
This belongs in Tutorials and Tips.

Unapproved for further review.

---

### Post by slavik on 2009-03-31
After reviewing your tutorial, I have the following points that I feel you need to address:

[LIST=1]
[*]Why are distribution packages being removed?
[*]The way your are replacing Java is bad, What about other users on the same system?
[*]What about other Java commands like javaws and javac?
[*]Are you sure that you are installing ALL the alternatives for Java related binaries?
[/LIST]

---

