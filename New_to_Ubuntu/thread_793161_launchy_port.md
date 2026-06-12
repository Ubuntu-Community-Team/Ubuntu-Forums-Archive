---
title: "launchy port"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-13
so there is a neat little program for windows called [launchy.]("http://www.launchy.net/") it is a small search tool for your computer, and various aspects of the insternet. i was wondering, since it IS open-source, if ict could be compiled, ported, etc. for ubuntu/linux. or perhaps there is an app like it already?

---

### Post by peitschie on 2008-05-13
Hi!

A program that I have found that does similar is Gnome-Do: [https://wiki.ubuntu.com/GnomeDo](https://wiki.ubuntu.com/GnomeDo)

There are equiavlent KDE apps, but I don't use KDE so I'll leave that for someone who does :)

---

### Post by Zopiac on 2008-05-20
> **peitschie said:**
> Hi!

A program that I have found that does similar is Gnome-Do: [https://wiki.ubuntu.com/GnomeDo](https://wiki.ubuntu.com/GnomeDo)

There are equiavlent KDE apps, but I don't use KDE so I'll leave that for someone who does :)

i cant figure out how to install :/

---

### Post by peitschie on 2008-05-20
That would be found on this page: [https://wiki.ubuntu.com/GnomeDo/Installation](https://wiki.ubuntu.com/GnomeDo/Installation)

Run the following in a terminal (Applications > Accessories > Terminal)
```

sudo aptitude install gnome-do gnome-do-plugin-rhythmbox gnome-do-plugins

```

Once that is installed, you need to start it.  From the terminal, run the following to test that it launches:
```

gnome-do

```

This should bring up a gnome-do dialog.  If it doesn't, hit Super(Windows key)+Space at the same time.

Assuming the above steps all worked, you will want to make it start automatically with your login session.  To do this, add the following as a new entry in the Sessions dialog (System > Preferences > Sessions > Startup Programs)
```

gnome-do --quiet

```

Then log-off and log-on again, and pressing Super+Space should bring up the Gnome-Do dialog!

---

### Post by Zopiac on 2008-05-26
ok, in launchy, i would type in google pizza and it would open opera and search google for pizza. when i do that in gnome do, as well as many commands, it brings me [here ]("http://search.creativecommons.org/?q=google+pizza&sourceid=Mozilla-search")

---

### Post by Zopiac on 2008-06-16
also, when i type in, say, songbird, it doesnt open songbird, or the folder its in. is there a way to do these?

---

