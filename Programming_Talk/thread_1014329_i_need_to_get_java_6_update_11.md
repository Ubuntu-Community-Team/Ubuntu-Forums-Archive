---
title: "i need to get java 6 update 11"
date: 2008-12-17
forum: Programming Talk
---

### Post by aszxcv on 2008-12-17
i need to get java 6 update 11

i am on 8.04 ubuntu.
i used sudo apt-get install sun-java6* awhile back but i got java 6.07 version.

my input of javac -version produces javac 1.6.0_07
and java -version produces java version "1.6.0_0"
OpenJDK Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)

---

### Post by reality1011 on 2008-12-17
go to sun's website and download and install it?


Here is some additional help from a previous post of mine:


ok so I just installed the most recent java by doing the following:

1.  Download the bin file ( not the rpm.bin) from here:[DOWNLOAD FROM SUN]("http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/VerifyItem-Start/jdk-6u10-linux-i586.bin?BundledLineItemUUID=kDtIBe.pnFAAAAEda_pSvLfj&OrderID=NylIBe.pObIAAAEdVPpSvLfj&ProductID=7GBIBe.pq0AAAAEb4aMQVbLE&FileName=/jdk-6u10-linux-i586.bin")

2. chmod 755 and move this file into the top level directory where java is installed... in my case it is in /usr/local/

```

cappetta@Linux-Box:~/internet-downloads$ which java
/usr/bin//java
cappetta@Linux-Box:~/internet-downloads$ ll /usr/bin/java
lrwxrwxrwx 1 root root 31 2008-02-16 19:59 /usr/bin/java -> /usr/local/jdk1.5.0_14/bin/java
cappetta@Linux-Box:~/internet-downloads$ 


```

3. execute 
```
sudo ./jdk-6u10-linux-i586.bin 
```

4. press space until you are required to type yes... then press enter... wait press enter again

5.  Remove the links and recreate them: 

```
cappetta@Linux-Box:/usr/local$ which java
/usr/bin//java
cappetta@Linux-Box:/usr/local$ ll /usr/bin/java
lrwxrwxrwx 1 root root 31 2008-02-16 19:59 /usr/bin/java -> /usr/local/jdk1.5.0_14/bin/java
cappetta@Linux-Box:/usr/local$ sudo rm /usr/bin/java
cappetta@Linux-Box:/usr/local$ sudo ln -s /usr/local/jdk1.6.0_10/bin/java /usr/bin/java
cappetta@Linux-Box:/usr/local$ ll /usr/bin/java
lrwxrwxrwx 1 root root 31 2008-11-19 22:25 /usr/bin/java -> /usr/local/jdk1.6.0_10/bin/java
cappetta@Linux-Box:/usr/local$ ll /usr/bin/javac
lrwxrwxrwx 1 root root 32 2008-02-16 19:59 /usr/bin/javac -> /usr/local/jdk1.5.0_14/bin/javac
cappetta@Linux-Box:/usr/local$ sudo rm /usr/bin/javac
cappetta@Linux-Box:/usr/local$ sudo ln -s /usr/local/jdk1.6.0_10/bin/javac /usr/bin/javac
cappetta@Linux-Box:/usr/local$ ll /usr/bin/javac
lrwxrwxrwx 1 root root 32 2008-11-19 22:25 /usr/bin/javac -> /usr/local/jdk1.6.0_10/bin/javac
cappetta@Linux-Box:/usr/local$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
cappetta@Linux-Box:/usr/local$ javac -version
javac 1.6.0_10
cappetta@Linux-Box:/usr/local$ 

```

---

### Post by albinootje on 2008-12-17
> **aszxcv said:**
> i need to get java 6 update 11

i am on 8.04 ubuntu.
i used sudo apt-get install sun-java6* awhile back but i got java 6.07 version.


By coincidence i had a friend visiting tonight with exactly the same question. Ubuntu Hardy and needing the Java 6 update 11

After quite some fiddling around i've managed to get it working.

Here are instructions based on the java.com instructions here :
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

However those original instructions are :

1) Outdated
2) Mistaken, because it contains a serious typo! 
(Because there's a space in the symlink part in the end which shouldn't be there)

========================

1. Open a terminal
2. Remove sun-java5-plugin and sun-java6-plugin packages :

   sudo apt-get remove --purge sun-java5-plugin sun-java6-plugin

3. Make a new directory called /usr/java :
   sudo mkdir /usr/java
   cd /usr/java/

   Move your downloaded file jre-6u11-linux-i586.bin 
   to the /usr/java/ directory
   For example : 
   sudo mv /home/steve.b/Desktop/jre-6u11-linux-i586.bin /usr/java/

4. Change the permission of the file you downloaded to be executable.
   sudo chmod +x /usr/java/jre-6u11-linux-i586.bin

   5. Verify that you have permission to execute the file. Type:
      ls -l

   6. Start the installation process.Type:
       sudo sh ./jre-6u11-linux-i586.bin

      This displays a binary license agreement. Read through the
agreement. Press the spacebar to display the next page. At the end,
enter yes to proceed with the installation. Type YES to agree to the
license agreement

7. When the installation has completed, you will see the word Done.
The installation completes

cd /usr/lib/mozilla/plugins/
sudo ln -s /usr/java/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so

That's it. 

Restart firefox, and type : about:plugins

And test java here : [http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3)

---

### Post by aszxcv on 2008-12-17
how do i get rid of ```
sudo apt-get install sun-java6*
``` from the first install

---

### Post by albinootje on 2008-12-17
> **aszxcv said:**
> how do i get rid of ```
sudo apt-get install sun-java6*
``` from the first install

sudo apt-get remove --purge sun-java6-*

---

### Post by erickelrojas on 2008-12-22
La instalación de la última versión de JRE la tengo siempre en mi web

[www.elleonplateadodeojosrojos.es/blog/instalacion-de-jre]("http://www.elleonplateadodeojosrojos.es/blog/instalacion-de-jre")

Hasta Siempre:guitar:

---

### Post by centos on 2009-01-27
Hello, I've installed java 6u11 but I can't get it working, "which java" shows /usr/bin/java, but the new one is in /usr/java/jre1.6.0_11, also java -version shows 
```
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Server VM (build 1.6.0_0-b12, mixed mode)

```

I guess the solution is in reality1011's post in 5, but I'm not sure what doues that mean exactly, so could someone explain it please?

---

### Post by Reiger on 2009-01-27
If you have multiple versions of Java set up properly you can edit the default (called by the java command) using update-alternatives.
Output taken from ```
sudo update-alternatives --help
```
```

Usage: update-alternatives [<option> ...] <command> 

Commands:
  --install <link> <name> <path> <priority>
    [--slave <link> <name> <path>] ...     
                           add a group of alternatives to the system.
  --remove <name> <path>   remove <path> from the <name> group alternative.
  --remove-all <name>      remove <name> group from the alternatives system.
  --auto <name>            switch the master link <name> to automatic mode. 
  --display <name>         display information about the <name> group.      
  --list <name>            display all targets of the <name> group.         
  --config <name>          show alternatives for the <name> group and ask the
                           user to select which one to use.                  
  --set <name> <path>      set <path> as alternative for <name>.             
  --all                    call --config on all alternatives.                

<link> is the symlink pointing to /etc/alternatives/<name>.
  (e.g. /usr/bin/pager)                                    
<name> is the master name for this link group.             
  (e.g. pager)                                             
<path> is the location of one of the alternative target files.
  (e.g. /usr/bin/less)                                        
<priority> is an integer; options with higher numbers have higher priority in
  automatic mode.                                                            

Options:
  --altdir <directory>     change the alternatives directory.
  --admindir <directory>   change the administrative directory.
  --verbose                verbose operation, more output.     
  --quiet                  quiet operation, minimal output.    
  --help                   show this help message.             
  --version                show the version.                   
prometheus@Bartix:~$ sudo update-alternatives --s java
update-alternatives: unknown option `--s'             

Usage: update-alternatives [<option> ...] <command>

Commands:
  --install <link> <name> <path> <priority>
    [--slave <link> <name> <path>] ...     
                           add a group of alternatives to the system.
  --remove <name> <path>   remove <path> from the <name> group alternative.
  --remove-all <name>      remove <name> group from the alternatives system.
  --auto <name>            switch the master link <name> to automatic mode. 
  --display <name>         display information about the <name> group.      
  --list <name>            display all targets of the <name> group.         
  --config <name>          show alternatives for the <name> group and ask the
                           user to select which one to use.                  
  --set <name> <path>      set <path> as alternative for <name>.             
  --all                    call --config on all alternatives.

<link> is the symlink pointing to /etc/alternatives/<name>.
  (e.g. /usr/bin/pager)
<name> is the master name for this link group.
  (e.g. pager)
<path> is the location of one of the alternative target files.
  (e.g. /usr/bin/less)
<priority> is an integer; options with higher numbers have higher priority in
  automatic mode.

Options:
  --altdir <directory>     change the alternatives directory.
  --admindir <directory>   change the administrative directory.
  --verbose                verbose operation, more output.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.

```
In particular, check out --set and --configure (the former is to register new additions, the latter to configure the default).

---

### Post by centos on 2009-01-27
So if I'm getting it right, point of this is that the new java will appear in
```
update-java-alternatives -l

```
which now returns
```
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

```
and will be possible to set it as default.
But ```
sudo update-alternatives --set java /usr/java/jre1.6.0_11/bin/

```
returns 
```
update-alternatives: Nemohu najít alternativu &#8222;/usr/java/jre1.6.0_11/bin/&#8220;.
``` (can't find alternative) :(

edit: I followed this tutorial [http://www.open-xchange.com/forum/archive/index.php/t-112.html](http://www.open-xchange.com/forum/archive/index.php/t-112.html) and for "java" and "javaws" it seems to work. Thanks.

---

