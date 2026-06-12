---
title: "Keryx - Need testers!"
date: 2008-08-01
forum: Programming Talk
---

### Post by EXCiD3 on 2008-08-01
So I've been working a lot recently on my open source project Keryx and just released my first alpha version of it (works but only extermely basic functionality at the moment). It basically collects information on your Ubuntu installation then lets you download packages (and soon all the dependencies) with python and a GTK interface that is portable and allows you to download the packages on a computer somewhere else without going into a lot of work writing down all the packages you need. This is especially useful for those of use with dialup and no internet at home. Soon I will be adding package update and dependency checking. I was just looking for a few more souls to burden with beta testing. If you would like to check it out please visit the homepage: [http://keryx.betaserver.org](http://keryx.betaserver.org) and digg it [http://digg.com/tech_news/First_Public_Alpha_release_of_Keryx_in_history](http://digg.com/tech_news/First_Public_Alpha_release_of_Keryx_in_history)

---

### Post by mssever on 2008-08-01
> **EXCiD3 said:**
> So I've been working a lot recently on my open source project Keryx and just released my first alpha version of it (works but only extermely basic functionality at the moment). It basically collects information on your Ubuntu installation then lets you download packages (and soon all the dependencies) with python and a GTK interface that is portable and allows you to download the packages on a computer somewhere else without going into a lot of work writing down all the packages you need. This is especially useful for those of use with dialup and no internet at home. Soon I will be adding package update and dependency checking. I was just looking for a few more souls to burden with beta testing. If you would like to check it out please visit the homepage: [http://keryx.betaserver.org](http://keryx.betaserver.org) and digg it [http://digg.com/tech_news/First_Public_Alpha_release_of_Keryx_in_history](http://digg.com/tech_news/First_Public_Alpha_release_of_Keryx_in_history)
In your tutorial, you say that Keryx won't work on Kubuntu. I don't run that distro, but I think your statement is incorrect. There's just an additional dependency: python-gtk2. (If you used Gnome-specific stuff, you'll need to add that to the list of dependencies, as well.)

---

### Post by EXCiD3 on 2008-08-01
Everything is pure PyGTK, no gnome dependencies. What i really meant was that a straight Kubuntu install (without anything being installed) would NOT work. Kubuntu's apps dont have any GTK interfaces and therefore for a fresh install of Kubuntu you would not have the dependencies, but you could however download them, install them and then use Keryx. I will be making a Qt interface that will be compatible with a Kubuntu fresh install without requiring any other dependencies. Thanks for pointing that out! Hope that clears it up a bit!

---

### Post by jb1229d on 2009-03-20
I just wanted to say. I have tried this program and as a dial up user with access to high speed elsewhere (Windows) this program is great. Solved all my very slow update problems. The only thing I needed to do was add a windows dll file to the WIN32 folder. The file was "gdiplus.dll.

---

### Post by EXCiD3 on 2009-03-21
What windows version were you running on? I have not tested it on anything newer than XP. There was already a missing DLL from XP that I have included. If you could let me know the exact filename I would be happy to include it in the download so nobody has any problems like that.

---

