---
title: "firefox java apps not loading ..."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Adamant on 2008-11-16
installed 8.10 - earlier today

ran firefox, wanted to play a couple java games (runescape inparticular if it matters) and i was getting a gray screen instead of java, so i googled it more than once... installed java6 by remove/add programs + terminal and it still isnt working.


java enabled, javascript enabled...

i accidentally my firefox :lolflag:


also i have a couple links to mx revolution / logitech g15 ... terminal operations and i was wondering if they'd still be able to use in 8.10 ?

---

### Post by taurus on 2008-11-16
Did you also install the plugin for java?  You can tell what kind of plugins do you have by typing this in the address field.

```
about:plugins
```
Otherwise, install the java plugin with

```
sudo apt-get install sun-java6-plugin
```

---

### Post by Adamant on 2008-11-16
about:plugins - i have every plugin there enabled except for the "demo print plugin"

terminal says i already have the newest version...

---

### Post by alienexplorers on 2008-11-16
Did you try running the java test on this page: [http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

---

### Post by Adamant on 2008-11-16
the little .. box thing loads - says that im using an older version of jre but 6.0 is current i think,

thats the only java applet that will load so far ...


edit: 
somehow "linerider" loads as well ...

i do know that the java applet requires a "cache" in order to load - im thinking that's the problem ? has anybody encountered this before ?

another edit, linerider is flash - not java ...

---

### Post by Adamant on 2008-11-16
(bump) =/

---

### Post by alienexplorers on 2008-11-16
When you loaded java did you run in terminal:
> sudo apt-get update && sudo apt-get install sun-java6-jre sunjava6-bin sun-java6-plugin

---

### Post by Adamant on 2008-11-16
cant remember exactly, it was from this forum though -
i might add that it says " starting applet " on the loading bar yet it never does ...


ran that and tried again, still nothing ..

---

### Post by TheBrewmaster on 2008-11-16
> **alienexplorers said:**
> When you loaded java did you run in terminal:
I'm basically having almost the identical problem, though running about:plugins in Firefox shows no sign of Java.  

When I run:
```
sudo apt-get update && sudo apt-get install sun-java6-jre sunjava6-bin sun-java6-plugin

```
it ends up with:
[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
E: Couldn't find package sunjava6-bin[/INDENT]
I've installed java from Sun, it appears that it's working OK, other than it just plain refuses work in Firefox.  I just get > Java Runtime Environment is not working on your system from the Sun Java test web site.
I do see and can run the Sun Java 6 Plugin Control Panel under the System, Preferences menu, and everything in there looks right.  
I'm sure there's some noob mistake that I've done, I dunno. :)

---

### Post by feimotion334 on 2008-11-17
what is the fastest way to make 1mil in runescape....[http://www.coolrunescape.com/](http://www.coolrunescape.com/)i am currently making 5k bow string which will get me about 500k but i don't know what to do after that.if u would like to look at my skills look at the highscores! plz help me.........!!!!!!!!!!![Runescape](http://www.coolrunescape.com/index.html)[Runescape gold](http://www.coolrunescape.com)Well.. around 3-4 years ago when i heard about runescape from a friend i decided to go check it out, i created 'Chavforlife' lol, you may laugh but it's true, i have no idea what made me think of that name, but yeah.. [runescape powerleveling](http://www.coolrunescape.com/runescapepowerleveling.html)But anyway, since then i've only used this account but now it's got to the stage i actually really regret making this name in the first place, everyday my name get's commented by random player's, some "nice" comments suprisingly and some just pure hate which i understand ;p. But like with this name i'm forever getting judged, flamed when they have never actually spoken to me but meh.[runescape cheats](http://www.coolrunescape.com/runescape-cheats.html)What about you guy's, any of you regret making your runescape account name?[http://www.maplemsmesos.com](http://www.maplemsmesos.com)   other game gold selling [http://www.coolrunescape.com/vgolds](http://www.coolrunescape.com/vgolds)

---

### Post by TheBrewmaster on 2008-11-17
> **TheBrewmaster said:**
> I'm basically having almost the identical problem, though running about:plugins in Firefox shows no sign of Java.  

So combing through the forums, and finding a lot of similar things, but either appear to not be resolved or turn out to be something different than what I am experiencing, I found something that's "good enough" for me (so far).
[http://www.uluga.ubuntuforums.org/showthread.php?t=535247](http://www.uluga.ubuntuforums.org/showthread.php?t=535247)
I ran the following suggested command:
```
sudo aptitude install ubuntu-restricted-extras
```
 It installed the icedtea-gcjwebplugin, among all the other things it loaded, including a few fonts that I'll never use, though they probably won't hurt me.  
The odd thing is, when going to the Sun Java test web site, [http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3)
It now oddly says I have Java 6 Update, with Sun Microsystems as the vendor, though it's displaying a little oddly, the "more Information" button is directly on top of the little animation.  

I guess I won't complain, as long as it will work for what I need it for. :)

---

