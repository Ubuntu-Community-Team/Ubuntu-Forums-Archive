---
title: "Android SDK Installation Problems"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by xcusmwah on 2008-11-02
Hello - 

I am trying to install Google Android SDK on Ubuntu 8.10.  I am following the directions below and am stuck on the part about configuring Eclipse.  To be more specific I am stuck at the part where it is asking me to add a site to Eclipse via Software Updates.  When I add the site they tell me to (note my screens don't exactly match theirs) it tells me that network connection problems occurred during search.  Below is a screenshot of what I am adding in.  I'm sure it is something easy but if someone could help me out I'd really appreciate it.  Thank you

[http://www.howtoforge.com/installing-google-android-sdk1.0-on-ubuntu8.04-desktop-p2](http://www.howtoforge.com/installing-google-android-sdk1.0-on-ubuntu8.04-desktop-p2)

---

### Post by dedmonds on 2008-11-23
I had a very similar problem installing the Android Development Tools (ADT) using the version of Eclipse in the Intrepid repos. I uninstalled that version of Eclipse and installed version 3.4.1 from the Eclipse website (Eclipse IDE for Java Developers at [_http://www.eclipse.org/downloads_](_http://www.eclipse.org/downloads_)). That solved the problem for me.

---

### Post by teknotuck on 2008-12-22
Actually same thing happens in all version of ubuntu, you can not use the versions of eclipse out of the ubuntu repositories and must download it manually, the sdk only works with versions 3.3 and 3.4 of eclipse.

---

### Post by cj4linux on 2009-10-31
For whomever it helps (& I've requested a new thread for this), I had a problem w/Ubuntu 9.10 x86_64 and Android 2 installing the SDK, worked it out with some help/input from an android forum & am posting it here if it helps anyone else:

1.)  Download android-sdk_r3-linux.tgz
2.)  Extract it & change your path in .bashrc to point to it's 'tools' folder.
3.)  Create a file called ~/.android/androidtool.cfg [from the aforementioned forum]
4.)  Add the following line to it [from the aforementioned forum]:
sdkman.force.http=true
5.)  Navigate to the aforementioned 'tools' folder
6.)  Run the following command 'android update sdk'.

That fixed the problem for me & believe it would be helpful for others w/Ubuntu 9.10 developing with the new Android 2 SDK.

Don't have much time for responses/follow-ups, but hope that this & the android documentation will help resolve any problems installing the SDK on this particular setup.  I'll try to revisit periodically.

Hope it helps anyone else w/the same problem.  (In particular, the first problem was that the 'android' tool as specified in the documentation was originally unable to pull from the web-site--the mod'ed file fixed that--and the follow-up problem was that the android tool GUI wasn't actually installing/updating the software; but, specifying the full 'android update sdk' worked-around that.

---

### Post by cj4linux on 2009-10-31
One additional note, I've recieved the following error when I use the 'Run [project].java' icon, which I've historically use for launching the android which I've seen some others have similiar issues with:

#  Internal Error (classFileParser.cpp:3075), pid=xxxx, tid=xxxxxxxxxxxxxx
#  Error: ShouldNotReachHere()

As a work-around, if you get this and you're developing for Android 2.0, I've gone to Run-->Run Configurations... then create a new configuration, for the 'Project:' use the Browse button and browse to the Android 2.0 project, under the 'Target' tab, click on Android 2.0 and then click on 'Start...' and 'Launch'.   Once it has launched and initialized (for the emulator) then click on the 'Run' and the application should run without the aforementioned problem.  Hope this helps anyone else w/this issue with Android 2.0 dev on Ubuntu 9.10 x86_64.

---

### Post by flipouk on 2009-11-10
I found this and it worked for me:

[http://groups.google.com/group/android-beginners/msg/70625c22a2f82d89](http://groups.google.com/group/android-beginners/msg/70625c22a2f82d89)

---

### Post by www.rzr.online.fr on 2010-01-26
> **flipouk said:**
> I found this and it worked for me:

[http://groups.google.com/group/android-beginners/msg/70625c22a2f82d89](http://groups.google.com/group/android-beginners/msg/70625c22a2f82d89)


Even with this GTK tweak it fails when i "start" a class that contains a main function (junit) , may this help:

[http://dtmilano.blogspot.com/2008/11/android-testing-on-android-platform.html](http://dtmilano.blogspot.com/2008/11/android-testing-on-android-platform.html)


My JVM is Java VM: OpenJDK 64-Bit Server VM (14.0-b16 mixed mode linux-amd64 )

---

