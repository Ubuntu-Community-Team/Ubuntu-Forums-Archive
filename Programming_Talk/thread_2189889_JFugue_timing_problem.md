---
title: "JFugue timing problem"
date: 2013-11-24
forum: Programming Talk
---

### Post by w.w.milner on 2013-11-24
There seems to be a problem with playback timing on Ubunto 12.04. Basic code like
Pattern pat = new Pattern("C D E F G");
Player player=new Player();
Player.play(pat);
results in a timing glitch around 40% of the time it is run.
Same code in Windows 7 has no such effect.
This is with JFugue 4 or 5, and Java 1.6 or 1.7, 64bit

---

### Post by r-senior on 2013-11-24
This almost looks like a bug report, was that your intention?

If you want to report bugs, you should do so via [Launchpad]("https://bugs.launchpad.net/") or as an upstream bug to the [JFugue]("http://www.jfugue.org/") developers.

---

### Post by w.w.milner on 2013-11-25
Not a clear bug report, since its not obvious where the problem is. I'm talking to David Koelle, who is writing JFugue. He says it sometimes happens in Windows with repeated notes. It does not happen if the output goes to a midi file rather than played live. So the problem might be
1. In the Java midi classes, which JFugue wraps. Probably not, since unless they are native, they would be the same bytecode on both OS
2. Or in how Ubuntu plays midi - which I have no idea about.

---

### Post by r-senior on 2013-11-25
Have you tried running it with VisualVM to see if the glitches occur when it garbage collects? Is it that kind of "delay" type glitch?

Are you using the Oracle JDK or OpenJDK on Ubuntu?

---

### Post by w.w.milner on 2013-11-25
I suspected it might be a garbage collection issue, but its such a brief snippet and no refernces are being nulled, so I thought it unlikely. I also thought there might be a Swing thread issue, but I get the same for a command line version.

This is the OpenJDK - would it be sensible to try with teh Oracle JDK?

---

### Post by r-senior on 2013-11-25
I don't think it's garbage collection. I can hear glitches but they don't coincide with a collection:

[ATTACH=CONFIG]248085[/ATTACH]

I made a long "song" with repeated notes and played it back. The VisualVM run shows that garbage collection is happening but the playback was smooth. 

I did a quick switch over to Oracle JDK 1.7 and I still get little clicks and pops. I didn't notice a significant difference between the JDKs.

I wouldn't call it a "timing" glitch though. It sounds more like a bit of dust on a vinyl record. The notes are still in time, as far as I can tell.

---

