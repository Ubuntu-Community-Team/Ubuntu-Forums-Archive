---
title: "Installing Java: Options"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by brodiesel on 2008-10-29
My attempts to install Java (so I can finally look at tall those pretty websites...) has demonstrated to me how much of a newbie I am. 

Trying to use synaptic, I'm not sure which version of RuntimeEnvironment to download. Sun? Open JDK? 

I have downloaded a package from the java site, but I'm not sure its the right one as all of their instructions are for OpenSuse and other such distros (I have downloaded both jre-6u7-linuxi586.bin and jre-. 
6u10-linux-i586.bin).
So command line or gui, how do I install this? (caveat: if you give me a command line way, I may be back here shortly asking questions)

---

### Post by AndyCooll on 2008-10-29
Either would be fine. I'd suggest OpenJDK.

:cool:

---

### Post by brodiesel on 2008-10-29
thanks andy, i saw the note you left on the other thred. what i tried was using synaptic to download and install the sun java RE package (with its dependent whatevers), and while the package successfully downloaded and installed, but the pages still wont load properly, and i am being told i am missing the plugin. 

the only thing i have thought of to try is enabling java in firefox prefs, and that was already turned on.

anybody have any ideas?

---

### Post by brodiesel on 2008-10-29
y'know, another thing about firefox while I'm on the topic. I have tried unsccuessfully to add things like ad-block, the google toolbar, google notebook, etc and none of them are working. They are all listed as downloaded and enabled in my browser, yet none of them work. 

????

---

### Post by jespdj on 2008-10-29
Sun Java 6 is the version that's most compatible. OpenJDK is good because it's open source and it's the default Java on Ubuntu 8.10, but unfortunately it doesn't work with all websites that use Java applets.

Install Sun Java 6 like this:
```
sudo apt-get install sun-java6-plugin
```
Then make sure that Sun Java is the Java that's actually used on your system (if you have multiple Java versions installed):
```
sudo update-alternatives --config java
```
Select Sun Java 6 in the menu that you see with this command.

---

### Post by kansasnoob on 2008-10-29
If this is Ubuntu 8.04 (aka Hardy) I always just install restricted-extras, at terminal:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

That should get you the bare minimum essential sun-java6-*** and some other goodies. 

What I'm unsure of is that if you've installed packages that might interfere with that we need to check for dependency problems so (again at terminal):

```
sudo apt-get -f install
```

If there's an output something like "use apt-get auto-clean" (or auto-remove) say yes "y" but also please copy-n-paste that entire output here, OK?

But I'd think you'll also want the best possible Flash so also do this:

```
sudo apt-get remove --purge flashplugin-nonfree
```

If you've installed a tar.gz version of flash also do this (if you're not sure you can do it anyway):

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Then go to the Adobe site and download the .deb Flash 10:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

When you're done go to File > Quit in Firefox - quit Firefox - then restart Firefox.

If you still have problems go to the url (address) window in Firefox and type:

```
about:plugins
```

And post that output here.

---

### Post by kansasnoob on 2008-10-29
> **brodiesel said:**
> y'know, another thing about firefox while I'm on the topic. I have tried unsccuessfully to add things like ad-block, the google toolbar, google notebook, etc and none of them are working. They are all listed as downloaded and enabled in my browser, yet none of them work. 

????

Each time you make changes to Firefox plugins you need to restart Firefox. For some reason I find that quitting Firefox by going to File > Quit works better than just clicking the X in the upper right hand corner.

I have occasionally had to restart the desktop by Ctrl > Alt > Backspace. I don't know why:confused:

---

### Post by brodiesel on 2008-10-29
thanks for the advice. Iwas at least able to confirm that I have java, and two versions at that.

so i did this:

> b@b-laptop:~$ sudo update-alternatives --config java
[sudo] password for b: 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2    
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
b@b-laptop:~$ 



and when i went to test it at the java site, i got this:

> Java Runtime Environment is not working on your system.


I also amde sure once again that java was selected to work on firefox and then restarted firefox. 

I'm gettin' hosed here...

---

### Post by kansasnoob on 2008-10-29
If this is 32 bit Hardy just do what I said.

It looks like you just have dependency problems.

We'll get it fixed!

---

### Post by kilroywashere on 2008-10-29
If you've followed jespdj's instructions to install the Sun Java 6 plug-in but are still having trouble, you may need to create the following symbolic links

```
ln -s etc/alternatives/mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

ln -s /etc/alternatives/firefox-javaplugin.so  /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

And then restart Firefox.  I ran into a similar problem when upgrading java distributions.  
[http://www.javatester.org/version.html]("http://www.javatester.org/version.html") was useful for me when trying to determine which plugin was the working.  Good luck

---

### Post by brodiesel on 2008-10-29
sweet! somehow i missed your earlier post, kn. anyway, i ran both of the appgets that you suggested, and now java is running. the only remamining question is that it says that I am using an older version (java version 6, udate 0) and that I should upgrade. necessary?

regardless, thanks for the help. the fact that there are so many users that are willing to help some moron they dont know use this product is one of my favorite things about ubuntu. i never walk away empty handed. hopefully someday i can know enough about this stuff to help somebody else....

---

### Post by kansasnoob on 2008-10-29
> **brodiesel said:**
> sweet! somehow i missed your earlier post, kn. anyway, i ran both of the appgets that you suggested, and now java is running. the only remamining question is that it says that I am using an older version (java version 6, udate 0) and that I should upgrade. necessary?

regardless, thanks for the help. the fact that there are so many users that are willing to help some moron they dont know use this product is one of my favorite things about ubuntu. i never walk away empty handed. hopefully someday i can know enough about this stuff to help somebody else....

Am I kn. ?

Hey I'm a noob too! I tried Linux several years ago when Lindows came out and hated it! February of this year I decided to give gOS a whirl, then Freespire, and I discovered Ubuntu!

If I had to make comparisons discovering Ubuntu was like discovering Win 95 after dealing with the Tandy!

As for the upgrade prompt, if you're getting an upgrade prompt in the terminal I'd like to see the actual text. Just copy-n-paste it here.

---

### Post by kansasnoob on 2008-10-29
Oh, and no Linux user is a moron!

We all start knowing nothing! I know only 1% of what I should know but that's OK.

The only real morons are those that think Windows is the only way!

---

### Post by brodiesel on 2008-10-29
yeah, i was abbreviating Kansas Noob to kn, but if you're not into the whole brevity thing... 

anyway, the plot thickens...

no, the upgrade prompt was from the Java webpage that I've been using to test if it was working properly. the last time, after doing those installs, it said it was working, but was outdated. i took its word that it was working, but then i went to the two original webpages that were giving me problems, and now they no longer say that i am missing plugins, but where the applet is supposed to run there's an empty box and on the bottom bar of firefox it says "applet not initialized." 

do you think this is an issue of updates, or might this somehow be related to the same reason none of my add-ons work?

---

### Post by kansasnoob on 2008-10-29
> **brodiesel said:**
> yeah, i was abbreviating Kansas Noob to kn, but if you're not into the whole brevity thing... 

anyway, the plot thickens...

no, the upgrade prompt was from the Java webpage that I've been using to test if it was working properly. the last time, after doing those installs, it said it was working, but was outdated. i took its word that it was working, but then i went to the two original webpages that were giving me problems, and now they no longer say that i am missing plugins, but where the applet is supposed to run there's an empty box and on the bottom bar of firefox it says "applet not initialized." 

do you think this is an issue of updates, or might this somehow be related to the same reason none of my add-ons work?

Well, briefly, you're almost always better off using packages from the repos. Which is to say that i'd stay with packages in Ubuntu's repos unless there's a real reason not to.

Basically, if it ain't broke don't fix it!

In the case of Flash I'm pretty sure Hardy still has flash 9 in the repos and Flash 10 is far superior!

Anyway if I don't feed my goats they're going to eat me!

---

### Post by brodiesel on 2008-10-29
aaahhh.... but you see, it IS broke, and I don't know how to fix it...

---

