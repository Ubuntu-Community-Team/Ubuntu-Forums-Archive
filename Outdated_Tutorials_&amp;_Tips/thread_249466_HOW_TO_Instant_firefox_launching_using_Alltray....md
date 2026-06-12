---
title: "HOW TO: Instant firefox launching using Alltray..."
date: 2006-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by JimmyJazz on 2006-09-02
If you are like me you use firefox alot through out the day and are constently opening and closing it
either to save on desktop clutter or just out of habit, with this how to you will be able to launch and instant firefox window simply by pressing F12 or if you launch firefox thru a menu option it will open much faster.
What we will be doing is using alltray to launch a firefox session at the beginning of our gnome session and hiding it in the background only to show it when one presses F12.

**First off you need Alltray...**

```
sudo gedit /etc/apt/sources.list
```

add...

```
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

```
to the sources list

```
sudo apt-get update
sudo apt-get install alltray
```

-------------------------------------------------------------------------------------------------

now we install our custom firefox script...

```
wget http://jimmyjazz.homeip.net:808/quick_firefox.tar.gz

tar xfv ./quick_firefox.tar.gz

cd ./quick_firefox/

sudo cp ./firefox-alltray /usr/lib/firefox/firefox-alltray

sudo ln /usr/lib/firefox/firefox-alltray -s /usr/bin/firefox-alltray

```

Now goto System>Preferences>Sessions>Startup Prgrams and add a new entry that launches the command firefox-alltray

[B]Done!

Whenever you need a quick browser you can press F12 to bring one up and press F12 again to hide it.[/B]

---

### Post by DC@DR on 2006-09-03
Thanks, this is useful and handy :)

---

### Post by Bastanteroma on 2006-11-01
Any tips for using this in xfce?

Thanks

---

### Post by haxer on 2006-11-01
why french?

---

