---
title: "What's the deal with Java?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by detroit/zero on 2008-05-06
OK. I just did a fresh install of 8.04. The Firefox 3 beta that ships with it is not at all to my liking, mainly because of the Beta status and lack of development for extensions I've grown accustomed to using and themes that make the browser integrate well into the desktop theme I use.

I installed Swiftweasel. I was able to restore my previous profile and have all my extensions, bookmarks, search plugins, etc. 

There seems to be a problem with Java, though. The Java plugin that comes with FF3 does not work with all Java web content - specifically Yahoo games. 

Long story short - I removed FF3 and anything to do with Java anywhere in my computer. I also removed Swiftweasel. I did a re-install of Swiftweasel, and then used Synaptic to reinstall the Sun JRE and browser plugin.

This is where I'm stuck:

[[IMG]http://img396.imageshack.us/img396/1627/screenshotfa3.th.png[/IMG]]("http://img396.imageshack.us/my.php?image=screenshotfa3.png")

Clicking on the Install Missing Plugin button does  tell me that I need to install the Java Runtime Environment. Installing it, however, is not a matter of clicking on the Install button; it's a matter of then being redirected to the Java website and following a long process of extracting, installing, and configuring of this that and the other that doesn't even work.

My question is rather simple, while I'm sure the answer is not: How can I make Java work?

I'll hold off on the rant about how devs should make something as essential to the modern web-browsing experience as Java a little easier to install and not rely on an open source equivalent (Iced Tea?) that doesn't even work as advertised.

I have to admit I was a little tantalized by the claims of FF3 being more integrated into the desktop and having the ability to run Java apps outside the browser and all that.. But  while some people can make it work, I doubt most can. Or at least I can't.

Anyways, can somebody help me with this Java thing? I'm sure there's some other Yahoo gamers in the forums..

---

### Post by c4v3m4n on 2008-05-06
This link helped me get java working, hope it helps you!

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/")

---

### Post by ggaaron on 2008-05-06
For me getting java to work was onty installing open-jdk in synaptic. If you really don't like it, you can use sun-jdk. Don't use iced-tea7 if you want stable java - it is development version.

---

### Post by HotShotDJ on 2008-05-06
> **detroit/zero said:**
> My question is rather simple, while I'm sure the answer is not: How can I make Java work?With Sun having open sourced Java, someday the openjdk stuff will work perfectly.  That day is not today.  Since I've never contributed even one line of code to any project, I am in no position to criticize the decision of developers to include that version of Java with Ubuntu 8.04.  I'll just say that I found it as useless as you did and leave it at that.

Luckily, it is VERY easy to get Java up and running by just using the tools provided in Ubuntu -- Synaptic.  My guess is that you may have installed the sun jre or jdk package but not the plugin.  The following is a list of steps, most of which I'm pretty sure you know already, but are included for others who may have the same problem and find this thread.

[LIST=1]
[*]Open Synaptic -- search for openjdk.  Mark every openjdk and icedtea package for complete removal
[*]Click "Apply"
[*]Now, change your search.  This time, search for sun-java.
[*]Mark for installation sun-java6-plugin (this should also pull in sun-java6-jre and sun-java6-bin.  If you need the full jdk, you may also select that.  Most people don't need the jdk.)
[*]Click "Apply"
[*]Close all open applications, log out, then log back in -- no need to reboot.
[*]Open Firefox and enjoy Java goodness
[/LIST]

---

### Post by ChompTheMan on 2008-05-06
Is *libjavaplugin_ijo.so* in /usr/lib/firefox/plugins/?  This was my problem and was solved by:

```
cd /usr/lib/firefox/plugins/

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_ijo.so
```

---

### Post by detroit/zero on 2008-05-06
OK, I got it figured out. Both HotshotDJ and ChompTheMan were very helpful, and I had to use both their methods to make things work.

Firstly, from HotShotDJ's post: I once again went through Synaptic and ticked everything that had to do with Java and marked it for complete removal. One thing that had escaped my notice previously was the Ubuntu Restricted Extras - the one with Flash, media support, some other things... and **Java**. Trying to make Java work with this plugin installed is an exercise in futility. I don't know enough to guess why, but I know over the last couple days I tried a million different ways to un-/re-install Java and the only package that got by me was the Restricted Extras. Once that thing was gone everything started to go easier. I marked Sun Java Plugin as an install and the dependencies came along with it.

Once it was finished, I did as Chomp suggested and made the symbolic link to the Java plugin module. Since I'm using Swiftweasel, the location was actually in /usr/local not /usr/lib, but it was easy enough to find.

One thing I did have to figure out through trial and error was that for Yahoo Games, the Java 1.5 plugin is the one to use, not the Java 1.6.

Let me say that again: Java 1.6 **will not** work with Yahoo Games. I had to use version 1.5 to make it work.

Now that all that is out of the way, I guess I have to go manually install flash and a host of other things. Oh well.. this is how we learn, right fellas?

---

### Post by zhanglini on 2008-05-09
> **HotShotDJ said:**
> With Sun having open sourced Java, someday the openjdk stuff will work perfectly.  That day is not today.  Since I've never contributed even one line of code to any project, I am in no position to criticize the decision of developers to include that version of Java with Ubuntu 8.04.  I'll just say that I found it as useless as you did and leave it at that.

Luckily, it is VERY easy to get Java up and running by just using the tools provided in Ubuntu -- Synaptic.  My guess is that you may have installed the sun jre or jdk package but not the plugin.  The following is a list of steps, most of which I'm pretty sure you know already, but are included for others who may have the same problem and find this thread.

[LIST=1]
[*]Open Synaptic -- search for openjdk.  Mark every openjdk and icedtea package for complete removal
[*]Click "Apply"
[*]Now, change your search.  This time, search for sun-java.
[*]Mark for installation sun-java6-plugin (this should also pull in sun-java6-jre and sun-java6-bin.  If you need the full jdk, you may also select that.  Most people don't need the jdk.)
[*]Click "Apply"
[*]Close all open applications, log out, then log back in -- no need to reboot.
[*]Open Firefox and enjoy Java goodness
[/LIST]

This worked for me thanks

---

### Post by alzie on 2008-05-11
After banging my head trying to get pogo.com to work combing detroit/zero and HotShotDJ's solutions worked for me.  Unistalling java and reinstalling with java 1.5 seems to have done the trick.  Many thanks :)

Edit: marked sun-java5-plugin

---

### Post by neutralstorm on 2008-05-11
> **alzie said:**
> After banging my head trying to get pogo.com to work combing detroit/zero and HotShotDJ's solutions worked for me.  Unistalling java and reinstalling with java 1.5 seems to have done the trick.  Many thanks :)

Edit: marked sun-java5-plugin

Thanks.

This was the answer for me too.
1.6 just would not work correctly. Removed it and installed 1.5 and all seems to work now. Gotta have my pogo fix. :lolflag:

---

### Post by BCtom on 2008-05-18
> **neutralstorm said:**
> Thanks.

This was the answer for me too.
1.6 just would not work correctly. Removed it and installed 1.5 and all seems to work now. Gotta have my pogo fix. :lolflag:

Yup--same here. Works like a charm with Sun-Java 5 (1.5) for Hardy and FF3. Now the Ububtu and Pogo communities can game happily with hours of enjoyment.

I have friends too who are going through Pogo withdrawal! They need this fix too! LOL

---

### Post by Itzmattu on 2008-05-27
> **alzie said:**
> After banging my head trying to get pogo.com to work combing detroit/zero and HotShotDJ's solutions worked for me.  Unistalling java and reinstalling with java 1.5 seems to have done the trick.  Many thanks :)

Edit: marked sun-java5-plugin

I actually just tried this myself. Removed all the linked files from Java6, uninstalled the package, installed Java5, yet pogo is still not working. Java6 and 5 both have the same problem for me. They both work fine as far as detecting that Java is working on FF3b5, but when the screen comes up to load the pogo game it eventually goes to a screen saying "You are playing as <user name>" and I hit OK. After that it simply loads the main pogo page again, with no user being logged in. This is still taking place in the pop-up window where it was originally loading, so I still have pogo.com with my mom's account logged in behind everything.

So basically it seems like Java is working, yet it is redirecting incorrectly. I have added pogo.com as an exception for FF3's pop-up blocker, and also disabled the Adblock Plus extension.

Any hints?

---

### Post by BCtom on 2008-05-27
> **Itzmattu said:**
> I actually just tried this myself. Removed all the linked files from Java6, uninstalled the package, installed Java5, yet pogo is still not working. Java6 and 5 both have the same problem for me. They both work fine as far as detecting that Java is working on FF3b5, but when the screen comes up to load the pogo game it eventually goes to a screen saying "You are playing as <user name>" and I hit OK. After that it simply loads the main pogo page again, with no user being logged in. This is still taking place in the pop-up window where it was originally loading, so I still have pogo.com with my mom's account logged in behind everything.

So basically it seems like Java is working, yet it is redirecting incorrectly. I have added pogo.com as an exception for FF3's pop-up blocker, and also disabled the Adblock Plus extension.

Any hints?

Hello Itzmattu,

I think part of your problem could be that you may still have other Java packages installed. For me it was a process of elimination, changing from Java6 to Java5, but also un-installing the other Java packages too, although not all of them. 

I originality had: openjadk-6  & Icedtea-Java 7. Once these were gone (un-installed) I hit paydirt!

Also, when I firsted loaded pogo.com with java5, it took a long time to start a game, like five minutes. Once I opend a few games and starting using them, everything started to become faster.

---

### Post by jd1ckson on 2008-05-29
Thank you so much!!!! I have spent 15+ hours on this problem, and the re-direct for the plugin/reinstalling all my Sun Java actually worked!!!! You guys rock out!

---

### Post by espiritu on 2008-06-01
i've tried just about all the solutions on the forum offered, i still am having trouble getting my java to work.

I have uninstalled all the other java plugins and reverted to java 1.5

tried reconfiguring using that link on the first page of this thread. Tried updating, installing from sun-java site. 

Nothing seems to work. Can anyone help me?

---

### Post by S1xp4ck on 2008-06-27
Thanks all, reverting to 1.5 did the trick for me too.  1.6 just doesn't seem to be working properly on sites like pogo and yahoo.  I too have banged my head for days on this issue.  I thank you all :D

---

### Post by onestep on 2008-06-29
I too could not play Yahoo Games on 8.04. I followed HotShotDJ's post but installed java5 and NOT 6 as suggested. Works GREAT!! Yahoo games now work.

---

### Post by rlacroix8 on 2008-06-29
I am a newbie with the Java problem and tried the method in [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/) However, got stuck on adding /usr/lib/jvm/java-6-sun to file /etc/jvm , presumably in terminal. Apparently I created inadvertently a file /etc/.jvm.swp which the system now recommends me to delete. Please help with (i) deleting this swap file and (ii) editing the /etc/jvm file.
Thanks

---

### Post by rlacroix8 on 2008-06-29
Many thanks. After hours of unfruitful attempts to get my Java to work, your suggestion was the answer!

---

### Post by rlacroix8 on 2008-06-29
Many thanks. After hours of unfruitful attempts to get my Java to work, your suggestion was the answer!

> **HotShotDJ said:**
> With Sun having open sourced Java, someday the openjdk stuff will work perfectly.  That day is not today.  Since I've never contributed even one line of code to any project, I am in no position to criticize the decision of developers to include that version of Java with Ubuntu 8.04.  I'll just say that I found it as useless as you did and leave it at that.

Luckily, it is VERY easy to get Java up and running by just using the tools provided in Ubuntu -- Synaptic.  My guess is that you may have installed the sun jre or jdk package but not the plugin.  The following is a list of steps, most of which I'm pretty sure you know already, but are included for others who may have the same problem and find this thread.

[LIST=1]
[*]Open Synaptic -- search for openjdk.  Mark every openjdk and icedtea package for complete removal
[*]Click "Apply"
[*]Now, change your search.  This time, search for sun-java.
[*]Mark for installation sun-java6-plugin (this should also pull in sun-java6-jre and sun-java6-bin.  If you need the full jdk, you may also select that.  Most people don't need the jdk.)
[*]Click "Apply"
[*]Close all open applications, log out, then log back in -- no need to reboot.
[*]Open Firefox and enjoy Java goodness
[/LIST]

---

### Post by isbront on 2008-09-21
> **HotShotDJ said:**
> With Sun having open sourced Java, someday the openjdk stuff will work perfectly.  That day is not today.  Since I've never contributed even one line of code to any project, I am in no position to criticize the decision of developers to include that version of Java with Ubuntu 8.04.  I'll just say that I found it as useless as you did and leave it at that.

Luckily, it is VERY easy to get Java up and running by just using the tools provided in Ubuntu -- Synaptic.  My guess is that you may have installed the sun jre or jdk package but not the plugin.  The following is a list of steps, most of which I'm pretty sure you know already, but are included for others who may have the same problem and find this thread.

[LIST=1]
[*]Open Synaptic -- search for openjdk.  Mark every openjdk and icedtea package for complete removal
[*]Click "Apply"
[*]Now, change your search.  This time, search for sun-java.
[*]Mark for installation sun-java6-plugin (this should also pull in sun-java6-jre and sun-java6-bin.  If you need the full jdk, you may also select that.  Most people don't need the jdk.)
[*]Click "Apply"
[*]Close all open applications, log out, then log back in -- no need to reboot.
[*]Open Firefox and enjoy Java goodness
[/LIST]
cannot locate sun-java6-plugin in step 4. please help as am having spades withdrawal and may need to resort to the dark side for fix.

---

### Post by BCtom on 2008-09-21
> **isbront said:**
> cannot locate sun-java6-plugin in step 4. please help as am having spades withdrawal and may need to resort to the dark side for fix.

Hi, 

You may need to just type in "Java" to broaden your search with synaptic. It is there. :)

As you can tell this is a work in progress issue with everyone trying to get onto Pogo with Ubuntu, FireFox and Open Source Java. It worked for me on my P.C., but it didn't on my laptop.

Hope this helps you out.

---

### Post by isbront on 2008-09-21
> **BCtom said:**
> Hi, 

You may need to just type in "Java" to broaden your search with synaptic. It is there. :)

As you can tell this is a work in progress issue with everyone trying to get onto Pogo with Ubuntu, FireFox and Open Source Java. It worked for me on my P.C., but it didn't on my laptop.

Hope this helps you out.

did "java" search.  still can't find sun-java6-plugin. does it have another name?

---

### Post by BCtom on 2008-09-21
> **isbront said:**
> did "java" search.  still can't find sun-java6-plugin. does it have another name?
  
No, that should of worked? The only other thing I can think of is you may not have your Synaptic Package Manager able to search all the repositories in the "main server" or restricted/multivers servers.

This is what mine looks like when I search "java."

 [IMG]file:///home/tom/Desktop/Screenshot-Synaptic%2520Package%2520Manager%2520.png[/IMG]

---

### Post by alzie on 2008-09-22
Isbront,  do you have "restricted" and "multiverse" enabled?

Look under system>administration>software sources

You'll need these to get sun-java

I hope this helps.

---

### Post by semcapital on 2008-09-22
Hello.

I'm having the same problem as isbront. I have main, universe, restricted and multiverse repositories checked. I am using 64bit linux, and it seems that the package sun-java6-plugin is only available for i386, unlike the other sun-java6-*! Does anybody know why? Do I have to build it from source? :confused:

[http://packages.ubuntu.com/hardy/sun-java6-plugin](http://packages.ubuntu.com/hardy/sun-java6-plugin)
[http://packages.ubuntu.com/hardy/sun-java6-bin](http://packages.ubuntu.com/hardy/sun-java6-bin)

---

### Post by ggaaron on 2008-09-22
You can't install it from source as it is binary only and only provided for 32 bits just as sun-java. If you want sun-java on 64 bit system you have to use 32 bit browser. gcj-plugin supports 64 bit, but I don't know if it works with sun-java.

---

### Post by semcapital on 2008-09-22
Well, I guess I'll try gcj then... :(
But there is sun-java6 for 64bits. You can see it in the repository. These are available on i386 and amd64:
[http://packages.ubuntu.com/hardy/sun-java6-bin](http://packages.ubuntu.com/hardy/sun-java6-bin)
[http://packages.ubuntu.com/hardy/sun-java6-jdk](http://packages.ubuntu.com/hardy/sun-java6-jdk)
[http://packages.ubuntu.com/hardy/sun-java6-demo](http://packages.ubuntu.com/hardy/sun-java6-demo)

These are architecture independent:
[http://packages.ubuntu.com/hardy/sun-java6-doc](http://packages.ubuntu.com/hardy/sun-java6-doc)
[http://packages.ubuntu.com/hardy/sun-java6-fonts](http://packages.ubuntu.com/hardy/sun-java6-fonts)
[http://packages.ubuntu.com/hardy/sun-java6-javadb](http://packages.ubuntu.com/hardy/sun-java6-javadb)
[http://packages.ubuntu.com/hardy/sun-java6-jre](http://packages.ubuntu.com/hardy/sun-java6-jre)

The only package from the sun-java6 "family" that is not available on amd64 is the plugin:
[http://packages.ubuntu.com/hardy/sun-java6-plugin](http://packages.ubuntu.com/hardy/sun-java6-plugin)

:(

---

### Post by ggaaron on 2008-09-22
Note that you can use 32 bit applications on 64 bit system and I'm quite sure that there is no sun-java compiled as 64 bit, I might be wrong though.

Mind that you probably want gcj plug-in with icedtea/openjdk rather than gcj itself as gcj classpath is not fully complete.

---

