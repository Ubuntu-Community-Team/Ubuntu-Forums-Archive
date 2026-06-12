---
title: "Programming Newcomer"
date: 2011-03-13
forum: Programming Talk
---

### Post by siskel on 2011-03-13
Hello, I've been a Linux System Admin all my work-life but recently I decided as a hobby to develop an application to administer my contacts information and further in the future be able to sync that to several smartphones.

With that being said I would say I have average knowledge when it comes to programming mostly from shell scripting skills so when it comes down to seriously program an app. I lack of what I would think is basic knowledge.

Well, my question is, does anybody can point me what tools I could use to develop an app in Java with GTK.

More specifically IDE recommendations and what would be the recommended setup when it comes to compilers (OpenJDK or SUN/Oracle JDK) and such.

If it's possibly you could tell me what can I install through aptitude since I setup a personal desktop with Ubuntu for this "hobby" I want to take.

I've read several guides and I'm kinda starting to do some work but when it comes to the guides I've found the most basic information like IDE recommendations or what do I need to install to have Java with GTK working is not provided, and even less for Ubuntu specifically.

Thanks for any help.
MP

---

### Post by GregBrannon on 2011-03-14
Did you review the stickies here?  Have you read the MANY threads on which IDE is best (it's still being decided)?  Once you learn some Java basics, for your next step to GUI programming learn Swing.

---

### Post by lykeion on 2011-03-14
> **siskel said:**
> Well, my question is, does anybody can point me what tools I could use to develop an app in Java with GTK.
java-gnome is Java bindings for GTK
Install: sudo apt-get install libjava-gnome-java
Homepage/Documentation: [http://java-gnome.sourceforge.net/4.0/doc/](http://java-gnome.sourceforge.net/4.0/doc/)
However if you're new to Java I'd suggest you use Swing to make your GUI.

> **siskel said:**
> More specifically IDE recommendations and what would be the recommended setup when it comes to compilers (OpenJDK or SUN/Oracle JDK) and such.
IDE: [IntelliJ Idea]("http://www.niftyeyeblog.com/intellij-idea-on-ubuntu/") or [Eclipse]("https://help.ubuntu.com/community/EclipseIDE")
JDK: For a personal project I'd suggest OpenJDK

---

### Post by tapasapat on 2011-03-14
IDE: IntelliJ Idea or Eclipse or NetBeans. Try and see what works for you.
JDK: I've heard people report issues about OpenJDK's performance in certain situations, but I can't comment on those as I use the Sun stuff myself.

---

### Post by siskel on 2011-03-14
Thanks a lot for replies, I will look into your recommendations.

As for Swing, I didn't know about it's existence I went for GTK because by being a Linux User I've hear a lot about it :).

Again Thank you, and I'll be posting about my project if you guys interested in checking it out.

---

