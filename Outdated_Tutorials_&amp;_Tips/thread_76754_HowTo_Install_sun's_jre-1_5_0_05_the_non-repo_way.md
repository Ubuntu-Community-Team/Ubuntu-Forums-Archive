---
title: "HowTo: Install sun's jre-1_5_0_05 the non-repo way"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Arktis on 2005-10-15
[color=red]**NOTE: These instructions were made for breezy and do not take firefox 1.5 into account.  An updated howto thread for the newer firefox on dapper with jre-1_5_0_06 is can be found [here]("http://ubuntuforums.org/showthread.php?t=148075").  You should only be manually installing sun jre/jdk if you can't follow the easier java-package installation method.**[/color]


I hope this will be useful to someone. I couldn't find java-package in the repositories because I hadn't added multiverse. So, I installed java in a different way.

First, download the linux runtime installer [here]("http://java.com/en/download/manual.jsp").  Do NOT get the rpm!  Get the one that says **Linux (self-extracting file)**.

After downloading, cd to where you downloaded the file and run:
 ```
sudo mv jre-1_5_0_05-linux-i586.bin /usr/local
cd /usr/local
sudo chmod a+x jre-1_5_0_05-linux-i586.bin
sudo sh jre-1_5_0_05-linux-i586.bin
``` Say 'yes' to the license agreement and watch it extract the files into a folder called jre1.5.0_05
 You're almost done.  Now you want to install the plugin for firefox:
  ```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
``` Firefox is now happily running java applets.
 The final steps are:
```
sudo ln -sf /usr/local/jre1.5.0_05/bin/java_vm /usr/bin/java_vm
sudo update-alternatives --install /usr/bin/java java /usr/local/jre1.5.0_05/bin/java 1
``` 
And now the java runtime environment appears in your list of choices when running '**sudo update-alternatives --config java**'! Go ahead and run that, and chose the sun java option. Then to check to make sure it worked, run '**java -version**', which should output something like this:
  ```
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
``` Done!
 
If you want to do some configurating with the java control pannel, run 'sh /usr/local/jre1.5.0_05/bin/ControlPanel'.

Enjoy! ;)


 =========================
 Removal Instructions
 
 If the time comes when you need/want to remove java, these commands will do the trick if you followed the howto exactly:
 ```
sudo rm /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
sudo rm /usr/bin/java_vm
sudo update-alternatives --remove java /usr/local/jre1.5.0_05/bin/java
``` 
 Then you'll want to  open up a  root nautilus  and go to /usr/loca/ and delete  the jre1.5.0_05 folder.  That should do it.
 =========================

---

### Post by rush_ad on 2005-10-15
i downloaded the amd64 self extracting file and installed it. but there is no 'plugin' directory in my installation...

how do i get firefox to work with java?

---

### Post by rush_ad on 2005-10-15
i know my java works becuase 

> rushad@patel-dorm:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)


---

### Post by Arktis on 2005-10-15
[quote=rush_ad]i downloaded the amd64 self extracting file and installed it. but there is no 'plugin' directory in my installation...

how do i get firefox to work with java?[/quote]

Correct me if I am wrong, but I don't think there's a 64 bit plugin for java.

---

### Post by 11hjpphty76lkjj on 2005-10-15
Finally--a java install how to that works.  Thank you!!

Aaron

---

### Post by astroboysoup on 2005-10-15
I always seem to get this error when I'm running binary files.

```
Extracting...
jre-1_5_0_05-linux-i586.bin: line 262: ./install.sfx.6908: cannot execute binary file
jre-1_5_0_05-linux-i586.bin: line 529: cd: jre1.5.0_05: No such file or directory

```

any ideas guys

---

### Post by rush_ad on 2005-10-16
[QUOTE=Arktis]Correct me if I am wrong, but I don't think there's a 64 bit plugin for java.[/QUOTE]

i solved it. there is no 64-bit plugin by sun java but there is by blackdown. need to install blackdown to use java

---

### Post by xMetaRidley on 2005-10-16
Thank you, works great!

---

### Post by odie5533 on 2005-10-16
When I try installing it the using the jdk, firefox won't start up. I looked in the dir I used for the location of the plugin and the plugin is there. Any ideas?

---

### Post by Arktis on 2005-10-16
I've updated the howto with removal instructions.

@**odie5533: **My 1st guess would be that since *the location of the plugin within the JDK's extracted directory is different than it is in the JRE's directory*, you've used the ln command in my howto and ended up with a broken link in your firefox plugins directory. Could you check your firefox plugins directory to see if the link is broken or not? My 2nd guess would be that you're using the wrong plugin for your architecture. What is your computer's architecture?

@**astroboysoup: **Have you checked the permissions on the files you are having trouble with? Also, I'm not clear on one point; are you saying that you have this trouble with other binaries or *just* the binaries from the JRE package?

If anyone else is having trouble with the JDK, I can post additional instructions. Manual installation of that isn't very different from the JRE, but there are some additional links you need to add to /usr/bin.  Also, as I staed to odie5533, the location of the plugin is different.

---

### Post by edal on 2005-10-17
Works first time using Breezy Badger

Ed Almos

---

### Post by majed on 2005-10-19
This Is One Great How-to!!!

---

### Post by dudus on 2005-10-19
Thank you very much.

You can test if it is working in this url

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by bennettg on 2005-10-19
followed the instructions.  when i try to run a java from the firefox, it hangs and firefox needs 2 b forced quit.

i am a noob.  the web site is [www.gotomypc.com](www.gotomypc.com) and it happens when it tries to load the universal viewer (java)

please help the dumbest noob ever

---

### Post by clparker on 2005-10-19
Works Great, Your The Man!!!

-clparker

---

### Post by majed on 2005-10-20
[QUOTE=bennettg]followed the instructions.  when i try to run a java from the firefox, it hangs and firefox needs 2 b forced quit.

i am a noob.  the web site is [www.gotomypc.com](www.gotomypc.com) and it happens when it tries to load the universal viewer (java)

please help the dumbest noob ever[/QUOTE]
The site works fine with my firefox.. maybe u wanna double check ur plugin links? follow the procedure again?!

---

### Post by vaskark on 2005-10-20
I followed the instructions and things seemed to work fine. I get the expected results of 'java -version' and both Limewire and Azureus work fine. It's the Firefox plugin that isn't loading.

jason@breezy:/usr/lib/mozilla-firefox/plugins$ ls -l
libjavaplugin_oji.so -> /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so

Nothing about java is displayed in 'about: plugins'. So what's going wrong here? Are there other symlinks that need to be created/redirected somewhere?

Ironically, the plugin loads fine in another browser I use ...

Thanks.

Update: D'oh. I wasn't putting the plugin link in my firefox beta's plugins folder. I suck. Works great now :)

---

### Post by Arktis on 2005-10-20
I think you just need to open firefox, edit > preferences > web features > enable java.

That other browser... it's epiphany, right?

Edit: Aha, so that's what it was.  I'm looking forward to that new firefox version, but I haven't tried the beta.  I'll probably just wait until it's released.

---

### Post by vaskark on 2005-10-20
[quote=Arktis]I think you just need to open firefox, edit > preferences > web features > enable java.

That other browser... it's epiphany, right?[/quote]
No it's Flock. Getting the plugin to work in that made me realize my original error: i put the plugin in /usr/lib/mozilla-firefox/plugins but i forgot to also put it in /usr/local/firefox/plugins (where I have the firefox beta stored). All is well now ;)

---

### Post by Knitter on 2005-10-21
[QUOTE=Arktis]
If anyone else is having trouble with the JDK, I can post additional instructions. Manual installation of that isn't very different from the JRE, but there are some additional links you need to add to /usr/bin.  Also, as I staed to odie5533, the location of the plugin is different.[/QUOTE]

I'm trying to install jdk right now. can you post the additional links and any other option needed? 

Thanks.

---

### Post by Arktis on 2005-10-21
>  I'm trying to install jdk right now. can you post the additional links and any other option needed? [FONT=monospace]
It is best to use the update-alternatives command to add the following links from your extracted JDK's bin folder into the /usr/bin path:

[/FONT][FONT=monospace]appletviewer
[/FONT][FONT=monospace]idlj
[/FONT][FONT=monospace]jar[/FONT]
[FONT=monospace]jarsigner[/FONT]
[FONT=monospace]javac
javadoc
javah
[/FONT][FONT=monospace]javap[/FONT]
[FONT=monospace]javaws
[/FONT][FONT=monospace]jdb[/FONT]
[FONT=monospace]rmid
[/FONT][FONT=monospace]serialver

For example, to add appletviewer from the JDK using update-alternatives, use the command:
```
sudo update-alternatives --install /usr/bin/appletviewer appletviewer /usr/local/jdk1.5.0_05/bin/appletviewer 1
```
[/FONT][FONT=monospace] You can just manually link them instead of using update-alternatives to manage the links, but I wouldn't recommend that.

If anyone thinks I missed anything, please do say something. ;)
[/FONT]

***Edit:** mr_crimp points out that I missed java_vm, which would be located in /usr/local/jdk1.5.0_05/jre/bin/java_vm.  He also notes that I should add that "the firefox plugin in jdk is also located in the jre directory inside the jdk folder (/usr/local/jdk1.5.0_05/jre/plugin/i386/ns7/libjavaplugin_oji.so".  Thankies.

---

### Post by ShiftyPowers on 2005-10-21
worked like a charm, thank you so much

---

### Post by jlv on 2005-10-21
[QUOTE=bennettg]followed the instructions.  when i try to run a java from the firefox, it hangs and firefox needs 2 b forced quit.[/QUOTE]

I had similar problems.  Some sites with java would open, others wouldn't and Firefox frequently froze.  Eventually, I disabled all my extensions and then re-enabled them, and the problem (for me at least) seems to have been the adblock extension.

---

### Post by Arktis on 2005-10-21
I think you're probably right. To test, I installed the adblock extension (which I've never used before) and I noticed right away when looking at this [test page]("http://www.java.com/en/download/help/testvm.xml") that the dancing guy isn't displayed and there is an adblock tag added. Disabling the extension only removed the tab. Only by uninstalling (not just disabling) the extension could I get the dancing guy back. I think it's safe to say that this extension messes a bit with java applets, though I have not experienced a crash yet. I'll keep testing it.

---

### Post by JakeSpeare on 2005-10-22
I followed this how to to install the 5.0 jdk.  All went well, but when I check the version, I get:

> 
jake@ibmp4:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

java also does not work in Firefox.

Any thoughts?

---

### Post by stevea1210 on 2005-10-22
[QUOTE=JakeSpeare]I followed this how to to install the 5.0 jdk.  All went well, but when I check the version, I get:



java also does not work in Firefox.

Any thoughts?[/QUOTE]


Run
```
sudo update-alternatives --config java
```

Choose the java version you just installed.  For me it was option 3.  That switches where it runs java from.  Then run 
```
java -version
```

to confirm and you should be fine :)

---

### Post by JakeSpeare on 2005-10-22
I only get two options and neither is java 5.0  ...

> jake@ibmp4:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number: 

---

### Post by stevea1210 on 2005-10-22
I would venture that some part of the install didn't go correct.  I would reccomend to follow the how-to again, and see what the results are.  Maybe there was a missed step. (no offense)

---

### Post by Arktis on 2005-10-22
What exactly happens when you issue

```
sudo update-alternatives --install /usr/bin/java java /usr/local/jdk1.5.0_05/bin/java 1
``` 
?

That's the command which is supposed to add the sun java to your list of alternatives, so obviously something must be wrong with that step.  You should also check your firefox plugin for java for things already mentioned in this topic.

---

### Post by iNerdSure on 2005-10-23
Many thanks. The intall works great for me. Considering I'm a Linux convert newbie. (Although I'm still struggling to break the NOsound barrier for the last 2 weeks!).

---

### Post by eko291 on 2005-10-23
Worked wonderfully!  Thanks!

---

### Post by JakeSpeare on 2005-10-23
works great now.  Thanks!

---

### Post by ming0 on 2005-10-27
problems running a jar
```
dean@dim:~/Desktop/iriverter-0.13r1$ java -jar ./iriverter.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3128 in java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Unknown Source)
        at org.eclipse.swt.widgets.Display.<clinit>(Unknown Source)
        at net.sourceforge.iriverter.ConverterUI.<init>(ConverterUI.java:29)
        at net.sourceforge.iriverter.ConverterUI.main(ConverterUI.java:682)
dean@dim:~/Desktop/iriverter-0.13r1$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```

thx in advance :)

---

### Post by Arktis on 2005-10-28
After googling, I believe this is a problem with eclipse, though I'm not exactly sure... There is a bug report filed against it and apparently a solution is offered.

[Bug Report]("https://bugs.eclipse.org/bugs/show_bug.cgi?id=88669")
[Some Guy's Blog]("http://dream-dimensions.de/blog/index.php")
[Sun Documentation]("http://java.sun.com/j2se/1.5.0/docs/api/java/lang/UnsatisfiedLinkError.html")

---

### Post by Worm on 2005-11-09
Arktis,
You're a champ.
I'm a Linux newbie and was getting ready to throw my laptop out of the window trying to get UltraVNC java viewer working.

Don't ever suppose that something is too newb to post! I'm proof of that.

Cheers!

Worm

---

### Post by chinaski on 2005-11-10
[QUOTE=Arktis]I hope this will be useful to someone.[/QUOTE]
yeeeesssss! ;)

---

### Post by mr_crimp on 2005-11-13
Thanks for this nice howto. I just have one question. 

I have installed jdk and was following your guide but at this part ```
sudo ln -sf /usr/local/jre1.5.0_05/bin/java_vm /usr/bin/java_vm
```

I couldn't find the java_vm in the directory (/usr/local/jdk1.5.0_05/bin/) so I just used the /usr/local/jdk1.5.0_05/bin/java instead. Is that wrong? Afterwards I found the java_vm but in this directory: /usr/local/jdk1.5.0_05/jre/bin/java_vm. What should I do now? Should I uninstall jdk and then reinstall it with the /usr/local/jdk1.5.0_05/jre/bin/java_vm? If so how do I uninstall it?

Once again thanks for the nice howto.

---

### Post by Arktis on 2005-11-14
Nah, just remove the link you substituted and add the proper one.   Thanks for pointing that out.  

Edit: Oh, and I should probably add that to the list of stuff for jdk.

---

### Post by mr_crimp on 2005-11-14
Thanks...

---

### Post by dragonfoundry on 2005-11-14
No other way to say it 


Thanks Arktis!!!  =D>

---

### Post by mr_crimp on 2005-11-15
Arktis, I don't know if you want to add this to your howto or if it's obvious but the firefox plugin in jdk is also located in the jre directory inside the jdk folder (/usr/local/jdk1.5.0_05/jre/plugin/i386/ns7/libjavaplugin_oji.so).

/thanks

---

### Post by renebe on 2005-11-20
This manual actually works like a charm! Thank you very much indeed.

---

### Post by KupernikuZ on 2005-11-29
Hi.
Tried to follow the guide, but without success.

Have followed the guide, until the last step: 'java -version'
wich give the following output:
> 
java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Then I restarted the Mozilla Firefox but I still can't view sites containing Java :-( 
What can I do?

System: Ubuntu 5,10 Mozilla-Firefox vers. 1,0,7 (Danish).

---

### Post by Arktis on 2005-11-30
What happens when you run "sudo update-alternatives --config java"?
Is java enabled in your firefox options?
Is the link in your firefox plugin directory a broken link?
Did you follow the instructions exactly or did you deviate in any way, such as where you extracted the java folder?

---

### Post by Danielle on 2005-11-30
hi, i just checked which java version i have and it's 1.4.2 :( i don't want the firefox plugin would that mean i only do the first step?

download, then

sudo mv jre-1_5_0_05-linux-i586.bin /usr/local
cd /usr/local
sudo chmod a+x jre-1_5_0_05-linux-i586.bin
sudo sh jre-1_5_0_05-linux-i586.bin

there's a bug with MS win. whereby if you install over-the-top the old version remains and as well as taking alot of HDD space is a security problem, do you know if Ubuntu has the same problem? thanks

---

### Post by Danielle on 2005-11-30
hi, i just installed over the top during the Azureus install :rolleyes:  i have the latest version now. but i think i still have the old version installed too. can some who knows about Ubuntu and has installed over the top of an old version check to see? 

this is a serious vulnerbility in Windows it leaves you open to java viruses and exploits, don't know about linux though. thanks

---

### Post by Danielle on 2005-11-30
**OK Linux boxes can be exploited by this too!!!**

you can read about it below.

> [color=red]The vulnerability was discovered by Jouko Pynnonen in April, was fixed by Sun in October and was announced last week. Java plugin versions 1.4.2_04 and 1.4.2_05 (and presumably earlier versions as well) were found to be vulnerable on both Linux and Windows.[/color]

[LINK](http://lwn.net/Articles/113640/)

maybe it's not the exploit i was thinking of, if you have updated to 1.5xx you are OK. the exploit i know of is to do with older versions not being erased by a new install when used with an auotupdater. maybe you should get everyone to use the version in this thread if they still have a 1.4xx version?

---

### Post by Arktis on 2005-11-30
If you want to remove the old java, you can do so using synaptec package manager or apt-get.

```
sudo apt-get remove java-gcj-compat
```

You can also remove the gij wrapper 4.0, but note that this will remove openoffice.org!  Lame...

```
 sudo apt-get remove gij-4.0
```

If you don't want to use the plugin, just don't make the link in the plugins directory and firefox won't use java.  To accomplish this, **DO ALL THE STEPS *except*** for these two:

cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so

I don't know why you would want to do that though... you wouldn't be opening yourself to the old java's vulnerability this way since the link points to the newer java...

The vulnerability you speak of will only effect you if you are using the older java.  As long as java -version reports you are using 1.5.0_05 and there is no older browser plugin present/linked in your plugins directory, you're fine.  You won't be at risk since there will be no way for the older java to get loaded.

---

### Post by Danielle on 2005-11-30
hi, thanks for the help. i haven't ever really used OOo so i don't know what you mean by " remove openoffice.org! Lame" do you mean the encoder? or it's not good lol

also, i use Opera, but i don't have it on by default i only enable it when it's needed about 2/3 times a year. i use it with Bittorrent though.

if i just do this:
sudo apt-get remove java-gcj-compat

will 1.5 still work OK? thanks

---

### Post by Arktis on 2005-11-30
[quote=Danielle]if i just do this:
sudo apt-get remove java-gcj-compat

will 1.5 still work OK? thanks[/quote]
Yes, 1.5 will still work if you do that.
[quote=Danielle]hi, thanks for the help. i haven't ever really used OOo so i don't know what you mean by " remove openoffice.org! Lame" do you mean the encoder? or it's not good lol[/quote]
You're very welcome. :smile: What I meant is that if you remove the gij-4.0, Open Office.org will also be removed because OOo depends on gij-4.0.  That is "lame" (bad, unfortunate, etc.).  I wasn't talking about the encoder.

---

### Post by Danielle on 2005-12-01
[QUOTE=Arktis]Yes, 1.5 will still work if you do that.

You're very welcome. :smile: What I meant is that if you remove the gij-4.0, Open Office.org will also be removed because OOo depends on gij-4.0.  That is "lame" (bad, unfortunate, etc.).  I wasn't talking about the encoder.[/QUOTE]
thanks, Arktis. i just reomved java-gcj-compat

---

### Post by Mike Buksas on 2005-12-07
Works great with jre-1_5_0_06 also. You just need to modify some paths in the obvious ways. (No, I did not discover this until I did it wrong first.)

Thanks for a great guide.

Mike

---

### Post by nrwilk on 2005-12-07
THANK YOU!  one of the last things before I can completely stop using windows!

::bow::

---

### Post by Danielle on 2005-12-22
hi, how do i update to jre-1_5_0_06 i have this version atm - java version "1.5.0_05"

i'm still abit worried about installing over the top incase the old version isn't removed/over-written :rolleyes: thanks

---

### Post by neels on 2006-01-11
Someone should mention that firefox needs to be restarted in order to get the plugin to work: close all windows, also the download manager, everything, then reopen. Also, installing in ~/.firefox/plugins/ did not work for me.

---

### Post by neels on 2006-01-11
[QUOTE=Danielle]hi, how do i update to jre-1_5_0_06 i have this version atm - java version "1.5.0_05"

i'm still abit worried about installing over the top incase the old version isn't removed/over-written :rolleyes: thanks[/QUOTE]
don't be afraid! just install next to it, alongside, or best remove the old one and replace it with the new one. Be sure to set all symbolic links / alternatives appropriately. Try `which java', `which javac' and `java -version' and `javac -version'

---

### Post by Christopher on 2006-03-16
I installed java to a tea the way Arktis guide shows I even did a java - version in console & i get : christopher@ubuntu:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing) & I even closed out all my Firefox pages and reloaded firefox and I go to the test page at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) and its tell me i don't have it installed. Im running Firefox v1.5.0.1 Ubuntu v5.10 and the NEWEST updated kernel & nvidia drivers. Im NEW to linux, can someone help. Thank you in advance.

---

### Post by Christopher on 2006-03-18
[QUOTE=Christopher]I installed java to a tea the way Arktis guide shows I even did a java - version in console & i get : christopher@ubuntu:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing) & I even closed out all my Firefox pages and reloaded firefox and I go to the test page at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) and its tell me i don't have it installed. Im running Firefox v1.5.0.1 Ubuntu v5.10 and the NEWEST updated kernel & nvidia drivers. Im NEW to linux, can someone help. Thank you in advance.[/QUOTE]

Any ideas anyone? Thank you in advance.

---

### Post by Christopher on 2006-03-19
Anyone? :confused:

---

### Post by Arktis on 2006-03-21
Oho, hi, man.  I didn't know people were still using this thread for help.  Sorry about that.  ;)

Well, you could have placed the link in the wrong place.  My original instructions in this thread apply to breezy's older firefox.  On my site, I've got an updated set of manual install instructions for dapper and the newer firefox.  You can click the link in my sig and then navigate your way to the howto section, or you can click this [direct link]("http://ubuntu.z42.us/modules.php?name=Content&pa=showpage&pid=1") to the relevant page.

**Edit:** You're using dapper, right?  If you're using firefox 1.5 on breezy, I can still help, but the plugin link is going to have to go to yet another different location than shown in either version of the howto.  Fun-fun, heheh. :)

---

### Post by rainstreet on 2006-03-21
hi christopher hope this helps you. i followed the wiki on installing firefox 1.5 and it puts it into the opts folder, if you did it that way this might help.


follow the howto changing _05 to _06
then when you get to install plugins for firefox i did this

cd /opt/firefox/plugins
sudo ln -s /usr/local/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so

then followed the rest of the howto to finish.

remember to restart firefox

to test go here
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

---

### Post by thenasko on 2006-05-03
I followed the instructions but still experience problems with jre 1.5. I have done this a number of times before and it always worked out of the box. However now it gives me:
```
atanas@galois:~$ java -version
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
```
Any help on this issue will be greatly appreciated.

---

