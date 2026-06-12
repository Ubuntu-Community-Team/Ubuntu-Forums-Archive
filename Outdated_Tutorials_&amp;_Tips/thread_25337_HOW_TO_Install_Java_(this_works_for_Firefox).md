---
title: "HOW TO: Install Java (this works for Firefox)"
date: 2005-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Rory on 2005-04-09
I've been searching like mad for a way to install java in my Firefox browser in Ubuntu/Kubuntu.  Finally found a good method, so I thought I'd share it here to save others from the same grief.  These are instructions for newbies, so anyone should be able to do this.  

I did this via Synaptic (which I installed via kynaptic, in Kubuntu).  


METHOD 1 (most current version of Java for Ubuntu):

In Synaptic, go: Settings>Repositories>select: New

Add...
 URI: [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports)
 Distribution:  hoary-backports
 Section(s):    main universe multiverse restricted
Click "ok"

Hit the green "Reload" icon in the main toolbar.  

Click "Search" icon in the main toolbar and then paste and search for: sun-j2re1.5

When the package appears, you're half way there.  You've successfully added the repository and found the package.  Now it's time to install it.

Click the sun-j2re1.5 package and select "mark for installation."  This will also automatically add other required packages.  Follow the steps to download.  

It may take a while to download, as it's 29mb. 

Once done, restart your Firefox browser and you now have java installed!




METHOD 2: (try this only if Method 1 doesn't work as it's java 1.4 from Debian but it works in hoary)
In Synaptic, go: Settings>Repositories>select: New

Add...
URI:    [ftp://ftp.tux.org/java/debian/](ftp://ftp.tux.org/java/debian/) 
Distribution:  sarge 
Section(s): non-free
Click: Ok

Hit the green "Reload" icon in the main toolbar.  
You'll get a GPG key error, which is okay (I don't know the steps to import the GPG key, but it didn't seem to matter.)

Click "Search" icon in the main toolbar and then paste and search for: j2re1.4

When the package appears, you're half way there.  You've successfully added the repository and found the package.  Now it's time to install it.

Click the j2re1.4 package and select "mark for installation."  This will also automatically add the java-common package, which is required.  Follow the steps to download.  

It may take a while to download.  j2re1.4 is 22.5mb.  java-common is 68.1kb. 

Once downloaded, you'll see it installing from the same Synaptic download window.  
** This is important ** 
Click: Terminal.  This will show a mini-view of console in Synaptic.  Accept the Java user agreement by clicking "ok" and then follow the sequence of steps in the java agreement process in the mini-console.

Once done, restart your Firefox browser and you now have java installed!

---

### Post by Z-Bo on 2005-04-09
I have to try this right now as I have also tried everything possible for about a week now.  If this works, I am going to vote you the pope.  Much thanks for posting your solution!!!

---

### Post by bored2k on 2005-04-09
Why take an old, debian package when you can 
a) Build your own Java 1.5 package or
b) Take it from Jdong's repositories.

---

### Post by humanity_to_others on 2005-04-09
Did you look at the unoffical ubuntu guide: [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) or [QUOTE=bored2k]Why take an old, debian package when you can 
a) Build your own Java 1.5 package or
b) Take it from Jdong's repositories.[/QUOTE]

---

### Post by Rory on 2005-04-09
I tried a variety of methods posted on various pages.  This is just the one that finally worked for me.  Use the one that works best for you.

---

### Post by bored2k on 2005-04-09
[QUOTE=Rory]I tried a variety of methods posted on various pages.  This is just the one that finally worked for me.  Use the one that works best for you.[/QUOTE]
 [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

Your sending people to the wrong direction, giving them Debian packages and old versions. Remember we want to stay as much  Ubuntu as we can ;).

---

### Post by Z-Bo on 2005-04-09
I tried everything in the wiki already, nothing worked...

---

### Post by bored2k on 2005-04-09
[QUOTE=Z-Bo]I tried everything in the wiki already, nothing worked...[/QUOTE]
 [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)
Add jdong's backports and download sun-j2re1.5, that's it then.

---

### Post by Rory on 2005-04-09
Just tried 1.5 from the jdong repository and it worked, so I've updated the HOWTO:.  Thanks.

---

### Post by Z-Bo on 2005-04-09
Oi, the debian packages didn't solve the Firefox problem.  I haven't the foggiest clue what is wrong, but am now going to try this jdong solution.

---

### Post by jeremy on 2005-04-10
The [http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre) method worked perfectly for me, but you must follow the next step, "Q: How to install J2SE Runtime Environment (JRE) Plug-in for Mozilla Firefox?" too.
If Firefox is open, make sure you close and reopen it.

---

### Post by Paul Sinnett on 2005-04-10
[QUOTE=Rory]
Add...
 URI: [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports)
 Distribution:  hoary-backports
 Section(s):    main universe multiverse restricted
[/QUOTE]

I just tried this but the package seems to have moved. I used:

distribution: hoary-extras
sections: restricted

---

