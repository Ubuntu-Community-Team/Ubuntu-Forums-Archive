---
title: "Frostwire refuses to run..."
date: 2008-07-30
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-30
I have it all installed, and all that jazz...
But when I go to open it, it loads  little bit, then stops and nothing ever opens up, not even an icon on the top right corner.

I've also reinstalled it a good three times.

What's going on? T_T

---

### Post by oliviacond on 2008-07-31
looks lke frosftwire is a jave program, i think u need openjdk-6-jre (can be found in synaptic)

---

### Post by diggafreak on 2008-07-31
So i briefly looked around for this but didnt see anyone with the problem I got..

I DLed 4.17 and when I load it up it never gets past a blue square (where frostwire should be but its all background, no tabs or windows)

Anyone with any idea how or why, please help. Thanks

(Also I am running the linux/ubuntu version)

Basically I loaded it up, installed and once it shows the loading screen it stops at 12% of HTML engine, pops the program up but its solid blue and I cant get past this. Sometimes cursor picks up a tab (changes to a 'clickable' cursor.) but Frosty stays ice cold (heh) Please help, I had 4.13.5 and worked fine, I tried to install it again and now its screwy. I would love to use the new upgrade. I keep removing the package and so forth and trying over and over with new DLs of 4.17 or 4.13.5 and now its always the same thing, 4.17 stays blue and 4.13.5 shows half the screen and the other have is solid grays. I always half to force quit the operation and I am getting po'ed. Please help

if the answer above is the solution I am way beginner on linux... how do I go about making it work. I DLed the latest java but it was all .bin files..and I ran into more problems.  Is the solution ran through the terminal?

---

### Post by tuxxy on 2008-07-31
install the latest java and then type this command into terminal and select the correct new sun-java

> sudo update-alternatives --config java

---

### Post by diggafreak on 2008-07-31
so when I DL the latest java like I said its all .bin and I cant do anything with it. So what do I do to install?  Sorry so newb...:confused:

---

### Post by tuxxy on 2008-07-31
digga, 

follow the guide on this page, you may need to scroll down a bit

[http://www.java.com/en/download/help/5000011400.xml](http://www.java.com/en/download/help/5000011400.xml)

---

### Post by diggafreak on 2008-08-01
everything looks cool, and I am trying it out, but does it work for ubuntu (I only ask cause its not on the list)

I dont know what the red hat and everything else is

---

### Post by tuxxy on 2008-08-04
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

---

### Post by diggafreak on 2008-08-05
k so I never made it through. I did run frostwire through terminal and it said:

Could not load properties from property file.

******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)


When I follow instructions in above posts it says no such file exists when I get to the first step of; cd/usr/java

---

### Post by SunnyRabbiera on 2008-08-05
Yeh I had issues with frostwire too, but it was resolved when I installed the regular java 5 and 6 and dumping open jdk.
I suggest getting the nornal java by enabling the extra repositories and forget about the java DL from the java site.

---

### Post by diggafreak on 2008-08-05
I am noob at this so how do I go about that?

---

### Post by SunnyRabbiera on 2008-08-05
Its easy enough, open up synaptic located under system > administration > synaptic package manager.
Synaptic is easy enough to figure out, go up to "settings" and then to "repositories"
after that you will have a new window where you can edit your repositories, by clicking on all the boxes off in the first tab except for the source code one.
Then in tab 2 do the same, check off all extra repositories the same way you did in the other tab and once again ignore the source code stuff.
Then after that just close off the repository editor.
Hit the "reload" button as it will suggest.
Then search for JRE.
Remove the open JDK by right or left clicking the box next to the package named openjdk-6-jre and selecting "mark for complete removal"
and then on the boxes next to the one that say Sun java packages (sun java5 and 6-bin) and select "mark for installation"
From this point on its very simple, if it needs extra packages it will tell you and just hit "apply"
If you have trouble use this guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by diggafreak on 2008-08-05
The second tab is 'third party' and every other one says source code, one says partner, and everyone says main restricted.. this right?  and click off the ones that dont have source code attached? also none of my searches for jre revealed a jdk file, just one frostwire, and sun-java6 bin and sun-java6 jre

---

### Post by SunnyRabbiera on 2008-08-05
> **diggafreak said:**
> The second tab is 'third party' and every other one says source code, one says partner, and everyone says main restricted.. this right?  and click off the ones that dont have source code attached?

Correct, those source code repositories are not needed really by the common user.

---

### Post by diggafreak on 2008-08-05
also none of my searches for jre revealed a jdk file, just one frostwire, and sun-java6 bin and sun-java6 jre

---

### Post by SunnyRabbiera on 2008-08-05
well in that case install the sun-java6 bin and sun-java6 jre packages.
Also search of other tags in synaptic like "java" "java runtime" "sun java" and the like.

---

### Post by diggafreak on 2008-08-06
I think i did it through terminal, thank you...will post any further problems, thanks for that link too

---

### Post by diggafreak on 2008-08-06
So lets see, I installed sun-java6-bin in terminal, then loaded frostwire, same blue screen after 12% of HTML Engine is loaded.  Then I went back into synaptic and repositories, still no openjdk anywhere.  Should I just remove the two sunjava6.jre and .bin files completely and start over or what? It says this when I installed in terminal:

Reading package lists... Done
Building dependency tree
Reading state information... Done
sun-java6-bin is already the newest version.
The following packages were automatically installed and are no longer required:
  xserver-xorg-video-amd linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16


Both Limewire 4.18 and Frostwire 4,17 do this, they get to 12% HTML Engine and then go blank

---

### Post by projecthikari on 2008-08-09
Oh!
Woah, I actually got replies. It was dead for a good day or two.

Thanks guys, frostwire works.

---

