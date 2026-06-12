---
title: "Big Aptitude/Apt problem"
date: 2005-01-25
forum: Repositories &amp; Backports
---

### Post by Drassk on 2005-01-25
I want to install a few programs which outright refuse to install due to unmet dependencies.  The problem is that apt is 'keeping back' like 300 packages and it won't let me update anything to a new version.  So, for example, I can't install Vega Strike because apt refuses to update libpng.

I hear that this can be gotten around by using dist-upgrade, but that wants to delete half of the programs on my system!  I'm using KDE right now which installed fine and if I use dist-upgrade, it will delete all my KDE files and a bunch of other stuff I installed.  Isn't there some better way?

---

### Post by Mumra on 2005-02-06
I have a similar problem here - I'm using the Universe repositories, but all I get is the vegastrike data and music packages, not the program itself. It appears to be in the main Debian repository - is this addable to the Apt list in Ubuntu?

---

### Post by Drassk on 2005-02-06
You can add the Debian repositories just by editing /etc/apt/sources.list , although they're not supported so they might break Ubuntu somehow.  

I ended up getting so annoyed with the aforementioned problem of 'apt-lock' that I just switched to Debian.  I might give Ubuntu another shot when they've had enough time to get things like that sorted out.

---

