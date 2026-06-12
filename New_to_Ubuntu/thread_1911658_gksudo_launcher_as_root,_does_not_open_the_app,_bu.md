---
title: "gksudo launcher as root, does not open the app, but .desktop file"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by intiyunta on 2012-01-19
Hi ppl. This is my first msg, since i am new to linux about a month.

i am running 11.10 server.

i am using gnome classic without effects

so i have installed krusader and i want to initate it as a root for manipulating the files without restrictions.

I looked over google how to make a launcher so i can do this without the terminal, so i ended creating an icon launcher on my top panel with this command line:

gksudo "gnome-open %u"

but when i drag and drop any icon program from my panel to it, it ask me for a root password but then it open the file.desktop instead of application, and that is what i want.

how can i do this??

many thanks.
Sergio

---

### Post by cortman on 2012-01-19
Whoa, whoa, whoa.

Ubuntu Server is a CLI only system. Have you installed Gnome on top of it?
Next, why on earth are you running Krusader (which is a KDE 3 app) in gnome? Why not use nautilus?
Next, opening it as root should be

```
gksudo krusader
```

or

```
kdesudo krusader
```

I'm not sure which, since you're running a KDE app in a Gnome environment.

I would recommend using nautilus, which can be launched the same way.

And if your goal is to run other programs as root, you can make a launcher for it the same way.

---

### Post by intiyunta on 2012-01-19
> **cortman said:**
> Whoa, whoa, whoa.

Ubuntu Server is a CLI only system. Have you installed Gnome on top of it?
Next, why on earth are you running Krusader (which is a KDE 3 app) in gnome? Why not use nautilus?
Next, opening it as root should be

```
gksudo krusader
```

or

```
kdesudo krusader
```

I'm not sure which, since you're running a KDE app in a Gnome environment.

I would recommend using nautilus, which can be launched the same way.

And if your goal is to run other programs as root, you can make a launcher for it the same way.

Ubuntu Server allows you to install a graphical interface so i choose gnome classic for it. I know it is better to administer it only from cmdline but i want to do this like this since i am a beginner. Maybe with time i will learn more commands and use the gui less often.

KDE apps may work on Gnome environment and visceversa. Maybe some required libs are not present but in general this kind of apps just work. 

I do not like nautilus, functions are very basics. Krusader has more features so i prefer it.

Yes, i did create the launcher, that is what i am asking about, because it open the .desktop file of dropped icons there, instead of opening the app pointed in .desktop file, with root privilegies, as i want.

Maybe i am not writing well in english, is not my native language. sorry, i do what i can.

Thanks.
Sergio.

---

### Post by cortman on 2012-01-19
> **intiyunta said:**
> Ubuntu Server allows you to install a graphical interface so i choose gnome classic for it. I know it is better to administer it only from cmdline but i want to do this like this since i am a beginner. Maybe with time i will learn more commands and use the gui less often.

KDE apps may work on Gnome environment and visceversa. Maybe some required libs are not present but in general this kind of apps just work. 

I do not like nautilus, functions are very basics. Krusader has more features so i prefer it.

Yes, i did create the launcher, that is what i am asking about, because it open the .desktop file of dropped icons there, instead of opening the app pointed in .desktop file, with root privilegies, as i want.

Maybe i am not writing well in english, is not my native language. sorry, i do what i can.

Thanks.
Sergio.

On the contrary, your English is excellent! As a monolingual English speaker, my hat's off to you there.

Running Krusader in Gnome is your prerogative- if you prefer it, go for it- I just didn't understand why not.

Perhaps I have misunderstood what you're trying to do. What I'm thinking is that you want to create a launcher on your panel that, when you click it, allows you to open Krusader as root?

If so, what I suggested via "gksudo Krusader" should work for you.

Good luck!

---

### Post by erngab on 2013-01-09
[Intiyunta]("http://ubuntuforums.org/member.php?u=1520318") how did you solve this?
I have the same problem with krusader.

---

### Post by intiyunta on 2013-01-09
> **erngab said:**
> [Intiyunta]("http://ubuntuforums.org/member.php?u=1520318") how did you solve this?
I have the same problem with krusader.

Right now, i am not using krusader. I am using Double Commander (doublecmd), because krusader hangs very often, and i must kill the app and relaunch it to get it work. I uninstalled it.

i hope this helps.

greetz,
Serg.

---

### Post by erngab on 2013-01-09
> **intiyunta said:**
> Right now, i am not using krusader. I am using Double Commander (doublecmd), because krusader hangs very often, and i must kill the app and relaunch it to get it work. I uninstalled it.

i hope this helps.

greetz,
Serg.

Thanks for Double Commander
Regards erngab!

---

### Post by mc4man on 2013-01-09
> **intiyunta said:**
> Hi ppl. This is my first msg, since i am new to linux about a month.

i am running 11.10 
, so i ended creating an icon launcher on my top panel with this command line:

gksudo "gnome-open %u"

but when i drag and drop any icon program from my panel to it, it ask me for a root password but then it open the file.desktop instead of application, and that is what i want.
Sergio
likely the wrong command for 11.10 onwards.
See here (Exec=gksudo "xdg-open %u"
[http://ubuntuforums.org/showpost.php?p=11657989&postcount=86](http://ubuntuforums.org/showpost.php?p=11657989&postcount=86)

---

