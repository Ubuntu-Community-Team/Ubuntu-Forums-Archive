---
title: "Eclipse 3.3 Europa - getting it to play nice"
date: 2007-09-16
forum: Programming Talk
---

### Post by alcon on 2007-09-16
Is anyone else having serious difficulty getting Eclipse 3.3 (Europa) to play nice with Ubuntu?

I started out on Dapper Drake, trying to upgrade from an only Eclipse 3.1 I'd been using for a while. I used Synaptic to remove 3.1, and since I couldn't find the updated version in the old Dapper repositories I tried to install it from the tar.gz files offered at on the eclipse website.  All appeared to go well until I tried updating using the eclipse update manager.  Nothing worked.  I couldn't download any plugins or updates, they all returned a "Verification Unsuccessful" error.  After futzing with this for a long time and attempting to find a solution with my meek googlefoo I gave up and decided it must be an issue with my now out of date Dapper Drake.

Now 3 hours late I've upgraded to Feisty Fawn and I'm still having issues.  Namely, the update manager won't even start now.  I noticed that the version of eclipse in the Feisty repositories is still only 3.2.2, is this for a reason?  Does Europa just not play nice with Ubuntu right now?  Or am I doing something horribly wrong?

My exact process thus far has been:
-Download the Eclipse package from the repositories to get any other required packages.  
-Remove Eclipse package form the repositories.
-Download Eclipse Europa .tar.gz from the Eclipse.org website.
-Unzip and untar to desktop.
-Start Eclipse (ignore missing welcome error - has consistently shown).
-Start update manager.
*Crash*

Anyone else running into similar problems?  Anyone else gotten it working and have advice to offer?

[EDIT] Ok, the initial problem was solved by installing the sun-6-java package from the repository and then pointing the system java home to it's java directory.  That got the update manager working.  Thanks everyone who helped out with that :)

I've now run into an all new fun problem, whereby the CDT hangs much the way the update manager used to.  Only there isn't a pattern to it near as I can tell.  When certain files are opened the CPU usage goes through the roof and doesn't go back down until you exit Eclipse.  For a while Eclipse still works, but after a minute or two it freezes up.

---

### Post by coffecup1978 on 2007-09-16
eclipse will struggle if you are still using gjc, try to download sunjava6 instead, it solved a few issues for me. I also just grabbed the linux tar.gz off eclipse.org and that ran fine with sunjava6. Hope it helps...

---

### Post by alcon on 2007-09-17
I can get it to start up fine, it's just the update manager that crashed.  Also: tried downloading and installing sunjava6, no luck.  Not sure I installed it right, I just ran the .bin script and then moved it into /usr/local/bin.  Is there something I have to configure in Eclipse to tell it to use that version of Java?

---

### Post by Fallen_Demon on 2007-09-17
I had the same problem with the gjc. Even now that eclipse is looking at the code with sunjava6 I still compile and run from terminal. You can edit what it uses by going... hang on.. eclipse is starting...  when you make a new project, you can change what compiler it uses on the project under jre

---

### Post by samjh on 2007-09-17
No problems so far with Eclipse 3.3.

My only complaint is that some of the dialog boxes are still too big, so I can't see the bottom (on a 1024x768 desktop).  But that's my usual complaint with Gnome/GTK programs whose makers neglect to use scroll panes.

---

### Post by alcon on 2007-09-17
> You can edit what it uses by going... hang on.. eclipse is starting... when you make a new project, you can change what compiler it uses on the project under jre

Well, that'll probably help if I go to run something.  But I doubt that'll help fix the Update Manager.

---

### Post by ynef on 2007-09-17
Make sure that you are using Sun's JRE by editing /etc/eclipse/java_home (if you installed it via Synaptic, don't know about the tarball version -- but you can have a file called .eclipserc in your home dir where you set the variable JAVA_HOME, which should work for the tarball too).

Eclipse has its own settings that doesn't obey Ubuntu's "java-alternatives" setting. You need to do it manually.

---

### Post by dazzwater on 2007-09-18
Hi, I had the same problem as you. Been searching high and low for the solution, and just managed to solve it by luck. Anyway, will post my solution here for the benefit of those like me.

Mine is a Ubuntu Feisty Fawn on x86. Had a previous Eclipse 3.2 installation from apt, but had been trying to install the WTP2.0 Europa all in one package for the past few days. It ran fine, just as in your case, but hangs or freezes whenever I click "Software Updates -> Find and Install" or "Software Updates -> Manage Configuration". The screen freezes for up to 6 hours before the window finally appears, and when I " force quit " before that, an error message appears with some stuff involving JVM, GCJ, launcher, jar, gij-4.1, the like (providing keywords here, bear with me).

There are some forums out there suggesting that the problem lies with the GTK2 version, so I updated it to no avail, and messed up my display in the process :( The problem with this update screen freeze lies solely, in my layman opinion, with the JVM version. My solution was to install Java6 (from apt), then adding the following line to the top of /etc/eclipse/java_home:

/usr/lib/jvm/java-6-sun-1.6.0.00

and then setting JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00 for good measure, and also creating a eclipserc file in home/<username>/.eclipse/ with the line /usr/lib/jvm/java-6-sun-1.6.0.00 just to be absolutely sure, though I'm sure only one of the above is necessary.

After that, and after "eclipse -initialize" and "eclipse -clean", eclipse 3.3 works like a dream =)

> **alcon said:**
> I can get it to start up fine, it's just the update manager that crashed.  Also: tried downloading and installing sunjava6, no luck.  Not sure I installed it right, I just ran the .bin script and then moved it into /usr/local/bin.  Is there something I have to configure in Eclipse to tell it to use that version of Java?

---

### Post by alcon on 2007-09-19
Alright, thanks a bunch that all helped with the update manager, but I'm still having serious issues with the cdt.  Namely, it's still hanging.  And it's apparently random now. Right now I'm pretty sure the hang has to do with it's trying to recover a previous workspace setting that was lost on a crash, but before that I have no idea what caused it.

Any ideas?  Also anyone know how to get it to *stop* trying to recover the lost data since I can now no longer get into that workspace?

---

### Post by fgossart on 2007-09-20
I think I have a solution... not the best but it works for me
problem seems to be with JRE.
try easyeclipse release 1.3.0 based on eclipse 3.3
when installed you can see that it uses is own JRE (jre folder in eclipse folder)
so I copy the contents of this folder in a jre folder under my eclipse 3.3. folder
then eclipse -initialize and eclipse -clean
Now I can update, and I can really use PDT.

---

### Post by Coyote21 on 2007-09-20
> **alcon said:**
> I can get it to start up fine, it's just the update manager that crashed.  Also: tried downloading and installing sunjava6, no luck.  Not sure I installed it right, I just ran the .bin script and then moved it into /usr/local/bin.  Is there something I have to configure in Eclipse to tell it to use that version of Java?

Follow this tutorial [http://www.crazysquirrel.com/computing/debian/java.jspx](http://www.crazysquirrel.com/computing/debian/java.jspx), and remove gcj in the end.

---

### Post by Keymone on 2007-09-20
what is the point of ubuntu repositories if i need to download standalone eclipse 3.3? is there any way to make application go into repository faster?

---

### Post by Coyote21 on 2007-10-01
> **Keymone said:**
> what is the point of ubuntu repositories if i need to download standalone eclipse 3.3? is there any way to make application go into repository faster?

Well you could try to post an feature request on launchpad, and maybe  the ubuntu staff will include it in the next ubuntu release.

---

### Post by jelofson on 2007-10-08
I also had the ubuntu managed eclipse version 3.2 running and ran into problems with 3.3 eruopa. Namely, it wouldn't run the software update. I read several of the posts and realized it was a java virtual machine issue. So, I installed sun-java6 via synaptic. It installs well enough but when I looked at what vm eclipse was using, it was not pointing to the correct place. It would default to a jre subfolder of the eclipse binary and then try to figure out what java you have on your system. Eclipse was using /usr/bin/java which seemed to be a sym link to /etc/alternatives/java which itself is a sym link to a java runtime. What I found to be dead simple was to run this:

update-alternatives --config java (as sudo)

and then, using the menu, point it to the newest java you have. Now everything works fine for me.

As another method, you can easily add the -vm switch to your eclipse startup.

$ eclipse -vm /usr/lib/jvm/java-6-sun/jre/bin/java

That also works.

I just have eclipse uncompressed to a folder in my home directory. 

Jon

---

