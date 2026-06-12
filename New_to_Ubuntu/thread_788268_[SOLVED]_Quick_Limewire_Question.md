---
title: "[SOLVED] Quick Limewire Question"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-05-09
If I use Limewire in my system will it garbage it up as it did with Windows?  I believe Ubuntu isn't as prone to the malware and spyware crap like M$ Windows but want to make sure first.

---

### Post by Bigtime_Scrub on 2008-05-09
I dont even think Linewire works with Linux. If it did I dont think you'd have any problems though.

---

### Post by drrwhistle3 on 2008-05-09
It says that download is available for Debian/ Ubuntu.

---

### Post by SunnyRabbiera on 2008-05-09
Yeh it works, but frostwire might be better.
[frostwire]("http://www.frostwire.com/")
Frostwire is identical to limewire and is based around the same code.
I would not worry about malware, as long as you are careful you should be fine.

---

### Post by Bigtime_Scrub on 2008-05-09
> **drrwhistle3 said:**
> It says that download is available for Debian/ Ubuntu.

Thats cool I didnt know that. I would still think you'd be ok. Most of the stuff that slows down PCs like spyware, viruses, trojans, worms, etc. are designed for Windows and Linux computers are largely immune.

---

### Post by tjwoosta on 2008-05-09
i use limewire, the deb packge from limewire.com works fine on ubuntu

i havnt had any problems whasoever

and about all the crap, your probably not going to get any because about 90% of viruses are simply incompatible with linux

i would however use caution when exchanging files with windows machines

---

### Post by kamitsukai on 2008-05-09
+1 for frostwire it has the same features of limewire pro for free! and it also comes with chat built in

---

### Post by Six_Digits on 2008-05-09
Frostwire works great! :)

---

### Post by tjwoosta on 2008-05-09
how do i make frostwire work?

i downloaded the .deb from the link above and it says it has a problem with my java (limewire works fine)

this is my error
```

tj@tj-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f1024749755, pid=17711, tid=1093491024
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid17711.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 17711 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

tj@tj-laptop:~$ 


```

---

### Post by rywibr on 2008-05-09
yeah, I definately suggest frostwire over limewire. mainly because:

Its better.

yeah, its that simple, it's just like limewire pro, but free, I've been using it for months and my PC is still functioning great:)

-ryan


> **tjwoosta said:**
> 
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)


weird...

---

### Post by SunnyRabbiera on 2008-05-09
ah you are running a 64bit computer... that kind of complicates things.

---

### Post by kamitsukai on 2008-05-09
I'm so glad i chose 32bit :)

---

### Post by IHATEDLINK on 2008-05-09
> **drrwhistle3 said:**
> If I use Limewire in my system will it garbage it up as it did with Windows?  I believe Ubuntu isn't as prone to the malware and spyware crap like M$ Windows but want to make sure first.

Don't use Limewire or frostwire or any kind of software that finish with wire
I know they works on Linux but they aren't a native application and they suck.
Why don't you use aMule? It's more secure, it's native, and it has a fun icon.

---

### Post by kamitsukai on 2008-05-09
amule? i hope your joking...please tell me your joking!

---

### Post by tjwoosta on 2008-05-09
> ah you are running a 64bit computer... that kind of complicates things.

yea i should have gone with 32bit, but is there a way i can make frostwire work anyway?

---

### Post by IHATEDLINK on 2008-05-09
> **kamitsukai said:**
> amule? i hope your joking...please tell me your joking!

I`m not. why? I've been using it for a while now and it works great.

---

### Post by Bigtime_Scrub on 2008-05-09
> **tjwoosta said:**
> yea i should have gone with 32bit, but is there a way i can make frostwire work anyway?

I think its prolly a java problem.

Try this:


sudo ln -s /usr/local/java /usr/java

---

### Post by tjwoosta on 2008-05-09
> 
I think its prolly a java problem.

Try this:


sudo ln -s /usr/local/java /usr/java 


i know its a java problem, but why is limewire working but frostwires not?

i tried making the link like you said but i still get the same error as before

any other ideas?

---

### Post by shifty_powers on 2008-05-09
> **ExpertAnalysis said:**
> You nor anyone here should be using Limewire because we all know precisely what you are trying to accomplish.  Stop using it!  This whole thread should be repoted to the RIAA for supporting this type of behaviour.

i'm assuming that's some kind of sarcasm....

anyways, wine, utorrent and the pirate bay ftw ;)

---

### Post by Bigtime_Scrub on 2008-05-09
> **ExpertAnalysis said:**
> You nor anyone here should be using Limewire because we all know precisely what you are trying to accomplish.  Stop using it!  This whole thread should be repoted to the RIAA for supporting this type of behaviour.

You dont know that. You are making lots of assumptions. 

Besides the government doesnt need people reporting other people to them, they have a decent big brother system already. Dont help them do their jobs.

---

### Post by shifty_powers on 2008-05-09
> **ExpertAnalysis said:**
> It's not sarcasm.  It's REALLY OBVIOUS you aren't using the file transfers for legitimate purposes so STOP TRYING TO FAKE IT.  YOU DO NOT FOOL ANYONE.  I work for an ISP and I'm sick and tired of trying to track down people that are clogging up the internet tubes with useless junk.

pfft.

get of your high horse for a minute and take your head out of your ***.

firstly, who the hell are you to assume what I or anyone else is doing with THEIR internet connections. I use utorrent for mainly linux, as i love playing around with different distros. (amongst other legitimate purposes).

And you know what? if you're sick of it, go and find another job. don't condemn people who you know nothing about. nothing like internet anonymity to bring out the troll in people ;) I'm not even going to get into the whole riaa argument, the organisation is frankly a joke and the less said about them the better.

have a nice day ;)

---

### Post by Steveway on 2008-05-09
> **ExpertAnalysis said:**
> It's not sarcasm.  It's REALLY OBVIOUS you aren't using the file transfers for legitimate purposes so STOP TRYING TO FAKE IT.  YOU DO NOT FOOL ANYONE.  I work for an ISP and I'm sick and tired of trying to track down people that are clogging up the internet tubes with useless junk.

Internet tubes? Dude you're spending way too much time on the computer.
Go take a rest outside, it's almost summer.

---

### Post by fatality_uk on 2008-05-09
> **ExpertAnalysis said:**
> It's not sarcasm.  It's REALLY OBVIOUS you aren't using the file transfers for legitimate purposes so STOP TRYING TO FAKE IT.  YOU DO NOT FOOL ANYONE.  I work for an ISP and I'm sick and tired of trying to track down people that are clogging up the internet tubes with useless junk.

Please tell me which ISP you work for. I mean tubes. Not just CABLES but TUBES. You must be running at LEAST 1000MB/s with TUBES :) :KS

---

### Post by Bigtime_Scrub on 2008-05-09
Ok I got one more trick for you to try and then Im out of ideas.

Code:
sudo apt-get install j2er1.4


Save the file to your desktop.
Open a terminal and copy/paste in the following two lines.

Code:

cd ~/Desktop
sudo dpkg --force-architecture -i FrostWire-4.10.9-2.i586.deb

Also, you can try to find j2re1.4 in synaptic.

---

### Post by tjwoosta on 2008-05-09
> 
It's not sarcasm. It's REALLY OBVIOUS you aren't using the file transfers for legitimate purposes so STOP TRYING TO FAKE IT. YOU DO NOT FOOL ANYONE. I work for an ISP and I'm sick and tired of trying to track down people that are clogging up the internet tubes with useless junk.


shut the hell up

you are really getting on my nerves

you are the one clogging up this forum with junk, i am on the verge of reporting you

the last theread i was in you were advising someone that they should reinstall ubuntu every week 

you dont know what your talking about and your giving people answeres like "do a clean install" for every simple problem people have




> Ok I got one more trick for you to try and then Im out of ideas.

Code:
sudoOk I got one more trick for you to try and then Im out of ideas.

Code:
sudo apt-get install j2er1.4


Save the file to your desktop.
Open a terminal and copy/paste in the following two lines.

Code:

cd ~/Desktop
sudo dpkg --force-architecture -i FrostWire-4.10.9-2.i586.deb

Also, you can try to find j2re1.4 in synaptic.

Save the file to your desktop.
Open a terminal and copy/paste in the following two lines.

Code:

cd ~/Desktop
sudo dpkg --force-architecture -i FrostWire-4.10.9-2.i586.deb

Also, you can try to find j2re1.4 in synaptic.


thanks for trying but apt-get install j2er1.4  says package not found

and i searched for j2re1.4 and jre1.4 and j2er1.4 and i just cant find the package you are telling me to install

---

### Post by WBL on 2008-05-09
> **tjwoosta said:**
> how do i make frostwire work?

i downloaded the .deb from the link above and it says it has a problem with my java (limewire works fine)

this is my error
```

tj@tj-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f1024749755, pid=17711, tid=1093491024
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid17711.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 17711 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

tj@tj-laptop:~$ 


```

You need to install java.  I think that you'll get it if you install the package ubuntu-restricted-extras.

-WBL

---

### Post by tjwoosta on 2008-05-09
> 
You need to install java. I think that you'll get it if you install the package ubuntu-restricted-extras.


i have java,   its java version "1.6.0_06" 
(it actually says that at the bottom of the error that i posted, but thanks for trying)

i already have lika all other java applications working too (its just frostwire)


guys i do have a large amount of patience for this kind of stuff, so any ideas at all im willing to try.

---

### Post by WBL on 2008-05-09
> **tjwoosta said:**
> i have java,   its java version "1.6.0_06" 
(it actually says that at the bottom of the error that i posted, but thanks for trying)

i already have lika all other java applications working too (its just frostwire)

That's strange, because my Frostwire works fine.  Of course, I prefer torrents, but sometimes I do like to get on Frostwire every now and then.  Good luck; I hope that you get it working.

-WBL

---

### Post by tjwoosta on 2008-05-09
yea i also prefer torrents for most things, but i like to get alot of my music from limewire (or hopefully frostwire) just because its quicker and easier than searching for torrents

thanks again for trying to help

> That's strange, because my Frostwire works fine

i think my problem is because im using 64bit ubuntu rather than 32bit, but even still there has got to be some way to make frostwire work isnt there?

---

### Post by kamitsukai on 2008-05-09
Of course that music is all legal downloads because you already own them on cd right? just like me :P

---

### Post by tjwoosta on 2008-05-09
well yea.. of course

---

### Post by WBL on 2008-05-09
> **tjwoosta said:**
> yea i also prefer torrents for most things, but i like to get alot of my music from limewire (or hopefully frostwire) just because its quicker and easier than searching for torrents

thanks again for trying to help



i think my problem is because im using 64bit ubuntu rather than 32bit, but even still there has got to be some way to make frostwire work isnt there?

Have you tried posting in the x86 64-bit part of this forum?  Maybe somebody lurking around there will know...

-WBL

---

