---
title: "Java &amp; JMF"
date: 2007-09-03
forum: Programming Talk
---

### Post by Qui on 2007-09-03
I have downloaded and Installed 

Java 1.6.0
JMF-2.1.1e

wrote a tiny application: A Media Player - it works flawlessly in windows - however, when i try to compile and run it in linux i get the following error after selecting a sample movie to play ("als.mpg"): 

Error: Unable to realize com.sun.media.codec.video.jmpx.Jmpx@1125127

i followed the instructions here:
[http://java.sun.com/products/java-media/jmf/2.1.1/setup-linux.html](http://java.sun.com/products/java-media/jmf/2.1.1/setup-linux.html)

nada; any suggestions will be appreciated, 
Qui

SYSTEM
--------------------------
Ubuntu 7.04 - Feisty Fawn (UP TO DATE)
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)
320GB HDD
3.2GHZ Celeron D
1 GB RAM
WIRELESS NETWK
BLAH! BLAH! BLAH!

---

### Post by Qui on 2007-09-03
solution, point to the JMF & use the export commands in the run file instead of the setenv: 

-----------------------------------------------------------------------------------

export JMFHOME=/opt/JMF-2.1.1e
export LD_LIBRARY_PATH=$JMFHOME/lib
export CLASSPATH=$JMFHOME/lib/jmf.jar

javac -classpath /opt/JMF-2.1.1e/lib/jmf.jar:. DVR.java
java -classpath /opt/JMF-2.1.1e/lib/jmf.jar:. DVR
-----------------------------------------------------------------------------------

---

### Post by forgewire on 2009-06-06
The solution is to use Windows because JMF doesn't work in 9.04 neither 8.04 with classpath set or without it:

Unable to realize com.sun.media.codec.video.jmpx.Jmpx@10655dd
Could not realize media player 
Error: Unable to realize com.sun.media.codec.video.jmpx.Jmpx@edc3a2
Could not realize media player

or:
Exception in thread "main" java.lang.NoClassDefFoundError: javax/media/NoPlayerException
at MediaTest.main
- is the best you can get out of it.):P

tail /etc/profile :

export JAVA_HOME=/home/demon/bin/jdk1.6.0_14
export PATH=$PATH:/home/demon/bin/jdk1.6.0_14/bin
export PATH=$PATH:.:/home/demon/bin/jdk1.6.0_14/jre/lib
export JAVA_PATH=/home/demon/bin/jdk1.6.0_14/bin
export JMFHOME=/home/demon/bin/JMF-2.1.1e
export JRE_HOME=/home/demon/bin/jdk1.6.0_14/jre
export CLASSPATH=$JMFHOME/lib/jmf.jar:.:
export LD_LIBRARY_PATH=$JMFHOME/lib:$LD_LIBRARY_PATH

But it work flawlessly on Windoze (the same code).

Correct me if I wrong and good luck with it

---

### Post by forgewire on 2009-06-11
I've just  sorted the problem by installing JMF from a source code.

---

### Post by johnrz86 on 2009-07-11
On Ubuntu 9.04, I solved this problem by copying all the *.so files from $JMFHOME/lib into /usr/lib. Not the cleanest solution I admit, but I needed it to work urgently.

---

### Post by froggyswamp on 2009-07-11
I'm impressed that people (are trying to) use JMF. Last time I checked it it was criticized for being buggy and cumbersome, those who are using it could comment on it please?

---

### Post by RevNomad on 2009-08-12
I have tried installing JMF several times for use with Impress. The two have never worked. I'm not a programmer nor am I a computer professional. Is there any simple way to install JMF and have it work with Openoffice.org?

---

### Post by Drone022 on 2009-08-13
I tried to use JMF in a project for university, it was horrible to use. Tons of bugs, not much support as far as I remember, is it still being maintained? I would advise against using it for anything important.

I ditched it completely in favour of writing a video player myself from scratch. Im surprised anyone uses it.

---

### Post by Drone022 on 2009-08-13
oh, this is from 2007. I was wondering why it had so many views yet so little posts.

---

### Post by RevNomad on 2009-08-13
> **Drone022 said:**
> oh, this is from 2007. I was wondering why it had so many views yet so little posts.

Because it is still an issue. I want to add audio and video to Impress presentations but cannot because (I'm told) OO.org needs JMF to run media. I would love a better solution.
NTP

---

### Post by udippel on 2009-11-10
> **RevNomad said:**
> I would love a better solution.
NTP

We all love a better solution. After fiddling with that silly JMF on Ubuntu, I found it.
sudo apt-get install ubuntu-restricted-extras
and here I can drop any media into a slide and - voilà - it works.

You see if it works easily: When you get some 'audio-ear', it won't. After the install, the media are replaced with a '?' in the slide, and then it works perfectly well.

---

