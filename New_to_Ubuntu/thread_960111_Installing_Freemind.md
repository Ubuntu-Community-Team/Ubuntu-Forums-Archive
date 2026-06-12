---
title: "Installing Freemind"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by quercusrobur on 2008-10-27
Hi, have downloaded Freemind from their website freemind-src-0.9.0_Beta_20.tar.gz rather than the repositries as I couldn't get these to work  but am not sure how to install from the downloaded package - can anyone advise, thanks!

---

### Post by nhasian on 2008-10-27
the readme file inside the archive says:

> To build FreeMind from the sources you need ant from
[http://ant.apache.org/](http://ant.apache.org/)

After having installed ant, try some of the instructions:

ant dist
	- to compile the sources
ant post
	- to create a new delivery version
ant run
	- to start FreeMind from the sources.
	

---

### Post by quercusrobur on 2008-10-27
OK, have looked at the manual as suggested in the Ant 'read me' file for install instructions but don't really understand them at all. So then tried to download ant from the repositries and got this message in the terminal; 

graham@graham-laptop:~$ ant
Error: JAVA_HOME is not defined correctly.
  We cannot execute /usr/lib/jvm/java-1.5.0-sun-1.5.0.13//bin/java
graham@graham-laptop:~$

---

### Post by nhasian on 2008-10-27
i'm no expert at compiling stuff from source, but maybe this will help:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by quercusrobur on 2008-10-27
Thanks for the link to the page, but again it seems to be getting very complicated when all I want to do is install the one program that i'm really missing from windows (I know that there are other mindmapping programs avaialble, but I work in collaboaration with somebody else that uses Freemind) 

I think I've given up yet again. Is there any chance that Freemind will one day be packaged and made easy to install?

---

### Post by hyper_ch on 2008-10-27
if it's not in the repos than you could volunteer and start compiling it and provide it as package.

---

### Post by quercusrobur on 2008-10-27
Isn't that rather like asking somebody who can't even find the clutch on their first driving lesson to drive a coach from London to Glasgow? Unfortunately I can't even figure out how to install it myself let alone get involved with processes like compiling!

---

### Post by Nepherte on 2008-10-27
You will rather be able to make the repository version to work than compiling it from source. What was the problem you were experiencing with the repository version?

---

### Post by quercusrobur on 2008-10-27
typing 'freemind' into the termnial brings up this message;

graham@graham-laptop:~$ freemind

Looking for user properties:
/home/graham/.freemind/user.properties

User properties found.
Default (System) Look & Feel: javax.swing.plaf.metal.MetalLookAndFeel
Warning: the font you have set as standard - null - is not available.
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module.
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module.

The Freemind screen comes up as per attached screenshot, but does not respond until eventually I have to force quit.

---

### Post by justfred on 2009-01-01
Did you progress on this :
I was able to install and run both the packaged (version 0.7) as  well as the last (stable) version from the freemind website (0.81 as a .deb package).

The only thing I did not manage to do is printing : something seems to be broken in java.

---

### Post by truth_forum on 2009-07-09
ive installed freemind in 8.10 using the synpatic manager. when i type freemind on th monitor the output is: 


The command could not be located because '/usr/bin' is not included in the PATH environment variable.

---

### Post by truth_forum on 2009-07-09
ive installed freemind in 8.10 using the synpatic manager. when i type freemind on th monitor the output is: 


The command could not be located because '/usr/bin' is not included in the PATH environment variable.
 any advise? thnxtnx.

---

