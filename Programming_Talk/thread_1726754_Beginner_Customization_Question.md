---
title: "Beginner Customization Question"
date: 2011-04-11
forum: Programming Talk
---

### Post by jmg158 on 2011-04-11
Okay, so I'm sure I'm revealing something about how little I know, but I decided to give Ubuntu a try so that I could learn more about linux. I have heard that it has massive customization capabilities and I'm very interested in that. Whether desktop customization or other things that was my main draw to linux as an OS.

However, looking around and reading tutorials and stuff I notice that most tutorials just direct me to use some premade 3rd party software, usually available in ubuntu software center. For example, I just read a tutorial on desktop customization that basically said "use Cairo-dock!"

I realize that its most likely way too ambitious for me to think that I can take on the project of creating one of these tools myself, but I'm still interested in how it's accomplished ya know?. 

For example, if I wanted to create a program like the one mentioned above, how would I go about writing it? How does the whole process work?

---

### Post by Paddy Landau on 2011-04-11
This is not a small question.

Ubuntu is designed for the "average" user.

Linux distributions aren't like, say, Windows or Mac, which combine the operating system with the GUI. Linux is the core, or "kernel." On top of that, you put programs. One of them is X Windows, which provides a GUI (I'm not too technical, so I may have some details wrong). Then Ubuntu puts Gnome on top of that. (Kubuntu uses KDE instead of Gnome.) On top of all that goes Metacity, if you choose no fancy desktop effects, or Compiz if you do. Put that together with a specific default selection of programs using Debian, and you have Ubuntu.

Once you realise that, you can see that there is a world of opportunity to customise Linux.

Even if you stick with Ubuntu, desktop effects are very customisable with Compiz (provided your graphics card will cope). Consider that Lubuntu and Mint are also Ubuntu-based, and you'll see how flexible it is even when staying close to the *buntu family.

---

### Post by Some Penguin on 2011-04-11
Depends what you mean.  If you want to add a widget to a desktop environment, you probably want to first decide which environment it's going to be (e.g. KDE, Gnome for the full-fledged environments; window managers otherwise, likewise).  That will tend to influence what libraries you use, e.g. Qt and GTK for KDE and Gnome respectively, as well as what functions you'll need to implement and how it gets configured.

If you want to radically alter behavior of existing things, like e.g. implementing a physics engine for windows so they can be pushed and bounced around the screen, you'll first need to figure out which piece of software is most responsible for performing the behavior (for this goofy example, tracking down the window manager... plus, probably whatever is responsible for loading configurations, so you could set things like coefficients of friction or elasticity of the screen borders without writing your own config handler).

---

### Post by randallecook on 2011-04-12
Paddy Landau has it basically right: it's not a small question and the Ubuntu graphical environment is built on lots of layers, with several alternatives for each.

If you want to explore customization, I would first learn more about what each of the layers is and what it is supposed to do, and maybe try installing and configuring alternate versions of each. Hopefully by then you will know which layer controls the functionality you want to modify. Next you could pull down the source for that layer and start hacking.

But beware, learning a big codebase like a GUI layer could be daunting! Major GUI components probably have active developer communities that you could approach. Fixing a few bugs would give you valuable experience and earn you much respect.

Best of luck to you.

---

### Post by Paddy Landau on 2011-04-12
> **randallecook said:**
> Fixing a few bugs would give you valuable experience and earn you much respect.
+1

I should also add that my description was a simplification.

Maybe you want to try something dead simple like [Puppy Linux]("http://puppylinux.org/"), and see how you can customise that, long before trying to attack anything as complex as Ubuntu.

---

