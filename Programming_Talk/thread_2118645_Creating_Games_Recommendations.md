---
title: "Creating Games Recommendations"
date: 2013-02-21
forum: Programming Talk
---

### Post by Gannin on 2013-02-21
First to give some background on myself.  I have a heavy background of Java application development, both client-side and web apps, and I have a little experience with Python.

I'd like to tinker around with creating games, and I'm looking for some recommendations on how to go about doing that.  I know there are some Java libraries along these lines (Java2D comes to mind) but the packaging and distribution of Java games seems a little messy and doesn't seem to integrate into the platform being used very well.  However I know that with the advent of Android, Java programming has gained more importance.

Whatever games I make I'd like for the focus to be on Linux, but it'd be nice if they were cross-platform too.  Any recommendations or guidance on a language or software package or anything?

---

### Post by tehcavil on 2013-02-21
> **Gannin said:**
> First to give some background on myself.  I have a heavy background of Java application development, both client-side and web apps, and I have a little experience with Python.

I'd like to tinker around with creating games, and I'm looking for some recommendations on how to go about doing that.  I know there are some Java libraries along these lines (Java2D comes to mind) but the packaging and distribution of Java games seems a little messy and doesn't seem to integrate into the platform being used very well.  However I know that with the advent of Android, Java programming has gained more importance.

Whatever games I make I'd like for the focus to be on Linux, but it'd be nice if they were cross-platform too.  Any recommendations or guidance on a language or software package or anything?

If you're used to java, I'd say stick with java and write a game using that. Just google around for open source game engines/libraries or at least graphics libraries.

---

### Post by trent.josephsen on 2013-02-22
Minecraft uses LWJGL and aside from the [sticky keys bug](http://www.minecraftforum.net/topic/134703-linux-stuck-keys-solution/) related to Mojang's stubborn reluctance to upgrade the library, it's always worked great for me on both platforms. They also seem to have found a workable solution to the packaging issue -- not great for a multi-user system perhaps, but quite reasonable. I wouldn't worry too much about that aspect though.

However, I'm not much of a game developer, so I can't make any real recommendation.

---

### Post by Virtuality314 on 2013-02-22
Also see [www.gamedev.net](www.gamedev.net)

---

### Post by MG&amp;TL on 2013-02-23
If you need physics, *pybox2d* has always worked nicely for me.

---

### Post by NilPointer on 2013-02-23
Developing games with Python and PyGame lib is quite easy and thanks to Python's dynamic nature you don't need to plan design through, you can easily change things on fly. Although, if you're more familiar with Java, it may be better to stick with it. Primary advantage of Java is it's availability. You're more likely to find Java on windows machine than Python (also from my experience, not all users want to install Python for different reasons, such as "yet another installed program will slow down my PC", but they have Java installed and may even be not aware of that, so running Java apps for typical windows user may be totally seamless), and it's best choice for Android (I was disappointed with Python port for Android).

---

### Post by danniel on 2013-03-03
If you already know Java, I don't think it will be hard for you to use C#. Have a look at **MonoGame** which is an open-source implementation of Microsoft XNA framework, based on the Mono project.

---

