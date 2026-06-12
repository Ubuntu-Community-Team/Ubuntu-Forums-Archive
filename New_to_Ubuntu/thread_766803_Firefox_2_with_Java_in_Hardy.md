---
title: "Firefox 2 with Java in Hardy"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by MightyMe on 2008-04-25
I need to run Firefox 2 in Hardy with Java support. I have downloaded and installed Firefox 2. 
Is there any way I can get it to use the IcedTea plugin which Firefox 3 seems to use or do I need to download a separate Java runtime?

---

### Post by MightyMe on 2008-04-25
I need to correct myself a little bit. I already have Java 1.6.0_06-b2 intalled and I just need to make my Firefox2 use it. Any ideas?

---

### Post by dstin1 on 2008-05-02
I have the same question.  Java works in firefox 3 but pogo does not.  I want to try ff2 for pogo but it tells me java is not installed and I know it is.  So how do I enable it?

---

### Post by Xiong Chiamiov on 2008-05-02
I think you need to copy the plugin from the FF3 directory over to the FF2 one.  Where it is I do not know, but you should be able to find out in Synaptic. (not quite sure how, I use adept)

---

### Post by dstin1 on 2008-05-02
I am thinking ff3 and 2 use the same directory because bookmarks and passwords and such are still there.  I also have no problem using flash with ff2 just java.

I also must apologize for jumping the thread but it is 6 days old and not solved and since I have the same problem I figured I could bump in and maybe also help out the creator.

I would also like to add I love the google toolbar but it does not work with ff3 even though I forced it to install it shows up ok but does not completely work, that is another reason I want ff2 complete as it was in gusty.

---

### Post by Xiong Chiamiov on 2008-05-02
I believe firefox uses two different folders for storing things like plugins, one in your home directory and one in /usr somewhere.  It's possible that FF3 is only utilizing one of them, and you need it to look at the other one as well?

---

### Post by dstin1 on 2008-05-02
I am open for hints on how to do that.

I see someone else has just started a topic of where ff3 stores plugins, I will check that out as well.

As a side not I think Firefox3 as a beta may have been a huge mistake.

---

### Post by Xiong Chiamiov on 2008-05-02
I honestly don't think that Firefox should be the default for you GNOMErs, since it isn't really the best browser for most people; they'd be better off with Opera or Kazehakase.  However, everyone's got Firefox drilled into their brains, so they'd go looking for it anyways.

As a side note, [Swiftweasel]("http://swiftweasel.wiki.sourceforge.net/Apt") (it's really Firefox, for real) is still operating under the 2.0 branch, if you want to check it out.  It's what I use.

---

### Post by dstin1 on 2008-05-02
I also use Opera and am about as happy with it as ff3.5b java seems to work ok most of the time but flash does not and from searching the forums there seems to be no solution to that.

I started using firefox in my windows days and loved it much better than IE and even IE7.

But I may try your other suggestion when I have time (now is not good):)

---

### Post by Unix_Slayer on 2008-05-04
Welp.... Java plugin is installed, and is working in FF2. Tested on Java.com. Problem is on Pogo, when you click to activate a game, it keeps asking if you want to install the plugin. Could be some html script error on Pogo itself. Java is indeed alive, but not working on Pogo.

---

### Post by ChocoTuar on 2008-05-04
I found FF3B to be a nuisance, so when I got Hardy I decided to downgrade back to FF2. It took me a while to get everything working like it was in Gutsy (in terms of Add-Ons), but I can't get java to work at all. When I go to a site that uses JRE, it tells me I need to install a plugin for JRE manually, and links me to the Sun site that lets me download and install a .rpm file, and THAT installation doesn't work.

Any way to get java on FF2/Hardy?

---

### Post by ChompTheMan on 2008-05-04
Is libjavaplugin_ijo.so in /usr/lib/firefox/plugins/?

---

### Post by txcrackers on 2008-05-04
As long as the Java plugin is installed in */usr/lib/firefox/plugins*, both FF2 and FF3 will use it properly. If you've got more than one JVM installed, you will need to use the ```
sudo update-java-alternatives
``` command to sort out which one to use.

I'm not familiar with Pogo, so if it has a Firefox-like plugin directory in your home directory, you can try a soft-link to the one in */usr/lib/firefox/plugins*.

---

### Post by MightyMe on 2008-05-12
I made a symbolic link in my firefox plugins directory to tha Java plugin and that worked.

---

### Post by dsiembab on 2008-05-14
try this I am playing cribbage in pogo even as i type [http://blog.clickonline.org.au/2007/04/30/ubuntu-linux-tip-of-the-day-installing-java-and-flash-on-ubuntu-firefox-and-other-browsers-fiesty-edgy-dapper-breezy/]("http://blog.clickonline.org.au/2007/04/30/ubuntu-linux-tip-of-the-day-installing-java-and-flash-on-ubuntu-firefox-and-other-browsers-fiesty-edgy-dapper-breezy/") worked for me

---

