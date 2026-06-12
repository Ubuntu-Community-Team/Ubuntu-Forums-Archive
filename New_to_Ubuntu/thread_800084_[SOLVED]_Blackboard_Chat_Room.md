---
title: "[SOLVED] Blackboard Chat Room"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by brightscreamer on 2008-05-19
Hello, all!

I really want to switch to Ubuntu exclusively, but the only thing holding me back is an issue I'm having in Blackboard opening up a chat room. I can do everything else in blackboard that I can think of, but when I click the link to open up a chat room, nothing happens at all. Any ideas?

Here's the link:

javascript: openRoom('541926042061','Course Introduction - For the First Chat:1:false:false',' My Name ','577174524131','S','541926414061','false','0','596142530181','true' )

---

### Post by billgoldberg on 2008-05-19
Please insert proper link.

Is it a flash or java problem?

I had better results from java using the epiphany browser than I did with firefox.

---

### Post by brightscreamer on 2008-05-19
That is the link. : (  I right-clicked and copied the link.

I'll try that browser you mentioned, though. Thanks!

---

### Post by brightscreamer on 2008-05-19
Upgraded to Hardy Heron, tried the Epiphany browser and Firefox, still no luck. I click the chat room link, but it doesn't even open up a new window. It doesn't do anything. Does anyone have any ideas? I can't make the full switch over to Ubuntu if it doesn't work with the chat rooms for my online classes. Please don't make me use Vista. Help!

---

### Post by shadowbuntu on 2008-05-19
> **brightscreamer said:**
> Upgraded to Hardy Heron, tried the Epiphany browser and Firefox, still no luck. I click the chat room link, but it doesn't even open up a new window. It doesn't do anything. Does anyone have any ideas? I can't make the full switch over to Ubuntu if it doesn't work with the chat rooms for my online classes. Please don't make me use Vista. Help!

This might have already been obvious... But did you disable all your pop-up blockers?

HTH

G.

---

### Post by brightscreamer on 2008-05-19
That's the first thing I checked, no dice. Thanks, though!

---

### Post by friendofpugs on 2008-05-19
See if it burps using Opera. Browsers are like potato chips, you can never have just one! :)

---

### Post by brightscreamer on 2008-05-20
No dice with Opera, either. It's weird. I click the javascript link for the chat room, and nothing happens. I right-click and try to open it in a new tab, and nothing comes up. Help please!

---

### Post by brightscreamer on 2008-05-20
Please help me! HELP ME RID MY LIFE OF WINDOWS!!!

---

### Post by brightscreamer on 2008-05-21
Am I posting this in the wrong forum? :confused:

---

### Post by OffAxis on 2008-05-21
you need to post the referring link; the javascript reference that you posted is a relative link - which doesn't do us much good in trying to figure out what's wrong.

You're in the right forum, we just need more info.

 So if you could post the address of the page BEFORE you have this issue, then we'll stand a better shot at giving you a solution.

---

### Post by DrOlaf on 2008-05-21
> **brightscreamer said:**
> Hello, all!

I really want to switch to Ubuntu exclusively, but the only thing holding me back is an issue I'm having in Blackboard opening up a chat room. I can do everything else in blackboard that I can think of, but when I click the link to open up a chat room, nothing happens at all. Any ideas?

Here's the link:

javascript: openRoom('541926042061','Course Introduction - For the First Chat:1:false:false',' My Name ','577174524131','S','541926414061','false','0','596142530181','true' )

Which version of Blackboard are you using? I can access the "Virtual Classroom" room on my University's Blackboard v7 server. I had to download the Sun JDK v6 to be able to do so, but I'm in the room now, as I type this. None of my students are, though, the slackers.

[EDIT] Sorry, I should have said: this is using FF3 under Ubuntu 8.04, 32 bit.

---

### Post by brightscreamer on 2008-05-21
This is the URL of the page that contains the link I'm trying to click:

O.k., maybe I shouldn't post the link. :(

Thanks for the tip!

I'm not sure how to check which version of Blackboard I'm using, though.

---

### Post by brightscreamer on 2008-05-21
Is this the version?

Blackboard Learning System - Vista Enterprise License (Release Vista 4.2.3) [14.0.7.37]

---

### Post by DrOlaf on 2008-05-21
Blackboard Vista is a different program to the one we use here, I'm afraid. I'll look into the specs and see what I can find out about it though.

The name of the software doesn't fill me with confidence though.

---

### Post by dark_harmonics on 2008-05-21
Not all web apps like the same version of java either. If you contact tech support of your school ask them which version their program prefers. PC Anywhere is a java applet that only worked when i changed the version of java it was using. I am of course assuming you already have some version installed. My company uses some other software that uses a specific java version and only certain features fail when you use the wrong one, just like in your problem. 

Hope some of that helps!

---

### Post by linuxinireland on 2008-05-21
> **brightscreamer said:**
> Am I posting this in the wrong forum? :confused:
No you are not at all dont get a bad impression. Check this out
UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY
 
 
 A quick and easy way to install most of the packages you need (Java, codecs for playing/ripping/converting music and video etc) is to use the command line. If you would rather use a graphical application with descriptions of packages, you can either use Add/Remove, Synaptic in Ubuntu and Xubuntu (System > Administration > Synaptic Package Manager in Ubuntu and Applications > System > Synaptic Package Manager in Xubuntu) and Adept in Kubuntu (KMenu > System > Adept). For the sake of speed, I suggest using the Terminal for most of this how-to. Open up the Terminal, then copy and paste the relevant command for your particular Ubuntu variant and architecture into it:
 
 32-Bit Ubuntu Users:
 
 sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly



And if you have more problems.

JAVA
 
 
 Java not working correctly? Close Firefox and then try this command below. Make sure you select the latest Java, which will be somewhere in /usr/lib:
 
 sudo update-alternatives --config java
 
 Still no go? Ubuntu 32-bit users who are trying to use Sun Java might want to make sure they don't have IcedTea/OpenJDK Java and it's plugin installed, as it will conflict with the Sun Java plugin:
 
 sudo apt-get remove icedtea-java7-bin icedtea-java7-jre icedtea-java7-plugin icedtea-gcjwebplugin openjdk-6-jre-headless openjdk-6-jre openjdk-6-jre-lib
 gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin pulseaudio-utils unrar w32codecs


thanks to [reassuringlyoffensive]("http://ubuntuforums.org/member.php?u=314581")

---

### Post by brightscreamer on 2008-05-21
This step:


sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly

WORKED!!! THANK YOU SO MUCH, EVERYONE!!! I'M FREE AT LAST!!!

---

