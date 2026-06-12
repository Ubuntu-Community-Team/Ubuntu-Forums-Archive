---
title: "Unable to install java plugin on firefox"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by kranthi117 on 2014-05-20
Hi All,

I have Ubuntu 14.04 64 bit. I've installed 32 bit jre
I get the following responses

$ which java
/opt/jre/jre32/jre1.7.0/bin/java
$ java -version
java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
Java HotSpot(TM) Server VM (build 21.0-b17, mixed mode)
$ ls -lA /usr/lib/mozilla/plugins/libjavaplugin.so 
lrwxrwxrwx 1 root root 44 May 20 18:09 /usr/lib/mozilla/plugins/libjavaplugin.so -> /opt/jre/jre32/jre1.7.0/lib/i386/libnpjp2.so

I've restarted my comuter but still about:plugis does not list my java plugin. Am I missing something obvious ? please advice.

---

### Post by sandyd on 2014-05-20
Firefox in Ubuntu 14.04 is 64bit.

Here are instructions to install java for firefox (64bit)
[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

It might be a good idea to remove the currrent plugin you have installed beforehand.

---

### Post by a_boilermaker on 2014-10-22
> **sandyd said:**
> Firefox in Ubuntu 14.04 is 64bit.

Here are instructions to install java for firefox (64bit)
[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

It might be a good idea to remove the currrent plugin you have installed beforehand.


sandyd,

THANK YOU MILLIONS FOR POSTING THIS LINK!
You're a saint.   I've been pounding my head against the wall so long I almost forgot what sent me on the mission to enable Java in the first place today.
I followed your link, cut and pasted the commands from the first two pink terminal windows, then skipped down to "Setting the Java environment variables" entered that command.  And behold, Java is now included in my Firefox browser Menu>Tools>Add-ons List.
I believe running the commands removed the generic Java install I'd attempted via. another wrong directive before I found your's.
I tried to follow the worthless (IMO) Oracle guide [http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395) & a number of different program installs from the ubuntu software center, but ubuntu 14.04 was unrelenting--it refused me administration permissions as the owner & one and only user.  I couldn't get around & kept slamming me.  I still don't understand how to get around the user permissions issue, but that's to master another day very soon.
Finally, something to smile about.

---

