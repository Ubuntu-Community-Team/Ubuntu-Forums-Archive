---
title: "Launch java on top of screensaver"
date: 2011-07-12
forum: Programming Talk
---

### Post by newelfik on 2011-07-12
Hello everyone,

I'm looking for an API or some issue to display information in java on screensaver.

I've a script in python which launch java app at screensaver start and kill java at end.

After surf a little on web, i've find : SaverBeans Screensaver SDK, but the project seems dead..

Have you got an idea in order to display some digit information in Java during screensaver ?

One problem is that the JFrame with alwaysOnTop= True, is always behind blackscreen of screensaver :(

---

### Post by t1497f35 on 2011-07-12
You're basically trying to work around the idea behind a screensaver since it was never meant for desktop apps to draw on top of it.

Unless you hook deep into the system (into the compositor, for example) I doubt you can do this in a cross-platform and reliable fashion.

The obvious solution would be to create your own custom Java screensaver which would explicitly work with such stuff in mind and set that screensaver as default.

---

### Post by newelfik on 2011-07-12
If I do this in java pure, it's mean that ScreenSaver is a jar file.

I'm not sure its possible. For the moment, its for linux os.

---

### Post by t1497f35 on 2011-07-12
There used to be a screensaver sdk but now it's dead and removed from jdic which is itself dead.

---

### Post by newelfik on 2011-07-12
Hmm, ok I was wrong, Linux allow .jar in /usr/lib/xscreensaver...

It's run, now I must display something in fullscreen

---

### Post by PaulM1985 on 2011-07-12
[http://download.oracle.com/javase/tutorial/extra/fullscreen/displaymode.html](http://download.oracle.com/javase/tutorial/extra/fullscreen/displaymode.html)

---

### Post by newelfik on 2011-07-13
Ok , I've get new recommandations.

I have to display the picture in full python, so I dev i little code which do that, a specific picture displayed in full screen. 

But when I use this code as screensaver, I always get a black screen on top off all application, and so.. on top of my picture :/

Any idea to fix bug ?

---

