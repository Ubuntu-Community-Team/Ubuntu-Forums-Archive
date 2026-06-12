---
title: "TRYING to setup java with geany."
date: 2009-11-29
forum: Programming Talk
---

### Post by xZachtmx on 2009-11-29
I want to get into java development so i installed the jdk and it is located /usr/lib/jvm/java-6-sun-1.6.0.15 .  I opened geany and made a .java hello world application with the following code 
```
import java.applet.*;
import java.awt.*;

public class HelloWorld extends Applet
{
  public void paint (Graphics g)
  {
    g.drawString("Hello World!", 50, 25);
  }
}

```

But i got an error: 
```
Exeption in thread "main" java.lang.NoSuchmethodError: Main geany
```

Can anyone help?

Thanks,
Zach

---

### Post by Virtual Liberty on 2009-11-30
I don't think that Geany can run applets.

---

### Post by froggyswamp on 2009-11-30
Unless you can't stand NetBeans for its sluggishness I'd definitely suggest using it. For a beginner it's (especially) good not because it does the work for you but because it often suggests you the right thing when you're doing it the wrong way, give it a try.

edit: anyway even NetBeans doesn't have built-in support for applets, so you'd rather create your applet as an app and test the applet inside a JFrame, when ready, make it an applet. And btw I hope you have a good reason to develop applets because they're mostly not welcome on webpages. You can create with Java many other interesting things like desktop applications/games etc..

---

### Post by JCoster on 2009-11-30
I'd use Eclipse- it's in the repos and runs applets.  Although it's not entirely intuitive at first, if you are going to be learning Java for a while it's definitely worth a look.

---

### Post by bsharp on 2009-11-30
My university uses [BlueJ]("http://www.bluej.org/") to teach Java. IMHO it's one of the most underrated java IDEs. The debugger is one of the best, and it has built-in applet support.

---

