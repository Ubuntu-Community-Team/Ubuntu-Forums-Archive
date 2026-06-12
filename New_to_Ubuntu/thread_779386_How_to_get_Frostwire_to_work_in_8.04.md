---
title: "How to get Frostwire to work in 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by vierranet on 2008-05-02
This is what I did and it worked..

First: remove frostwire if currently installed.

Second: sudo apt-get install sun-java6-jdk

Third: sudo update-java-alternatives -s java-6-sun

Fourth: Download Frostwire from [http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads)

Fifth: After installing Happy Frostwireing....

---

### Post by Tom--d on 2008-05-02
All I did was install Java runtime 6 (in Add/remove) and then installed Frost wire. 

:)

---

### Post by 127.0.0.1 on 2008-05-17
I'll be damned. I've tried everything and nothing seemed to work untill i tried this and it didn't appear to do much but it worked :shock: Thanks man.:)

---

### Post by ruffneck on 2008-05-18
> **vierranet said:**
> This is what I did and it worked..

First: remove frostwire if currently installed.

Second: sudo apt-get install sun-java6-jdk

Third: sudo update-java-alternatives -s java-6-sun

Fourth: Download Frostwire from [http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads)

Fifth: After installing Happy Frostwireing....

thanks!

---

### Post by CloudFX on 2008-05-18
also see [https://wiki.ubuntu.com/FrostWire](https://wiki.ubuntu.com/FrostWire)

---

### Post by sooperspook on 2008-05-24
I did that and Frostwire works but now a web page I go to doesn't work, no animations or anything.

Would this fix have anything to do with it or just a coincidence?

---

### Post by jamesstansell on 2008-05-24
> **sooperspook said:**
> I did that and Frostwire works but now a web page I go to doesn't work, no animations or anything.

Would this fix have anything to do with it or just a coincidence?

Likely just a coincidence, but it depends a little on how the animations are done.  What page is it?

---

### Post by sooperspook on 2008-05-28
> **jamesstansell said:**
> Likely just a coincidence, but it depends a little on how the animations are done.  What page is it?

don't worry about it. Turns out to be just a coincidence. :)
Thanks anyway. :)

---

### Post by ragadanga63 on 2008-06-07
Worked for me.  Thanks a million.

---

### Post by billgoldberg on 2008-06-07
getting frostwire to work in 8.04 is the exact same method of getting it to work in any OS in the world.

First install java, then frostwire.

The only tricky thing in ubuntu, is that if you installed "ubuntu-restricted-extras" you'll need to remove open-java or frostwire won't work, regardless if you installed sun-java6-jre or not.

---

### Post by BLTicklemonster on 2008-06-21
Tried everything in here. Removed frostwire each time I did anything different for java, and still:

```
bill@bill-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fa74897c755, pid=7820, tid=1097505104
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid7820.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  7820 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

bill@bill-desktop:~$ 

```

Maybe I should pull back to java 5 instead of 6?


Edit: GOT IT WORKING.

This thread:
[http://ubuntuforums.org/showthread.php?t=780083](http://ubuntuforums.org/showthread.php?t=780083)

Install the 32 bit version of java
```

 sudo apt-get install ia32-sun-java6-bin 

(this should also install ia32-libs)

```
Select your java version
```

sudo update-alternatives --config java

choose the ia32 one

```

Voila

---

### Post by whistlerspa on 2008-06-22
None of this has worked for me - is there anything els that i can try?

---

### Post by CraigPaleo on 2008-06-22
Hi everyone. I'm a noob and Frostwire was the first app I downoaded without using the repository. It didn't work but after reading this. This:```

sudo update-java-alternatives -s java-6-sun
``` worked! 

I'd love to convince my sister to install Ubuntu. You see, her daughter invariably downloads viruses with Limewire on their windows machine. I think Ubuntu has everything they would need but having to use the terminal would be a turn-off for them. How often does an average desktop user have to use the terminal? Is it only when installing apps that aren't in the repository?

Thanks,

Craig

___________________
[Carnivorous Zero Carb]("http://www.rawpaleoforum.com/carnivorous-zero-carb-approach/")

---

### Post by CraigPaleo on 2008-07-06
I had Frostwire working fine until I installed Weather Bug. Now it won't launch at all. I don't know if there's any connection or if it's just a coincidence. 

Craig

---

### Post by Foster Grant on 2008-07-06
> **CraigPaleo said:**
> I had Frostwire working fine until I installed Weather Bug. Now it won't launch at all. I don't know if there's any connection or if it's just a coincidence. 

Craig

Why did you install WeatherBug (AKA AdwareBug/NagwareBug)? GNOME comes with a panel applet called Weather Report that gives you local conditions, NWS forecasts and Weather Channel radar; the key differences are that it doesn't ask for money, show you advertisements or require Java to run.

[LIST=1]
[*]Right-click one of your panels (I keep mine on the upper panel).
[*]Select *Add To Panel ..*
[*]In the dialog box, scroll down to Weather Report (in GNOME 2.22, it's all the way at the bottom) and select it.
[*]Hit the Add button. Close the dialog box.
[*]Right-click the resulting panel icon and move it to exactly where you want it, then click to place it there.
[*]Right-click the icon again and choose the *Preferences* item. In the first panel of the dialog box, choose your measurement preferences. In the second, choose your location.
[*]Uninstall Weather Bug.
[/LIST]

Avant Window Manager also has a weather applet, but it's not as informative as the GNOME applet.

---

### Post by T2manner on 2008-07-06
I wonder why people are having problems with this.
I didn't encounter a single problem.

---

### Post by CraigPaleo on 2008-07-07
> **Foster Grant said:**
> Why did you install WeatherBug (AKA AdwareBug/NagwareBug)? GNOME comes with a panel applet called Weather Report that gives you local conditions, NWS forecasts and Weather Channel radar; the key differences are that it doesn't ask for money, show you advertisements or require Java to run.

[LIST=1]
[*]Right-click one of your panels (I keep mine on the upper panel).
[*]Select *Add To Panel ..*
[*]In the dialog box, scroll down to Weather Report (in GNOME 2.22, it's all the way at the bottom) and select it.
[*]Hit the Add button. Close the dialog box.
[*]Right-click the resulting panel icon and move it to exactly where you want it, then click to place it there.
[*]Right-click the icon again and choose the *Preferences* item. In the first panel of the dialog box, choose your measurement preferences. In the second, choose your location.
[*]Uninstall Weather Bug.
[/LIST]

Avant Window Manager also has a weather applet, but it's not as informative as the GNOME applet.

Thanks. But, I installed Weather Bug because the Weather Report applet was at least 24 hours behind for my area and even the nearest location was about 30 miles away in Punta Gorda.

I still want to get Frostwire to launch again.

Craig

---

### Post by CraigPaleo on 2008-07-07
> **T2manner said:**
> I wonder why people are having problems with this.
I didn't encounter a single problem.

I have a relatively new machine. Ubuntu is the ONLY distribution that would run on my machine at all in the live version. I'm thinking that may be a problem. Kubuntu would install but it would keep freezing. Ubuntu with GNOME is much better in my opinion!

Craig

---

### Post by kulturloseramerikaner on 2008-07-08
Well heck I can get it installed just fine... Same deal as before on Gutsy and Feisty...
However, it is now steadfastly refusing to connect to the network.  I've tried reinstalling with no luck, before and after updating all the Java packages.

---

### Post by CraigPaleo on 2008-07-08
Okay, I got rid of Weather Bug and redid this command: ```
sudo update-java-alternatives -s java-6-sun
```
Frostwire is working once again! The Linux version of Weather Bug isn't nag/addware - at least not yet. It did work pretty well but could its installation have undone the command that originally got Frostwire working in the first place? I highly suspect this since it uses Java also.

Craig

---

### Post by CraigPaleo on 2008-07-08
> **kulturloseramerikaner said:**
> Well heck I can get it installed just fine... Same deal as before on Gutsy and Feisty...
However, it is now steadfastly refusing to connect to the network.  I've tried reinstalling with no luck, before and after updating all the Java packages.

I'm no expert but it sounds more like a network/firewall problem maybe having something to do with ports or something rather than Frostwire itself. You might want to try a Frostwire support forum. I had problems when I first installed aMule on my Mac. I had to go into the router and enable certain ports to keep from getting a low ID.

Craig

____________________
[Raw Weston Price]("http://www.rawpaleoforum.com/raw-weston-price/")

---

### Post by balanovich on 2008-07-11
I installed frostwire and everything seemed to have gone well, except that when I click on it in "applications", nothing happens.

I have installed ubuntu-restricted-extras so I should delete open-java.

how do I do that ?

I typed sudo update-java-alternatives -s java-6-sun

after a buch of line, I got :

update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-6-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so

Is that bad ?

---

### Post by chris09 on 2008-08-19
hey man i have run the first command and works but when i try to do  update-java-alternatives -s java6-sun it tells me:

update-java-alternatives: directory does not exist: /usr/lib/jvm/java6-sun

---

### Post by chris09 on 2008-08-19
ok man after i do all 4 steps i finish installing but does not open it just says its installed but nothing happens i get this after the installation file:///home/edgar/Desktop/Screenshot.png

---

### Post by CraigPaleo on 2008-08-19
Did you mean to upload a screenshot?


__________________
[Raw Paleolithic Diet]("http://www.rawpaleodiet.com")

---

### Post by HebrewTheHammer on 2008-08-21
Thanks

---

### Post by pboxinator on 2009-04-25
I get this message in the terminal when I try to run FrostWire, its very annoying and I tried everything. I'm using 8.10 BTW.

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

---

