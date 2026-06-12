---
title: "[SOLVED] Firefox 3.0 5b java error"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-18
:confused:

Ok so I have done everything I know to do (thats not saying much) :lolflag: 
but anyway

I do have 1 or 2 games I like to play with friends at yahoo games. in order to do that it needs to see that java is enabled in firefox.  I get an erro that says its not everytime I try to start one of the online games.  


Anyway got any ideas I have attached a screen shot so you can see what it says I have java enabled within the fire fox control panel 

Ideas would be a help 

~D

---

### Post by shifty_powers on 2008-05-18
have you looked in add/remove in the applicatins menu?

look for java and ubuntu restricted extras, and install ;)

---

### Post by mbarak on 2008-05-18
The problem with ubuntu-restricted-extras is that it installs openjava instead of sun's java
to install sun's java look for it in add/remove programs or run this command
```
sudo apt-get install sun-java6-plugin
```

if you already installed ubuntu-restricted-extras run these commands to remove openjdk and install sun's java:
```

sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib icedtea-gcjwebplugin
sudo apt-get install sun-java6-plugin
```
and, you should be able to play your yahoo games :)

---

### Post by autocrosser on 2008-05-18
This came up during development--To have the best java use with Firefox 3--Goto Synaptic & search for Java...Scroll down until you see "IceTea" (Java 7 development) & install the gcjwebplugin, jre & plugin.

Then restart your browser & make sure that in "Plug-ins" you are using the "Icetea" plugin.

---

### Post by mbarak on 2008-05-18
> **autocrosser said:**
> This came up during development--To have the best java use with Firefox 3--Goto Synaptic & search for Java...Scroll down until you see "IceTea" (Java 7 development) & install the gcjwebplugin, jre & plugin.

Then restart your browser & make sure that in "Plug-ins" you are using the "Icetea" plugin.

icedtea-java7 installs openjdk-6 which does not work with all java applets on the internet (ex: facebook photo uploader just to name one)

---

### Post by autocrosser on 2008-05-18
Hmmmmm--I don't seem to have any problems with it--but I don't do facebook--just applets. So I would agree--use Sun Java 6 until Sun gets it's act together & releases OpenJava 7.

---

### Post by hufferd on 2008-05-18
ah so this maybe where my issue is 

I get this error in the add remove programs menu 

"Sun Java 6.0 Plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by hufferd on 2008-05-18
Is there an issue with running on a 64 bit system?

---

### Post by autocrosser on 2008-05-18
In a word--yes. You should look in the Tutorial forum--I seem to recall a work-around posted there....

---

### Post by hufferd on 2008-05-18
> **autocrosser said:**
> In a word--yes. You should look in the Tutorial forum--I seem to recall a work-around posted there....

Thanks for the help auto I will take a look

---

### Post by shifty_powers on 2008-05-18
heh, i see, didn't realise you were running the 64-bit hardy.

well you can force packages to run in 32-bit mode, but I can't tell you how off the top of my head, there will be a how to floating around ;)

---

