---
title: "Trying to install PCGen w/Lucid Lynx, problems with Java"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by joeyfixit on 2012-03-01
I downloaded a program called PCGen (an Open Source RPG Character Generator at [http://pcgen.sourceforge.net/03_get_pcgen.php]("http://pcgen.sourceforge.net/03_get_pcgen.php")) with Lucid Lynx on my laptop and am trying to run it. I keep getting a message saying it needs Java to run. I have Java up and running through the Software Center (version 6, I think). This problem also happens if I download the Windows version and try and run it with Wine.

I'm admittedly not tech savvy or big on Terminal code. There's probably a much easier way to install this that I'm overlooking.

Suggestions?

---

### Post by joeyfixit on 2012-03-01
I downloaded a program called PCGen (an Open Source RPG Character Generator at [http://pcgen.sourceforge.net/03_get_pcgen.php](http://pcgen.sourceforge.net/03_get_pcgen.php)) with Lucid Lynx on my laptop and am trying to run it. I keep getting a message saying it needs Java to run. I have Java up and running through the Software Center (version 6, I think). This problem also happens if I download the Windows version and try and run it with Wine.

I'm admittedly not tech savvy or big on Terminal code. There's probably a much easier way to install this that I'm overlooking.

Suggestions?

---

### Post by cariboo on 2012-03-01
Please don't create multiple threads on the same subject. I have merged your two threads.

You may need to install Oracle java in order to get your program to run. See [here]("http://www.java.com/en/download/help/linux_install.xml").

---

### Post by nylanfs on 2012-03-08
Yes PCGen **before** v5.17.11 requires Oracle Java, OpenJDK has issues with Swing that makes the dialogue boxes and tabs used either display wrong or be completely blank.

5.17.11+ **is** compatible with OpenJDK, but it is VERY unstable. It's not the rock stable alpha's that have been one of the hallmarks of PCGen development.

---

