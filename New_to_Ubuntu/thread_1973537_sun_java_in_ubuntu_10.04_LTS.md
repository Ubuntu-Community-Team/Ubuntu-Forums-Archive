---
title: "sun java in ubuntu 10.04 LTS"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by idom on 2012-05-04
I am trying to install sun java in ubuntu 10.04 LTS

I am following instructions from 
[https://help.ubuntu.com/community/Java#Manual_method](https://help.ubuntu.com/community/Java#Manual_method)

 $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin)
 $ chmod u+x jre-6u31-linux-i586.bin
 $ ./jre-6u31-linux-i586.bin
 $ mv jre1.6.0_31 /usr/lib/jvm/
 $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_31/bin/java" 1
 $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jre1.6.0_31/lib/i386/libnpjp2.so" 1

when I do 

log is attahced. 


idom-desktop:~> wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin)
--2012-05-05 08:57:40--  [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin)
Resolving download.oracle.com... 122.178.225.26, 122.178.225.56
Connecting to download.oracle.com|122.178.225.26|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](https://edelivery.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin) [following]
--2012-05-05 08:57:40--  [https://edelivery.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](https://edelivery.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin)
Resolving edelivery.oracle.com... 184.84.202.174
Connecting to edelivery.oracle.com|184.84.202.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-05-05 08:57:42--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com|122.178.225.26|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `jre-6u31-linux-i586.bin'

100%[===================================================================================================================================================================================================>] 5,307       --.-K/s   in 0.01s   

2012-05-05 08:57:42 (358 KB/s) - `jre-6u31-linux-i586.bin' saved [5307/5307]

idom-desktop:~> chmod u+x jre-6u31-linux-i586.bin
idom-desktop:~> ./jre-6u31-linux-i586.bin
./jre-6u31-linux-i586.bin: 1: cannot open html: No such file
./jre-6u31-linux-i586.bin: 2: cannot open head: No such file
./jre-6u31-linux-i586.bin: 3: cannot open title: No such file
./jre-6u31-linux-i586.bin: 3: Request: not found
./jre-6u31-linux-i586.bin: 4: cannot open META: No such file
./jre-6u31-linux-i586.bin: 5: cannot open link: No such file
./jre-6u31-linux-i586.bin: 6: cannot open link: No such file
: not foundlinux-i586.bin: 7: 
./jre-6u31-linux-i586.bin: 8: cannot open body: No such file
./jre-6u31-linux-i586.bin: 9: cannot open div: No such file
./jre-6u31-linux-i586.bin: 10: cannot open table: No such file
./jre-6u31-linux-i586.bin: 11: cannot open tr: No such file
./jre-6u31-linux-i586.bin: 12: Syntax error: redirection unexpected

Please help.

Regards,
idom

---

### Post by jtarin on 2012-05-04
Your trying to execute ./jre-6u31-linux-i586.bin in a location where it is not.

---

### Post by PivotalEpiphany on 2012-05-05
If you open Synaptic Package manager, type in the Search field *Sun Java.* You'll see the common files + extras.

Hope this helps.

---

### Post by idom on 2012-05-05
> **jtarin said:**
> Your trying to execute ./jre-6u31-linux-i586.bin in a location where it is not.

that does not seem to be case. 
idom-desktop:~> ls -al ./jre-6u31-linux-i586.bin
-rwxr--r-- 1 idom idom 5307 2012-03-21 02:52 ./jre-6u31-linux-i586.bin

---

### Post by idom on 2012-05-05
> **FetalVivisection said:**
> If you open Synaptic Package manager, type in the Search field *Sun Java.* You'll see the common files + extras.

Hope this helps.

I don't see extras I just see common and I installed it now what do i need to do to use this?

---

### Post by GreenWhite on 2012-05-05
For me, the easiest way is to manually install.

To get started, press Ctrl – Alt T. Remove all other installations of OpenJDK from your system.

sudo apt-get purge openjdk*

 

After that, go and download Java JRE package from [http://www.oracle.com/technetwork/java/javase/downloads/jre-7u4-download-1591157.html](http://www.oracle.com/technetwork/java/javase/downloads/jre-7u4-download-1591157.html)

When prompted, save the download. Please select the 32 or 64 bit .tar.gz version file from the list.

then extract the java packages you downloaded.

tar -xvf ~/Downloads/jre-7u4-linux-i586.tar.gz

 

Next, create your java 7 folder by running the commands below.

sudo mkdir -p /usr/lib/jvm/jre1.7.0

  

Then move all the extracted files and folders into the java 7 folder.

sudo mv jre1.7.0_04/* /usr/lib/jvm/jre1.7.0/

 

Next, run the commands below to install / update java 7

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre1.7.0/jre1.7.0_04/bin/java 0


 

Next, create a plugin folder in your home directory by running the commands below.

mkdir ~/.mozilla/plugins 

  

Finally, link the java plugin to your profile.

ln -s /usr/lib/jvm/jre1.7.0/jre1.7.0_04/lib/i386/libnpjp2.so ~/.mozilla/plugins/

 

That’s it.


 

If your system profile is AMD64, then link java to your profile by running the commands below.

ln -s /usr/lib/jvm/jre1.7.0/lib/amd64/libnpjp2.so ~/.mozilla/plugins/



Removal/Updates


Removal is easy. Manually delete the ln file in .mozilla plugins and also the usr/lib/jvm/jre1.7.0/*

Repeat the steps with the new file (executable)

Note: Upon executing the first command, you will receive an error. Execute it again to proceed with the new install.

---

### Post by Cheesemill on 2012-05-05
> **Porkyrider said:**
> If you open Synaptic Package manager, type in the Search field *Sun Java.* You'll see the common files + extras.[IMG]<snip>[/IMG]
No you wont.
It's been removed from the repositories for legal reasons.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Cheesemill on 2012-05-05
If you dont mind using Oracle Java 7 it can be installed by doing:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by idom on 2012-05-05
It works. 

Thanks a lot. 

Regards,
idom

> **GreenWhite said:**
> For me, the easiest way is to manually install.

To get started, press Ctrl – Alt T. Remove all other installations of OpenJDK from your system.

sudo apt-get purge openjdk*

 

After that, go and download Java JRE package from [http://www.oracle.com/technetwork/java/javase/downloads/jre-7u4-download-1591157.html](http://www.oracle.com/technetwork/java/javase/downloads/jre-7u4-download-1591157.html)

When prompted, save the download. Please select the 32 or 64 bit .tar.gz version file from the list.

then extract the java packages you downloaded.

tar -xvf ~/Downloads/jre-7u4-linux-i586.tar.gz

 

Next, create your java 7 folder by running the commands below.

sudo mkdir -p /usr/lib/jvm/jre1.7.0

  

Then move all the extracted files and folders into the java 7 folder.

sudo mv jre1.7.0_04/* /usr/lib/jvm/jre1.7.0/

 

Next, run the commands below to install / update java 7

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jre1.7.0/jre1.7.0_04/bin/java 0


 

Next, create a plugin folder in your home directory by running the commands below.

mkdir ~/.mozilla/plugins 

  

Finally, link the java plugin to your profile.

ln -s /usr/lib/jvm/jre1.7.0/jre1.7.0_04/lib/i386/libnpjp2.so ~/.mozilla/plugins/

 

That’s it.


 

If your system profile is AMD64, then link java to your profile by running the commands below.

ln -s /usr/lib/jvm/jre1.7.0/lib/amd64/libnpjp2.so ~/.mozilla/plugins/



Removal/Updates


Removal is easy. Manually delete the ln file in .mozilla plugins and also the usr/lib/jvm/jre1.7.0/*

Repeat the steps with the new file (executable)

Note: Upon executing the first command, you will receive an error. Execute it again to proceed with the new install.

---

