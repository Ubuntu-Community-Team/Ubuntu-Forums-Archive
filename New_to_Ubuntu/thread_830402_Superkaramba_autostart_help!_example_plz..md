---
title: "Superkaramba autostart help! example plz."
date: 2008-06-15
forum: New to Ubuntu
---

### Post by mashimaro on 2008-06-15
Hi, I'm trying to configure superkaramba to autostart with widgets when kubuntu starts up. I'm trying to follow these instructions:
[http://docs.kde.org/kde3/en/kdeutils/superkaramba/superkaramba.pdf](http://docs.kde.org/kde3/en/kdeutils/superkaramba/superkaramba.pdf)

If you scroll down you'll see the question:

"How do I set up my themes to automatically run at startup?"

As an answer it contains:
> [ Desktop Entry ]
Exec = superkaramba { location of theme file }. theme
Name ={ theme name }
Type = Application
X -KDE - StartupNotify = false

Can anyone give me an example with the parameters filled in the given format?

Thanks!

---

### Post by Farmer of Bricks on 2009-01-03
What theme/widget do you want to run? For a theme/widget "liquid_weather", saved to file:///home/USER/lwp-15.0/liquid_weather.theme
```

[ Desktop Entry ]
Exec = superkaramba file:///home/USER/lwp-15.0/liquid_weather.theme
Name =Liquid Weather
Type = Application
X -KDE - StartupNotify = false

```

Of course, you'll have to replace the name variable and the filepath with those for your file, and then save the file as Name.desktop to file:///home/user/.kde/Autostart/

---

