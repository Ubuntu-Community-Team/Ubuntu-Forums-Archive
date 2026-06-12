---
title: "HOWTO: Setup Subversion + eclipse"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Cavalierski on 2006-06-03
**This post is duplicated. Please refer to [http://ubuntuforums.org/showthread.php?t=187739](http://ubuntuforums.org/showthread.php?t=187739) for the latest info.**

Here is the how-to for setting up the subversion client with eclipse and the server.  Hope this will help you more productive coding :D 

**[COLOR="Red"][Client - Eclipse with plugin] [/COLOR]**
Assume that you have already installed eclipse & j2sdk1.5-sun.
If you face problem starting up the eclipse you can find the answer in this forum. Most likely it is related to "java_home". Just for the instant check
```

cd /etc/eclipse
cat java_home

```
If you don't see  _/usr/lib/j2sdk1.5-sun/_ commented out in the first line, modify it. Mine looks like this..
```

ubuntu% cat java_home
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun/
#/usr/lib/jvm/java-gcj
#/usr/lib/kaffe/pthreads
#/usr/lib/sablevm
#/usr/lib/fjsdk
#/usr/lib/j2se/1.5
#/usr/lib/j2se/1.4
#/usr/lib/j2sdk1.5-ibm
#/usr/lib/j2sdk1.4-ibm
#/usr/lib/j2sdk1.5-sun
#/usr/lib/j2sdk1.4-sun

```

Ok then , let's get started.
Step1: Installing the plug-in (subclipse)
Launch eclipse and go to : 
help->s/w updates ->find and install->search for new features
Then press "new remote site" and add "http://subclipse.tigris.org/update"
Then follow the instraction to install the plugin.

Step2: Install library needed for subversion from eclipse
```
sudo apt-get install libsvn-javahl
```

Step3: Grance at subversion perspective
Follow this then you can see the svn perspective :-D 
window->Opne Perspective-> Other->SVN Repository Explorer

If you already have subversion server running, you can access to it by right clicking svn repository explorer then 
new -> create remote folder

**[COLOR="Red"][Server - Subversion] [/COLOR]**
Step1: Install package
```
sudo apt-get subversion subversion-helper-scripts subersion-tools
```

Step2: Create repository folder & bind it to subversion. You can deploy it wherever you want. This is my case.

```
sudo mkdir -p /var/local/svn/projectx
svnadmin create /var/local/svn/projectx
sudo chown -R username:usergroup /var/local/svn/projectx
```

Step3: Set configuration for subversion server
```
cd /var/local/svn/projectx/conf
sudo gedit  svnserve.conf
--
[general]
 anon-access = read
 auth-access = write
 password-db = passwd # This refer to passwd file in the same folder
 realm =Cavalier Repository
--

```

Ok then set the authentication for the access to the subversion server. In the same folder there is already the file named "passwd", all you need to do is edit this plain text file.

```
sudo gedit passwd
--
 [users]
username = password #<- you can modify here to whom you want to allow the access 
--
```

Setup for the subversion server is done :-D You can run it as a daemon by:
```
sudo /usr/bin/svnserve -d
```

However you most likely want to run automatically as xinet.d Then install xinetd first and set it up.
```
sudo apt-get install xinetd
sudo gedit /etc/xinet.d/svnserve
--
service svnserve
{
    disable         = no
    port            = 3690
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = /usr/bin/svnserve
    server          = -i -r /var/local/svn/dj15fw
}
--

sudo gedit /etc/services
# modify the port "3690/tcp" line like this below
--
svnserve		3690/tcp	# Subversion protocol
--

```

After the configuration , restart xinetd :
```
sudo /etc/init.d/xinetd restart
```

OK Done !!
Now I have subversion server & client for the productive open source development.. Enjoy coding:KS

---

### Post by Kuraboy on 2006-06-05
[QUOTE=Cavalierski]
**[COLOR="Red"][Client - Eclipse with plugin] [/COLOR]**
Assume that you have already installed eclipse & j2sdk1.5-sun.
If you face problem starting up the eclipse you can find the answer in this forum. Most likely it is related to "java_home". Just for the instant check
```

cd /etc/eclipse
cat java_home

```
If you don't see  _/usr/lib/j2sdk1.5-sun/_ commented out in the first line, modify it. Mine looks like this..
```

ubuntu% cat java_home
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.
/usr/lib/j2sdk1.5-sun/
#/usr/lib/jvm/java-gcj
#/usr/lib/kaffe/pthreads
#/usr/lib/sablevm
#/usr/lib/fjsdk
#/usr/lib/j2se/1.5
#/usr/lib/j2se/1.4
#/usr/lib/j2sdk1.5-ibm
#/usr/lib/j2sdk1.4-ibm
#/usr/lib/j2sdk1.5-sun
#/usr/lib/j2sdk1.4-sun

```
[/QUOTE]

hi!

I dont know what is wrong with me, but I dont have the j2sdk1.5, and I couldnt find it, so while I was searching I thought maybe JDK is the same thing as SDK?

so I changed it to */usr/lib/jvm/java-1.5.0-sun-1.5.0.06* instead and took away ubuntu% cat java_home because eclipse thinks it's a jvm.

I posted this, if someone like me couldn't find sdk1.5 just go to synaptic download sun-java5-jdk.

correct me if I am wrong, thnx again for your help, I finally solved my svn checkout problem by making eclipse go first to the right place... thnx again \\:D/

---

### Post by Cavalierski on 2006-06-05
[QUOTE=Kuraboy]I dont know what is wrong with me, but I dont have the j2sdk1.5, and I couldnt find it, so while I was searching I thought maybe JDK is the same thing as SDK?[/QUOTE]

Hi, regarding the naming of JDK and SDK, here is the brief explanation.
After the Java version 1.2, it is called **"Java 2 SDK"**. So the right name is **SDK**. However among the developer, it doesn't really matter as we understand what it is :D 



[QUOTE=Kuraboy]so I changed it to */usr/lib/jvm/java-1.5.0-sun-1.5.0.06* instead and took away ubuntu% cat java_home because eclipse thinks it's a jvm.

I posted this, if someone like me couldn't find sdk1.5 just go to synaptic download sun-java5-jdk.

correct me if I am wrong, thnx again for your help, I finally solved my svn checkout problem by making eclipse go first to the right place... thnx again \\:D/[/QUOTE]

As far as I see your package (sun-java5-jdk) , it also fine. The reason why you couldn't see my package is the difference of the /etc/apt/source.lst :-\" 

wonderring if you miss one of the following repos.

> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-[B]free 


In addition, if you continue please see [http://ubuntuforums.org/showthread.php?t=187739](http://ubuntuforums.org/showthread.php?t=187739) as I did a [/B]duplicate post..

---

