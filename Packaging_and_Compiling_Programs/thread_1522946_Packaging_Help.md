---
title: "Packaging Help"
date: 2010-07-02
forum: Packaging and Compiling Programs
---

### Post by Tak11 on 2010-07-02
I'm packaging a java application I've been working on.

[https://edge.launchpad.net/jhippo]("https://edge.launchpad.net/jhippo")

I'm using jh_makepkg from javahelper, and edited my configuration files to what I thought was correct.

**debian/control**
```

Source: jhippo
Section: misc
Priority: optional
Maintainer: tak <tak.31337@gmail.com>
Build-Depends: debhelper (>> 7), javahelper (>= 0.24) 
Build-Depends-Indep: default-jdk
Standards-Version: 3.8.1
Homepage: https://edge.launchpad.net/jhippo

Package: jhippo
Architecture: all
Depends: ${java:Depends}, ${misc:Depends}
Description: Dynamic modular Java IRC bot, built on the pircbot api. 
     it has a lot of built in functionality (flood protection, in chat google searching etc.)
     and is easily extended.

```

**debian/rules**
```

#!/usr/bin/make -f

export JAVA_HOME=/usr/lib/jvm/default-java

# Put depended upon jars in here
# export CLASSPATH=

%:
	dh --with javahelper $@

```

**debian/jhippo.install**
```

jhippo.jar usr/share/jhippo
lib/pircbot.jar usr/share/jhippo

```

**debian/jhippo.links**
```

usr/share/jhippo/jhippo.jar usr/bin/jhippo

```

**debian/javabuild**
```

JAVA_HOME=/usr/lib/jvm/default-java
CLASSPATH=lib/pircbot.jar
jh_build jhippo.jar src

```

**debian/jhippo.manifest**
```

usr/share/jhippo/jhippo.jar:
 Main-Class: jhippo.Main
 Class-Path: lib/pircbot.jar
 Debian-Java-Home: /usr/lib/jvm/default-java

```

---

### Post by Tak11 on 2010-07-08
bump, anyone? I'm still blocked by this

---

### Post by SevenMachines on 2010-07-09
hi, what exactly is the problem you're having? If you attach your debian directory or have a ppa thats good too

---

### Post by Tak11 on 2010-07-09
> **SevenMachines said:**
> hi, what exactly is the problem you're having? If you attach your debian directory or have a ppa thats good too

oh sorry, I forgot to post that :P 

cp: cannot stat `debian/tmp/jhippo.jar': No such file or directory
dh_install: cp -a debian/tmp/jhippo.jar debian/jhippo/usr/share/jhippo/ returned exit code 1

---

### Post by Tak11 on 2010-07-09
[http://www.2shared.com/file/Yo8aReYk/debian.html](http://www.2shared.com/file/Yo8aReYk/debian.html)

this is my debian file (7zip compressed)

---

### Post by SevenMachines on 2010-07-10
using lp:jhippo i dont get any build at all, some sort of problem finding lib/pircbot.jar in the CLASSPATH i imagine. i'll try and look at it properly after the weekend but i've really not much of a clue when it comes to ant builds. 
```
jhippo-1.0$ debuild -b -us -uc
 dpkg-buildpackage -rfakeroot -D -us -uc -b
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package jhippo
dpkg-buildpackage: source version 2.0.31-0ubuntu1
dpkg-buildpackage: source changed by Lance Colton <tak.31337@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh --with javahelper clean
   dh_testdir
   dh_auto_clean
Buildfile: build.xml

-pre-init:

-init-private:

-init-user:

-init-project:

-init-macrodef-property:

-do-init:

-post-init:

-init-check:

-init-macrodef-javac:

-init-macrodef-junit:

-init-debug-args:

-init-macrodef-nbjpda:

-init-macrodef-debug:

-init-macrodef-java:

-init-presetdef-jar:

init:

-deps-clean-init:
   [delete] Deleting: /home/niall/Desktop/temp/jhippo-1.0/build/built-clean.properties

deps-clean:

-warn-already-built-clean:
[propertyfile] Updating property file: /home/niall/Desktop/temp/jhippo-1.0/build/built-clean.properties

-do-clean:
   [delete] Deleting directory /home/niall/Desktop/temp/jhippo-1.0/build

-post-clean:

clean:

BUILD SUCCESSFUL
Total time: 1 second
   dh_clean
   jh_clean
 debian/rules build
dh --with javahelper build
   dh_testdir
   dh_auto_configure
   jh_linkjars
   dh_auto_build
Buildfile: build.xml

-pre-init:

-init-private:

-init-user:

-init-project:

-init-macrodef-property:

-do-init:

-post-init:

-init-check:

-init-macrodef-javac:

-init-macrodef-junit:

-init-debug-args:

-init-macrodef-nbjpda:

-init-macrodef-debug:

-init-macrodef-java:

-init-presetdef-jar:

init:

-deps-jar-init:

deps-jar:
    [mkdir] Created dir: /home/niall/Desktop/temp/jhippo-1.0/build

-warn-already-built-jar:
[propertyfile] Updating property file: /home/niall/Desktop/temp/jhippo-1.0/build/built-jar.properties

-check-automatic-build:

-clean-after-automatic-build:

-verify-automatic-build:

-pre-pre-compile:
    [mkdir] Created dir: /home/niall/Desktop/temp/jhippo-1.0/build/classes

-pre-compile:

-compile-depend:

-do-compile:
    [mkdir] Created dir: /home/niall/Desktop/temp/jhippo-1.0/build/empty
    [javac] Compiling 29 source files to /home/niall/Desktop/temp/jhippo-1.0/build/classes
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:32: package org.jibble.pircbot does not exist
    [javac] import org.jibble.pircbot.IrcException;
    [javac]                          ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:34: package org.jibble.pircbot does not exist
    [javac] import org.jibble.pircbot.PircBot;
    [javac]                          ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:40: cannot find symbol
    [javac] symbol: class PircBot
    [javac] public class JHippo extends PircBot {
    [javac]                             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:30: package org.jibble.pircbot does not exist
    [javac] import org.jibble.pircbot.User;
    [javac]                          ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:68: cannot find symbol
    [javac] symbol  : method setName(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]         this.setName(properties.getProperty("nick"));
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:69: cannot find symbol
    [javac] symbol  : method setVersion(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]         this.setVersion("JHippo v2.0a");
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:70: cannot find symbol
    [javac] symbol  : method setVerbose(boolean)
    [javac] location: class jhippo.JHippo
    [javac]         this.setVerbose(true);
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:71: cannot find symbol
    [javac] symbol  : method setAutoNickChange(boolean)
    [javac] location: class jhippo.JHippo
    [javac]         this.setAutoNickChange(true);
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:72: cannot find symbol
    [javac] symbol  : method setLogin(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]         this.setLogin("JHippo");
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:78: method does not override or implement a method from a supertype
    [javac]     @Override
    [javac]     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:89: method does not override or implement a method from a supertype
    [javac]     @Override
    [javac]     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:101: cannot find symbol
    [javac] symbol  : method reconnect()
    [javac] location: class jhippo.JHippo
    [javac]             reconnect();
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:104: cannot find symbol
    [javac] symbol  : class IrcException
    [javac] location: class jhippo.JHippo
    [javac]         } catch (IrcException ex) {
    [javac]                  ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:98: method does not override or implement a method from a supertype
    [javac]     @Override
    [javac]     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:113: cannot find symbol
    [javac] symbol  : method getName()
    [javac] location: class jhippo.JHippo
    [javac]         if (recipientNick.equals(Main.bot.getName())) {
    [javac]                                          ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:114: cannot find symbol
    [javac] symbol  : method joinChannel(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.joinChannel(channel);
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:120: cannot find symbol
    [javac] symbol  : method ban(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.ban(channel, kickerNick);
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:121: cannot find symbol
    [javac] symbol  : method kick(java.lang.String,java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.kick(channel, kickerNick, "Beware. I am a robot");
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/JHippo.java:109: method does not override or implement a method from a supertype
    [javac]     @Override
    [javac]     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/Main.java:127: cannot find symbol
    [javac] symbol  : method connect(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]         bot.connect(properties.getProperty("server"));
    [javac]            ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/Main.java:129: cannot find symbol
    [javac] symbol  : method identify(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             bot.identify(properties.getProperty("password"));
    [javac]                ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/Main.java:131: cannot find symbol
    [javac] symbol  : method joinChannel(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]         bot.joinChannel(properties.getProperty("channel"));
    [javac]            ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Authentication/Access.java:75: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(bot.getChannel(), "access level changed");
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Authentication/Login.java:77: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(bot.getPrivateSender(),
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Authentication/Login.java:81: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(bot.getPrivateSender(),
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Authentication/Register.java:100: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(bot.getPrivateSender(),
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Crypto.java:61: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(sendTo, encryptor.hashData(parameters.getBytes()));
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Crypto.java:63: cannot find symbol
    [javac] symbol  : method sendAction(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendAction(sendTo, "Could not encrypt.");
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/FloodProtection.java:62: cannot find symbol
    [javac] symbol  : method kick(java.lang.String,java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.kick(bot.getChannel(), this.sender, new StringBuilder().append("Flood Detected over span of : ").append(df.format(difference)).toString());
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Google.java:99: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(channel, " Results:");
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Google.java:101: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(channel, (i+1) + ". ");
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Google.java:103: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(channel, j.getString("titleNoFormatting"));
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Google.java:104: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(channel, j.getString("url"));
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Google.java:108: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "Could not complete search request..");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:45: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "   Registration: \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:46: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!register *password* \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:47: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!login    *password* \n\n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:48: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, " ");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:50: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "Normal commands: \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:51: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!md5      *string to encrypt* \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:52: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!google   *string to search* \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:53: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!say      *send to* *message*         (rq. access lvl 2) \n\n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:54: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, " ");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:56: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "   Oper commands: \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:57: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!kick   *person*                      (rq. access lvl 1) \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:58: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!join   *channel*                     (rq. access lvl 3) \n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:59: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!quit   *channel* *reason*            (rq. access lvl 3)\n");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Help.java:60: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]               Main.bot.sendMessage(channel, "!access *person* *new access level*   (rq. access lvl 4)");
    [javac]                       ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Join.java:54: cannot find symbol
    [javac] symbol  : method joinChannel(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.joinChannel(channel, (String) tokenParameters.nextElement());
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Join.java:56: cannot find symbol
    [javac] symbol  : method joinChannel(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.joinChannel(channel);
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:61: cannot find symbol
    [javac] symbol  : class User
    [javac] location: class jhippo.functions.Kick
    [javac]             User[] users = Main.bot.getUsers(channel);
    [javac]             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:61: cannot find symbol
    [javac] symbol  : method getUsers(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             User[] users = Main.bot.getUsers(channel);
    [javac]                                    ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:66: cannot find symbol
    [javac] symbol  : class User
    [javac] location: class jhippo.functions.Kick
    [javac]             for (User user : users) {
    [javac]                  ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:73: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(channel, totalUsers);
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:74: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(channel, "A vote was called (!vote y, or !vote n): [" + voteRequired + "/" + userCount + "]");
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:81: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(channel, "yes: " + Vote.voteYes + " no: " + Vote.voteNo);
    [javac]                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:84: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(channel, "Vote failed.");
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Kick.java:87: cannot find symbol
    [javac] symbol  : method kick(java.lang.String,java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.kick(channel, parameters, "vote success.");
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Quit.java:51: cannot find symbol
    [javac] symbol  : method quitServer(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.quitServer("Mission Complete");
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Quit.java:54: cannot find symbol
    [javac] symbol  : method quitServer(java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.quitServer(parameters);
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/functions/Say.java:58: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]                 Main.bot.sendMessage(sendTo,
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONArray.java:122: warning: [unchecked] unchecked call to add(E) as a member of the raw type java.util.ArrayList
    [javac]                 this.myArrayList.add(null);
    [javac]                                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONArray.java:125: warning: [unchecked] unchecked call to add(E) as a member of the raw type java.util.ArrayList
    [javac]                 this.myArrayList.add(x.nextValue());
    [javac]                                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONArray.java:171: warning: [unchecked] unchecked call to add(E) as a member of the raw type java.util.ArrayList
    [javac]                 this.myArrayList.add(JSONObject.wrap(o));  
    [javac]                                     ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONArray.java:644: warning: [unchecked] unchecked call to add(E) as a member of the raw type java.util.ArrayList
    [javac]         this.myArrayList.add(value);
    [javac]                             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONArray.java:758: warning: [unchecked] unchecked call to set(int,E) as a member of the raw type java.util.ArrayList
    [javac]             this.myArrayList.set(index, value);
    [javac]                                 ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONObject.java:245: warning: [unchecked] unchecked call to put(K,V) as a member of the raw type java.util.Map
    [javac]                 this.map.put(e.getKey(), wrap(e.getValue()));
    [javac]                             ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONObject.java:939: warning: [unchecked] unchecked call to put(K,V) as a member of the raw type java.util.Map
    [javac]                         map.put(key, wrap(result));
    [javac]                                ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONObject.java:1049: warning: [unchecked] unchecked call to put(K,V) as a member of the raw type java.util.Map
    [javac]             this.map.put(key, value);
    [javac]                         ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/JSONObject.java:1177: warning: [unchecked] unchecked call to TreeSet(java.util.Collection<? extends E>) as a member of the raw type java.util.TreeSet
    [javac]       return new TreeSet(this.map.keySet()).iterator();
    [javac]              ^
    [javac] /home/niall/Desktop/temp/jhippo-1.0/src/jhippo/util/Vote.java:79: cannot find symbol
    [javac] symbol  : method sendMessage(java.lang.String,java.lang.String)
    [javac] location: class jhippo.JHippo
    [javac]             Main.bot.sendMessage(this.channel, voteYes + " " + voteNo);
    [javac]                     ^
    [javac] 62 errors
    [javac] 9 warnings

BUILD FAILED
/home/niall/Desktop/temp/jhippo-1.0/nbproject/build-impl.xml:413: The following error occurred while executing this line:
/home/niall/Desktop/temp/jhippo-1.0/nbproject/build-impl.xml:199: Compile failed; see the compiler error output for details.

Total time: 3 seconds
dh_auto_build: ant returned exit code 1
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1340:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

```

---

### Post by SevenMachines on 2010-07-10
sorry, how very saturday morning of me :) i've added pircbot.jar to the ant build. the problem is with your paths in the install file and so on. note the diference between relative paths and system install paths, the system paths need a leading /. so for example, to install mybin in your source root directory to /usr/bin you would have an install file like

mybin   /usr/bin

not 
mybin usr/bin


the below works (to build the deb anyway) itll need something more to actually run properly i think, a script in /usr/bin rather than a link maybe?

debian/jhippo.install:
> dist/JHippo.jar /usr/share/jhippo
lib/pircbot.jar /usr/share/jhippo
debian/jhippo.manifest:

> /usr/share/jhippo/JHippo.jar:
 Main-Class: jhippo.Main
 Class-Path: lib/pircbot.jar
 Debian-Java-Home: /usr/lib/jvm/default-java
debian/jhippo.links:
> /usr/share/jhippo/JHippo.jar /usr/bin/jhippo


[EDIT] Note that JHippo.jar is build by default in dist/ and has upper case letters too

---

### Post by Tak11 on 2010-07-10
Thank you sooooooo much!!!!

is there a way to launch jhippo and immediately return to the terminal with a bash script. (similar to launching firefox from bash)

---

### Post by Tak11 on 2010-10-29
I wrote a guide for packaging java applications into a debian format here:

[http://tak11.info/?p=20](http://tak11.info/?p=20)

---

