---
title: "Installed Java, still cant load flash"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Corey4666 on 2008-07-27
I have had this problem since installing Ubuntu hardy on my dell inspiron1501. websites like youtube.com will not load the video at all, it does not even show the box where the video should be. Also a program that uses Java would never start up, Then i installed Java and now the program that depends on Java now works and loads. Still youtube.com does not load video I am not sure what to do I've followed a few topics on this website and still cant fix the problem. 

This is what my Terminal says:

```
eviscerate@eviscerate-laptop:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

```

Javas website has a test to detect if Java is working and it says if you can see the little guy dancing in the window it is working. I can see it but still like i said youtube wont work.

---

### Post by eightmillion on 2008-07-27
Have you installed the flash plugin? If you haven't, type this in a terminal:
> sudo apt-get install flashplugin-nonfree
then restart firefox.

---

### Post by Corey4666 on 2008-07-27
Thanks for the super fast reply this is what it says.

```
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by eightmillion on 2008-07-27
Go to Tools>Addons and click on the plugins tab. Make sure flash is listed there and enabled.

---

### Post by Corey4666 on 2008-07-27
Quick time enabled
Shockwave Flash enabled
Totem, Vlc, Wmp Enabled

Everything is enabled from DivX to a iTunes plugin etc.

---

### Post by rockerphil on 2008-07-27
i know it's a bit of a pain, but have you considered going back to FF2? it seems to like Java & Flash better (at least for me)

---

### Post by RuleMaker on 2008-07-27
In firefox's addressbar type "about:plugins" (without quotes) and see if you have "Shockwave Flash" installed. If not then you have to [download flash player]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") and install it.

---

### Post by Corey4666 on 2008-07-27
> **rockerphil said:**
> i know it's a bit of a pain, but have you considered going back to FF2? it seems to like Java & Flash better (at least for me)

whats FF2? a plugin? is it in the Add/Remove thing?


also the about : plugins says i got shockwave and it says its enabled.

---

### Post by flick on 2008-07-27
FF2 is just an abbreviation for Firefox 2. If you're running Hardy Heron, by default Firefox 3 is installed.

After installing the flash plugin, logging out and then logging back in has done the trick for me in the past. Your mileage may vary.

---

### Post by Corey4666 on 2008-07-27
ohh lol FF yeah Firefox should of realized that and yes i got FF3 installed. I installed the plugins long ago maybe a week so i restarted plenty of times since then.

---

### Post by flick on 2008-07-27
Any chance you have javascript turned off in your browser, or some extension like NoScript loaded on your copy of Firefox? YouTube won't work in those cases.

For what it's worth, I use NoScript myself, because I'm a paranoid freak.

---

### Post by koji042 on 2008-07-27
I think VLC may have taken over Flash Player's role in Firefox. That might be the reason why flash doesn't work despite the fact that you have flash installed. If that's the case, there should be a list in Preferences somewhere that deals with all file extensions in Firefox. That or try disabling VLC and see if anything heppens. 

I wish I could help you more, but I'm not at home right now. >.<

Oh well, hope that helps. :)

---

### Post by RuleMaker on 2008-07-27
Java has nothing to do with flash, if you have shockwave flash installed and enabled and flashplugin-nonfree too then you should be able to view flash.
If not then try this:
```
sudo apt-get purge flashplugin-nonfree
```
And then reinstall it:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by gjoellee on 2008-07-27
I have had a problem one time there was a plugin that disturbed flash, if this is the case remove the plugin the disturbs flash...

Also try to use flash 10BETA

---

### Post by mick222 on 2008-07-27
flash 10 works fine for me i  think you should try disabling the vlc plugin

---

### Post by stevoo on 2008-07-27
Indeed try Flash 10 Beta.
It works fine for me having problem with others.

So DOwnload here 
[Download !! ! ! !]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")

Open the directory extract the tar.gz file
Open a terminal and cd into the dir : flashplayer10_install_linux_070208
then run : 
```
 sh flashplayer-installer 
```
that will begin the installation
close all firefox windows and re open them and see ....

---

### Post by alzie on 2008-07-27
You my try removing java6 and replacing it with sun java5.

I know there are issues with flash games at pogo and yahoo and the current solution is to go back to sun java5

I have no problems with you tube and I'm still using flash nonfree from the repositories.

I hope this is a help.

---

### Post by Corey4666 on 2008-07-27
about:plugins says i got flash installed. I have not tried firefox2 i didn't think downgrading would fix the problem but i will try it when i get the chance.

---

### Post by Corey4666 on 2008-08-03
I tried everyones suggestions except for flash 10 and the idea to downgrade to Java 5 but the only reason i didn't try those is because i don't know how.

---

### Post by alzie on 2008-08-03
If you want to try downgrading flash, open synaptic package manager
System>Administration>Synaptic Package Manager

Search for "sun java"

Mark sun-java6-bin, sun-java6-jre and sun-java6-plugin for removal.
Mark sun-java5-bin, sun-java5-jre and sun-java5-plugin for installation.
Click Apply.

I hope this helps

---

### Post by Corey4666 on 2008-08-03
thanks for the help i cant try it right now but i will get back to you as soon as i can maybe tommarow hopefully

---

