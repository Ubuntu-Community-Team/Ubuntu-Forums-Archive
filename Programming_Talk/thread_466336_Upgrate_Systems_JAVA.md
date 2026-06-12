---
title: "Upgrate Systems JAVA??"
date: 2007-06-06
forum: Programming Talk
---

### Post by cytutchi on 2007-06-06
Hello

I have downloaded and installed JAVA_ee_sdk 5_01
i installed it to the directory that i wanted and set the path for $JAVA_HOME!
Is there anything else i need to do?? because if i type java -version
it still gives me the java1.4.2 that is the default of my system!!! :/

So i did install a newer version but still Kubuntu look at the original one! How can i change that??? Any clues? why doesnt it see the newr version?

---

### Post by KaeseEs on 2007-06-06
Yes.```
sudo update-alternatives --config java
```...and select the java you just installed.

Also, in the future you are much better off installing packages via Synaptic, aptitude or apt-get (which use your system's install database) than to just download a binary installer.  Good luck!

---

### Post by cytutchi on 2007-06-07
great Thenx~

But lets say if i want to unistall the one i just downloaded & installed so as to use the sudo apt-get
then i should just delete the java_home variable and all the folder where i installed it n that is it or i need something else to do???

the command to install java through my system is:

sudo apt-get java_6.0    ??

Sorry if my questions sound silly but love Kubuntu n want to find out as much as i can!

Plus i love this forum!!!!! 

Thenx again

---

### Post by cytutchi on 2007-06-07
Nevermind....i Found it and all good

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
here is where i got my answer plus with the command to choose the version which i want to use so...all good!!!!

thenx a lot though !!!!!! :)

---

