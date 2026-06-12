---
title: "sun java six plugin runescape?????"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by rhyswprice on 2008-07-30
ok im completely new to ubuntu i made a cheap gaming pc mainly for runescape high detail. i cannot seem to get runescape high detail to work with icedtea plugin...i saw on a forum somewhere to disable that and install sun java 6 plugin. the trouble is when i download sun java plugin i get the message error: wrong architecture i386 or something like that so i cant get on high detail which like i say is mainly why i built this pc. can anyone please help me to get this to work when i open runescape low detail i get on ok but only with unsigned applet. when i open high detail it says plugins required to display media. this is all very well but when i download/install the plugins (icedtea) i get an error saying that runescape cant save to cache. i have tried to no avail changing to unsigned applet and creating a dir manually for the cache and i have changed the permissions on this dir. nothing seems to work and when i change permissions on the folder and apply them it doesn't work and goes back to default :confused::confused::confused: im really stuck now please help!

---

### Post by LinuxRocks713 on 2008-07-31
Please post more clearly next time, with proper punctuation and spelling so that we can understand you better.

In response to your questions, to install Sun's Proprietary Java, execute the following:
```

sudo apt-get install sun-java6-bin

```

---

### Post by rhyswprice on 2008-08-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

thats what i get upon running executing that code but now i have a different error when i open runescap hd. any ideas or suggestions greatly appreciated i'l give more details on the new error asap.

edit: gcjwebplugin error: Failed to run /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/../../bin/pluginappletviewer.  For more detail rerun "firefox -g" in a terminal window.

that opens on a new window when i open rs hd.

---

### Post by tinny on 2008-08-01
Not sure what you might have done wrong. But to clean up and try again (the same way ive installed Java 6 on my machine).

Clean up
```

sudo apt-get remove --purge sun-java6*

```

To install the Sun Java 6 environment...

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

Then to check your install

```

java -version

```

If it all worked you should see something like this

```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

---

### Post by rhyswprice on 2008-08-08
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * j2re1.4
 * kaffe
 * cacao
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


thats what i get after following the instructions given :(

---

### Post by Thelasko on 2008-08-08
What architecture are you running? (32-bit or 64-bit) Also, it helps to remove icedtea after you install java6.  It's not supposed to make a difference, but I've heard it does.

---

### Post by tinny on 2008-08-08
> **rhyswprice said:**
> The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * j2re1.4
 * kaffe
 * cacao
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


thats what i get after following the instructions given :(


You ran these commands, right?

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

You may need to manually setup "java".

```

sudo update-alternatives --config java

```

try and select the "/usr/lib/jvm/java-6-sun/jre/bin/java" option, you should have it if you ran the first set of commands (eg. sudo apt-get install...)

---

### Post by bohica on 2008-08-09
```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

Unfortunately I get this. My pc is an AMD64 running hardy heron.

julian@williamstown:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by tinny on 2008-08-09
> **bohica said:**
> ```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

Unfortunately I get this. My pc is an AMD64 running hardy heron.

julian@williamstown:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

I just did some research and it appears that the sun-java6-plugin is not available for your architecture (AMD64 bit).

So it looks like you are out of luck :(

FYI: Here is the feature request for this package.
[https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

---

### Post by NewNerd99 on 2008-08-09
Thanks Thelasko on removing Icedtea. Did the trick in low detail. Checking HD now.

Cheers

---

### Post by waspbr on 2008-08-09
I had the same problem, but i am not sure what i did  exactly but now it sorta works... sound is still a problem tho...

I am running intrepid ibex, so it maybe a little different, but maybe the same package is in the hardy repos.

anyway I installed this package called cacao from synaptic. but haven't really selected it as my default java environment.

then I did 

```
sudo update-alternatives --config java
```

and these options came up

```
  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/cacao
```

long story short , I have open jdk, sun jre and cacao. Not sure which one is running the show on the runnescape thing but it should be the sun plugin. I did select it as the default jre when I ran the command above. 

well,  for the fullscreen, check the FAQ  of runnescape, search for linux... it maybe that it only works because it is running in intrepid, on the very least you can have some hope that it will run on the next distro...

---

### Post by starcannon on 2008-08-09
If your a college student that uses or will use Blackboard, DO NOT use sun-java-6, instead use sun-java 5, blackboard tests will crash on sun-java 6, if your lucky your professor will reset your test for you, if not... 
RunescapeHD and Classic both work fine with sun-java 5.

If you prefer a GUI for installing and uninstalling software be sure to look in:
System->Administration->Synaptic Package Manager
its a very nice gui that will help you accomplish the same tasks.

remove icedtea, its a pos, opensource does NOT equate higher quality. There is room enough in the linux boat for both closed and open sourced applications, use the ones that work.

That said, learning the cli is very advantageous, I generally use a combination of both gui, and cli to get the maximum benefit.

---

### Post by tinny on 2008-08-09
> **waspbr said:**
> I had the same problem, but i am not sure what i did  exactly but now it sorta works... sound is still a problem tho...

I am running intrepid ibex, so it maybe a little different, but maybe the same package is in the hardy repos.

anyway I installed this package called cacao from synaptic. but haven't really selected it as my default java environment.

then I did 

```
sudo update-alternatives --config java
```

and these options came up

```
  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/bin/cacao
```

long story short , I have open jdk, sun jre and cacao. Not sure which one is running the show on the runnescape thing but it should be the sun plugin. I did select it as the default jre when I ran the command above. 

well,  for the fullscreen, check the FAQ  of runnescape, search for linux... it maybe that it only works because it is running in intrepid, on the very least you can have some hope that it will run on the next distro...

Looks to me like your running OpenJDK as default and it works under intrepid, cool!

To know for sure what the default Java setup is:

```

java -version
javac- version

```

BTW: Intrepid doesnt have a 64bit version of sun-java6-plugin :(

---

### Post by bohica on 2008-08-09
> **tinny said:**
> I just did some research and it appears that the sun-java6-plugin is not available for your architecture (AMD64 bit).

So it looks like you are out of luck :(

FYI: Here is the feature request for this package.
[https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

Ah well sh*t happens. I am burning the i386 version at the moment. I gues I&#314;l upgrade when the AMD64 bit gets its own version of java plugins.

---

### Post by tinny on 2008-08-09
> **bohica said:**
> Ah well sh*t happens. I am burning the i386 version at the moment. I gues I&#314;l upgrade when the AMD64 bit gets its own version of java plugins.

Yeah good call. When I had a 64bit AMD I ran the i386 version of Ubuntu and it was fine.

64bit is over rated anyway

---

### Post by waspbr on 2008-08-13
I disagree, depending on what you use your pc for it is extremely handy  to use all of your 64 bit cpu power.


I can open blackboard without a hitch and I am on intrepid 64...

---

### Post by Thelasko on 2008-08-13
> **waspbr said:**
> I disagree, depending on what you use your pc for it is extremely handy  to use all of your 64 bit cpu power.


I can open blackboard without a hitch and I am on intrepid 64...

I hear the open Java works brilliantly in Intrepid.  I hope it get's backported to Hardy, I want to stay with the LTS for a while.  But if Intrepid is that much better...

---

### Post by tinny on 2008-08-13
> **waspbr said:**
> I disagree, depending on what you use your pc for it is extremely handy  to use all of your 64 bit cpu power.


I can open blackboard without a hitch and I am on intrepid 64...

In theory its great, but most software is not designed to make use of it. :(

---

### Post by Methuselah on 2008-08-13
> **tinny said:**
> In theory its great, but most software is not designed to make use of it. :(

Mostly the proprietary stuff unfortunately.
Open source can generally be rebuilt for amd64 and generally works.
In many cases you can run 32bit programs on 64bit OS but a browser plugin probably creates additional challenges.

---

### Post by Thelasko on 2008-08-13
> **tinny said:**
> In theory its great, but most software is not designed to make use of it. :(

I think your confusing [multi-core]("http://en.wikipedia.org/wiki/Amdahl%27s_law") with [64-bit]("http://en.wikipedia.org/wiki/X86-64#Operating_mode_explanation").

Multi-core software needs to be designed to run on multi-core hardware, or else it yields little to no speed increase.

64-bit systems simply need their software compiled on a 64-bit machine to achieve a speed increase.  Therefore, anything open source works great on a 64-bit system (like Linux) since it can be readily compiled on a 64-bit machine.

The only software that needs to be designed specially for 64-bit systems are the kernel and compilers.

---

