---
title: "Trouble installing Java"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Crossbow on 2008-04-22
I am having a terrible time trying to install Java. I download the "Linux RPM (self-extracting file)" and try to follow the instructions [here.]("http://www.java.com/en/download/help/5000010500.xml#rpm") I only get to step 4. There's no "java" file in my directory, so I tried it in other directories, got nowhere, just left it on my desktop. Changed it to executable, ran it in a terminal, now I have the "jre-6u<version>-linux-i586.rpm." Then I'm stuck on step 7 because I can't do anything with it. I just get "No such file or directory."

---

### Post by Xiong Chiamiov on 2008-04-22
You can [get it through the repos]("http://www.psychocats.net/ubuntu/java") instead of all that nasty nonsense.  Also see [how to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

BTW, .rpm's are only for Red Hat.

---

### Post by Crossbow on 2008-04-22
Repos?

---

### Post by Xiong Chiamiov on 2008-04-22
Repos is short for repositories, a very nifty thing in some distributions of Linux.  There's actually a link there in my post, just the new forums don't seem to think we need any visual clue that there *is* a link.

---

### Post by Sef on 2008-04-22
To install Java the easy way:

Applications > Add/Remove > Change the top right box to All Available Applications > Search: (type in) Sun Java 6 > click on Sun Java Web Start > Apply Changes > Apply > Close > Close

Repos are short for repositories, where most all the applications that you need are centrally located.  To read more, click [here]("http://www.ubuntu.com/community/ubuntustory/components") and [here]("https://help.ubuntu.com/community/Repositories").

---

### Post by PeterJS on 2008-04-22
> **Xiong Chiamiov said:**
> Repos is short for repositories, a very nifty thing in some distributions of Linux.  There's actually a link there in my post, just the new forums don't seem to think we need any visual clue that there *is* a link.

Think of it as an added challenge for new users :)

The real tragedy is that [installing java with apt url ](apt:/sun-java6-plugin)(< that's a link) is easier, but just as hard to read.

---

### Post by mistertee on 2008-04-22
Hi, I'm having a bit of a problem as well...I've installed both JRE 1.5 and 1.6 but I can't get Firefox or Opera to find them.  When I try this:  sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/libjavaplugin_oji.so /usr/lib/firefox/plugins/

the link comes back as broken!  What am I doing wrong?  Also, I don't see Sun Java Webstart in the packages available in Add/Remove, only the JRE and plugin both of which I've installed.

Thanks!

---

### Post by chunchengch on 2008-04-22
install Java in Hardy:

[COLOR="Red"]$ sudo apt-get install sun-java6-jre sun-java6-bin[/COLOR]

symbol link Java to Firefox:

[COLOR="Red"]$ cd /usr/lib/mozilla/plugins
$ sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so[/COLOR]

---

### Post by PeterJS on 2008-04-22
You're looking in the wrong place for the plugin, it should be at:
```

/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so

```
But more importantly, the sun-java-plugin package didn't handle this automatically for you?

---

### Post by mistertee on 2008-04-23
Nope, but your path looks like it made a valid sym link.  Thanks a bunch for that!  Now to test...standby.

---

### Post by mistertee on 2008-04-23
Woohoo!  Finally working.  But yeah I don't know what's up with the plugin packages.  I installed it for both 1.5 and 1.6, neither setup the plugins automatically.  Thanks again PeterJS!

---

### Post by Crossbow on 2008-04-23
> **Sef said:**
> To install Java the easy way:

Applications > Add/Remove > Change the top right box to All Available Applications > Search: (type in) Sun Java 6 > click on Sun Java Web Start > Apply Changes > Apply > Close > Close

Repos are short for repositories, where most all the applications that you need are centrally located.  To read more, click [here]("http://www.ubuntu.com/community/ubuntustory/components") and [here]("https://help.ubuntu.com/community/Repositories").


Oh, that. I already tried that. It's not on there.

---

### Post by Crossbow on 2008-04-23
> **Xiong Chiamiov said:**
> You can [get it through the repos]("http://www.psychocats.net/ubuntu/java") instead of all that nasty nonsense.  Also see [how to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

BTW, .rpm's are only for Red Hat.


Okay, I tried that link. It's not available with the synaptic package manager . I already installed every single thing that said "java" on it. I've still got nothing. Rebooted twice.

---

### Post by Crossbow on 2008-04-23
... so I changed the settings for updates on synaptic, and then I got a bunch of updates, which are still installing. Hopefully one of them will be what I need.

ETA: ... and now I have 29 new items that say "sun java."

---

### Post by txcrackers on 2008-04-23
If you've installed either or both of the Java versions (1.5, 6) via APT/Synaptic/whatever, there's a nifty little script that you'll want to run (and not worry about the plugin link):

```
sudo update-java-alternatives
```

Just make sure you've installed the appropriate *plugin* packages (**sun-java5-plugin**, **sun-java6-plugin**) as well as at least the Runtime.

---

### Post by Sef on 2008-04-23
> Oh, that. I already tried that. It's not on there.

1) Did you change the top box to 'All Available Applications'.

2) If you did, then you have problem with the repositories.

3) That is how I download java, so I know it works.

---

### Post by Crossbow on 2008-04-23
I installed all of these. I'm still getting error messages. 

[IMG]http://img.photobucket.com/albums/v97/Crossbow/Screenshot-SynapticPackageManage-1.png[/IMG]

---

### Post by ad_267 on 2008-04-23
Whoa you don't need all of that installed.
All I have installed is sun-java6-bin, sun-java6-re and sun-java6-plugin and everything works fine for me. I installed java using the restricted extras package.

---

### Post by Crossbow on 2008-04-23
> **ad_267 said:**
> Whoa you don't need all of that installed.
All I have installed is sun-java6-bin, sun-java6-re and sun-java6-plugin and everything works fine for me. I installed java using the restricted extras package.

I figured I didn't need all of it, but I did it anyway. Still not working, though. And yeah, I checked to make sure it's enabled on my browser. 

I only even know about it because this silly jigsaw puzzle site informed me I didn't have Java. It's no big deal but it's REALLY BUGGING ME that I can't figure out what's wrong!

---

### Post by PeterJS on 2008-04-23
I assume you're using firefox, what does about:plugins have to say about java? Have you looked at update-java-alternatives as txcrackers mentioned above? which jres/jdks does it show?

---

### Post by ad_267 on 2008-04-23
Try uninstalling all of those java packages and then install the package "ubuntu-restricted-extras." That package installed java properly for me as well as other things like flash and codecs for mp3.

---

### Post by Crossbow on 2008-04-23
> **ad_267 said:**
> Try uninstalling all of those java packages and then install the package "ubuntu-restricted-extras." That package installed java properly for me as well as other things like flash and codecs for mp3.

All right, trying that now.

ETA: No change. 

> **PeterJS said:**
> I assume you're using firefox, what does about:plugins have to say about java? Have you looked at update-java-alternatives as txcrackers mentioned above? which jres/jdks does it show?

Yes, Firefox 2.0.0.14. I'm not sure where you want me to look about the plugins. In add-ons>get add ons, there are no Java items. 

Yes, I ran update-java-alternatives but I didn't know what the results meant. I'll do it again.

ETA: 

usage: update-java-alternatives [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help

---

### Post by stchman on 2008-04-23
> **Crossbow said:**
> I am having a terrible time trying to install Java. I download the "Linux RPM (self-extracting file)" and try to follow the instructions [here.]("http://www.java.com/en/download/help/5000010500.xml#rpm") I only get to step 4. There's no "java" file in my directory, so I tried it in other directories, got nowhere, just left it on my desktop. Changed it to executable, ran it in a terminal, now I have the "jre-6u<version>-linux-i586.rpm." Then I'm stuck on step 7 because I can't do anything with it. I just get "No such file or directory."

To install Java, first enable all the repositories and do the following in a terminal:

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

If you want Java 1.6 then sub 6 for 5 in the above statement.

---

### Post by Crossbow on 2008-04-23
> **stchman said:**
> To install Java, first enable all the repositories and do the following in a terminal:

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

If you want Java 1.6 then sub 6 for 5 in the above statement.

No change. 

According to the Java website, I have it and the applets are working.

---

### Post by Crossbow on 2008-04-23
I'm giving up. Java appears to be installed and working, but for whatever reason this one particular site that used to work fine for me with Ubuntu 6.10 is not working with 7.10.
[http://www.jigzone.com/](http://www.jigzone.com/)

Message:

[http://www.jigzone.com/puzzles/F9055D54E579](http://www.jigzone.com/puzzles/F9055D54E579) wants to load an applet.
GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!

But when I click the "trust applet" option, still nothing.

---

### Post by Crossbow on 2008-04-23
Okay, I lied, I'm not giving up. This is driving me crazy.

Just tried it with Opera instead of Firefox. Same problem.

---

### Post by PeterJS on 2008-04-23
I guess i should have been more clear, the option on update-java-alternative I was  asking about was running it with the -l (for list) flag, ie:
```

update-java-alternative -l

```
That should show you all the java instances that are installed that can be used. If it's the case that the jvm you want is installed but not in use, you can change it there, not sure which option you want. A more manual method would be installing galternatives, and setting all the java options to use the jvm you want.

---

### Post by Crossbow on 2008-04-23
> **PeterJS said:**
> I guess i should have been more clear, the option on update-java-alternative I was  asking about was running it with the -l (for list) flag, ie:
```

update-java-alternative -l

```
That should show you all the java instances that are installed that can be used. If it's the case that the jvm you want is installed but not in use, you can change it there, not sure which option you want. A more manual method would be installing galternatives, and setting all the java options to use the jvm you want.


It says: 

java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj

---

### Post by PeterJS on 2008-04-23
> **Crossbow said:**
> It says: 

java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj

There we go. See the number there in the second column? that's the priority, gcj has a priority through the roof so it gets used. To change to use the sun jvm you would run:
```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by Crossbow on 2008-04-23
> **PeterJS said:**
> There we go. See the number there in the second column? that's the priority, gcj has a priority through the roof so it gets used. To change to use the sun jvm you would run:
```

sudo update-java-alternatives -s java-6-sun

```

It made no difference. 

I'm thinking it may have nothing to do with Java at all.

---

### Post by oldsoundguy on 2008-04-23
in a quick scan, did not see this guide posted ..  handiest thing there is for installing a LOT of things including Java:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

There soon will be one for Hardy for those using same .. they have a guide for many versions other than the one linked above.

Sharpen up those cut and paste skills and learn to use dual windows!!

---

### Post by Crossbow on 2008-04-23
> **oldsoundguy said:**
> in a quick scan, did not see this guide posted ..  handiest thing there is for installing a LOT of things including Java:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

There soon will be one for Hardy for those using same .. they have a guide for many versions other than the one linked above.

Sharpen up those cut and paste skills and learn to use dual windows!!

OK, thanks, but Java is definitely installed now. I don't think that's the problem. I'm now getting a "failed to start in a reasonable time" message.

---

### Post by Crossbow on 2008-04-24
I THINK I KNOW THE PROBLEM. 

Only I don't know how to fix it. On the Firefox help site someone pointed out that I have two flash files installed and I need to delete the older one. Problem is, I don't know how. 

**Cannot move "/usr/lib/fir...ashplayer.so" to the trash because you do not have permissions to change it or its parent folder.**

I assume I can do it in a terminal only I don't know the commands.

---

### Post by PeterJS on 2008-04-24
Which two flash players do you have installed? And the reason you can't just delete the files from nautilus is that they are system files (ie owned by root), and only the onwer of a file (or the directory enclosing it) can delete a file. If you want to run nautilus with elevated privilages, you can by opening the run dialog (alt+f2) with the command **gksudo nautilus**. Gksudo is Gtk super user do. Or from the terminal you can cd /to/the/path/to/flash/ and then delete it with:
```

sudo rm filename

```

---

### Post by Crossbow on 2008-04-24
I have: 

Shockwave Flash 9.0 r124
Shockwave Flash 9.0 r48 

Which are in two different places. I'd never have known they were both there except that the Firefox form automatically pulls that information when you post, which is very handy.

ETA: 

"rm: cannot remove `libflashplayer.so': No such file or directory"

Do I have to put in the whole path?

ETA: 

 rm: cannot remove `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory

ETA: More confused than ever now. 

The flashplayer file is gone, even though I kept getting the message that it could not be removed. How could that happen? And I'm still having the exact same problem - the file being gone didn't solve anything.

---

### Post by Crossbow on 2008-04-24
Plug-ins: 

Shockwave Flash
    File name: /usr/lib/flashplugin-nonfree/libflashplayer.so
    Shockwave Flash 9.0 r124

Totem Web Browser Plugin 2.20.0
    File name: /usr/lib/totem/libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

Windows Media Player Plug-in 10 (compatible; Totem)
    File name: /usr/lib/totem/libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

DivX® Web Player
    File name: /usr/lib/totem/libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

QuickTime Plug-in 7.2.0
    File name: /usr/lib/totem/libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

GCJ Web Browser Plugin 0.92
    File name: /usr/lib/classpath/libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

Java(TM) Plug-in 1.6.0_03-b05
    File name: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

---

### Post by Crossbow on 2008-04-27
Still not working. I've asked on another Ubuntu forum and a Firefox forum. People seem to agree it's a Java problem, but the Java applet tests work fine.

---

### Post by drhiii on 2008-04-27
I am having same No-Joy issues with Java and Firefox, in this case, 3. 

Java installed fine.  When I do an    about:plugins    tho, I get the following which is mighty thin for reported plugins.  I followed a Multimedia How-To to a T and everything else seemed to play nice, except for FF3. Sigh... still, ya have to love Ubuntu.  I do not mind this stuff at all.  An adventure fer sure, and considering that I can pretty much do everything anyway, hey... am beyond happy.



Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No

---

### Post by Crossbow on 2008-04-27
Also did not work: icedtea-java7

---

### Post by boazjones on 2008-04-28
I'm having a problem with the Sun Java 6.0 Plugin. "Sun Java 6.0 Plugin cannot be installed on your computer type (amd64). Either the application requries special hardware features or the vendor decided to not support your computer type." Is there an alternative?

Furthermore, I have downloaded NetBeans IDE 6.1 - "netbeans-6.1-linux.sh"

I am new, so I don't quite have the hang of the cd (change directory), ls (navigate to list files), and console installation shuffle required.

Please send help? Thank you.

---

