---
title: "HOWTO: jUnit 4 and Eclipse"
date: 2007-06-05
forum: Programming Talk
---

### Post by jonlatane on 2007-06-05
As many of you know, the version of Eclipse that is included in Ubuntu's repositories is missing jUnit 4 due to legal restrictions on its use of Java 5, etc.  Thus, if you try to add jUnit 4 libraries to your path, you get lots of problems.

An easy fix is to copy some files over but that's more complex than it needs to be.  Attached is a .deb file (created with checkinstall and a Makefile - will not handle dependencies so you need to install Eclipse and Java 5+) that will install jUnit 4 for you.

So, uh, the howto goes like this:

[LIST=1]
[*]Install the deb file
[/LIST]

P.S. If anyone knows how to make a deb file manually (I don't know how to create archives with just "." as a folder name) or at least get checkinstall's requires function to work, let me know and I will set dependencies for eclipse and sun-java5-jdk or sun-java6-jdk.

---

### Post by Hendrixski on 2007-06-05
You mean ```
sudo apt-get install eclipse-jdt-gcj
``` which includes JUNIT as one of teh plugins for eclipse.

---

### Post by jonlatane on 2007-06-05
That package is for GCJ, and is jUnit 3 - the old version, I believe.  In any case, jUnit 4 does not work for me in a system with that package installed.  jUnit 4 is the newer version that uses annotations and certain reflective capabilities that are only available in Java 5+ (non-OSS).  However, I did just test this package on a different box and seem to be having trouble getting my package to work; I'm looking into what might be causing it.

**Update:** Okay, so it seems to be working on one of my machines and not on the other.  I'll try and figure out what the problem is another time.  If the package doesn't work, don't worry, I'll try and release an update ASAP.

---

### Post by nimafl on 2007-10-15
I downloaded the package you send us and I attempted to install it using the package manager. I installed it, but eclipse still does not like the junit 4.1 package. How do I make eclipse accept this package? The package installed perfectly into the /usr/lib/eclipse/plugin directory but eclipse does not see this.

I am using Gutsy
I am on eclipse 3.2.2

---

### Post by harbertc on 2008-03-24
I was having the same issue as nimafl, but figured it out. It turns out the installer created the files as root and Eclipse did not have access to read them.

Try "sudo chmod +r -R *" on the junit4 plug in directory and restarting Eclipse.

---

### Post by Endolith on 2008-05-31
> **jonlatane said:**
> or at least get checkinstall's requires function to work

Do you mean the "Requires" field in checkinstall?  I try to edit that and nothing happens.

---

### Post by Robert.L.McPherson on 2009-11-01
In addition to installing Eclipse and Junit4 on my new ubuntu machine, I also did a similar installation on my wife's Windows Vista machine last week. Interestingly, I ran into the exact same problem, where the latest "stable" version of eclipse that I downloaded for Windows only worked with Junit3.8. The easiest solution posted on a number of Windows related forums said to simply add the newer Junit package to the build path. This works for other package upgrades as well, such as Ant. I tried this with the ubuntu installed version of Eclipse, and it worked great... just like it did with Windows. This leads me to think perhaps it is not just an ubuntu issue. Regardless of whether or not that is the case, if anyone would like to try this fix, I think it is worth the few seconds it takes to give it a shot, before taking on the more drastic approach of manually reinstalling Eclipse on your own. And, for the record, I had a FAR easier time getting my Java, Apache, and Eclipse setup running in ubuntu than I did on Windows. I am SO glad I have ubuntu Linux on my own machine. My wife can struggle with Windows if she wants to, but as for me... ;-).

Here is the simple fix:

-Download Junit4x from Apache, and pretty much unzip and store the file wherever you want on your computer
-Within Eclipse, go to the "Package" menu item, and select "Properties".
-In the "Properties" popup window, select "Build Path" in the menu list in the left pane
-Then select the Libraries tab
-Select the "Add Library" button, and find the Junit4 folder that you unzipped and downloaded

That's all there is to it. You should find that your Junit4 classes run fine from there. If you ever need to install an updated jar file instead of an entire library, you can do it the same way, only select the "Add External Jars" button intead of "Add Library." I have had success with both. Hopefully this saves some time and frustration for some of you.

---

